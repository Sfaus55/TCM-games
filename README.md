# TCM-games
Games to help study TCM material for those currently in a TCM program
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
  </section>

</body>
</html>
