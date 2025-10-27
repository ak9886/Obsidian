---
updated_at: 2025-10-27T10:38:12.037+05:30
edited_seconds: 10
---
`markdown
# **ChatApp Using JDBC**  
**Project Report**

---

<center>
**ChatApp Using JDBC**  
<br>
**Students:**  
SHRAVAN ADITYAN J — RA2411030010436  
ADARSH KOSHY — RA2411030010400  
SHARANABDHI VINODH — RA2411030010406  
DHEERAJ KUMAR — RA2411030010395  
<br>
**Course:** B.E. / B.Tech — [Specify]  
**Guide:** [Guide Name]  
**Semester:** [Specify Semester]  
**Institution:** [Your Institution], Chennai  
**Submission Date:** [Enter Date]  
</center>

---

## Abstract  
This project implements a simple, robust ChatApp built with Java on the backend using JDBC to connect to a MySQL database. The system allows registered users to authenticate, create one-to-one chat sessions, persist messages, and view chat history. The design emphasizes reliable database connectivity, ACID-safe message storage, and a minimal web front-end (Servlet + JSP) for usability. Implementation demonstrates schema design (users, chats, messages), JDBC connection pooling, prepared statements to prevent SQL injection, and simple message-fetching APIs. Primary results include a working prototype that supports concurrent users on a single MySQL instance and persistent message history accessible from Chennai/local deployments.  

**Keywords:** ChatApp, JDBC, MySQL, Java, Message Persistence

---

# Page 2 — Problem Statement, Objectives, Scope

## 1. Introduction / Background  
Chat applications are essential for real-time communication in modern apps. Many chat systems rely on frameworks or external real-time services; this project demonstrates how to build a basic, maintainable ChatApp using plain Java + JDBC + MySQL, suitable for learning core concepts: database modelling, connection handling, and simple web front-end integration. The system targets small groups or educational deployments (e.g., labs in Chennai).

## 2. Problem Statement  
Existing simple chat demos often bypass persistent storage or use specialized messaging servers. The problem: demonstrate a clear, JDBC-based design for reliable message persistence and retrieval without external messaging brokers.

## 3. Objectives  
- Implement user registration and login backed by MySQL using JDBC.  
- Persist one-to-one messages with timestamps and sender/receiver metadata.  
- Provide a web UI (Servlet + JSP) to send/receive messages and view history.  
- Use prepared statements and connection pooling to ensure performance and security.  
- Demonstrate basic concurrency handling for multiple clients.

## 4. Scope & Limitations  
- Scope: one-to-one chats, user authentication, message persistence, basic UI.  
- Limitations: no multimedia (images/video) support, no push notifications (polling-based refresh), not horizontally distributed (single MySQL instance), no end-to-end encryption.  
- Deployment scope: suitable for a lab server in Chennai or local machine.  
- Performance: intended for small user counts; scaling requires architectural changes.

## 5. Use Case Diagram  
```mermaid
%% Use Case: ChatApp (simple)
%% Render with a Mermaid-capable viewer
actor User
User --> (Register / Login)
User --> (Start Chat)
User --> (Send Message)
User --> (View Chat History)
(User) --> (Logout)
````

---

# Page 3 — Tools, Design & Data Model

## 6. Technology Stack

- Java 11 (or 17)
    
- Maven (build)
    
- MySQL 8.x
    
- JDBC (java.sql + HikariCP for pooling)
    
- Servlet API + JSP (simple web UI) or optional JavaFX for desktop client
    
- IntelliJ IDEA (development)
    
- OS / Deployment: Ubuntu / Windows / local server in Chennai
    

## 7. System Architecture (short paragraph + diagram)

The system uses a three-tier architecture: Web UI (Servlet/JSP) → Java backend (servlets / controllers, service layer) → MySQL via JDBC. The backend layer manages JDBC connections via a pool, performs CRUD on user and message tables, and exposes endpoints that the UI calls (forms / AJAX polling). This keeps the UI thin and the business logic centralized.

**Architecture (text diagram):**

```
[Browser UI (JSP/HTML/JS)] <--HTTP--> [Servlet Controller / Service Layer (Java)] <--JDBC--> [MySQL Database]
```

## 8. Data Model / Key Tables / Inputs & Outputs

**Key tables:**

