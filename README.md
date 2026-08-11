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
}

header {
  background: linear-gradient(135deg, #1b5e20, #388e3c);
  color: white;
  padding: 28px 20px;
  text-align: center;
  border-radius: 0 0 25px 25px;
}

header h1 {
  margin: 0;
  font-size: 28px;
}

.container {
  max-width: 700px;
  margin: auto;
  padding: 18px;
}

.search {
  width: 100%;
  padding: 15px;
  border: none;
  border-radius: 12px;
  margin-bottom: 20px;
  font-size: 16px;
  box-shadow: 0 2px 8px rgba(0,0,0,.12);
}

.card {
  background: white;
  padding: 20px;
  margin-bottom: 18px;
  border-radius: 18px;
  box-shadow: 0 3px 12px rgba(0,0,0,.08);
}

.card h2 {
  color: #1b5e20;
}

.books {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}

.book {
  background: #e8f5e9;
  border: none;
  color: #1b5e20;
  padding: 14px 8px;
  border-radius: 10px;
  font-weight: bold;
  font-size: 15px;
}

.book:hover {
  background: #c8e6c9;
}

#bookMessage {
  display: none;
  margin-top: 18px;
  padding: 15px;
  background: #e8f5e9;
  border-radius: 10px;
}

footer {
  text-align: center;
  padding: 25px;
  color: #777;
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
  id="search"
  type="text"
  placeholder="🔍 Search for a Bible book..."
  onkeyup="searchBooks()"
>

<div class="card">
  <h2>📜 Today's Bible Verse</h2>

  <p>
    “Trust in the LORD with all thine heart; and lean not unto thine own
    understanding.”
  </p>

  <strong>Proverbs 3:5</strong>
</div>

<div class="card">
  <h2>📚 Old Testament</h2>

  <div class="books" id="oldTestament">

    <button class="book" onclick="openBook('Genesis')">Genesis</button>
    <button class="book" onclick="openBook('Exodus')">Exodus</button>
    <button class="book" onclick="openBook('Leviticus')">Leviticus</button>
    <button class="book" onclick="openBook('Numbers')">Numbers</button>
    <button class="book" onclick="openBook('Deuteronomy')">Deuteronomy</button>
    <button class="book" onclick="openBook('Joshua')">Joshua</button>
    <button class="book" onclick="openBook('Judges')">Judges</button>
    <button class="book" onclick="openBook('Ruth')">Ruth</button>
    <button class="book" onclick="openBook('1 Samuel')">1 Samuel</button>
    <button class="book" onclick="openBook('2 Samuel')">2 Samuel</button>
    <button class="book" onclick="openBook('1 Kings')">1 Kings</button>
    <button class="book" onclick="openBook('2 Kings')">2 Kings</button>
    <button class="book" onclick="openBook('1 Chronicles')">1 Chronicles</button>
    <button class="book" onclick="openBook('2 Chronicles')">2 Chronicles</button>
    <button class="book" onclick="openBook('Ezra')">Ezra</button>
    <button class="book" onclick="openBook('Nehemiah')">Nehemiah</button>
    <button class="book" onclick="openBook('Esther')">Esther</button>
    <button class="book" onclick="openBook('Job')">Job</button>
    <button class="book" onclick="openBook('Psalms')">Psalms</button>
    <button class="book" onclick="openBook('Proverbs')">Proverbs</button>
    <button class="book" onclick="openBook('Ecclesiastes')">Ecclesiastes</button>
    <button class="book" onclick="openBook('Song of Solomon')">Song of Solomon</button>
    <button class="book" onclick="openBook('Isaiah')">Isaiah</button>
    <button class="book" onclick="openBook('Jeremiah')">Jeremiah</button>
    <button class="book" onclick="openBook('Lamentations')">Lamentations</button>
    <button class="book" onclick="openBook('Ezekiel')">Ezekiel</button>
    <button class="book" onclick="openBook('Daniel')">Daniel</button>
    <button class="book" onclick="openBook('Hosea')">Hosea</button>
    <button class="book" onclick="openBook('Joel')">Joel</button>
    <button class="book" onclick="openBook('Amos')">Amos</button>
    <button class="book" onclick="openBook('Obadiah')">Obadiah</button>
    <button class="book" onclick="openBook('Jonah')">Jonah</button>
    <button class="book" onclick="openBook('Micah')">Micah</button>
    <button class="book" onclick="openBook('Nahum')">Nahum</button>
    <button class="book" onclick="openBook('Habakkuk')">Habakkuk</button>
    <button class="book" onclick="openBook('Zephaniah')">Zephaniah</button>
    <button class="book" onclick="openBook('Haggai')">Haggai</button>
    <button class="book" onclick="openBook('Zechariah')">Zechariah</button>
    <button class="book" onclick="openBook('Malachi')">Malachi</button>

  </div>
</div>

<div class="card">
  <h2>✝️ New Testament</h2>

  <div class="books" id="newTestament">

    <button class="book" onclick="openBook('Matthew')">Matthew</button>
    <button class="book" onclick="openBook('Mark')">Mark</button>
    <button class="book" onclick="openBook('Luke')">Luke</button>
    <button class="book" onclick="openBook('John')">John</button>
    <button class="book" onclick="openBook('Acts')">Acts</button>
    <button class="book" onclick="openBook('Romans')">Romans</button>
    <button class="book" onclick="openBook('1 Corinthians')">1 Corinthians</button>
    <button class="book" onclick="openBook('2 Corinthians')">2 Corinthians</button>
    <button class="book" onclick="openBook('Galatians')">Galatians</button>
    <button class="book" onclick="openBook('Ephesians')">Ephesians</button>
    <button class="book" onclick="openBook('Philippians')">Philippians</button>
    <button class="book" onclick="openBook('Colossians')">Colossians</button>
    <button class="book" onclick="openBook('1 Thessalonians')">1 Thessalonians</button>
    <button class="book" onclick="openBook('2 Thessalonians')">2 Thessalonians</button>
    <button class="book" onclick="openBook('1 Timothy')">1 Timothy</button>
    <button class="book" onclick="openBook('2 Timothy')">2 Timothy</button>
    <button class="book" onclick="openBook('Titus')">Titus</button>
    <button class="book" onclick="openBook('Philemon')">Philemon</button>
    <button class="book" onclick="openBook('Hebrews')">Hebrews</button>
    <button class="book" onclick="openBook('James')">James</button>
    <button class="book" onclick="openBook('1 Peter')">1 Peter</button>
    <button class="book" onclick="openBook('2 Peter')">2 Peter</button>
    <button class="book" onclick="openBook('1 John')">1 John</button>
    <button class="book" onclick="openBook('2 John')">2 John</button>
    <button class="book" onclick="openBook('3 John')">3 John</button>
    <button class="book" onclick="openBook('Jude')">Jude</button>
    <button class="book" onclick="openBook('Revelation')">Revelation</button>

  </div>

  <div id="bookMessage"></div>

</div>

<div class="card">
  <h2>🙏 Prayer</h2>

  <p>
    Lord, help me to understand Your Word, grow in faith,
    and live according to Your will. Amen.
  </p>
</div>

</div>

<footer>
  © 2026 Bible Study App
</footer>

<script>

function openBook(book) {

  const message = document.getElementById("bookMessage");

  message.innerHTML =
    "<strong>📖 " + book + "</strong><br><br>" +
    "You selected " + book + ".<br>" +
    "The chapter and verse reader will be added next. 🙏";

  message.style.display = "block";
}

function searchBooks() {

  const search =
    document.getElementById("search").value.toLowerCase();

  const books =
    document.querySelectorAll(".book");

  books.forEach(function(book) {

    const name =
      book.textContent.toLowerCase();

    if (name.includes(search)) {
      book.style.display = "block";
    } else {
      book.style.display = "none";
    }

  });
}

</script>

</body>

</html>

