<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>🧠 Tricky Mind Academy</title>

<style>
*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

body{
    font-family:Arial, sans-serif;
    background:linear-gradient(135deg,#111827,#1e1b4b,#312e81);
    color:white;
    min-height:100vh;
}

button{
    font-family:inherit;
    cursor:pointer;
}

.app{
    width:100%;
    max-width:900px;
    margin:auto;
    min-height:100vh;
    padding:18px;
}

/* HEADER */
.header{
    display:flex;
    justify-content:space-between;
    align-items:center;
    gap:10px;
    margin-bottom:20px;
}

.logo{
    font-size:22px;
    font-weight:bold;
}

.stats{
    display:flex;
    gap:8px;
}

.stat{
    background:rgba(255,255,255,.1);
    border:1px solid rgba(255,255,255,.15);
    padding:8px 12px;
    border-radius:12px;
    font-size:14px;
}

/* SCREEN */
.screen{
    display:none;
}

.screen.active{
    display:block;
}

/* HOME */
.hero{
    text-align:center;
    padding:45px 20px;
    background:rgba(255,255,255,.08);
    border-radius:25px;
    border:1px solid rgba(255,255,255,.12);
    box-shadow:0 15px 50px rgba(0,0,0,.3);
}

.hero .icon{
    font-size:70px;
    margin-bottom:15px;
}

.hero h1{
    font-size:36px;
    margin-bottom:12px;
}

.hero p{
    color:#d1d5db;
    line-height:1.6;
    margin-bottom:25px;
}

.primary-btn{
    border:none;
    background:linear-gradient(135deg,#8b5cf6,#6366f1);
    color:white;
    padding:14px 28px;
    border-radius:14px;
    font-size:17px;
    font-weight:bold;
    box-shadow:0 8px 20px rgba(99,102,241,.35);
}

.primary-btn:hover{
    transform:translateY(-2px);
}

/* LEVEL SCREEN */
.section-title{
    margin-bottom:15px;
}

.level-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(130px,1fr));
    gap:12px;
}

.level-card{
    background:rgba(255,255,255,.08);
    border:1px solid rgba(255,255,255,.12);
    border-radius:16px;
    padding:20px 10px;
    text-align:center;
    transition:.2s;
}

.level-card:hover{
    transform:translateY(-3px);
    background:rgba(255,255,255,.13);
}

.level-number{
    font-size:25px;
    font-weight:bold;
    margin-bottom:7px;
}

.level-type{
    color:#c4b5fd;
    font-size:13px;
}

.locked{
    opacity:.45;
}

.lock-icon{
    font-size:25px;
}

/* GAME */
.game-card{
    background:rgba(255,255,255,.08);
    border:1px solid rgba(255,255,255,.12);
    border-radius:22px;
    padding:22px;
}

.level-info{
    display:flex;
    justify-content:space-between;
    margin-bottom:18px;
    color:#c4b5fd;
}

.question{
    font-size:25px;
    line-height:1.45;
    margin-bottom:25px;
}

.options{
    display:grid;
    gap:12px;
}

.option{
    width:100%;
    text-align:left;
    background:#1f2937;
    border:2px solid #374151;
    color:white;
    padding:15px;
    border-radius:13px;
    font-size:16px;
    transition:.2s;
}

.option:hover{
    border-color:#8b5cf6;
    background:#292f3d;
}

.option.correct{
    background:#14532d;
    border-color:#22c55e;
}

.option.wrong{
    background:#7f1d1d;
    border-color:#ef4444;
}

.feedback{
    min-height:50px;
    margin-top:20px;
    padding:14px;
    border-radius:12px;
    background:rgba(0,0,0,.2);
    line-height:1.5;
}

.next-btn{
    display:none;
    margin-top:15px;
}

/* RESULT */
.result{
    text-align:center;
    padding:35px 20px;
    background:rgba(255,255,255,.08);
    border-radius:22px;
}

.result-icon{
    font-size:65px;
    margin-bottom:15px;
}

.result h2{
    margin-bottom:10px;
}

.result p{
    color:#d1d5db;
    line-height:1.6;
    margin-bottom:20px;
}

/* BACK */
.back-btn{
    border:none;
    background:#374151;
    color:white;
    padding:10px 15px;
    border-radius:10px;
    margin-bottom:15px;
}

/* MOBILE */
@media(max-width:600px){

    .app{
        padding:12px;
    }

    .hero h1{
        font-size:28px;
    }

    .hero .icon{
        font-size:55px;
    }

    .question{
        font-size:21px;
    }

    .header{
        align-items:flex-start;
    }

    .logo{
        font-size:18px;
    }

    .stat{
        padding:7px 8px;
        font-size:12px;
    }
}
</style>
</head>

<body>

