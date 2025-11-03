---
updated_at: 2025-11-03T22:28:51.789+05:30
edited_seconds: 50
---
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>DSA Quiz</title>
<style>
body {
  font-family: "Inter", sans-serif;
  background: #1e1e1e;
  color: #e0e0e0;
  line-height: 1.6;
  padding: 2rem;
}
.question {
  background: #2b2b2b;
  border-radius: 1rem;
  margin: 1rem 0;
  padding: 1rem 1.5rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.4);
}
button {
  background: #0078d7;
  border: none;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  cursor: pointer;
  margin-top: 0.5rem;
}
button:hover {
  background: #005fa3;
}
.answer {
  display: none;
  margin-top: 0.8rem;
  background: #333;
  padding: 0.8rem;
  border-radius: 0.5rem;
}
</style>
</head>
<body>

<h1>DSA Quiz</h1>

<div class="question">
  <h3>1. What is the time complexity of binary search?</h3>
  <ul>
    <li>A. O(n)</li>
    <li>B. O(log n)</li>
    <li>C. O(n log n)</li>
    <li>D. O(1)</li>
  </ul>
  <button onclick="toggleAnswer(this)">Show Answer</button>
  <div class="answer">Answer: B. O(log n)</div>
</div>

<div class="question">
  <h3>2. What data structure is used in recursion?</h3>
  <ul>
    <li>A. Queue</li>
    <li>B. Stack</li>
    <li>C. Linked List</li>
    <li>D. Tree</li>
  </ul>
  <button onclick="toggleAnswer(this)">Show Answer</button>
  <div class="answer">Answer: B. Stack</div>
</div>

<script>
function toggleAnswer(button) {
  const answer = button.nextElementSibling;
  const isHidden = answer.style.display === "none" || answer.style.display === "";
  answer.style.display = isHidden ? "block" : "none";
  button.textContent = isHidden ? "Hide Answer" : "Show Answer";
}
</script>

</body>
</html>
```
