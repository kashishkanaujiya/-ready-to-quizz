# h<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Quick Quiz</title>
  <style>
    body { font-family: sans-serif; display: grid; place-items: center; min-height: 90vh; background: #f4f6f8; }
    .card { background: white; padding: 24px; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.08); width: 340px; }
    .btn { display: block; width: 100%; margin: 8px 0; padding: 10px; border: 1px solid #ddd; border-radius: 6px; cursor: pointer; text-align: left; }
    .btn:hover { background: #eef2ff; border-color: #6366f1; }
  </style>
</head>
<body>
  <div class="card" id="quiz-box">
    <h3 id="question-text">Loading...</h3>
    <div id="options-container"></div>
  </div>

  <script>
    const questions = [
      { q: "What does HTML stand for?", options: ["Hyper Text Markup Language", "High Tech Modern Language", "Hyperlink Text Mode Layout"], answer: 0 },
      { q: "Which language runs in the browser?", options: ["Java", "C++", "JavaScript"], answer: 2 }
    ];

    let current = 0;
    let score = 0;

    function renderQuestion() {
      if (current >= questions.length) {
        document.getElementById("quiz-box").innerHTML = `<h3>Quiz Finished!</h3><p>Your score: ${score} / ${questions.length}</p>`;
        return;
      }
      const item = questions[current];
      document.getElementById("question-text").innerText = item.q;
      const container = document.getElementById("options-container");
      container.innerHTML = "";

      item.options.forEach((opt, idx) => {
        const btn = document.createElement("button");
        btn.className = "btn";
        btn.innerText = opt;
        btn.onclick = () => {
          if (idx === item.answer) score++;
          current++;
          renderQuestion();
        };
        container.appendChild(btn);
      });
    }

    renderQuestion();
  </script>
</body>
</html>ttps://<your-username>.github.io/my-quiz/
