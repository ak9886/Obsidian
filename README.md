# 📲 Sync Obsidian Notes with GitHub (Phone + PC)

## 🧰 Tools Required
- **Obsidian** on both PC and phone
- **GitHub account**
- **Git client for PC** (e.g., Git CLI, GitHub Desktop)
- **Git client for mobile** (e.g., [Working Copy](https://apps.apple.com/app/working-copy-git-client/id896694807) for iOS, [MGit](https://play.google.com/store/apps/details?id=com.manichord.mgit) or [Termux + Git](https://f-droid.org/packages/com.termux/) for Android)

---

## 🗂 Folder Setup

1. Create a **private GitHub repo** named something like `obsidian-notes`.
2. On your **PC**:
   - Clone the repo locally:
     ```bash
     git clone https://github.com/your-username/obsidian-notes.git
     ```
   - Open the cloned folder as your **vault** in Obsidian.
   - Add `.obsidian/` to `.gitignore` (optional, prevents syncing workspace configs):
     ```
     .obsidian/
     ```

---

## 🔁 Workflow (PC)

1. **Add or edit notes** in Obsidian.
2. **Push changes to GitHub**:
   ```bash
   git add .
   git commit -m "Update notes"
   git push origin main
