<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>For Arni 🎂</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500&family=Great+Vibes&family=Poppins:wght@300;400&display=swap" rel="stylesheet">

<style>
*{box-sizing:border-box;margin:0;padding:0}

body{
  min-height:200vh;
  display:grid;
  place-items:center;
  overflow-x:hidden;
  font-family:"Poppins",sans-serif;
  background: radial-gradient(circle at top, #ffe3ef 0%, #eadcff 38%, #d7f3ff 100%);
}

/* cinematic entrance */
body.loaded .card{
  animation:zoomIn 1.4s ease forwards;
}
@keyframes zoomIn{
  from{transform:scale(.85); opacity:0}
  to{transform:scale(1); opacity:1}
}

/* floating glow background */
body::before{
  content:"";
  position:fixed;
  inset:0;
  pointer-events:none;
  background:
    radial-gradient(circle at 20% 18%, rgba(255,255,255,.4), transparent 25%),
    radial-gradient(circle at 80% 30%, rgba(255,255,255,.25), transparent 20%);
  animation:glow 8s ease-in-out infinite alternate;
}
@keyframes glow{
  from{transform:scale(1)}
  to{transform:scale(1.05)}
}

/* CARD */
.card{
  width:min(430px,92vw);
  height:min(650px,88vh);
  border-radius:30px;
  background:rgba(255,248,251,.65);
  backdrop-filter:blur(18px);
  position:relative;
  overflow:hidden;
  text-align:center;
  padding:34px 28px;
  box-shadow:0 20px 60px rgba(124,63,111,.18);
  opacity:0;
  transform:scale(.85);
}

h1{
  font-family:"Playfair Display",serif;
  font-size:24px;
  background:linear-gradient(90deg,#d86b8f,#8b5cf6);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
}

.name{
  font-family:"Great Vibes",cursive;
  font-size:62px;
  color:#b16aa6;
  margin:6px 0 10px;
}

/* LETTERS */
p{
  font-size:14px;
  color:#4b4453;
  opacity:0;
  transform:translateY(14px);
  transition:.8s ease;
}
p.show{
  opacity:1;
  transform:translateY(0);
}

/* ===================== */
/* BOUQUET (GIFT REVEAL) */
/* ===================== */
.bouquet-wrap{
  position:absolute;
  left:0;
  right:0;
  bottom:0;
  height:58%;
  opacity:0;
  transform:translateY(40px) scaleY(.7);
  transform-origin:bottom;
  transition:1.6s cubic-bezier(.2,.9,.2,1);
}

.bouquet-wrap.show{
  opacity:1;
  transform:translateY(0) scaleY(1);
}

/* bouquet image */
.bouquet-img{
  width:100%;
  height:100%;
  object-fit:cover;
  object-position:center bottom;
  position:absolute;
}

/* soft cinematic fade */
.bouquet-overlay{
  position:absolute;
  inset:0;
  background:linear-gradient(to top, rgba(255,230,240,.95), transparent 45%);
}

/* fold animation */
.fold{
  position:absolute;
  bottom:0;
  width:50%;
  height:60%;
  background:linear-gradient(135deg,#fff,#ffb6d2);
  z-index:3;
  transition:1.5s ease;
}

.fold.left{
  left:0;
  clip-path:polygon(0 0,100% 0,80% 100%,0 100%);
}

.fold.right{
  right:0;
  clip-path:polygon(0 0,100% 0,100% 100%,20% 100%);
}

/* when revealed */
.bouquet-wrap.show .fold.left{
  transform:translateX(-120%) rotate(-8deg);
}
.bouquet-wrap.show .fold.right{
  transform:translateX(120%) rotate(8deg);
}

/* final text */
.final{
  position:absolute;
  bottom:18px;
  width:100%;
  text-align:center;
  font-family:"Great Vibes",cursive;
  font-size:26px;
  color:white;
  opacity:0;
  transform:translateY(10px);
  transition:1s ease 1s;
  text-shadow:0 2px 10px rgba(0,0,0,.3);
}

.bouquet-wrap.show .final{
  opacity:1;
  transform:translateY(0);
}

/* PETALS (parallax) */
.petal{
  position:fixed;
  top:-10vh;
  font-size:18px;
  pointer-events:none;
  z-index:10;
  opacity:.8;
}

/* sparkle */
.sparkle{
  position:fixed;
  font-size:10px;
  color:white;
  animation:twinkle 3s infinite alternate;
}
@keyframes twinkle{
  from{opacity:.2}
  to{opacity:1}
}

</style>
</head>

<body>

<audio id="music" loop>
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_9c6a0cdb4f.mp3">
</audio>

<div class="card">

  <h1>happy birthday</h1>
  <div class="name">Arni ♡</div>

  <p id="l1">i didn’t wanna just send a simple message…</p>
  <p id="l2">kasi you’re not someone ordinary to me</p>
  <p id="l3">you make things feel lighter</p>
  <p id="l4">and that means more than you think</p>

  <div class="bouquet-wrap" id="bouquet">
    <img class="bouquet-img" src="./image.jpg">
    <div class="bouquet-overlay"></div>

    <div class="fold left"></div>
    <div class="fold right"></div>

    <div class="final">
      Happy Birthday, Arni 💗
    </div>
  </div>

</div>

<script>
document.body.classList.add("loaded");

/* LETTERS */
const lines=["l1","l2","l3","l4"];
lines.forEach((id,i)=>{
  setTimeout(()=>{
    document.getElementById(id).classList.add("show");
  }, i*1500);
});

/* sparkles */
for(let i=0;i<20;i++){
  const s=document.createElement("div");
  s.className="sparkle";
  s.innerText="✨";
  s.style.left=Math.random()*100+"vw";
  s.style.top=Math.random()*100+"vh";
  document.body.appendChild(s);
}

/* petals */
function petals(){
  const list=["🌸","🌷","💮"];
  for(let i=0;i<35;i++){
    const p=document.createElement("div");
    p.className="petal";
    p.innerText=list[Math.floor(Math.random()*list.length)];

    let x=Math.random()*window.innerWidth;
    let drift=(Math.random()*200-100);
    let dur=6000+Math.random()*3000;
    let start=performance.now();

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

/* bouquet reveal */
const bouquet=document.getElementById("bouquet");
let shown=false;

function reveal(){
  if(shown) return;
  shown=true;

  bouquet.classList.add("show");
  petals();
  document.getElementById("music").play().catch(()=>{});
}

/* triggers */
setTimeout(reveal,9000);
window.addEventListener("click",reveal,{once:true});
window.addEventListener("scroll",()=>{
  if(window.scrollY>120) reveal();
});

/* parallax (light movement only, no breaking transforms) */
window.addEventListener("mousemove",(e)=>{
  const x=(e.clientX/window.innerWidth-0.5)*10;
  const y=(e.clientY/window.innerHeight-0.5)*10;
  document.querySelector(".card").style.transform=`translate(${x}px,${y}px)`;
});
</script>

</body>
</html>
