<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bible Study App</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f4f7f5;
  color: #222;
  transition: 0.3s;
}

body.dark {
  background: #121212;
  color: #eee;
}

header {
  background: linear-gradient(135deg, #1b5e20, #388e3c);
  color: white;
  padding: 28px 20px;
  border-radius: 0 0 25px 25px;
}

header h1 {
  margin: 0;
  font-size: 28px;
}

header p {
  margin-bottom: 0;
}

.container {
  max-width: 700px;
  margin: auto;
  padding: 18px;
}

.search {
  width: 100%;
  padding: 14px;
  border: none;
  border-radius: 12px;
  margin-bottom: 18px;
  box-shadow: 0 2px 8px rgba(0,0,0,.12);
}

.card {
  background: white;
  padding: 20px;
  margin-bottom: 16px;
  border-radius: 18px;
  box-shadow: 0 3px 12px rgba(0,0,0,.08);
}

.dark .card {
  background: #1e1e1e;
}

.card h2 {
  color: #1b5e20;
  margin-top: 0;
}

.dark .card h2 {
  color: #81c784;
}

.verse {
  font-size: 19px;
  line-height: 1.6;
  font-style: italic;
}

button {
  background: #1b5e20;
  color: white;
  border: none;
  padding: 12px 17px;
  border-radius: 10px;
  font-size: 15px;
  margin: 5px 3px;
}

button:hover {
  background: #2e7d32;
}

.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

.topic {
  padding: 18px;
  background: #e8f5e9;
  border-radius: 14px;
  text-align: center;
  font-weight: bold;
}

.dark .topic {
  background: #263b29;
}

footer {
  text-align: center;
  padding: 25px;
  color: #777;
}

.dark footer {
  color: #aaa;
}

#message {
  display: none;
  margin-top: 12px;
  padding: 12px;
  background: #e8f5e9;
  border-radius: 10px;
}

.dark #message {
  background: #263b29;
}
</style>
</head>

<body>

<header>
  <h1>📖 Bible Study App</h1>
  <p>Grow in God's Word Every Day</p>
</header>

<div class="container">

  <input
    class="search"
    type="text"
    id="search"
    placeholder="🔍 Search Bible studies..."
    onkeyup="searchStudy()"
  >

  <div class="card">
    <h2>🌅 Today's Bible Verse</h2>

    <p class="verse">
      “Trust in the LORD with all thine heart; and lean not unto thine own
      understanding.”
    </p>

    <strong>Proverbs 3:5</strong>

    <br><br>

    <button onclick="favoriteVerse()">❤️ Favorite</button>
    <button onclick="shareVerse()">📤 Share</button>

    <div id="message"></div>
  </div>

  <div class="card" id="study">
    <h2>📚 Today's Bible Study</h2>

    <h3>Walking in Faith</h3>

    <p>
      Faith means trusting God even when we cannot see the whole picture.
      God's Word teaches us to depend on Him and follow His direction.
    </p>

    <button onclick="startStudy()">Start Bible Study</button>

    <div id="studyMessage"></div>
  </div>

  <div class="card">
    <h2>📖 Bible</h2>

    <div class="grid">
      <div class="topic">Genesis</div>
      <div class="topic">Psalms</div>
      <div class="topic">Proverbs</div>
      <div class="topic">Matthew</div>
      <div class="topic">John</div>
      <div class="topic">Romans</div>
    </div>
  </div>

  <div class="card">
    <h2>🔥 Study Topics</h2>

    <div class="grid">
      <div class="topic">Faith</div>
      <div class="topic">Prayer</div>
      <div class="topic">Obedience</div>
      <div class="topic">Love</div>
      <div class="topic">Wisdom</div>
      <div class="topic">Purpose</div>
    </div>
  </div>

  <div class="card">
    <h2>🙏 Today's Prayer</h2>

    <p>
      Lord, help me to trust You, obey Your Word, and grow stronger in faith
      every day. Give me wisdom to make the right decisions and strength to
      follow Your will. Amen.
    </p>
  </div>

  <div class="card">
    <h2>⚙️ App Settings</h2>

    <button onclick="toggleDarkMode()">🌙 Dark Mode</button>
  </div>

</div>

<footer>
  © 2026 Bible Study App<br>
  Built to help believers grow in God's Word.
</footer>

<script>

function startStudy() {
  document.getElementById("studyMessage").innerHTML =
    "<p><strong>Welcome to your Bible study! 🙏</strong><br>" +
    "Take a few minutes today to read God's Word, meditate on it, " +
    "and put it into practice.</p>";

  document.getElementById("studyMessage").style.display = "block";
}

function favoriteVerse() {
  localStorage.setItem(
    "favoriteVerse",
    "Proverbs 3:5 - Trust in the LORD with all thine heart."
  );

  document.getElementById("message").innerHTML =
    "❤️ Verse added to your favorites!";
  document.getElementById("message").style.display = "block";
}

function shareVerse() {
  const text =
    "Proverbs 3:5 - Trust in the LORD with all thine heart.";

  if (navigator.share) {
    navigator.share({
      title: "Bible Study App",
      text: text
    });
  } else {
    navigator.clipboard.writeText(text);

    document.getElementById("message").innerHTML =
      "📋 Verse copied. You can now share it.";
    document.getElementById("message").style.display = "block";
  }
}

function toggleDarkMode() {
  document.body.classList.toggle("dark");

  if (document.body.classList.contains("dark")) {
    localStorage.setItem("darkMode", "on");
  } else {
    localStorage.setItem("darkMode", "off");
  }
}

function searchStudy() {
  const search = document
    .getElementById("search")
    .value
    .toLowerCase();

  const study = document.getElementById("study");

  if (search === "") {
    study.style.display = "block";
    return;
  }

  if (
    study.innerText.toLowerCase().includes(search)
  ) {
    study.style.display = "block";
  } else {
    study.style.display = "none";
  }
}

if (localStorage.getItem("darkMode") === "on") {
  document.body.classList.add("dark");
}

</script>

</body>
</html>