|Table|Columns (primary columns shown)|Purpose|
|---|--:|---|
|`users`|`id` (INT PK), `username` (VARCHAR), `password_hash` (VARCHAR), `created_at` (DATETIME)|Store registered users|
|`chats`|`id` (INT PK), `user1_id` (INT FK), `user2_id` (INT FK), `created_at` (DATETIME)|One-to-one chat sessions|
|`messages`|`id` (BIGINT PK), `chat_id` (INT FK), `sender_id` (INT FK), `text` (TEXT), `sent_at` (DATETIME)|Persisted messages|

**Inputs:** user credentials, message text, chat selection.  
**Outputs:** chat message list, status responses (OK / error).

---

# Page 4 — 5 Step-by-Step Worked Procedure

> **Note:** image placeholders are included — replace with actual screenshots captured from your local deployment (recommended resolution: 1280×720). For each step, sample SQL and JDBC code are provided.

---

## Step 1 — Database Setup (SQL commands + description)

**SQL schema (run in MySQL):**

```sql
-- Create database
CREATE DATABASE chatapp CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
USE chatapp;

-- Users table
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(100) NOT NULL UNIQUE,
  password_hash VARCHAR(255) NOT NULL,
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);

-- Chats table (one-to-one chat)
CREATE TABLE chats (
  id INT AUTO_INCREMENT PRIMARY KEY,
  user1_id INT NOT NULL,
  user2_id INT NOT NULL,
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  CONSTRAINT fk_chat_user1 FOREIGN KEY (user1_id) REFERENCES users(id),
  CONSTRAINT fk_chat_user2 FOREIGN KEY (user2_id) REFERENCES users(id)
);

-- Messages
CREATE TABLE messages (
  id BIGINT AUTO_INCREMENT PRIMARY KEY,
  chat_id INT NOT NULL,
  sender_id INT NOT NULL,
  text TEXT NOT NULL,
  sent_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  CONSTRAINT fk_msg_chat FOREIGN KEY (chat_id) REFERENCES chats(id),
  CONSTRAINT fk_msg_sender FOREIGN KEY (sender_id) REFERENCES users(id),
  INDEX idx_chat_sent_at (chat_id, sent_at)
);
```

**Image (placeholder):**  
`![DB Schema](./images/db_schema.png)`

---

## Step 2 — JDBC Connectivity Setup (JDBC code + explanation)

**pom.xml dependency (Maven):**

```xml
<!-- Add in your pom.xml -->
<dependencies>
  <dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.33</version>
  </dependency>
  <dependency>
    <groupId>com.zaxxer</groupId>
    <artifactId>HikariCP</artifactId>
    <version>5.0.1</version>
  </dependency>
</dependencies>
```

**Connection pool setup (HikariCP example):**

```java
// DBConfig.java
import com.zaxxer.hikari.HikariConfig;
import com.zaxxer.hikari.HikariDataSource;
import javax.sql.DataSource;

public class DBConfig {
    private static HikariDataSource ds;

    static {
        HikariConfig config = new HikariConfig();
        config.setJdbcUrl("jdbc:mysql://localhost:3306/chatapp?serverTimezone=UTC");
        config.setUsername("chatuser");
        config.setPassword("chatpass");
        config.setMaximumPoolSize(10);
        config.addDataSourceProperty("cachePrepStmts","true");
        config.addDataSourceProperty("prepStmtCacheSize","250");
        config.addDataSourceProperty("prepStmtCacheSqlLimit","2048");
        ds = new HikariDataSource(config);
    }

    public static DataSource getDataSource() {
        return ds;
    }
}
```

**Image (placeholder):**  
`![JDBC Connection Setup](./images/jdbc_setup.png)`

---

## Step 3 — Backend: DAO & Prepared Statements (examples)

**UserDAO: register & findByUsername**

```java
// UserDao.java (snippets)
import java.sql.*;
import javax.sql.DataSource;

public class UserDao {
    private final DataSource ds;
    public UserDao(DataSource ds) { this.ds = ds; }

    public int registerUser(String username, String passwordHash) throws SQLException {
        String sql = "INSERT INTO users (username, password_hash) VALUES (?, ?)";
        try (Connection c = ds.getConnection();
             PreparedStatement ps = c.prepareStatement(sql, Statement.RETURN_GENERATED_KEYS)) {
            ps.setString(1, username);
            ps.setString(2, passwordHash);
            ps.executeUpdate();
            try (ResultSet rs = ps.getGeneratedKeys()) {
                if (rs.next()) return rs.getInt(1);
            }
        }
        return -1;
    }

    public User findByUsername(String username) throws SQLException {
        String sql = "SELECT id, username, password_hash FROM users WHERE username = ?";
        try (Connection c = ds.getConnection();
             PreparedStatement ps = c.prepareStatement(sql)) {
            ps.setString(1, username);
            try (ResultSet rs = ps.executeQuery()) {
                if (rs.next()) {
                    return new User(rs.getInt("id"), rs.getString("username"), rs.getString("password_hash"));
                }
            }
        }
        return null;
    }
}
```

