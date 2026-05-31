<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Arni 🎂</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500&family=Great+Vibes&family=Inter:wght@300;400&display=swap" rel="stylesheet">

<style>
body {
  margin: 0;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #ffd6e0, #e6e6fa, #d6f0ff);
  font-family: "Inter", sans-serif;
  overflow: hidden;
}

/* 🎈 balloons */
.balloon {
  position: absolute;
  width: 50px;
  height: 65px;
  border-radius: 50%;
  opacity: 0.3;
  animation: float 12s linear infinite;
}
@keyframes float {
  from { transform: translateY(100vh); }
  to { transform: translateY(-10vh); }
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
}

/* header */
.header {
  transition: 1s;
}
.header.hide {
  opacity: 0;
}

/* title */
h1 {
  font-family: "Playfair Display", serif;
  font-size: 24px;
  color: #c06c84;
}

.name {
  font-family: "Great Vibes", cursive;
  font-size: 44px;
  color: #9d6bb0;
}

/* message text */
p {
  font-size: 15px;
  color: #444;
  opacity: 0;
  transform: translateY(10px);
  transition: 0.8s;
}
.show {
  opacity: 1;
  transform: translateY(0);
}

/* hide old text */
.text.hide {
  opacity: 0;
}

/* 💐 bouquet FULL + CLEAR */
.bouquet {
  position: absolute;
  bottom: -100%;
  left: 0;
  width: 100%;
  height: 100%;

  background: url('https://images.pexels.com/photos/931177/pexels-photo-931177.jpeg?auto=compress&cs=tinysrgb&w=1200')
              center/cover no-repeat;

  transition: 2s ease;
}

/* reveal */
.bouquet.show {
  bottom: 0;
}

/* 💖 FINAL TEXT (READABLE) */
.final {
  position: absolute;
  bottom: 60px;
  width: 100%;
  padding: 0 20px;
  text-align: center;

  font-family: "Inter", sans-serif;
  font-size: 16px;
  line-height: 1.6;

  color: white;
  text-shadow: 0 4px 15px rgba(0,0,0,0.4);

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
  animation: fall linear forwards;
}
@keyframes fall {
  from { transform: translateY(-10vh); }
  to { transform: translateY(110vh); }
}
</style>
</head>

<body>

<div class="card">

  <div id="header" class="header">
    <h1>happy birthday,</h1>
    <div class="name">Arni 💗</div>
  </div>

  <div id="text" class="text">
    <p id="l1">i didn’t wanna just send a simple message…</p>
    <p id="l2">kasi you’re not someone ordinary to me</p>
    <p id="l3">you make things feel lighter</p>
    <p id="l4">and that means more than you think</p>
  </div>

  <div id="bouquet" class="bouquet">
    <div class="final">
      Happy Birthday, Arni 💖<br><br>
      i’m really glad i met you.<br>
      you deserve all the soft and happy things in life 🌸
    </div>
  </div>

</div>

<script>
// balloons
const colors = ["#ffafcc","#a2d2ff","#cdb4db"];
for (let i = 0; i < 12; i++) {
  const b = document.createElement("div");
  b.className = "balloon";
  b.style.background = colors[i%3];
  b.style.left = Math.random()*100 + "vw";
  b.style.animationDuration = (8 + Math.random()*6) + "s";
  document.body.appendChild(b);
}

// text animation
const lines = ["l1","l2","l3","l4"];
lines.forEach((id, i) => {
  setTimeout(() => {
    document.getElementById(id).classList.add("show");
  }, i * 1800);
});

// petals
function createPetals() {
  const petals = ["🌸","💮","🌺"];
  for (let i = 0; i < 30; i++) {
    const p = document.createElement("div");
    p.className = "petal";
    p.innerText = petals[Math.floor(Math.random()*petals.length)];
    p.style.left = Math.random()*100 + "vw";
    p.style.animationDuration = (4 + Math.random()*4) + "s";
    document.body.appendChild(p);

    setTimeout(() => p.remove(), 8000);
  }
}

// reveal
setTimeout(() => {
  document.getElementById("bouquet").classList.add("show");

  // hide old content
  document.getElementById("header").classList.add("hide");
  document.getElementById("text").classList.add("hide");

  createPetals();
}, 9000);
</script>

</body>
</html>
