<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>English Master Hub | Searchable Mindmaps</title>
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;600&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #0d1117;
            --card: #161b22;
            --accent: #58a6ff;
            --text: #c9d1d9;
            --white: #f0f6fc;
            --sidebar-width: 300px;
        }

        body { background-color: var(--bg); color: var(--text); font-family: 'Outfit', sans-serif; margin: 0; display: flex; }

        /* Sidebar & Search */
        .sidebar {
            width: var(--sidebar-width);
            background: var(--card);
            height: 100vh;
            position: fixed;
            border-right: 1px solid #30363d;
            padding: 20px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
        }

        .search-container { margin-bottom: 20px; }
        #searchBar {
            width: 100%;
            padding: 12px;
            background: #0d1117;
            border: 1px solid #30363d;
            border-radius: 8px;
            color: white;
            box-sizing: border-box;
            outline: none;
        }
        #searchBar:focus { border-color: var(--accent); }

        .sidebar h2 { font-family: 'Playfair Display', serif; color: var(--white); font-size: 1.4rem; margin: 0 0 15px 0; }

        .lesson-link {
            padding: 10px 15px;
            color: var(--text);
            text-decoration: none;
            border-radius: 8px;
            margin-bottom: 5px;
            transition: 0.3s;
            cursor: pointer;
            font-size: 0.9rem;
        }
        .lesson-link:hover { background: rgba(88, 166, 255, 0.1); color: var(--accent); }
        .lesson-link.active { background: var(--accent); color: var(--bg); font-weight: 600; }

        /* Main Content */
        .main-content { margin-left: var(--sidebar-width); padding: 40px; width: 100%; }
        h1 { font-family: 'Playfair Display', serif; font-size: 2.5rem; color: var(--white); margin: 0 0 30px 0; }

        .grid-8 { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; }
        .box { background: var(--card); border: 1px solid #30363d; padding: 20px; border-radius: 12px; transition: 0.3s; }
        .box:hover { border-color: var(--accent); transform: translateY(-5px); }
        .box h3 { color: var(--accent); margin-top: 0; font-size: 1.1rem; }

        @media (max-width: 768px) {
            body { flex-direction: column; }
            .sidebar { width: 100%; height: auto; position: relative; border-right: none; }
            .main-content { margin-left: 0; padding: 20px; }
        }
    </style>
</head>
<body>

<div class="sidebar">
    <h2>📖 English Hub</h2>
    <div class="search-container">
        <input type="text" id="searchBar" placeholder="Search lessons or topics..." onkeyup="filterLessons()">
    </div>
    <div id="menu"></div>
</div>

<div class="main-content">
    <div id="display"></div>
</div>

<script>
const lessons = {
    "midnight": {
        title: "The Midnight Visitor",
        data: [
            {h:"Ausable", p:"Fat, witty spy who uses intelligence over weapons."},
            {h:"Max", p:"The intruder who is tricked by a fake balcony story."},
            {h:"Fowler", p:"Writer who learns real spies don't always look like heroes."},
            {h:"Setting", p:"6th floor of a French hotel; height is a tactical tool."},
            {h:"The Lie", p:"The imaginary balcony created to trap Max."},
            {h:"The Bluff", p:"Claiming police are at the door to cause panic."},
            {h:"The Twist", p:"The visitor was only Henry the waiter with drinks."},
            {h:"Theme", p:"Brain beats brawn in a crisis."}
        ]
    },
    "letter": {
        title: "A Letter to God",
        data: [
            {h:"Lencho", p:"Farmer with extreme, blind faith in God's help."},
            {h:"The Hailstorm", p:"Destroys crops entirely, leading to his plea."},
            {h:"The Letter", p:"Writes to God asking for 100 pesos."},
            {h:"Postmaster", p:"Collects 70 pesos to prevent Lencho's faith from shaking."},
            {h:"The Irony", p:"Lencho calls his helpers 'a bunch of crooks'."},
            {h:"Setting", p:"A lonely house on a hill crest."},
            {h:"Faith", p:"Theme: Faith can move mountains but can also lead to blind greed."},
            {h:"Moral", p:"The complexity of human nature and gratitude."}
        ]
    },
    "flying": {
        title: "Two Stories about Flying",
        data: [
            {h:"The Seagull", p:"A young bird afraid to take his first flight."},
            {h:"Hunger", p:"The motivation that finally forced the seagull to dive."},
            {h:"The Family", p:"Parents used 'taunting' to encourage his independence."},
            {h:"Black Aeroplane", p:"The mysterious pilot who guided the narrator through a storm."},
            {h:"The Storm", p:"Narrator takes a risk flying his old Dakota into clouds."},
            {h:"Mystery", p:"The second plane was never found on the radar."},
            {h:"Theme", p:"Courage and the power of the subconscious mind."},
            {h:"Conflict", p:"Overcoming fear vs. following safety."}
        ]
    },
    "bus": {
        title: "Madam Rides the Bus",
        data: [
            {h:"Valli", p:"An 8-year-old girl with a strong desire to explore."},
            {h:"The Goal", p:"A bus ride to the nearest town and back."},
            {h:"Planning", p:"She meticulously saved coins and calculated timings."},
            {h:"The Conductor", p:"A jolly man who called her 'Madam'."},
            {h:"The Dead Cow", p:"A sight that taught her about the reality of death."},
            {h:"Maturity", p:"Valli's transition from curiosity to understanding life/death."},
            {h:"Independence", p:"Taking the journey alone without her mother knowing."},
            {h:"Theme", p:"The loss of childhood innocence through experience."}
        ]
    },
    "mandela": {
        title: "Nelson Mandela: Freedom",
        data: [
            {h:"Apartheid", p:"System of racial discrimination in South Africa."},
            {h:"May 10", p:"The historic inauguration day of democracy."},
            {h:"Courage", p:"The triumph over fear, not the absence of it."},
            {h:"Freedom", p:"It is indivisible; chains on one are chains on all."},
            {h:"Twin Obligations", p:"Duty to family vs. Duty to people/country."},
            {h:"The Oppressor", p:"A prisoner of prejudice who needs liberation too."},
            {h:"Sacrifice", p:"Built on the blood of thousands of patriots."},
            {h:"Equality", p:"The vision of a non-racial, democratic society."}
        ]
    },
    "necklace": {
        title: "The Necklace",
        data: [
            {h:"Matilda Loisel", p:"A woman unhappy with her simple life."},
            {h:"The Invitation", p:"The chance to enter the world of high society."},
            {h:"The Loan", p:"Borrowing a diamond necklace from Mme Forestier."},
            {h:"The Loss", p:"Losing the jewel leads to 10 years of grueling debt."},
            {h:"The Truth", p:"The original necklace was only an imitation (fake)."},
            {h:"Lesson", p:"Honesty and contentment are better than false pride."},
            {h:"Irony", p:"They ruined their lives for something worthless."},
            {h:"Matilda's Change", p:"From a dreamer to a hard-working, rough woman."}
        ]
    }
};

function filterLessons() {
    let input = document.getElementById('searchBar').value.toLowerCase();
    let links = document.getElementsByClassName('lesson-link');
    
    for (let i = 0; i < links.length; i++) {
        let title = links[i].innerText.toLowerCase();
        links[i].style.display = title.includes(input) ? "block" : "none";
    }
}

function init() {
    const menu = document.getElementById('menu');
    Object.keys(lessons).forEach(key => {
        let a = document.createElement('div');
        a.className = 'lesson-link';
        a.innerText = lessons[key].title;
        a.onclick = () => render(key);
        menu.appendChild(a);
    });
    render('midnight');
}

function render(id) {
    const l = lessons[id];
    let html = <h1>${l.title}</h1><div class="grid-8">;
    l.data.forEach(box => {
        html += <div class="box"><h3>${box.h}</h3><p>${box.p}</p></div>;
    });
    html += </div>;
    document.getElementById('display').innerHTML = html;
    document.querySelectorAll('.lesson-link').forEach(link => {
        link.classList.toggle('active', link.innerText === l.title);
    });
}
init();
</script>
</body>
</html>
