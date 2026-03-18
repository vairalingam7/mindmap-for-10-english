<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>English Hub | All Lessons</title>
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;600&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
    <style>
        :root { --bg: #0d1117; --card: #161b22; --accent: #58a6ff; --text: #c9d1d9; --white: #f0f6fc; }
        body { background-color: var(--bg); color: var(--text); font-family: 'Outfit', sans-serif; margin: 0; display: flex; }
        .sidebar { width: 300px; background: var(--card); height: 100vh; position: fixed; border-right: 1px solid #30363d; padding: 20px; box-sizing: border-box; }
        #searchBar { width: 100%; padding: 12px; background: #0d1117; border: 1px solid #30363d; border-radius: 8px; color: white; margin-bottom: 20px; }
        .lesson-link { padding: 10px; color: var(--text); cursor: pointer; border-radius: 6px; margin-bottom: 5px; transition: 0.2s; }
        .lesson-link:hover { background: rgba(88, 166, 255, 0.1); color: var(--accent); }
        .lesson-link.active { background: var(--accent); color: var(--bg); font-weight: bold; }
        .main-content { margin-left: 300px; padding: 40px; width: 100%; }
        h1 { font-family: 'Playfair Display', serif; color: var(--white); font-size: 2.5rem; }
        .grid-8 { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; }
        .box { background: var(--card); border: 1px solid #30363d; padding: 20px; border-radius: 12px; }
        .box h3 { color: var(--accent); margin-top: 0; }
        @media (max-width: 768px) { body { flex-direction: column; } .sidebar { width: 100%; height: auto; position: relative; } .main-content { margin-left: 0; } }
    </style>
</head>
<body>

<div class="sidebar">
    <h2 style="color:white">📖 English Hub</h2>
    <input type="text" id="searchBar" placeholder="Search lessons..." onkeyup="filterLessons()">
    <div id="menu"></div>
</div>

<div class="main-content">
    <div id="display"></div>
</div>

<script>
const lessons = {
    "letter": {
        title: "A Letter to God",
        data: [
            {h:"Lencho", p:"A simple farmer with immense faith in God."},
            {h:"Conflict", p:"A hailstorm destroys his corn field completely."},
            {h:"The Action", p:"Writes a letter to God asking for 100 pesos."},
            {h:"Postmaster", p:"Kind man who collects 70 pesos to help him."},
            {h:"Irony", p:"Lencho calls the post office staff 'crooks'."},
            {h:"Setting", p:"A house on the crest of a low hill."},
            {h:"Faith", p:"The story shows faith can be both powerful and blind."},
            {h:"Moral", p:"One should recognize the kindness of fellow humans."}
        ]
    },
    "midnight": {
        title: "The Midnight Visitor",
        data: [
            {h:"Ausable", p:"A clever spy who doesn't look like a spy at all."},
            {h:"Max", p:"The intruder who gets tricked by a fake balcony."},
            {h:"The Lie", p:"Ausable invents a story about a balcony to trap Max."},
            {h:"The Knock", p:"Claimed to be police, but was just the waiter."},
            {h:"Fowler", p:"A writer who learns that wit beats weapons."},
            {h:"Location", p:"Top floor of a French hotel."},
            {h:"Theme", p:"Presence of mind is the greatest weapon."},
            {h:"Resolution", p:"Max jumps into the void and falls to his end."}
        ]
    },
    "mandela": {
        title: "Nelson Mandela: Freedom",
        data: [
            {h:"Apartheid", p:"System of racial segregation in South Africa."},
            {h:"Inauguration", p:"May 10, 1994, at the Union Buildings."},
            {h:"Courage", p:"Triumph over fear, not the absence of it."},
            {h:"Obligations", p:"Duty to family and duty to the nation."},
            {h:"Freedom", p:"It is indivisible; chains on one are chains on all."},
            {h:"Oppressor", p:"Needs liberation just as much as the oppressed."},
            {h:"Struggle", p:"Won by the sacrifice of thousands of patriots."},
            {h:"Equality", p:"The dream of a non-racial democratic society."}
        ]
    }
};

function filterLessons() {
    let input = document.getElementById('searchBar').value.toLowerCase();
    let links = document.getElementsByClassName('lesson-link');
    for (let link of links) {
        link.style.display = link.innerText.toLowerCase().includes(input) ? "block" : "none";
    }
}

function render(id) {
    const l = lessons[id];
    let html = <h1>${l.title}</h1><div class="grid-8">;
    l.data.forEach(box => { html += <div class="box"><h3>${box.h}</h3><p>${box.p}</p></div>; });
    html += </div>;
    document.getElementById('display').innerHTML = html;
    document.querySelectorAll('.lesson-link').forEach(link => {
        link.classList.toggle('active', link.getAttribute('data-id') === id);
    });
}

const menu = document.getElementById('menu');
Object.keys(lessons).forEach(key => {
    let div = document.createElement('div');
    div.className = 'lesson-link';
    div.innerText = lessons[key].title;
    div.setAttribute('data-id', key);
    div.onclick = () => render(key);
    menu.appendChild(div);
});

render('letter'); // Starts with A Letter to God visible
</script>
</body>
</html>