<div class="app">

    <!-- HEADER -->
    <div class="header">

        <div class="logo">
            🧠 Tricky Mind
        </div>

        <div class="stats">
            <div class="stat">
                ⭐ <span id="score">0</span>
            </div>

            <div class="stat">
                🏆 <span id="progress">0/10</span>
            </div>
        </div>

    </div>


    <!-- HOME SCREEN -->
    <section id="homeScreen" class="screen active">

        <div class="hero">

            <div class="icon">🧠</div>

            <h1>Tricky Mind Academy</h1>

            <p>
                প্রশ্নের উত্তর দাও, Logic ব্যবহার করো,
                Puzzle সমাধান করো এবং ধীরে ধীরে
                কঠিন Level unlock করো!
            </p>

            <button class="primary-btn" onclick="openLevels()">
                🎮 PLAY GAME
            </button>

        </div>

    </section>


    <!-- LEVEL SCREEN -->
    <section id="levelScreen" class="screen">

        <button class="back-btn" onclick="showScreen('homeScreen')">
            ← Home
        </button>

        <h2 class="section-title">
            🎯 Choose Level
        </h2>

        <div id="levelGrid" class="level-grid"></div>

    </section>


    <!-- GAME SCREEN -->
    <section id="gameScreen" class="screen">

        <button class="back-btn" onclick="openLevels()">
            ← Levels
        </button>

        <div class="game-card">

            <div class="level-info">

                <span id="levelTitle">
                    Level 1
                </span>

                <span id="questionNumber">
                    Question
                </span>

            </div>

            <div id="question" class="question"></div>

            <div id="options" class="options"></div>

            <div id="feedback" class="feedback"></div>

            <button
                id="nextButton"
                class="primary-btn next-btn"
                onclick="nextQuestion()">
                Next →
            </button>

        </div>

    </section>


    <!-- RESULT SCREEN -->
    <section id="resultScreen" class="screen">

        <div class="result">

            <div class="result-icon">
                🎉
            </div>

            <h2>Level Complete!</h2>

            <p id="resultText"></p>

            <button
                class="primary-btn"
                onclick="openLevels()">
                Choose Next Level
            </button>

        </div>

    </section>

</div>


<script>

/* =====================================================
   GAME DATA
   নতুন Level এখানে যোগ করা যাবে
   ===================================================== */

const levels = [

    {
        id:1,
        type:"MCQ",
        title:"Tricky Question",

        questions:[
            {
                question:"একটি ঘরে ৫টি মোমবাতি জ্বলছে। ২টি মোমবাতি নিভিয়ে দেওয়া হলো। ঘরে মোট কতটি মোমবাতি রইল?",

                options:[
                    "২টি",
                    "৩টি",
                    "৫টি",
                    "৭টি"
                ],

                answer:2,

                explanation:
                "মোমবাতি নিভে গেলেও ঘর থেকে চলে যায়নি। তাই মোট ৫টি মোমবাতিই আছে।"
            }
        ]
    },


    {
        id:2,
        type:"MCQ",
        title:"Position Logic",

        questions:[
            {
                question:
                "একটি দৌড়ে তুমি দ্বিতীয় স্থানে থাকা ব্যক্তিকে পেরিয়ে গেলে। এখন তুমি কোন স্থানে?",

                options:[
                    "প্রথম",
                    "দ্বিতীয়",
                    "তৃতীয়",
                    "চতুর্থ"
                ],

                answer:1,

                explanation:
                "তুমি দ্বিতীয় ব্যক্তিকে পেরিয়েছো, তাই তার জায়গা অর্থাৎ দ্বিতীয় স্থানে গেছো।"
            }
        ]
    },


    {
        id:3,
        type:"MCQ",
        title:"Number Logic",

        questions:[
            {
                question:
                "ধারাটি দেখো: 2, 4, 6, 8, ?",

                options:[
                    "9",
                    "10",
                    "11",
                    "12"
                ],

                answer:1,

                explanation:
                "প্রতিবার ২ করে বাড়ছে। তাই উত্তর ১০।"
            }
        ]
    },


    {
        id:4,
        type:"MCQ",
        title:"Thinking Challenge",

        questions:[
            {
                question:
                "তোমার কাছে ৩টি আপেল আছে। তুমি ২টি নিয়ে নিলে তোমার কাছে কতটি আপেল থাকবে?",

                options:[
                    "১টি",
                    "২টি",
                    "৩টি",
                    "৫টি"
                ],

                answer:1,

                explanation:
                "তুমি ২টি আপেল নিয়ে নিয়েছো, তাই তোমার কাছে ২টি থাকবে।"
            }
        ]
    },


    {
        id:5,
        type:"MCQ",
        title:"Logic Test",

        questions:[
            {
                question:
                "একটি ঘড়িতে ৩টা বাজলে ঘণ্টার কাঁটা ও মিনিটের কাঁটার মধ্যে কোণ কত?",

                options:[
                    "30°",
                    "60°",
                    "90°",
                    "180°"
                ],

                answer:2,

                explanation:
                "৩টার সময় ঘণ্টার কাঁটা ৩-এর দিকে এবং মিনিটের কাঁটা ১২-এর দিকে থাকে। কোণ ৯০°।"
            }
        ]
    },


    {
        id:6,
        type:"MCQ",
        title:"Pattern",

        questions:[
            {
                question:
                "1, 3, 5, 7, ?",

                options:[
                    "8",
                    "9",
                    "10",
                    "11"
                ],

                answer:1,

                explanation:
                "প্রতিবার ২ করে বাড়ছে। তাই উত্তর ৯।"
            }
        ]
    },


    {
        id:7,
        type:"MCQ",
        title:"Quick Logic",

        questions:[
            {
                question:
                "একটি সপ্তাহে মোট কত দিন?",

                options:[
                    "5",
                    "6",
                    "7",
                    "8"
                ],

                answer:2,

                explanation:
                "এক সপ্তাহে ৭ দিন।"
            }
        ]
    },


    {
        id:8,
        type:"MCQ",
        title:"Number Challenge",

        questions:[
            {
                question:
                "5 × 5 = ?",

                options:[
                    "10",
                    "20",
                    "25",
                    "30"
                ],

                answer:2,

                explanation:
                "৫ × ৫ = ২৫।"
            }
        ]
    },


    {
        id:9,
        type:"MCQ",
        title:"Science",

        questions:[
            {
                question:
                "মানুষ শ্বাস নেওয়ার সময় প্রধানত কোন গ্যাস গ্রহণ করে?",

                options:[
                    "অক্সিজেন",
                    "কার্বন ডাই-অক্সাইড",
                    "হিলিয়াম",
                    "হাইড্রোজেন"
                ],

                answer:0,

                explanation:
                "মানুষ শ্বাস নেওয়ার সময় অক্সিজেন গ্রহণ করে।"
            }
        ]
    },


    {
        id:10,
        type:"MCQ",
        title:"Final Challenge",

        questions:[
            {
                question:
                "একটি সংখ্যার দ্বিগুণ ২০ হলে সংখ্যাটি কত?",

                options:[
                    "5",
                    "10",
                    "15",
                    "20"
                ],

                answer:1,

                explanation:
                "10 × 2 = 20। তাই উত্তর ১০।"
            }
        ]
    }

];


