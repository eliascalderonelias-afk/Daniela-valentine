#   
<!doctype html>  
<html lang="en">  
<head>  
<meta charset="utf-8"/>  
<meta name="viewport" content="width=device-width,initial-scale=1"/>  
<title>For Daniela 🌷</title>  
  
<style>  
:root{  
  --bg1:#1a0f2e;  
  --bg2:#3b1a4f;  
  --pink:#ff4d8d;  
  --pink2:#ff9fc4;  
  --tulip:#ff6fae;  
  --white:#fff7ff;  
}  
  
*{box-sizing:border-box}  
html,body{height:100%;margin:0;font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto}  
  
body{  
  overflow:hidden;  
  color:var(--white);  
  background:  
    radial-gradient(900px 600px at 20% 15%, rgba(255,111,174,.25), transparent 60%),  
    radial-gradient(900px 600px at 80% 70%, rgba(255,159,196,.2), transparent 60%),  
    linear-gradient(135deg,var(--bg1),var(--bg2));  
}  
  
.glow{  
  position:absolute;inset:-40%;  
  background:conic-gradient(from 0deg,rgba(255,111,174,.0),rgba(255,111,174,.2),rgba(255,255,255,.08),rgba(255,111,174,.0));  
  filter:blur(70px);  
  animation:float 10s ease-in-out infinite alternate;  
  pointer-events:none;  
}  
@keyframes float{  
  from{transform:translate(-2%,-2%) rotate(-10deg)}  
  to{transform:translate(2%,2%) rotate(10deg)}  
}  
  
.wrap{  
  height:100%;  
  display:grid;  
  place-items:center;  
  padding:20px;  
  position:relative;  
}  
  
.card{  
  width:min(560px,92vw);  
  padding:28px 24px;  
  border-radius:30px;  
  background:rgba(255,255,255,.1);  
  border:1px solid rgba(255,255,255,.25);  
  backdrop-filter:blur(16px);  
  text-align:center;  
  box-shadow:0 25px 80px rgba(0,0,0,.4);  
}  
  
h1{margin:6px 0;font-size:32px}  
.to{opacity:.9}  
.name{  
  background:rgba(255,111,174,.25);  
  padding:4px 12px;  
  border-radius:999px;  
  font-weight:700;  
}  
  
.question{  
  margin:18px 0;  
  font-size:22px;  
}  
  
.stage{  
  position:relative;  
  height:120px;  
}  
  
button{  
  border:0;  
  border-radius:999px;  
  padding:14px 22px;  
  font-size:16px;  
  font-weight:700;  
  cursor:pointer;  
}  
  
#yes{  
  background:linear-gradient(135deg,var(--pink),var(--pink2));  
  color:#2a0b1d;  
  box-shadow:0 15px 35px rgba(255,77,141,.45);  
}  
  
#no{  
  position:absolute;  
  background:rgba(255,255,255,.15);  
  color:white;  
  border:1px solid rgba(255,255,255,.3);  
}  
  
.signature{  
  margin-top:14px;  
  font-size:13px;  
  opacity:.8;  
}  
  
.overlay{  
  position:fixed;  
  inset:0;  
  display:none;  
  place-items:center;  
  background:rgba(15,8,30,.5);  
  backdrop-filter:blur(8px);  
  z-index:50;  
}  
  
.overlay.show{display:grid}  
  
.modal{  
  width:min(520px,92vw);  
  padding:26px;  
  border-radius:30px;  
  background:rgba(255,255,255,.12);  
  border:1px solid rgba(255,255,255,.3);  
  text-align:center;  
}  
  
.big{font-size:64px;animation:pulse 1.1s infinite}  
@keyframes pulse{50%{transform:scale(1.1)}}  
  
.confetti{  
  position:fixed;  
  inset:0;  
  pointer-events:none;  
  z-index:60;  
}  
  
.piece{  
  position:absolute;  
  top:-20px;  
  animation:fall linear forwards;  
}  
  
@keyframes fall{  
  to{transform:translate(var(--dx),110vh) rotate(var(--rot));opacity:0}  
}  
</style>  
</head>  
  
<body>  
<div class="glow"></div>  
  
<div class="wrap">  
  <div class="card">  
    <h1>Happy Valentine’s Day 💘</h1>  
    <p class="to">For <span class="name">Daniela Lisseth Lomas</span></p>  
    <div class="question">Will you be my Valentine?</div>  
  
    <div class="stage" id="stage">  
      <button id="yes">Yes 🌷</button>  
      <button id="no">No 🙈</button>  
    </div>  
  
    <div class="signature">— from Elias 💖</div>  
  </div>  
</div>  
  
<div class="overlay" id="overlay">  
  <div class="modal">  
    <div class="big">💖</div>  
    <h2>I Love You</h2>  
    <p>Daniela, you make my world softer, warmer, and brighter 🌷</p>  
    <button id="next">One more thing ✨</button>  
  </div>  
</div>  
  
<div class="overlay" id="overlay2">  
  <div class="modal">  
    <div class="big">🌷</div>  
    <h2>Forever You</h2>  
    <p>No matter where life goes, it’s always you.</p>  
    <button onclick="closeAll()">Close 💗</button>  
  </div>  
</div>  
  
<div class="confetti" id="confetti"></div>  
  
<audio id="music" loop>  
  <source src="https://cdn.pixabay.com/audio/2023/02/28/audio_4c8b35a77a.mp3" type="audio/mpeg">  
</audio>  
  
<script>  
const noBtn=document.getElementById("no");  
const stage=document.getElementById("stage");  
const yesBtn=document.getElementById("yes");  
const overlay=document.getElementById("overlay");  
const overlay2=document.getElementById("overlay2");  
const confetti=document.getElementById("confetti");  
const music=document.getElementById("music");  
  
function moveNo(){  
  const r=stage.getBoundingClientRect();  
  noBtn.style.left=Math.random()*(r.width-80)+"px";  
  noBtn.style.top=Math.random()*(r.height-40)+"px";  
}  
noBtn.addEventListener("mouseenter",moveNo);  
noBtn.addEventListener("touchstart",e=>{e.preventDefault();moveNo()});  
  
function hearts(){  
  const items=["💖","💗","🌷","💕","💞"];  
  for(let i=0;i<80;i++){  
    const p=document.createElement("div");  
    p.className="piece";  
    p.textContent=items[Math.floor(Math.random()*items.length)];  
    p.style.left=Math.random()*window.innerWidth+"px";  
    p.style.setProperty("--dx",(Math.random()*200-100)+"px");  
    p.style.setProperty("--rot",(Math.random()*360)+"deg");  
    p.style.animationDuration=(2+Math.random()*2)+"s";  
    confetti.appendChild(p);  
    p.addEventListener("animationend",()=>p.remove());  
  }  
}  
  
yesBtn.addEventListener("click",()=>{  
  music.play();  
  overlay.classList.add("show");  
  hearts();  
});  
  
document.getElementById("next").onclick=()=>{  
  overlay.classList.remove("show");  
  overlay2.classList.add("show");  
  hearts();  
};  
  
function closeAll(){  
  overlay2.classList.remove("show");  
}  
</script>  
</body>  
</html>  
