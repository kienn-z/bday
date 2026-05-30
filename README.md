<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>For Arni 🎂</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500&family=Great+Vibes&family=Poppins:wght@300;400&display=swap" rel="stylesheet">

<style>
*{box-sizing:border-box;margin:0;padding:0}

body{
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  font-family:"Poppins",sans-serif;
  background: radial-gradient(circle at top, #ffe3ef 0%, #eadcff 45%, #d7f3ff 100%);
  overflow:hidden;
}

/* CARD */
.card{
  width:min(430px,92vw);
  height:min(650px,88vh);
  border-radius:30px;
  background:rgba(255,248,251,.75);
  backdrop-filter:blur(18px);
  position:relative;
  overflow:hidden;
  text-align:center;
  padding:30px;
  box-shadow:0 20px 60px rgba(124,63,111,.18);
}

/* TEXT */
h1{
  font-family:"Playfair Display",serif;
  font-size:24px;
  background:linear-gradient(90deg,#d86b8f,#8b5cf6);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
}

.name{
  font-family:"Great Vibes",cursive;
  font-size:60px;
  color:#b16aa6;
  margin:6px 0 10px;
}

p{
  font-size:14px;
  color:#4b4453;
  margin:10px 0;
}

/* GIFT */
.gift{
  position:absolute;
  inset:0;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  background:rgba(255,255,255,.35);
  z-index:5;
}

.box{
  width:160px;
  height:160px;
  background:linear-gradient(135deg,#ffb6d2,#a855f7);
  border-radius:16px;
  position:relative;
  cursor:pointer;
  box-shadow:0 20px 40px rgba(0,0,0,.25);
  transition:.6s ease;
}

.box::before,
.box::after{
  content:"";
  position:absolute;
  background:#fff;
}

.box::before{
  width:100%;
  height:18px;
  top:50%;
  transform:translateY(-50%);
}

.box::after{
  width:18px;
  height:100%;
  left:50%;
  transform:translateX(-50%);
}

/* OPEN STATE */
.gift.open{
  opacity:0;
  transform:scale(.7);
  pointer-events:none;
  transition:1s ease;
}

/* BOUQUET (SAFE DISPLAY) */
.bouquet{
  position:absolute;
  inset:0;
  opacity:0;
  transform:translateY(30px);
  transition:1.2s ease;
}

.bouquet.show{
  opacity:1;
  transform:translateY(0);
}

/* IMAGE SAFETY */
.bouquet img{
  width:100%;
  height:100%;
  object-fit:cover;
  object-position:center bottom;
  display:block;
}

/* overlay */
.overlay{
  position:absolute;
  inset:0;
  background:linear-gradient(to top, rgba(255,230,240,.85), transparent 55%);
}

/* message */
.final{
  position:absolute;
  bottom:20px;
  width:100%;
  text-align:center;
  font-family:"Great Vibes",cursive;
  font-size:28px;
  color:white;
  text-shadow:0 2px 12px rgba(0,0,0,.4);
}

/* petals */
.petal{
  position:fixed;
  top:-10vh;
  font-size:18px;
  pointer-events:none;
}

/* sparkles */
.sparkle{
  position:fixed;
  font-size:10px;
  color:white;
  animation:twinkle 2.5s infinite alternate;
}
@keyframes twinkle{
  from{opacity:.2}
  to{opacity:1}
}
</style>
</head>

<body>

<div class="card">

  <!-- GIFT -->
  <div class="gift" id="gift">
    <div class="box" onclick="openGift()"></div>
    <p>tap to open gift 🎁</p>
  </div>

  <!-- CONTENT -->
  <h1>happy birthday</h1>
  <div class="name">Arni ♡</div>

  <p>i didn’t wanna just send a simple message…</p>
  <p>kasi you’re not someone ordinary to me</p>
  <p>you make things feel lighter</p>
  <p>and that means more than you think</p>

  <!-- BOUQUET -->
  <div class="bouquet" id="bouquet">
    <img src="./image.jpg" alt="bouquet"
         onerror="this.style.background='#ffd6e7'">
    <div class="overlay"></div>
    <div class="final">
      Happy Birthday, Arni 💗<br>
      i’m really glad i met you
    </div>
  </div>

</div>

<script>

let opened = false;

function openGift(){
  if(opened) return;
  opened = true;

  document.getElementById("gift").classList.add("open");

  setTimeout(()=>{
    document.getElementById("bouquet").classList.add("show");
    petals();
    sparkles();
    music();
  }, 900);
}

/* MUSIC */
function music(){
  const a = new Audio("https://cdn.pixabay.com/download/audio/2022/03/15/audio_9c6a0cdb4f.mp3");
  a.loop = true;
  a.play().catch(()=>{});
}

/* PETALS */
function petals(){
  const list=["🌸","🌷","💮"];

  for(let i=0;i<30;i++){
    const p=document.createElement("div");
    p.className="petal";
    p.innerText=list[Math.floor(Math.random()*list.length)];

    let x=Math.random()*window.innerWidth;
    let drift=(Math.random()*200-100);
    let start=performance.now();
    let dur=6000;

    function fall(t){
      let p01=Math.min((t-start)/dur,1);
      let y=p01*window.innerHeight;
      p.style.transform=`translate(${x+drift*p01}px,${y}px)`;
      p.style.opacity=1-p01;
      if(p01<1) requestAnimationFrame(fall);
      else p.remove();
    }

    document.body.appendChild(p);
    requestAnimationFrame(fall);
  }
}

/* sparkles */
function sparkles(){
  for(let i=0;i<15;i++){
    const s=document.createElement("div");
    s.className="sparkle";
    s.innerText="✨";
    s.style.left=Math.random()*100+"vw";
    s.style.top=Math.random()*100+"vh";
    document.body.appendChild(s);
  }
}

</script>

</body>
</html>