/* =====================================================
   GAME STATE
   ===================================================== */

let score = 0;

let unlockedLevel = 1;

let currentLevel = null;

let currentQuestion = 0;

let answered = false;


/* =====================================================
   STARTUP
   ===================================================== */

loadGame();

renderLevels();

updateStats();


/* =====================================================
   SCREEN SYSTEM
   ===================================================== */

function showScreen(id){

    document.querySelectorAll(".screen")
        .forEach(screen => {
            screen.classList.remove("active");
        });

    document.getElementById(id)
        .classList.add("active");
}


/* =====================================================
   OPEN LEVELS
   ===================================================== */

function openLevels(){

    renderLevels();

    showScreen("levelScreen");
}


/* =====================================================
   LEVEL LIST
   ===================================================== */

function renderLevels(){

    const grid =
        document.getElementById("levelGrid");

    grid.innerHTML = "";

    levels.forEach(level => {

        const card =
            document.createElement("div");

        const unlocked =
            level.id <= unlockedLevel;

        card.className =
            "level-card " +
            (unlocked ? "" : "locked");

        if(unlocked){

            card.innerHTML = `

                <div class="level-number">
                    ${level.id}
                </div>

                <div class="level-type">
                    ${level.type}
                </div>

                <div style="margin-top:8px;">
                    ${level.title}
                </div>

            `;

            card.onclick = function(){
                startLevel(level.id);
            };

        }else{

            card.innerHTML = `

                <div class="lock-icon">
                    🔒
                </div>

                <div class="level-number">
                    Level ${level.id}
                </div>

                <div class="level-type">
                    Locked
                </div>

            `;
        }

        grid.appendChild(card);
    });
}


/* =====================================================
   START LEVEL
   ===================================================== */

function startLevel(levelId){

    currentLevel =
        levels.find(level => level.id === levelId);

    if(!currentLevel){
        return;
    }

    currentQuestion = 0;

    answered = false;

    showScreen("gameScreen");

    showQuestion();
}


/* =====================================================
   SHOW QUESTION
   ===================================================== */

function showQuestion(){

    const q =
        currentLevel.questions[currentQuestion];

    answered = false;

    document.getElementById("levelTitle")
        .textContent =
        `Level ${currentLevel.id} • ${currentLevel.title}`;

    document.getElementById("questionNumber")
        .textContent =
        `${currentQuestion + 1}/${currentLevel.questions.length}`;

    document.getElementById("question")
        .textContent =
        q.question;

    document.getElementById("feedback")
        .textContent =
        "উত্তরটি বেছে নাও 👇";

    document.getElementById("nextButton")
        .style.display = "none";

    const options =
        document.getElementById("options");

    options.innerHTML = "";

    q.options.forEach((option,index)=>{

        const button =
            document.createElement("button");

        button.className = "option";

        button.textContent = option;

        button.onclick = function(){

            checkAnswer(index,button);

        };

        options.appendChild(button);

    });
}


/* =====================================================
   CHECK ANSWER
   ===================================================== */

function checkAnswer(selected,button){

    if(answered){
        return;
    }

    answered = true;

    const q =
        currentLevel.questions[currentQuestion];

    const allButtons =
        document.querySelectorAll(".option");

    allButtons.forEach(btn=>{
        btn.disabled = true;
    });


    if(selected === q.answer){

        button.classList.add("correct");

        score += 10;

        document.getElementById("feedback")
            .innerHTML =
            "✅ <b>সঠিক উত্তর!</b><br>" +
            q.explanation;

    }else{

        button.classList.add("wrong");

        allButtons[q.answer]
            .classList.add("correct");

        document.getElementById("feedback")
            .innerHTML =
            "❌ <b>ভুল উত্তর!</b><br>" +
            "সঠিক উত্তর: " +
            q.options[q.answer] +
            "<br><br>" +
            q.explanation;
    }


    updateStats();

    saveGame();

    document.getElementById("nextButton")
        .style.display = "inline-block";
}


/* =====================================================
   NEXT QUESTION
   ===================================================== */

function nextQuestion(){

    currentQuestion++;

    if(
        currentQuestion >=
        currentLevel.questions.length
    ){

        finishLevel();

        return;
    }

    showQuestion();
}


/* =====================================================
   FINISH LEVEL
   ===================================================== */

function finishLevel(){

    if(currentLevel.id === unlockedLevel){

        unlockedLevel++;

        if(unlockedLevel > levels.length){

            unlockedLevel = levels.length;

        }
    }

    saveGame();

    updateStats();

    document.getElementById("resultText")
        .textContent =
        `তুমি Level ${currentLevel.id} শেষ করেছো! ` +
        `তোমার বর্তমান Score ${score} ⭐`;

    showScreen("resultScreen");
}


