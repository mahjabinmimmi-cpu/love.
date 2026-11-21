
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday Rudro 🎂</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    overflow: hidden;
    height: 100vh;
    font-family: Georgia, serif;
    background: linear-gradient(135deg, #160b24, #4b163b, #901c52);
    color: white;
}

.screen {
    height: 100vh;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 25px;
    position: absolute;
    inset: 0;
    opacity: 0;
    visibility: hidden;
    transition: opacity 1s ease, visibility 1s;
}

.screen.active {
    opacity: 1;
    visibility: visible;
}

.content {
    max-width: 650px;
    z-index: 2;
}

h1 {
    font-size: clamp(2.5rem, 8vw, 5rem);
    color: #ffb9da;
    text-shadow: 0 0 15px #ff4f9a, 0 0 35px #ff4f9a;
    margin-bottom: 25px;
}

p {
    font-size: clamp(1.1rem, 4vw, 1.5rem);
    line-height: 1.9;
    color: #ffe6f2;
}

button {
    border: 1px solid #ffb9da;
    background: rgba(255, 182, 213, 0.15);
    color: white;
    padding: 14px 28px;
    border-radius: 40px;
    font-size: 17px;
    margin-top: 30px;
    cursor: pointer;
    backdrop-filter: blur(8px);
    transition: 0.3s;
}

button:hover {
    background: #ff77b7;
    transform: scale(1.06);
    box-shadow: 0 0 25px #ff77b7;
}

.emoji {
    font-size: 70px;
    margin-bottom: 20px;
    animation: pulse 2s infinite;
}

.small {
    color: #ffc6df;
    font-size: 17px;
    letter-spacing: 2px;
}

.heart {
    position: fixed;
    bottom: -40px;
    animation: floatUp linear forwards;
    pointer-events: none;
    z-index: 1;
}

.sparkle {
    position: fixed;
    animation: sparkle 3s infinite alternate;
    pointer-events: none;
}

@keyframes pulse {
    50% { transform: scale(1.12); }
}

@keyframes floatUp {
    to {
        transform: translateY(-110vh) rotate(360deg);
        opacity: 0;
    }
}

@keyframes sparkle {
    from { opacity: 0.2; transform: scale(0.7); }
    to { opacity: 1; transform: scale(1.3); }
}

.fadeAway {
    animation: fadeAway 2s forwards;
}

@keyframes fadeAway {
    to {
        opacity: 0;
        transform: translateY(-100px) scale(0.7);
        filter: blur(10px);
    }
}
</style>
</head>

<body>

<!-- SCREEN 1 -->
<div class="screen active" id="screen1">
    <div class="content" id="firstContent">
        <div class="emoji">🎂✨🎈</div>
        <h1>Happy Birthday<br>Rudro</h1>
        <p class="small">A little surprise is waiting for you...</p>
    </div>
</div>

<!-- SCREEN 2 -->
<div class="screen" id="screen2">
    <div class="content">
        <div class="emoji">🌙💌</div>
        <h1>For You</h1>
        <p>
            May your days be filled with laughter,<br>
            your dreams come true one by one,<br>
            and your life be surrounded by happiness,<br>
            peace and beautiful moments.
        </p>
        <p style="margin-top:20px">
            You deserve all the wonderful things<br>
            life has to offer. ✨
        </p>
        <button onclick="nextScreen(3)">Tap for the next surprise 💗</button>
    </div>
</div>

<!-- SCREEN 3 -->
<div class="screen" id="screen3">
    <div class="content">
        <div class="emoji">💗</div>
        <h1>Love You</h1>
        <p>
            More than words can ever say.<br>
            Sending you endless love<br>
            and warm wishes today. 💕
        </p>
        <button onclick="nextScreen(4)">One last surprise 🎁</button>
    </div>
</div>

<!-- SCREEN 4 -->
<div class="screen" id="screen4">
    <div class="content">
        <div class="emoji">🎉🎂🥳</div>
        <h1>Again,<br>Happy Birthday Rudro!</h1>
        <p>
            Keep smiling, keep shining,<br>
            and make this year unforgettable. ❤️
        </p>
        <button onclick="restart()">Replay the surprise ↻</button>
    </div>
</div>

<script>
let current = 1;

function nextScreen(number) {
    document.getElementById("screen" + current).classList.remove("active");
    document.getElementById("screen" + number).classList.add("active");
    current = number;
    createHearts(25);
}

function restart() {
    document.getElementById("screen" + current).classList.remove("active");
    document.getElementById("screen1").classList.add("active");
    current = 1;
    createHearts(30);
}

function createHearts(amount) {
    const symbols = ["❤️", "💗", "💕", "✨", "🌸", "💖"];

    for (let i = 0; i < amount; i++) {
        const heart = document.createElement("div");
        heart.className = "heart";
        heart.innerHTML = symbols[Math.floor(Math.random() * symbols.length)];

        heart.style.left = Math.random() * 100 + "vw";
        heart.style.animationDuration = (4 + Math.random() * 5) + "s";
        heart.style.fontSize = (15 + Math.random() * 25) + "px";

        document.body.appendChild(heart);

        setTimeout(() => heart.remove(), 9000);
    }
}

// Initial floating hearts
createHearts(30);

// First birthday text fades away, then the next message appears
setTimeout(() => {
    const first = document.getElementById("firstContent");
    first.classList.add("fadeAway");

    setTimeout(() => {
        nextScreen(2);
    }, 1800);
}, 5000);
</script>

</body>
</html>
