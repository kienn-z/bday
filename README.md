<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>For Arni 🎂</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500&family=Great+Vibes&family=Poppins:wght@300;400&display=swap" rel="stylesheet">

<style>
*{box-sizing:border-box;margin:0;padding:0}

body{
  min-height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  font-family:"Poppins",sans-serif;
  background: radial-gradient(circle at top, #ffe3ef 0%, #eadcff 40%, #d7f3ff 100%);
  overflow-x:hidden;
}

/* soft glow */
body::before{
  content:"";
  position:fixed;
  inset:0;
  pointer-events:none;
  background:
    radial-gradient(circle at 20% 20%, rgba(255,255,255,.4), transparent 25%),
    radial-gradient(circle at 80% 30%, rgba(255,255,255,.2), transparent 20%);
}

/* CARD */
.card{
  width:min(430px,92vw);
  height:min(650px,88vh);
  border-radius:30px;
  background:rgba(255,248,251,.7);
  backdrop-filter:blur(18px);
  position:relative;
  overflow:hidden;
  text-align:center;
  padding:34px 28px;
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
  font-size:64px;
  color:#b16aa6;
  margin:6px 0 10px;
}

p{
  font-size:14px;
  color:#4b4453;
  margin:14px 0;
}

/* BOUQUET — ALWAYS VISIBLE */
.bouquet-wrap{
  position:absolute;
  left:0;
  right:0;
  bottom:0;
  height:60%;
}

.bouquet-img{
  width:100%;
  height:100%;
  object-fit:cover;
  object-position:center bottom;
}

/* overlay soft fade */
.overlay{
  position:absolute;
  inset:0;
  background:linear-gradient(to top, rgba(255,230,240,.85), transparent 50%);
}

/* message ON bouquet */
.final{
  position:absolute;
  bottom:20px;
  width:100%;
  text-align:center;
  font-family:"Great Vibes",cursive;
  font-size:28px;
  color:white;
  text-shadow:0 2px 12px rgba(0,0,0,.35);
}

/* petals */
.petal{
  position:fixed;
  top:-10vh;
  font-size:18px;
  pointer-events:none;
  z-index:10;
}

/* sparkles */
.sparkle{
  position:fixed;
  font-size:10px;
  color:white;
  opacity:.7;
  animation:twinkle 2.5s infinite alternate;
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

  <p>i didn’t wanna just send a simple message…</p>
  <p>kasi you’re not someone ordinary to me</p>
  <p>you make things feel lighter</p>
  <p>and that means more than you think</p>

  <!-- BOUQUET ALWAYS SHOWN -->
  <div class="bouquet-wrap">

    <img class="bouquet-img" src="./image.jpg" alt="bouquet">

    <div class="overlay"></div>

    <div class="final">
      Happy Birthday, Arni 💗<br>
      i’m really glad i met you
    </div>

  </div>

</div>

<script>
/* sparkles */
for(let i=0;i<18;i++){
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
  for(let i=0;i<30;i++){
    const p=document.createElement("div");
    p.className="petal";
    p.innerText=list[Math.floor(Math.random()*list.length)];

    let x=Math.random()*window.innerWidth;
    let drift=(Math.random()*200-100);
    let start=performance.now();
    let dur=7000;

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

/* auto effects */
setTimeout(()=>{
  petals();
  document.getElementById("music").play().catch(()=>{});
}, 1500);
</script>

</body>
</html>