/* =====================================================
   STATS
   ===================================================== */

function updateStats(){

    document.getElementById("score")
        .textContent = score;

    document.getElementById("progress")
        .textContent =
        `${Math.min(unlockedLevel - 1,levels.length)}/${levels.length}`;
}


/* =====================================================
   SAVE GAME
   ===================================================== */

function saveGame(){

    localStorage.setItem(
        "trickyMindScore",
        score
    );

    localStorage.setItem(
        "trickyMindUnlocked",
        unlockedLevel
    );
}


/* =====================================================
   LOAD GAME
   ===================================================== */

function loadGame(){

    const savedScore =
        localStorage.getItem("trickyMindScore");

    const savedLevel =
        localStorage.getItem("trickyMindUnlocked");

    if(savedScore !== null){

        score =
            Number(savedScore);
    }

    if(savedLevel !== null){

        unlockedLevel =
            Number(savedLevel);
    }

    if(unlockedLevel < 1){
        unlockedLevel = 1;
    }
}


/* =====================================================
   FUTURE GAME SYSTEM
   ===================================================== */

/*
   ভবিষ্যতে এখানে আমরা যোগ করব:

   1. 🧩 BLOCK PUZZLE
   2. 🤖 ROBOT MOVEMENT
   3. 🔁 REPEAT BLOCK
   4. ❓ IF / ELSE
   5. 🔢 VARIABLE
   6. 🧮 MATH PUZZLE
   7. 🔬 SCIENCE LEVEL
   8. 💻 CODING LOGIC
   9. 🐛 DEBUGGING
   10. 🏆 ACHIEVEMENT
   11. ❤️ LIFE SYSTEM
   12. 💰 COIN SYSTEM
   13. 🛍️ SHOP
   14. 🌎 WORLD / MAP
   15. 🔥 DAILY CHALLENGE

   নতুন content পুরনো system-এর সঙ্গে
   যোগ করা হবে।
*/

</script>
<!-- =========================================================
     TRICKY MIND - ADVANCED EDUCATION SYSTEM
     এই অংশটি পুরোনো Game System-এর উপর ADD করা হচ্ছে।
     পুরোনো code মুছবেন না।
========================================================= -->

<script>

/* =========================================================
   ADVANCED CATEGORY DATABASE
========================================================= */

