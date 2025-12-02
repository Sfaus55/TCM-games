<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Study & Play Hub</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f4f4f4;
    }
    header {
      background: #222;
      color: white;
      padding: 20px;
      text-align: center;
      font-size: 2rem;
    }
    nav {
      background: #444;
      padding: 10px;
      display: flex;
      justify-content: center;
      gap: 20px;
    }
    nav a {
      color: white;
      text-decoration: none;
      font-weight: bold;
    }
    .section {
      padding: 30px;
      max-width: 1000px;
      margin: auto;
    }
    .materials, .games {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 20px;
    }
    .card {
      background: white;
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }
    iframe {
      width: 100%;
      height: 300px;
      border-radius: 10px;
      border: none;
    }
  </style>
</head>
<body>
  <header>Study & Play Hub</header>

  <nav>
    <a href="#materials">Study Materials</a>
    <a href="#games">Study Games</a>
  </nav>

  <section id="materials" class="section">
    <h2>Study Materials</h2>
    <p>Store PDFs, links, flashcards, charts, and videos here.</p>
    <div class="materials">
      <div class="card">
        <h3>Acupuncture Point Chart</h3>
        <p>Downloadable PDF or reference image.</p>
      </div>
      <div class="card">
        <h3>TCM Notes</h3>
        <p>Upload class notes, summaries, and study guides.</p>
      </div>
      <div class="card">
        <h3>Quizlet Sets</h3>
        <p>Embed or link your flashcard sets.</p>
      </div>
    </div>
  </section>

  <section id="games" class="section">
    <h2>Study Games</h2>
    <p>Fun games to help memorize TCM points, channels, and functions.</p>
    <div class="games">
      <div class="card">
        <h3>Flashcard Game</h3>
        <iframe src="https://quizlet.com/latest"></iframe>
      </div>
      <div class="card">
        <h3>Memory Match</h3>
        <iframe src="https://www.memozor.com/memory-games"></iframe>
      </div>
      <div class="card">
        <h3>Snake Break</h3>
        <iframe src="https://playsnake.org/"></iframe>
      </div>
    </div>
    <script>
    // Simple localStorage-based material adder
    function addMaterial() {
      const title = document.getElementById('matTitle').value.trim();
      const link = document.getElementById('matLink').value.trim();
      if (!title || !link) return alert('Please enter both a title and a link.');

      const materials = JSON.parse(localStorage.getItem('materials') || '[]');
      materials.push({ title, link });
      localStorage.setItem('materials', JSON.stringify(materials));
      renderMaterials();
      document.getElementById('matTitle').value = '';
      document.getElementById('matLink').value = '';
    }

    function renderMaterials() {
      const container = document.getElementById('user-materials');
      const materials = JSON.parse(localStorage.getItem('materials') || '[]');
      container.innerHTML = '';
      materials.forEach(m => {
        const div = document.createElement('div');
        div.className = 'card';
        div.innerHTML = `<h3>${m.title}</h3><a href="${m.link}" target="_blank">Open Material</a>`;
        container.appendChild(div);
      });
    }

    window.onload = renderMaterials;
  </script>

  <section id="tcm-game" class="section">
    <h2>TCM Point Matching Game</h2>
    <p>Match the acupuncture point to its correct function!</p>

    <div class="card" id="game-area" style="text-align:center;">
      <h3 id="game-question">Loading...</h3>
      <div id="game-options" style="margin-top:20px;"></div>
      <p id="game-feedback" style="font-weight:bold; margin-top:15px;"></p>
      <button onclick="nextQuestion()" style="margin-top:20px; padding:10px 20px; border:none; background:#222; color:white; border-radius:8px; cursor:pointer;">Next</button>
    </div>
  </section>

  <script>
    const tcmData = [
      { point: 'LU 5', fx: 'Clears heat, descends rebellious Qi' },
      { point: 'LI 4', fx: 'Releases exterior, regulates face' },
      { point: 'ST 36', fx: 'Tonifies Qi and blood, harmonizes ST' },
      { point: 'LU 1', fx: 'Clears LU heat, stops cough' },
      { point: 'LI 10', fx: 'Harmonizes ST & intestines' }
    ];

    let current = {};

    function nextQuestion() {
      const q = tcmData[Math.floor(Math.random() * tcmData.length)];
      current = q;
      document.getElementById('game-question').textContent = `What is the function of ${q.point}?`;

      const options = shuffle(tcmData.map(i => i.fx));
      const container = document.getElementById('game-options');
      container.innerHTML = '';

      options.forEach(op => {
        const btn = document.createElement('button');
        btn.textContent = op;
        btn.style.display = 'block';
        btn.style.margin = '10px auto';
        btn.style.padding = '10px';
        btn.style.width = '80%';
        btn.style.border = '1px solid #333';
        btn.style.borderRadius = '8px';
        btn.style.cursor = 'pointer';
        btn.onclick = () => checkAnswer(op);
        container.appendChild(btn);
      });

      document.getElementById('game-feedback').textContent = '';
    }

    function checkAnswer(ans) {
      const feedback = document.getElementById('game-feedback');
      if (ans === current.fx) {
        feedback.textContent = 'Correct! 🎉';
        feedback.style.color = 'green';
      } else {
        feedback.textContent = 'Wrong ❌ Try again!';
        feedback.style.color = 'red';
      }
    }

    function shuffle(arr) {
      return arr.sort(() => Math.random() - 0.5);
    }

    nextQuestion();
  </script>

</section>
</body>
</html>
