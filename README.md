<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Arni 🎂</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500&family=Great+Vibes&family=Poppins:wght@300;400&display=swap" rel="stylesheet">

<style>
body {
  margin: 0;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #ffd6e0, #e6e6fa, #d6f0ff);
  font-family: "Poppins", sans-serif;
  overflow: hidden;
}

/* 🎈 balloons (BEHIND EVERYTHING) */
.balloon {
  position: absolute;
  width: 50px;
  height: 65px;
  border-radius: 50%;
  opacity: 0.4;
  animation: float 12s linear infinite;
  z-index: 0;
}
.balloon::after {
  content:"";
  position:absolute;
  width:2px;
  height:40px;
  background:#aaa;
  top:65px;
  left:50%;
}
@keyframes float {
  from { transform: translateY(100vh); }
  to { transform: translateY(-10vh); }
}

/* ✨ sparkles */
.sparkle {
  position: absolute;
  font-size: 10px;
  opacity: 0.5;
  animation: twinkle 3s infinite alternate;
}
@keyframes twinkle {
  from { opacity: 0.2; }
  to { opacity: 1; }
}

/* 💌 card */
.card {
  width: 400px;
  height: 520px;
  border-radius: 28px;
  background: rgba(255,255,255,0.75);
  backdrop-filter: blur(18px);
  text-align: center;
  padding: 30px;
  box-shadow: 0 20px 60px rgba(0,0,0,0.15);
  position: relative;
  overflow: hidden;
  z-index: 2;
}

/* title */
h1 {
  font-family: "Playfair Display", serif;
  font-size: 24px;
  background: linear-gradient(90deg, #ff7aa2, #7b5cff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* script name */
.name {
  font-family: "Great Vibes", cursive;
  font-size: 44px;
  color: #a06cd5;
}

/* text */
p {
  font-size: 14px;
  color: #444;
  opacity: 0;
  transform: translateY(10px);
  transition: 0.8s;
}
.show {
  opacity: 1;
  transform: translateY(0);
}

/* 💐 FULL COVER BOUQUET */
.bouquet {
  position: absolute;
  bottom: -100%;
  left: 0;
  width: 100%;
  height: 100%;
  background:
    linear-gradient(to top, rgba(255,255,255,0.95), rgba(255,255,255,0.2)),
    url('https://images.pexels.com/photos/931177/pexels-photo-931177.jpeg?auto=compress&cs=tinysrgb&w=1200') center/cover no-repeat;
  transition: 2.5s ease;
  z-index: 3;
}

/* reveal = FULL COVER */
.bouquet.show {
  bottom: 0;
}

/* 💌 final text ON TOP OF FLOWERS */
.final {
  position: absolute;
  bottom: 40px;
  width: 100%;
  text-align: center;
  font-family: "Great Vibes", cursive;
  font-size: 26px;
  color: #ff4d6d;
  opacity: 0;
  transition: 1.5s;
}

.bouquet.show .final {
  opacity: 1;
}

/* 🌸 petals */
.petal {
  position: absolute;
  font-size: 16px;
  opacity: 0.7;
  animation: fall linear forwards;
  z-index: 4;
}

@keyframes fall {
  from {
    transform: translateY(-10vh) rotate(0deg);
  }
  to {
    transform: translateY(100vh) rotate(360deg);
  }
}
</style>
</head>

<body>

<!-- 🎵 MUSIC -->
<audio id="music" loop>
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_9c6a0cdb4f.mp3?filename=happy-birthday-piano-version-110624.mp3">
</audio>

<script>
// 🎈 balloons
const colors = ["#ffafcc","#a2d2ff","#cdb4db"];
for (let i = 0; i < 12; i++) {
  const b = document.createElement("div");
  b.className = "balloon";
  b.style.background = colors[i%3];
  b.style.left = Math.random()*100 + "vw";
  b.style.animationDuration = (8 + Math.random()*6) + "s";
  document.body.appendChild(b);
}

// ✨ sparkles
const stars = ["✨","✦","✧"];
for (let i = 0; i < 30; i++) {
  const s = document.createElement("div");
  s.className = "sparkle";
  s.innerText = stars[Math.floor(Math.random()*stars.length)];
  s.style.left = Math.random()*100 + "vw";
  s.style.top = Math.random()*100 + "vh";
  document.body.appendChild(s);
}

// 🎵 play music
let played = false;
document.body.addEventListener("click", () => {
  if (!played) {
    document.getElementById("music").play().catch(()=>{});
    played = true;
  }
});
</script>

<div class="card">

  <h1>happy birthday,</h1>
  <div class="name">Arni 💗</div>

  <p id="l1">i didn’t wanna just send a simple message…</p>
  <p id="l2">kasi you’re not someone ordinary to me</p>
  <p id="l3">you make things feel lighter</p>
  <p id="l4">and that means more than you think</p>

  <div id="bouquet" class="bouquet">
    <div class="final">
      Happy Birthday, Arni 💖<br>
      i’m really glad i met you
    </div>
  </div>

</div>

<script>
const lines = ["l1","l2","l3","l4"];

lines.forEach((id, i) => {
  setTimeout(() => {
    document.getElementById(id).classList.add("show");
  }, i * 1800);
});

// 🌸 petals
function createPetals() {
  const petals = ["🌸","💮","🌺"];
  for (let i = 0; i < 35; i++) {
    const p = document.createElement("div");
    p.className = "petal";
    p.innerText = petals[Math.floor(Math.random()*petals.length)];
    p.style.left = Math.random()*100 + "vw";
    p.style.animationDuration = (5 + Math.random()*3) + "s";
    document.body.appendChild(p);

    setTimeout(() => p.remove(), 8000);
  }
}

// reveal bouquet
setTimeout(() => {
  document.getElementById("bouquet").classList.add("show");
  createPetals();
}, 9000);
</script>

</body>
</html>