const advancedCategories = [

{
    id:"iq",
    icon:"🧠",
    name:"IQ & Logic",
    description:"Pattern, reasoning ও tricky brain challenge",
    questions:[

        {
            visual:`
                <div class="visual-grid">
                    <div>▲</div><div>●</div><div>▲</div>
                    <div>●</div><div>▲</div><div>●</div>
                    <div>▲</div><div>●</div><div>❓</div>
                </div>
            `,
            question:"Pattern অনুযায়ী শেষ ঘরে কোন চিহ্নটি থাকবে?",
            options:["▲","●","■","◆"],
            answer:1,
            explanation:"▲ এবং ● পর্যায়ক্রমে এসেছে। তাই শেষ ঘরে ● হবে।"
        },

        {
            visual:`
                <div class="visual-row">
                    <div class="visual-box">2</div>
                    <div>→</div>
                    <div class="visual-box">6</div>
                    <div>→</div>
                    <div class="visual-box">18</div>
                    <div>→</div>
                    <div class="visual-box">?</div>
                </div>
            `,
            question:"প্রতিটি সংখ্যা আগের সংখ্যার ৩ গুণ। ? এর জায়গায় কী হবে?",
            options:["36","48","54","60"],
            answer:2,
            explanation:"2×3=6, 6×3=18, তাই 18×3=54।"
        },

        {
            visual:`
                <div class="visual-grid two">
                    <div>🔵 🔵</div>
                    <div>🔴</div>
                    <div>🔵</div>
                    <div>❓</div>
                </div>
            `,
            question:"যদি 🔵 = 2 এবং 🔴 = 3 হয়, তাহলে 🔵🔵 + 🔴 কত?",
            options:["5","6","7","8"],
            answer:2,
            explanation:"🔵🔵 = 4 এবং 🔴 = 3। মোট 7।"
        },

        {
            visual:`
                <div class="big-visual">
                    🐱 → 🐶 → 🐱 → 🐶 → ❓
                </div>
            `,
            question:"ধারাটি দেখে পরের ছবিটি কী হবে?",
            options:["🐱","🐶","🐭","🐰"],
            answer:0,
            explanation:"বিড়াল ও কুকুর পর্যায়ক্রমে এসেছে। তাই পরেরটি 🐱।"
        },

        {
            visual:`
                <div class="visual-row">
                    <div class="visual-box">3</div>
                    <div>+</div>
                    <div class="visual-box">5</div>
                    <div>=</div>
                    <div class="visual-box">8</div>
                </div>
            `,
            question:"একই নিয়মে 7 এবং 9 ব্যবহার করলে ফল কত?",
            options:["14","15","16","17"],
            answer:2,
            explanation:"এখানে নিয়ম হলো দুই সংখ্যাকে যোগ করা। 7+9=16।"
        },

        {
            visual:`
                <div class="big-visual">
                    🟦 🟦 🟥 🟦 🟦 🟥 🟦 🟦 ❓
                </div>
            `,
            question:"Pattern অনুযায়ী ❓ কোন রঙ হবে?",
            options:["🟦","🟥","🟩","🟨"],
            answer:1,
            explanation:"প্রতি ৩টি ঘরে 🟦 🟦 🟥 পুনরাবৃত্তি হচ্ছে।"
        }
    ]
},

{
    id:"math",
    icon:"🧮",
    name:"Math Brain",
    description:"গণিত নয় শুধু—Mathematical reasoning",
    questions:[

        {
            visual:`
                <div class="big-visual">
                    2 → 6 → 12 → 20 → 30 → ❓
                </div>
            `,
            question:"ধারাটির পরের সংখ্যা কত?",
            options:["36","40","42","44"],
            answer:2,
            explanation:"পার্থক্যগুলো 4, 6, 8, 10। পরের পার্থক্য 12। তাই 30+12=42।"
        },

        {
            visual:`
                <div class="number-table">
                    <div>4</div><div>7</div><div>11</div>
                    <div>6</div><div>5</div><div>11</div>
                    <div>8</div><div>9</div><div>?</div>
                </div>
            `,
            question:"প্রতিটি সারিতে প্রথম দুই সংখ্যার যোগফল তৃতীয় সংখ্যা। ? কত?",
            options:["15","16","17","18"],
            answer:2,
            explanation:"8+9=17।"
        },

        {
            visual:`
                <div class="balance">
                    ⚖️<br>
                    🍎🍎 = 10
                    <br><br>
                    🍎 + ⭐ = 8
                </div>
            `,
            question:"একটি 🍎-এর মান কত?",
            options:["3","4","5","6"],
            answer:2,
            explanation:"দুটি 🍎 = 10। তাই একটি 🍎 = 5।"
        },

        {
            visual:`
                <div class="big-visual">
                    🔺 + 🔺 + 🔺 = 21
                </div>
            `,
            question:"একটি 🔺-এর মান কত?",
            options:["5","6","7","8"],
            answer:2,
            explanation:"21 ÷ 3 = 7।"
        },

        {
            visual:`
                <div class="big-visual">
                    🕐 3:00
                    <br>
                    ⏩ + 2 ঘণ্টা 30 মিনিট
                </div>
            `,
            question:"ঘড়িতে 3:00 বাজে। 2 ঘণ্টা 30 মিনিট পরে কয়টা বাজবে?",
            options:["5:00","5:30","6:00","6:30"],
            answer:1,
            explanation:"3:00 + 2:30 = 5:30।"
        },

        {
            visual:`
                <div class="big-visual">
                    🔵 🔵 🔵 🔵
                    <br>
                    মোট বল = 20
                </div>
            `,
            question:"সব বল সমান হলে প্রতিটি বলের মূল্য কত?",
            options:["4","5","6","10"],
            answer:1,
            explanation:"20 ÷ 4 = 5।"
        }
    ]
},

{
    id:"science",
    icon:"🔬",
    name:"Science",
    description:"Physics, Biology, Chemistry ও Space",
    questions:[

        {
            visual:`
                <div class="big-visual">
                    ☀️ → 🌍 → 🌑
                </div>
            `,
            question:"এই ধরনের অবস্থানে ছায়া/গ্রহণের ঘটনায় সূর্য, পৃথিবী ও চাঁদের সম্পর্ক কীভাবে কাজ করে?",
            options:[
                "চাঁদ পৃথিবীর ছায়ায় আসে",
                "পৃথিবী সূর্যের ছায়ায় আসে",
                "সূর্য পৃথিবীর চারদিকে ঘোরে",
                "চাঁদ সূর্যকে ঘিরে ঘোরে না"
            ],
            answer:0,
            explanation:"চাঁদ পৃথিবীর ছায়ায় ঢুকলে Lunar Eclipse বা চন্দ্রগ্রহণ হতে পারে।"
        },

        {
            visual:`
                <div class="big-visual">
                    🧲  ←  🔩
                </div>
            `,
            question:"ছবির কোন বস্তুটি চুম্বকের আকর্ষণে আসতে পারে?",
            options:["লোহার পেরেক","কাঠের টুকরো","কাগজ","প্লাস্টিক"],
            answer:0,
            explanation:"লোহা চুম্বকের দ্বারা আকৃষ্ট হয়।"
        },

        {
            visual:`
                <div class="big-visual">
                    🌱
                    <br>
                    ☀️ + 💧 + CO₂
                </div>
            `,
            question:"উদ্ভিদ খাদ্য তৈরির প্রক্রিয়াটির নাম কী?",
            options:["Respiration","Photosynthesis","Digestion","Evaporation"],
            answer:1,
            explanation:"উদ্ভিদ সূর্যালোক ব্যবহার করে Photosynthesis-এর মাধ্যমে খাদ্য তৈরি করে।"
        },

        {
            visual:`
                <div class="big-visual">
                    🌍
                    <br>
                    🌙 ↺
                </div>
            `,
            question:"চাঁদ প্রধানত কোন জ্যোতিষ্ককে প্রদক্ষিণ করে?",
            options:["সূর্য","পৃথিবী","মঙ্গল","বৃহস্পতি"],
            answer:1,
            explanation:"চাঁদ পৃথিবীকে প্রদক্ষিণ করে।"
        },

        {
            visual:`
                <div class="big-visual">
                    💧 → ☁️ → 🌧️
                </div>
            `,
            question:"জলীয় বাষ্প ঠান্ডা হয়ে ছোট জলকণায় পরিণত হওয়ার প্রক্রিয়াটি কী?",
            options:["Evaporation","Condensation","Melting","Freezing"],
            answer:1,
            explanation:"Water vapour ঠান্ডা হয়ে liquid droplets হলে তাকে condensation বলে।"
        },

        {
            visual:`
                <div class="big-visual">
                    🫁
                </div>
            `,
            question:"মানুষের শরীরে ফুসফুসের প্রধান কাজ কী?",
            options:[
                "রক্ত তৈরি করা",
                "গ্যাসের আদান-প্রদান",
                "খাদ্য হজম করা",
                "হাড় তৈরি করা"
            ],
            answer:1,
            explanation:"ফুসফুস অক্সিজেন গ্রহণ ও কার্বন ডাই-অক্সাইড বের করার কাজে সাহায্য করে।"
        }
    ]
},

{
    id:"geography",
    icon:"🌍",
    name:"Geography",
    description:"Map, Earth, climate, country ও physical geography",
    questions:[

        {
            visual:`
                <div class="compass">
                    <div>⬆️ N</div>
                    <div>W ◀️ ➡️ E</div>
                    <div>⬇️ S</div>
                </div>
            `,
            question:"মানচিত্রে উত্তর দিকে যাওয়ার পর ডান দিকে ঘুরলে কোন দিকে যাবে?",
            options:["West","South","East","North"],
            answer:2,
            explanation:"উত্তরের দিকে মুখ করলে ডান দিক হলো East বা পূর্ব।"
        },

        {
            visual:`
                <div class="big-visual">
                    🏔️
                    <br>
                    ⛰️ ⛰️
                </div>
            `,
            question:"অনেক উঁচু প্রাকৃতিক ভূমিরূপকে সাধারণত কী বলা হয়?",
            options:["Plain","Mountain","Valley","Island"],
            answer:1,
            explanation:"Mountain হলো উচ্চ ও খাড়া প্রাকৃতিক ভূমিরূপ।"
        },

        {
            visual:`
                <div class="big-visual">
                    🌊 🏝️ 🌊
                </div>
            `,
            question:"চারদিকে জল দ্বারা ঘেরা স্থলভাগকে কী বলা হয়?",
            options:["Peninsula","Island","Plateau","Valley"],
            answer:1,
            explanation:"চারদিকে জল এবং মাঝখানে স্থলভাগ হলে সেটি Island বা দ্বীপ।"
        },

        {
            visual:`
                <div class="big-visual">
                    ☀️
                    <br>
                    🌧️
                    <br>
                    🌴
                </div>
            `,
            question:"উষ্ণ ও আর্দ্র অঞ্চলে প্রচুর বৃষ্টিপাত হলে কোন ধরনের বন বেশি দেখা যায়?",
            options:[
                "Tropical Rainforest",
                "Tundra",
                "Desert",
                "Polar Ice"
            ],
            answer:0,
            explanation:"উষ্ণ ও অতিবৃষ্টিপ্রবণ অঞ্চলে Tropical Rainforest দেখা যায়।"
        },

        {
            visual:`
                <div class="big-visual">
                    🌊
                    <br>
                    ➡️➡️➡️
                </div>
            `,
            question:"সমুদ্রের জলের নিয়মিত ওঠানামার সঙ্গে কোন শক্তির সম্পর্ক রয়েছে?",
            options:["চাঁদ ও সূর্যের মহাকর্ষ","শুধু বাতাস","শুধু বৃষ্টি","পাহাড়"],
            answer:0,
            explanation:"Tide বা জোয়ার-ভাটায় প্রধান ভূমিকা চাঁদের মহাকর্ষের; সূর্যেরও প্রভাব আছে।"
        },

        {
            visual:`
                <div class="big-visual">
                    🗺️
                    <br>
                    🇮🇳
                </div>
            `,
            question:"ভারত কোন মহাদেশে অবস্থিত?",
            options:["Europe","Asia","Africa","South America"],
            answer:1,
            explanation:"ভারত এশিয়া মহাদেশের অংশ।"
        }
    ]
},

{
    id:"visual",
    icon:"🧩",
    name:"Visual Puzzle",
    description:"ছবি দেখে খুঁজে বের করো",
    questions:[

        {
            visual:`
                <div class="visual-grid">
                    <div>🔴</div><div>🔵</div><div>🟢</div>
                    <div>🔵</div><div>🟢</div><div>🔴</div>
                    <div>🟢</div><div>🔴</div><div>❓</div>
                </div>
            `,
            question:"প্রতিটি row ও column-এ তিনটি আলাদা রঙ একবার করে আছে। শেষ ঘরে কী হবে?",
            options:["🔴","🔵","🟢","🟡"],
            answer:1,
            explanation:"শেষ row-তে 🟢 এবং 🔴 আছে, তাই বাকি রঙ হবে 🔵।"
        },

        {
            visual:`
                <div class="big-visual">
                    ⭐ ⭐ ⭐ ⭐
                    <br>
                    ⭐ ⭐ ❌ ⭐
                    <br>
                    ⭐ ⭐ ⭐ ⭐
                </div>
            `,
            question:"ছবিতে অন্যগুলোর থেকে আলাদা চিহ্নটি কোনটি?",
            options:["প্রথম ⭐","মাঝের ❌","শেষ ⭐","কোনোটিই নয়"],
            answer:1,
            explanation:"মাঝের চিহ্নটি ⭐ নয়, ❌।"
        }
    ]
},

{
    id:"coding",
    icon:"💻",
    name:"Coding Logic",
    description:"Algorithm, sequence, condition ও debugging",
    questions:[

        {
            visual:`
                <div class="code-block">
                    START<br>
                    ↓<br>
                    MOVE<br>
                    ↓<br>
                    TURN<br>
                    ↓<br>
                    MOVE<br>
                    ↓<br>
                    ❓
                </div>
            `,
            question:"একটি Robot-কে একই কাজ বারবার করাতে কোন ধারণাটি সবচেয়ে উপযোগী?",
            options:["Loop","Color","Sound","Delete"],
            answer:0,
            explanation:"একই instruction বারবার চালানোর জন্য Loop ব্যবহার করা হয়।"
        },

        {
            visual:`
                <div class="code-block">
                    IF key = true<br>
                    → OPEN DOOR<br>
                    ELSE<br>
                    → STAY
                </div>
            `,
            question:"এখানে IF কী করছে?",
            options:[
                "একটি condition পরীক্ষা করছে",
                "সব code মুছে দিচ্ছে",
                "শুধু ছবি দেখাচ্ছে",
                "গেম বন্ধ করছে"
            ],
            answer:0,
            explanation:"IF একটি condition সত্য না মিথ্যা তা পরীক্ষা করে।"
        },

        {
            visual:`
                <div class="code-block">
                    MOVE<br>
                    MOVE<br>
                    MOVE<br>
                    MOVE
                </div>
            `,
            question:"একই MOVE চারবার না লিখে কোন ধারণা ব্যবহার করা যায়?",
            options:["Loop","Variable","Image","Sound"],
            answer:0,
            explanation:"Loop দিয়ে একই instruction একাধিকবার চালানো যায়।"
        }
    ]
}

];