**Image (placeholder):**  
`![DAO Code Screenshot](./images/dao_code.png)`

---

## Step 4 — Message flow: Create chat & store message (JDBC + SQL)

**Create or fetch chat (ensure unique pair):**

```sql
-- Pseudocode SQL logic (illustrative)
SELECT id FROM chats WHERE (user1_id = ? AND user2_id = ?) OR (user1_id = ? AND user2_id = ?);
-- If not exists, INSERT INTO chats (user1_id, user2_id) VALUES (?, ?);
```

**Insert message (Java snippet):**

```java
public long saveMessage(int chatId, int senderId, String text) throws SQLException {
    String sql = "INSERT INTO messages (chat_id, sender_id, text) VALUES (?, ?, ?)";
    try (Connection c = ds.getConnection();
         PreparedStatement ps = c.prepareStatement(sql, Statement.RETURN_GENERATED_KEYS)) {
        ps.setInt(1, chatId);
        ps.setInt(2, senderId);
        ps.setString(3, text);
        ps.executeUpdate();
        try (ResultSet rs = ps.getGeneratedKeys()) {
            if (rs.next()) return rs.getLong(1);
        }
    }
    return -1;
}
```

**Image (placeholder):**  
`![Send Message Flow](./images/send_message.png)`

---

## Step 5 — Front-end & Polling (Servlet + JSP + AJAX pattern)

**Front-end flow (step-by-step):**

1. **Login Page (JSP)** — user logs in (POST to `/login`).  
    `![Login Screenshot](./images/login_screen.png)`
    
2. **User List / Chat Selection** — show list of contacts (AJAX GET `/users`).  
    `![User List](./images/users_list.png)`
    
3. **Chat Window** — load messages for chat via AJAX (`GET /chat/{chatId}/messages?since=...`) and display.  
    `![Chat Window](./images/chat_window.png)`
    
4. **Send Message** — POST to `/chat/{chatId}/messages` with JSON payload; backend saves via JDBC and returns status + message metadata. Front-end appends message to conversation.
    
5. **Polling or Long-Poll** — front-end polls every 2–3 seconds or implements long-poll to fetch new messages. (For production, use WebSocket; outside current scope.)
    

**Sample AJAX (fetch new messages):**

```javascript
// pollMessages.js (simple polling)
setInterval(async () => {
  const res = await fetch(`/chat/${chatId}/messages?after=${lastTimestamp}`);
  if (res.ok) {
    const msgs = await res.json();
    // append msgs to UI and update lastTimestamp
  }
}, 2500);
```

**Image (placeholder):**  
`![AJAX Polling](./images/polling.png)`

---

## Extra: Security & Best Practices (brief)

- Use bcrypt or Argon2 for password hashing (never store plain text).
    
- Use prepared statements (shown) to avoid SQL injection.
    
- Use HTTPS for transport in deployed setups.
    
- Limit polling frequency; consider WebSocket for production.
    
- Apply connection pooling (HikariCP used) for performance.
    

---

## Deliverables (what to submit)

- Project report (this Markdown)
    
- Source code (Maven project)
    
- SQL schema file (`schema.sql`)
    
- Readme with environment setup (MySQL user, DB creation)
    
- Screenshots folder (`/images`) with front-end and DB screenshots (capture from local Chennai lab server or development machine)
    

---

## Check

Spelling, grammar, and logical consistency reviewed. Replace placeholders (`[Guide Name]`, `[Specify]`, images and submission date) with project-specific values before final submission.

---

**Q1:** **Do you want the front-end implemented as Servlet+JSP (web) or as a JavaFX desktop client?**  
**Q2:** **Should I include full code for login, chat servlet, and message DAO in the report, or only key excerpts as above?**  
**Q3:** **Do you want a sample `docker-compose.yml` to run MySQL and the ChatApp locally (Chennai lab friendly)?**