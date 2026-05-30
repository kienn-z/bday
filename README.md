<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>For Arni 🎂</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500&family=Great+Vibes&family=Poppins:wght@300;400&display=swap" rel="stylesheet">

<style>
*{box-sizing:border-box}
html,body{margin:0;padding:0}
body{
  min-height:100vh;
  display:grid;
  place-items:center;
  overflow-x:hidden;
  font-family:"Poppins",sans-serif;
  background:
    radial-gradient(circle at top, #ffe3ef 0%, #eadcff 38%, #d7f3ff 100%);
}

body::before{
  content:"";
  position:fixed;
  inset:0;
  pointer-events:none;
  background:
    radial-gradient(circle at 20% 18%, rgba(255,255,255,.42), transparent 20%),
    radial-gradient(circle at 82% 15%, rgba(255,255,255,.25), transparent 18%),
    radial-gradient(circle at 70% 72%, rgba(255,255,255,.18), transparent 22%);
  animation:bgGlow 8s ease-in-out infinite alternate;
}

@keyframes bgGlow{
  from{transform:scale(1); opacity:.72}
  to{transform:scale(1.03); opacity:1}
}

.sparkle{
  position:fixed;
  font-size:10px;
  color:#fff;
  opacity:.6;
  animation:twinkle 2.8s infinite alternate;
  pointer-events:none;
  z-index:1;
}
@keyframes twinkle{
  from{opacity:.2; transform:scale(.85)}
  to{opacity:1; transform:scale(1.15)}
}

.card{
  width:min(430px,92vw);
  height:min(650px,88vh);
  border-radius:30px;
  background:rgba(255,248,251,.62);
  backdrop-filter:blur(18px);
  position:relative;
  overflow:hidden;
  z-index:2;
  text-align:center;
  padding:34px 28px;
  border:1px solid rgba(255,255,255,.55);
  box-shadow:
    0 20px 60px rgba(124,63,111,.18),
    inset 0 0 0 1px rgba(255,255,255,.55);
}

.card::before{
  content:"";
  position:absolute;
  inset:10px;
  border-radius:24px;
  border:1px solid rgba(255,255,255,.65);
  pointer-events:none;
}

.card::after{
  content:"";
  position:absolute;
  inset:-12px;
  border-radius:40px;
  border:2px solid rgba(255,182,200,.22);
  box-shadow:
    0 0 18px rgba(255,182,200,.22),
    0 0 38px rgba(201,182,255,.18),
    0 0 70px rgba(255,255,255,.12);
  animation:fairyGlow 2.8s ease-in-out infinite alternate;
  pointer-events:none;
}

@keyframes fairyGlow{
  from{opacity:.45; filter:blur(1px)}
  to{opacity:1; filter:blur(0)}
}

h1{
  font-family:"Playfair Display",serif;
  font-size:24px;
  margin:10px 0 0;
  background:linear-gradient(90deg,#d86b8f,#8b5cf6);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  position:relative;
  z-index:4;
}

.name{
  font-family:"Great Vibes",cursive;
  font-size:clamp(52px,8vw,64px);
  line-height:1;
  color:#b16aa6;
  margin:6px 0 10px;
  position:relative;
  z-index:4;
}

p{
  font-size:14px;
  color:#4b4453;
  opacity:0;
  transform:translateY(12px);
  transition:.8s ease;
  margin:18px 0;
  position:relative;
  z-index:4;
}
.show{
  opacity:1;
  transform:translateY(0);
}

/* bouquet area */
.bouquet-wrap{
  position:absolute;
  left:0;
  right:0;
  bottom:0;
  height:56%;
  z-index:3;
  opacity:0;
  transform:translateY(24%);
  transition:transform 2.2s cubic-bezier(.2,.9,.2,1), opacity 1.2s ease;
  overflow:hidden;
  pointer-events:none;
}
.bouquet-wrap.show{
  opacity:1;
  transform:translateY(0);
}

.bouquet-img{
  position:absolute;
  inset:0;
  width:100%;
  height:100%;
  object-fit:cover;
  object-position:center bottom;
  display:block;
  z-index:1;
}

.bouquet-overlay{
  position:absolute;
  inset:0;
  z-index:2;
  background:
    linear-gradient(to top, rgba(255, 229, 237, .92) 0%, rgba(255,255,255,0) 42%),
    linear-gradient(to bottom, rgba(255,255,255,.10) 0%, rgba(255,255,255,.06) 100%);
}

.bouquet-fold{
  position:absolute;
  bottom:0;
  width:36%;
  height:42%;
  background:linear-gradient(135deg, rgba(255,255,255,.35), rgba(255,190,210,.75));
  z-index:3;
  filter:blur(.3px);
}

.bouquet-fold.left{
  left:-2%;
  clip-path:polygon(0 0, 100% 0, 76% 100%, 0 100%);
  transform:skewX(-12deg);
}

.bouquet-fold.right{
  right:-2%;
  clip-path:polygon(0 0, 100% 0, 100% 100%, 24% 100%);
  transform:skewX(12deg);
}

.wrap-shadow{
  position:absolute;
  left:10%;
  right:10%;
  bottom:-4px;
  height:18px;
  background:radial-gradient(ellipse at center, rgba(120,40,80,.25), transparent 70%);
  filter:blur(8px);
  z-index:2;
}

.final{
  position:absolute;
  left:0;
  right:0;
  bottom:22px;
  z-index:5;
  text-align:center;
  font-family:"Great Vibes",cursive;
  font-size:28px;
  color:#fff;
  text-shadow:0 2px 14px rgba(120,20,60,.55);
  opacity:0;
  transition:1.2s ease;
}
.bouquet-wrap.show .final{
  opacity:1;
}

.petal{
  position:fixed;
  top:-10vh;
  font-size:18px;
  opacity:.85;
  z-index:10;
  pointer-events:none;
  filter:drop-shadow(0 3px 2px rgba(255,120,160,.25));
}

.scroll-hint{
  position:fixed;
  bottom:18px;
  left:50%;
  transform:translateX(-50%);
  color:rgba(90,60,90,.75);
  font-size:12px;
  letter-spacing:.08em;
  text-transform:uppercase;
  z-index:20;
  animation:hintPulse 1.5s ease-in-out infinite alternate;
}
@keyframes hintPulse{
  from{opacity:.5; transform:translateX(-50%) translateY(0)}
  to{opacity:1; transform:translateX(-50%) translateY(-6px)}
}
</style>
</head>

<body>

<audio id="music" loop>
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_9c6a0cdb4f.mp3?filename=happy-birthday-piano-version-110624.mp3">
</audio>

<div class="scroll-hint">scroll / tap to reveal</div>

<div class="card" id="card">
  <h1>happy birthday,</h1>
  <div class="name">Arni ♡</div>

  <p id="l1">i didn’t wanna just send a simple message…</p>
  <p id="l2">kasi you’re not someone ordinary to me</p>
  <p id="l3">you make things feel lighter</p>
  <p id="l4">and that means more than you think</p>

  <div id="bouquetWrap" class="bouquet-wrap">
    <img class="bouquet-img" src="./image.jpg" alt="bouquet">
    <div class="bouquet-overlay"></div>
    <div class="bouquet-fold left"></div>
    <div class="bouquet-fold right"></div>
    <div class="wrap-shadow"></div>
    <div class="final">
      Happy Birthday, Arni! 💗<br>
      i’m really glad i met you
    </div>
  </div>
</div>

<script>
const lines = ["l1","l2","l3","l4"];
lines.forEach((id, i) => {
  setTimeout(() => document.getElementById(id).classList.add("show"), i * 1800);
});

for (let i = 0; i < 18; i++) {
  const s = document.createElement("div");
  s.className = "sparkle";
  s.innerText = ["✨","✦","✧"][Math.floor(Math.random()*3)];
  s.style.left = Math.random()*100 + "vw";
  s.style.top = Math.random()*100 + "vh";
  s.style.animationDuration = (2 + Math.random()*2) + "s";
  document.body.appendChild(s);
}

let played = false;
function playMusic(){
  if (played) return;
  document.getElementById("music").play().catch(()=>{});
  played = true;
}

function createPetals(count=42){
  const petals = ["🌸","💮","🌺","🌷"];
  for (let i = 0; i < count; i++) {
    const p = document.createElement("div");
    p.className = "petal";
    p.innerText = petals[Math.floor(Math.random()*petals.length)];
    const startX = Math.random() * window.innerWidth;
    const drift = (Math.random() * 220 - 110);
    const size = 12 + Math.random() * 16;
    const dur = 5.5 + Math.random() * 3.5;
    p.style.left = startX + "px";
    p.style.fontSize = size + "px";
    p.style.opacity = 0.5 + Math.random() * 0.5;
    document.body.appendChild(p);

    const start = performance.now();
    function fall(now){
      const t = (now - start) / 1000;
      const p01 = Math.min(t / dur, 1);
      const ease = 1 - Math.pow(1 - p01, 3);
      const x = startX + drift * ease + Math.sin(t * 2.2) * 16;
      const y = -30 + (window.innerHeight + 80) * ease;
      const rot = t * 160;
      p.style.transform = `translate(${x - startX}px, ${y}px) rotate(${rot}deg)`;
      p.style.opacity = String(1 - p01);
      if (p01 < 1) requestAnimationFrame(fall);
      else p.remove();
    }
    requestAnimationFrame(fall);
  }
}

const bouquetWrap = document.getElementById("bouquetWrap");
function reveal(){
  bouquetWrap.classList.add("show");
  createPetals();
  playMusic();
}

setTimeout(reveal, 9000);
window.addEventListener("click", reveal, { once: true });
window.addEventListener("scroll", () => {
  const y = window.scrollY;
  bouquetWrap.style.transform = `translateY(${Math.max(0, 24 - y/18)}px)`;
});
</script>

</body>
</html>