/* =========================================================
   ADVANCED CSS
========================================================= */

const advancedStyle = document.createElement("style");

advancedStyle.textContent = `

.advanced-title{
    font-size:28px;
    margin-bottom:8px;
}

.advanced-subtitle{
    color:#cbd5e1;
    margin-bottom:20px;
    line-height:1.5;
}

.category-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
    gap:14px;
}

.category-card{
    background:linear-gradient(
        145deg,
        rgba(255,255,255,.12),
        rgba(255,255,255,.05)
    );

    border:1px solid rgba(255,255,255,.15);
    border-radius:20px;
    padding:22px 14px;
    color:white;
    cursor:pointer;
    transition:.2s;
    text-align:center;
}

.category-card:hover{
    transform:translateY(-5px);
    border-color:#a78bfa;
    background:rgba(139,92,246,.2);
}

.category-icon{
    font-size:45px;
    margin-bottom:10px;
}

.category-name{
    font-size:18px;
    font-weight:bold;
    margin-bottom:6px;
}

.category-description{
    font-size:12px;
    color:#cbd5e1;
    line-height:1.4;
}

.visual-question{
    margin-bottom:20px;
}

.visual-panel{
    background:#0f172a;
    border:1px solid #334155;
    border-radius:18px;
    padding:20px;
    margin-bottom:20px;
    text-align:center;
    overflow:hidden;
}

.visual-grid{
    display:grid;
    grid-template-columns:repeat(3,70px);
    gap:8px;
    justify-content:center;
}

.visual-grid div{
    height:65px;
    display:flex;
    align-items:center;
    justify-content:center;
    background:#1e293b;
    border-radius:10px;
    font-size:30px;
}

.visual-grid.two{
    grid-template-columns:repeat(2,90px);
}

.visual-row{
    display:flex;
    justify-content:center;
    align-items:center;
    gap:10px;
    font-size:25px;
    flex-wrap:wrap;
}

.visual-box{
    background:#312e81;
    border:2px solid #6366f1;
    border-radius:12px;
    min-width:55px;
    padding:12px;
    font-size:22px;
    font-weight:bold;
}

.big-visual{
    font-size:32px;
    line-height:1.8;
    padding:10px;
}

.number-table{
    display:grid;
    grid-template-columns:repeat(3,65px);
    gap:7px;
    justify-content:center;
}

.number-table div{
    background:#312e81;
    padding:16px;
    border-radius:10px;
    font-weight:bold;
    font-size:20px;
}

.balance{
    font-size:25px;
    line-height:1.5;
}

.compass{
    font-size:22px;
    line-height:2;
}

.code-block{
    display:inline-block;
    text-align:left;
    background:#020617;
    border:1px solid #475569;
    border-radius:12px;
    padding:18px 25px;
    color:#a7f3d0;
    font-family:monospace;
    line-height:1.8;
}

.advanced-option{
    margin-bottom:10px;
}

.advanced-result{
    margin-top:15px;
    padding:15px;
    border-radius:14px;
    background:rgba(255,255,255,.08);
    line-height:1.6;
}

`;

