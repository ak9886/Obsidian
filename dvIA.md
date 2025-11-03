---
updated_at: 2025-11-03T22:36:12.867+05:30
edited_seconds: 10
---
```dataviewjs
const questions = [
  {
    q: "Which of the following best describes the property of a Binary Search Tree?",
    options: [
      "A. Every node must have zero or two children.",
      "B. Height of subtrees differ by at most one.",
      "C. Left < Root < Right.",
      "D. All levels filled except last."
    ],
    answer: "C. Left < Root < Right."
  },
  {
    q: "What is the purpose of chaining in hashing?",
    options: [
      "A. Handle collisions.",
      "B. Rehash keys.",
      "C. Resize the table.",
      "D. Ensure unique hashes."
    ],
    answer: "A. Handle collisions."
  }
];

// shuffle in place
for (let i = questions.length - 1; i > 0; i--) {
  const j = Math.floor(Math.random() * (i + 1));
  [questions[i], questions[j]] = [questions[j], questions[i]];
}

for (let q of questions) {
  dv.el("div", `
  <div class="question">
    <h3>${q.q}</h3>
    <ul>${q.options.map(o => `<li>${o}</li>`).join("")}</ul>
    <button onclick="this.nextElementSibling.style.display =
      this.nextElementSibling.style.display==='none'?'block':'none'">
      Show/Hide Answer
    </button>
    <div class="answer" style="display:none;">Answer: ${q.answer}</div>
  </div>
  `);
}
```