document.head.appendChild(advancedStyle);


/* =========================================================
   CREATE ADVANCED CATEGORY SCREEN
========================================================= */

const advancedScreen =
document.createElement("section");

advancedScreen.id = "advancedScreen";
advancedScreen.className = "screen";

advancedScreen.innerHTML = `

<button class="back-btn"
        onclick="showScreen('homeScreen')">
    ← Home
</button>

<h2 class="advanced-title">
    🎓 Brain Academy
</h2>

<p class="advanced-subtitle">
    শুধু মুখস্থ নয় — চিন্তা করো, বিশ্লেষণ করো এবং সমাধান বের করো।
</p>

<div id="advancedCategoryGrid"
     class="category-grid">
</div>

`;

document.querySelector(".app")
.appendChild(advancedScreen);


/* =========================================================
   ADD BRAIN ACADEMY BUTTON TO HOME
========================================================= */

const hero = document.querySelector(".hero");

const brainButton =
document.createElement("button");

brainButton.className = "primary-btn";

brainButton.style.marginTop = "12px";
brainButton.style.background =
"linear-gradient(135deg,#ec4899,#8b5cf6)";

brainButton.textContent =
"🧠 Brain Academy";

brainButton.onclick =
function(){
    openAdvancedCategories();
};

hero.appendChild(brainButton);


/* =========================================================
   RENDER CATEGORIES
========================================================= */

function openAdvancedCategories(){

    const grid =
    document.getElementById(
        "advancedCategoryGrid"
    );

    grid.innerHTML = "";

    advancedCategories.forEach(category=>{

        const card =
        document.createElement("div");

        card.className =
        "category-card";

        card.innerHTML = `

            <div class="category-icon">
                ${category.icon}
            </div>

            <div class="category-name">
                ${category.name}
            </div>

            <div class="category-description">
                ${category.description}
            </div>

            <div style="margin-top:10px;color:#c4b5fd;">
                ${category.questions.length} Questions
            </div>
        `;

        card.onclick =
        function(){
            startAdvancedCategory(category.id);
        };

        grid.appendChild(card);

    });

    showScreen("advancedScreen");
}


/* =========================================================
   ADVANCED GAME STATE
========================================================= */

let advancedCategory = null;
let advancedQuestionIndex = 0;
let advancedScore = 0;


/* =========================================================
   START CATEGORY
========================================================= */

function startAdvancedCategory(categoryId){

    advancedCategory =
    advancedCategories.find(
        category => category.id === categoryId
    );

    if(!advancedCategory){
        return;
    }

    advancedQuestionIndex = 0;
    advancedScore = 0;

    showAdvancedQuestion();
}


/* =========================================================
   SHOW ADVANCED QUESTION
========================================================= */

function showAdvancedQuestion(){

    const q =
    advancedCategory.questions[
        advancedQuestionIndex
    ];

    const screen =
    document.getElementById(
        "advancedScreen"
    );

    screen.innerHTML = `

        <button class="back-btn"
                onclick="openAdvancedCategories()">
            ← Categories
        </button>

        <div class="game-card">

            <div class="level-info">

                <span>
                    ${advancedCategory.icon}
                    ${advancedCategory.name}
                </span>

                <span>
                    ${advancedQuestionIndex + 1}
                    /
                    ${advancedCategory.questions.length}
                </span>

            </div>

            <div class="visual-panel">
                ${q.visual}
            </div>

            <div class="question">
                ${q.question}
            </div>

            <div id="advancedOptions"
                 class="options">
            </div>

            <div id="advancedFeedback"
                 class="advanced-result">
                উত্তরটি নির্বাচন করো 👇
            </div>

            <button
                id="advancedNext"
                class="primary-btn"
                style="display:none;margin-top:15px;"
                onclick="nextAdvancedQuestion()">
                Next →
            </button>

        </div>
    `;


    const optionsBox =
    document.getElementById(
        "advancedOptions"
    );


    q.options.forEach((option,index)=>{

        const button =
        document.createElement("button");

        button.className =
        "option advanced-option";

        button.textContent =
        option;

        button.onclick =
        function(){

            checkAdvancedAnswer(
                index,
                button
            );

        };

        optionsBox.appendChild(button);

    });


    showScreen("advancedScreen");
}


/* =========================================================
   CHECK ADVANCED ANSWER
========================================================= */

function checkAdvancedAnswer(
    selected,
    button
){

    const q =
    advancedCategory.questions[
        advancedQuestionIndex
    ];

    const buttons =
    document.querySelectorAll(
        ".advanced-option"
    );

    buttons.forEach(btn=>{
        btn.disabled = true;
    });


    if(selected === q.answer){

        button.classList.add("correct");

        advancedScore += 10;

        document.getElementById(
            "advancedFeedback"
        ).innerHTML =
        `
        ✅ <b>সঠিক!</b><br>
        ${q.explanation}
        `;

    }else{

        button.classList.add("wrong");

        buttons[q.answer]
            .classList.add("correct");

        document.getElementById(
            "advancedFeedback"
        ).innerHTML =
        `
        ❌ <b>ভুল।</b><br>
        সঠিক উত্তর:
        <b>${q.options[q.answer]}</b>
        <br><br>
        ${q.explanation}
        `;
    }


    document.getElementById(
        "advancedNext"
    ).style.display = "inline-block";
}


/* =========================================================
   NEXT ADVANCED QUESTION
========================================================= */

function nextAdvancedQuestion(){

    advancedQuestionIndex++;

    if(
        advancedQuestionIndex >=
        advancedCategory.questions.length
    ){

        finishAdvancedCategory();

        return;
    }

    showAdvancedQuestion();
}


/* =========================================================
   FINISH ADVANCED CATEGORY
========================================================= */

function finishAdvancedCategory(){

    const total =
    advancedCategory.questions.length * 10;

    const percentage =
    Math.round(
        (advancedScore / total) * 100
    );


    document.getElementById(
        "advancedScreen"
    ).innerHTML = `

        <div class="result">

            <div class="result-icon">
                🏆
            </div>

            <h2>
                ${advancedCategory.name}
                Complete!
            </h2>

            <p>
                Score:
                <b>${advancedScore}/${total}</b>
                <br><br>
                Accuracy:
                <b>${percentage}%</b>
            </p>

            <button
                class="primary-btn"
                onclick="openAdvancedCategories()">
                🔄 আবার খেলুন
            </button>

            <button
                class="primary-btn"
                style="margin-top:10px;background:#374151;"
                onclick="showScreen('homeScreen')">
                🏠 Home
            </button>

        </div>
    `;

    showScreen("advancedScreen");
}


/* =========================================================
   END OF ADVANCED SYSTEM
========================================================= */

</script>
</body>
</html>
