<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Raja Shekhar Raju — Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800;900&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#020d12;
  --surface:#051820;
  --card:#071e28;
  --border:#0d3040;
  --a1:#00ffcc;   /* mint */
  --a2:#00b4d8;   /* sky */
  --a3:#0077b6;   /* ocean */
  --a4:#06d6a0;   /* emerald */
  --a5:#38b000;   /* green */
  --warn:#f4d35e; /* yellow accent */
  --text:#e0f7f4;
  --muted:#4a7c8a;
  --card2:#041520;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--text);font-family:'Outfit',sans-serif;overflow-x:hidden;cursor:none}

/* ─── CURSOR ─── */
#cDot{position:fixed;width:10px;height:10px;background:var(--a1);border-radius:50%;pointer-events:none;z-index:9999;transform:translate(-50%,-50%);transition:width .15s,height .15s;box-shadow:0 0 10px var(--a1)}
#cRing{position:fixed;width:38px;height:38px;border:1.5px solid rgba(0,255,204,.4);border-radius:50%;pointer-events:none;z-index:9998;transform:translate(-50%,-50%);transition:width .3s,height .3s,border-color .3s}

/* ─── CANVAS ─── */
#bg-canvas{position:fixed;inset:0;z-index:0;pointer-events:none;opacity:.7}

/* ─── NAV ─── */
nav{
  position:fixed;top:0;left:0;right:0;z-index:300;
  display:flex;justify-content:space-between;align-items:center;
  padding:1.1rem 3rem;
  background:rgba(2,13,18,.82);
  backdrop-filter:blur(18px);
  border-bottom:1px solid rgba(0,255,204,.08);
}
.logo{
  font-family:'JetBrains Mono',monospace;font-size:.95rem;font-weight:500;
  color:var(--a1);letter-spacing:.06em;
}
.logo span{color:var(--muted)}
nav ul{display:flex;gap:2rem;list-style:none}
nav a{
  text-decoration:none;font-size:.75rem;font-weight:500;
  letter-spacing:.14em;text-transform:uppercase;color:var(--muted);
  transition:color .2s;position:relative;padding-bottom:3px;
}
nav a::after{content:'';position:absolute;bottom:0;left:0;width:0;height:1px;background:var(--a1);transition:width .3s}
nav a:hover{color:var(--a1)}
nav a:hover::after{width:100%}

/* ─── HERO ─── */
#hero{
  position:relative;min-height:100vh;display:flex;align-items:center;
  padding:8rem 3rem 4rem;z-index:1;overflow:hidden;
}
.orb{position:absolute;border-radius:50%;filter:blur(90px);pointer-events:none}
.o1{width:520px;height:520px;background:radial-gradient(circle,rgba(0,255,204,.18) 0%,transparent 70%);top:-60px;right:-60px;animation:breathe 9s ease-in-out infinite}
.o2{width:380px;height:380px;background:radial-gradient(circle,rgba(0,180,216,.14) 0%,transparent 70%);bottom:-40px;left:8%;animation:breathe 12s ease-in-out infinite 3s}
.o3{width:220px;height:220px;background:radial-gradient(circle,rgba(6,214,160,.12) 0%,transparent 70%);top:35%;left:38%;animation:breathe 7s ease-in-out infinite 1.5s}
@keyframes breathe{0%,100%{transform:scale(1);opacity:.8}50%{transform:scale(1.12);opacity:1}}

.hero-inner{position:relative;z-index:2;max-width:820px}

.h-badge{
  display:inline-flex;align-items:center;gap:.6rem;
  border:1px solid rgba(0,255,204,.28);background:rgba(0,255,204,.05);
  padding:.42rem 1.1rem;border-radius:100px;
  font-family:'JetBrains Mono',monospace;font-size:.68rem;letter-spacing:.12em;
  color:var(--a1);margin-bottom:1.8rem;
  opacity:0;animation:up .6s .1s forwards;
}
.badge-dot{width:6px;height:6px;background:var(--a1);border-radius:50%;box-shadow:0 0 8px var(--a1);animation:blink 1.6s infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.2}}

.h-name{
  font-size:clamp(2.6rem,7.5vw,6.4rem);font-weight:900;line-height:.96;
  letter-spacing:-.03em;margin-bottom:1.4rem;
  opacity:0;animation:up .8s .3s forwards;
}
.hn1{display:block;color:var(--text)}
.hn2{
  display:block;
  background:linear-gradient(120deg,var(--a1) 0%,var(--a2) 45%,var(--a4) 100%);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  background-size:200%;animation:shift 5s ease infinite .8s;
}
@keyframes shift{0%,100%{background-position:0%}50%{background-position:100%}}

.h-type{
  font-family:'JetBrains Mono',monospace;font-size:.98rem;
  color:var(--muted);margin-bottom:2.2rem;min-height:1.5em;
  opacity:0;animation:up .7s .5s forwards;
}
#typed{color:var(--a2)}
.blk{animation:blk .8s step-end infinite;color:var(--a1)}
@keyframes blk{0%,100%{opacity:1}50%{opacity:0}}

.h-sub{
  font-size:.93rem;line-height:1.88;color:var(--muted);
  max-width:480px;margin-bottom:2.4rem;
  opacity:0;animation:up .7s .7s forwards;
}
.h-sub b{color:var(--a2);font-weight:500}

.h-btns{display:flex;gap:1rem;flex-wrap:wrap;opacity:0;animation:up .7s .9s forwards}

.btn{
  display:inline-flex;align-items:center;gap:.5rem;
  padding:.88rem 1.9rem;font-size:.8rem;font-weight:600;
  font-family:'Outfit',sans-serif;letter-spacing:.07em;text-transform:uppercase;
  text-decoration:none;border-radius:6px;transition:all .25s;cursor:none;
}
.btn-glow{
  background:linear-gradient(135deg,var(--a1),var(--a4));color:#020d12;
  box-shadow:0 0 0 rgba(0,255,204,0);
}
.btn-glow:hover{transform:translateY(-3px);box-shadow:0 8px 32px rgba(0,255,204,.35)}
.btn-ghost{border:1.5px solid var(--border);color:var(--muted)}
.btn-ghost:hover{border-color:var(--a1);color:var(--a1);transform:translateY(-3px)}

.h-stats{
  display:flex;gap:2.8rem;flex-wrap:wrap;
  margin-top:3.5rem;padding-top:2rem;
  border-top:1px solid var(--border);
  opacity:0;animation:up .7s 1.1s forwards;
}
.sn{
  font-size:2.1rem;font-weight:800;display:block;
  background:linear-gradient(135deg,var(--a1),var(--a2));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.sl{font-size:.62rem;letter-spacing:.18em;text-transform:uppercase;color:var(--muted);margin-top:.1rem}

.scroll-cue{
  position:absolute;bottom:2.4rem;left:3rem;
  display:flex;align-items:center;gap:.8rem;
  font-size:.62rem;letter-spacing:.22em;text-transform:uppercase;color:var(--muted);
  opacity:0;animation:up .6s 1.4s forwards;
}
.scl{width:42px;height:1px;background:var(--border);position:relative;overflow:hidden}
.scl::after{content:'';position:absolute;inset:0;background:linear-gradient(90deg,var(--a1),var(--a4));animation:scan 2s ease-in-out infinite}
@keyframes scan{0%{transform:translateX(-100%)}100%{transform:translateX(100%)}}

/* ─── SECTIONS ─── */
section{position:relative;z-index:1;padding:6rem 3rem}
.eyebrow{
  display:flex;align-items:center;gap:.8rem;
  font-family:'JetBrains Mono',monospace;font-size:.63rem;
  letter-spacing:.26em;text-transform:uppercase;color:var(--a1);margin-bottom:.8rem;
}
.eyebrow::before{content:'';width:26px;height:1px;background:var(--a1)}
.sec-h{font-size:clamp(1.9rem,3.8vw,3rem);font-weight:800;line-height:1.1;margin-bottom:3rem}

/* ─── ABOUT ─── */
#about{background:var(--surface)}
.about-g{display:grid;grid-template-columns:1fr 1fr;gap:4rem;align-items:start}
.ab-txt{font-size:.91rem;line-height:1.94;color:var(--muted)}
.ab-txt p+p{margin-top:1rem}
.ab-txt strong{color:var(--text)}
.ab-card{
  background:var(--card);border:1px solid var(--border);border-radius:10px;padding:2rem;
  position:relative;overflow:hidden;
}
.ab-card::before{
  content:'';position:absolute;top:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,var(--a1),var(--a2),var(--a4));
}
.ab-row{
  display:flex;justify-content:space-between;align-items:center;
  padding:.85rem 0;border-bottom:1px solid var(--border);font-size:.81rem;
}
.ab-row:last-child{border-bottom:none}
.ab-row .lbl{color:var(--muted)}
.ab-row .val{color:var(--text);font-weight:500}
.ab-row .val.live{color:var(--a1);font-weight:600}

/* ─── PROJECTS ─── */
#projects{}
.proj-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(320px,1fr));gap:1.6rem}
.proj-card{
  background:var(--card);border:1px solid var(--border);border-radius:10px;
  padding:2rem;display:flex;flex-direction:column;gap:1.2rem;
  position:relative;overflow:hidden;
  opacity:0;transform:translateY(26px);
  transition:opacity .5s,transform .5s,border-color .3s,box-shadow .3s;
}
.proj-card.vis{opacity:1;transform:translateY(0)}
.proj-card::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(0,255,204,.04),rgba(0,180,216,.02),transparent 60%);
  opacity:0;transition:opacity .3s;pointer-events:none;
}
.proj-card:hover{border-color:rgba(0,255,204,.35);box-shadow:0 0 28px rgba(0,255,204,.09)}
.proj-card:hover::before{opacity:1}
.proj-top{display:flex;justify-content:space-between;align-items:flex-start;gap:1rem}
.proj-icon{
  width:46px;height:46px;border-radius:8px;
  display:flex;align-items:center;justify-content:center;
  font-size:1.4rem;flex-shrink:0;
}
.proj-links{display:flex;gap:.6rem}
.proj-link{
  width:32px;height:32px;border:1px solid var(--border);border-radius:6px;
  display:flex;align-items:center;justify-content:center;font-size:.75rem;
  color:var(--muted);text-decoration:none;transition:all .2s;cursor:none;
}
.proj-link:hover{border-color:var(--a1);color:var(--a1)}
.proj-name{font-size:1.1rem;font-weight:700;color:var(--text)}
.proj-desc{font-size:.82rem;line-height:1.7;color:var(--muted)}
.proj-tags{display:flex;flex-wrap:wrap;gap:.5rem;margin-top:.3rem}
.tag{
  padding:.25rem .7rem;border-radius:100px;font-size:.68rem;font-weight:500;
  letter-spacing:.06em;border:1px solid var(--border);color:var(--muted);
  transition:all .2s;
}
.proj-card:hover .tag{border-color:rgba(0,255,204,.2);color:var(--a2)}
.proj-stat{
  display:flex;align-items:center;gap:.5rem;
  font-size:.72rem;color:var(--muted);padding-top:.8rem;border-top:1px solid var(--border);
}
.pstat-dot{width:5px;height:5px;border-radius:50%;background:var(--a1);box-shadow:0 0 6px var(--a1)}

/* ─── SKILLS ─── */
#skills{background:var(--surface)}
.sk-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:1.1rem}
.sk{
  background:var(--card);border:1px solid var(--border);border-radius:8px;
  padding:1.5rem 1.3rem;display:flex;flex-direction:column;gap:.9rem;
  opacity:0;transform:translateY(22px) scale(.97);
  transition:opacity .4s,transform .4s,border-color .3s,box-shadow .3s;
}
.sk.vis{opacity:1;transform:translateY(0) scale(1)}
.sk:hover{border-color:rgba(0,255,204,.3);box-shadow:0 0 20px rgba(0,255,204,.07);transform:translateY(-4px) scale(1.02)!important}
.sk-ico{font-size:1.7rem;line-height:1}
.sk-nm{font-size:.78rem;font-weight:600;letter-spacing:.04em;color:var(--text)}
.sk-bg{height:3px;background:rgba(255,255,255,.05);border-radius:3px;overflow:hidden}
.sk-fill{height:100%;width:0;border-radius:3px;background:linear-gradient(90deg,var(--a1),var(--a4));transition:width 1.1s cubic-bezier(.22,1,.36,1) .2s}

/* ─── EDUCATION ─── */
#education{}
.tl{position:relative;padding-left:2.4rem}
.tl::before{
  content:'';position:absolute;left:0;top:0;bottom:0;width:1px;
  background:linear-gradient(to bottom,var(--a1),var(--a2),var(--a4),transparent);
}
.tl-it{
  position:relative;padding:0 0 3.2rem 2rem;
  opacity:0;transform:translateX(-20px);
  transition:all .5s cubic-bezier(.22,1,.36,1);
}
.tl-it.vis{opacity:1;transform:translateX(0)}
.tl-it::before{
  content:'';position:absolute;left:-.42rem;top:.3rem;
  width:10px;height:10px;border-radius:50%;background:var(--a1);
  box-shadow:0 0 0 3px rgba(0,255,204,.2),0 0 14px rgba(0,255,204,.5);
  animation:dot-pulse 2.5s ease-in-out infinite;
}
@keyframes dot-pulse{0%,100%{box-shadow:0 0 0 3px rgba(0,255,204,.2),0 0 14px rgba(0,255,204,.4)}50%{box-shadow:0 0 0 6px rgba(0,255,204,.1),0 0 22px rgba(0,255,204,.7)}}
.tl-yr{font-family:'JetBrains Mono',monospace;font-size:.62rem;letter-spacing:.2em;text-transform:uppercase;color:var(--a1);margin-bottom:.45rem}
.tl-sch{font-size:1.25rem;font-weight:700;margin-bottom:.3rem}
.tl-deg{font-size:.81rem;color:var(--muted);margin-bottom:.75rem}
.tl-score{
  display:inline-flex;align-items:center;gap:.4rem;
  background:rgba(0,255,204,.06);border:1px solid rgba(0,255,204,.2);
  padding:.28rem .85rem;border-radius:100px;font-size:.72rem;color:var(--a1);
}

/* ─── CONTACT ─── */
#contact{background:var(--surface);text-align:center}
.ct-eyebrow{justify-content:center}
.ct-eyebrow::before{display:none}
.ct-card{
  max-width:560px;margin:0 auto;
  background:var(--card);border:1px solid var(--border);border-radius:14px;
  padding:3rem 2.4rem;position:relative;overflow:hidden;
}
.ct-card::before{
  content:'';position:absolute;top:0;left:0;right:0;height:3px;
  background:linear-gradient(90deg,var(--a1),var(--a2),var(--a4),var(--a1));
  background-size:300%;animation:shift 5s ease infinite;
}
.ct-card::after{content:'';position:absolute;inset:0;background:radial-gradient(ellipse at 50% -10%,rgba(0,255,204,.06),transparent 60%);pointer-events:none}
.ct-email{font-size:1rem;font-weight:600;color:var(--a1);margin-bottom:.5rem;word-break:break-all}
.ct-phone{font-size:.86rem;color:var(--muted);margin-bottom:.4rem}
.ct-loc{font-size:.72rem;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-bottom:2rem}
.ct-btns{display:flex;gap:1rem;justify-content:center;flex-wrap:wrap;position:relative;z-index:1}

/* ─── FOOTER ─── */
footer{
  position:relative;z-index:1;padding:1.8rem 3rem;
  border-top:1px solid var(--border);
  display:flex;justify-content:space-between;align-items:center;
  font-size:.7rem;color:var(--muted);letter-spacing:.1em;
}

/* ─── KEYFRAMES ─── */
@keyframes up{from{opacity:0;transform:translateY(22px)}to{opacity:1;transform:translateY(0)}}

/* ─── MOBILE ─── */
@media(max-width:768px){
  nav{padding:1rem 1.5rem}
  nav ul{display:none}
  #hero,section{padding:5rem 1.4rem 3rem}
  .about-g{grid-template-columns:1fr;gap:2rem}
  .h-stats{gap:1.5rem}
  footer{flex-direction:column;gap:.4rem;text-align:center}
}
</style>
</head>
<body>

<canvas id="bg-canvas"></canvas>
<div id="cDot"></div>
<div id="cRing"></div>

<!-- NAV -->
<nav>
  <div class="logo">&lt;<span>RSR</span> /&gt;</div>
  <ul>
    <li><a href="#about">About</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#education">Education</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="orb o1"></div>
  <div class="orb o2"></div>
  <div class="orb o3"></div>
  <div class="hero-inner">
    <div class="h-badge"><span class="badge-dot"></span>Available for Internships</div>
    <h1 class="h-name">
      <span class="hn1">Raja Shekhar</span>
      <span class="hn2">Raju</span>
    </h1>
    <div class="h-type"><span id="typed"></span><span class="blk">|</span></div>
    <p class="h-sub">
      <b>Front-End Developer</b> skilled in JavaScript (ES6+), HTML5, CSS3, and React —
      crafting responsive interfaces that <b>boosted mobile traffic by 20%</b>.
    </p>
    <div class="h-btns">
      <a href="https://github.com" target="_blank" class="btn btn-glow">↗ GitHub</a>
      <a href="#projects" class="btn btn-ghost">View Projects</a>
    </div>
    <div class="h-stats">
      <div><span class="sn" data-t="20">0</span><span class="sl">% Mobile Boost</span></div>
      <div><span class="sn" data-t="9">0</span><span class="sl">+ Technologies</span></div>
      <div><span class="sn" data-t="4">0</span><span class="sl">Projects Built</span></div>
      <div><span class="sn" data-t="100">0</span><span class="sl">% Board Score</span></div>
    </div>
  </div>
  <div class="scroll-cue"><span class="scl"></span>Scroll down</div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="eyebrow">Introduction</div>
  <div class="sec-h">About Me</div>
  <div class="about-g">
    <div class="ab-txt">
      <p>I'm a <strong>detail-oriented Front-End Developer</strong> currently pursuing B.Tech in Electronics &amp; Communication Engineering at Sai Spurthi Institute of Technology (2023–2027).</p>
      <p>I love crafting <strong>clean, responsive UIs</strong> that feel smooth on every screen. I implemented responsive designs that improved mobile traffic by <strong>20%</strong> — and I'm always pushing for better.</p>
      <p>Outside coding I'm on the <strong>cricket pitch</strong>, traveling to new places, or learning something new to level up my skills.</p>
    </div>
    <div class="ab-card">
      <div class="ab-row"><span class="lbl">Location</span><span class="val">Sathupally, Telangana</span></div>
      <div class="ab-row"><span class="lbl">Degree</span><span class="val">B.Tech — ECE</span></div>
      <div class="ab-row"><span class="lbl">College</span><span class="val">Sai Spurthi Institute</span></div>
      <div class="ab-row"><span class="lbl">Graduation</span><span class="val">2027</span></div>
      <div class="ab-row"><span class="lbl">Focus</span><span class="val">Front-End Development</span></div>
      <div class="ab-row"><span class="lbl">Status</span><span class="val live">● Open to Internships</span></div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="eyebrow">Work</div>
  <div class="sec-h">Projects</div>
  <div class="proj-grid" id="projGrid"></div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="eyebrow">Expertise</div>
  <div class="sec-h">Skills &amp; Technologies</div>
  <div class="sk-grid" id="skGrid"></div>
</section>

<!-- EDUCATION -->
<section id="education">
  <div class="eyebrow">Academic Journey</div>
  <div class="sec-h">Education</div>
  <div class="tl">
    <div class="tl-it" data-d="0">
      <div class="tl-yr">2023 — 2027</div>
      <div class="tl-sch">Sai Spurthi Institute of Technology</div>
      <div class="tl-deg">B.Tech · Electronics &amp; Communication Engineering</div>
      <span class="tl-score">📊 7.60 CGPA</span>
    </div>
    <div class="tl-it" data-d="150">
      <div class="tl-yr">2023</div>
      <div class="tl-sch">Vidya Bharathi Jr College</div>
      <div class="tl-deg">Senior Secondary (XII) · Science</div>
      <span class="tl-score">🎯 81.00%</span>
    </div>
    <div class="tl-it" data-d="300">
      <div class="tl-yr">2021</div>
      <div class="tl-sch">Mother Teresa Techno School</div>
      <div class="tl-deg">Secondary (X) · Telangana Board</div>
      <span class="tl-score">🏆 100.00%</span>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="eyebrow ct-eyebrow">Get In Touch</div>
  <div class="sec-h" style="text-align:center">Let's Connect</div>
  <div class="ct-card">
    <div class="ct-email">rajashekharrajusrinadhuni@gmail.com</div>
    <div class="ct-phone">+91 9492531779</div>
    <div class="ct-loc">📍 Sathupally, Telangana, India</div>
    <div class="ct-btns">
      <a href="mailto:rajashekharrajusrinadhuni@gmail.com" class="btn btn-glow">Send Email</a>
      <a href="https://github.com" target="_blank" class="btn btn-ghost">↗ GitHub</a>
    </div>
  </div>
</section>

<footer>
  <span>© 2026 Srinadhuni Raja Shekhar Raju</span>
  <span>Built with HTML · CSS · JS</span>
</footer>

<script>
/* ── CURSOR ── */
const cD=document.getElementById('cDot'),cR=document.getElementById('cRing');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY});
(function loop(){
  cD.style.cssText=`position:fixed;left:${mx}px;top:${my}px;width:10px;height:10px;background:var(--a1);border-radius:50%;pointer-events:none;z-index:9999;transform:translate(-50%,-50%);box-shadow:0 0 10px var(--a1)`;
  rx+=(mx-rx)*.1;ry+=(my-ry)*.1;
  cR.style.left=rx+'px';cR.style.top=ry+'px';
  requestAnimationFrame(loop);
})();
document.querySelectorAll('a,button').forEach(el=>{
  el.addEventListener('mouseenter',()=>{cR.style.width='52px';cR.style.height='52px';cR.style.borderColor='rgba(0,255,204,.7)'});
  el.addEventListener('mouseleave',()=>{cR.style.width='38px';cR.style.height='38px';cR.style.borderColor='rgba(0,255,204,.4)'});
});

/* ── CANVAS GRID + PARTICLES ── */
const cvs=document.getElementById('bg-canvas'),ctx=cvs.getContext('2d');
let W,H,pts=[];
function resize(){
  W=cvs.width=window.innerWidth;H=cvs.height=window.innerHeight;
  pts=[];
  for(let i=0;i<55;i++) pts.push({x:Math.random()*W,y:Math.random()*H,r:Math.random()*1.4+.3,vx:(Math.random()-.5)*.28,vy:(Math.random()-.5)*.28,o:Math.random()*.35+.08});
}
window.addEventListener('resize',resize);resize();
const PC=['rgba(0,255,204,','rgba(0,180,216,','rgba(6,214,160,'];
function draw(){
  ctx.clearRect(0,0,W,H);
  /* grid */
  ctx.strokeStyle='rgba(0,255,204,.025)';ctx.lineWidth=1;
  for(let x=0;x<W;x+=70){ctx.beginPath();ctx.moveTo(x,0);ctx.lineTo(x,H);ctx.stroke()}
  for(let y=0;y<H;y+=70){ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(W,y);ctx.stroke()}
  /* particles */
  pts.forEach((p,i)=>{
    p.x+=p.vx;p.y+=p.vy;
    if(p.x<0)p.x=W;if(p.x>W)p.x=0;if(p.y<0)p.y=H;if(p.y>H)p.y=0;
    ctx.beginPath();ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
    ctx.fillStyle=PC[i%PC.length]+p.o+')';ctx.fill();
  });
  /* connections */
  for(let i=0;i<pts.length;i++) for(let j=i+1;j<pts.length;j++){
    const d=Math.hypot(pts[i].x-pts[j].x,pts[i].y-pts[j].y);
    if(d<110){ctx.beginPath();ctx.moveTo(pts[i].x,pts[i].y);ctx.lineTo(pts[j].x,pts[j].y);ctx.strokeStyle=`rgba(0,255,204,${(1-d/110)*.05})`;ctx.lineWidth=.5;ctx.stroke()}
  }
  requestAnimationFrame(draw);
}
draw();

/* ── TYPEWRITER ── */
const words=['Front-End Developer','React Developer','JavaScript Coder','UI Craftsman','Web Builder'];
let wi=0,ci=0,del=false;
function type(){
  const w=words[wi];
  document.getElementById('typed').textContent=w.slice(0,ci);
  if(!del){ci++;if(ci>w.length){del=true;setTimeout(type,1500);return}}
  else{ci--;if(ci<0){del=false;wi=(wi+1)%words.length;ci=0;setTimeout(type,400);return}}
  setTimeout(type,del?55:105);
}
type();

/* ── COUNT UP ── */
const cObs=new IntersectionObserver(es=>{es.forEach(e=>{if(e.isIntersecting){
  const el=e.target,t=+el.dataset.t,s=performance.now();
  (function tick(n){const p=Math.min((n-s)/1800,1);el.textContent=Math.round(p*t);if(p<1)requestAnimationFrame(tick)})(s);
  cObs.unobserve(el);
}})},{threshold:.5});
document.querySelectorAll('.sn').forEach(el=>cObs.observe(el));

/* ── PROJECTS ── */
const projects=[
  {
    icon:'🛒',
    iconBg:'rgba(0,255,204,.1)',
    name:'E-Commerce Website',
    desc:'A fully responsive online store with product listings, cart functionality, and checkout flow. Built with HTML, CSS and JavaScript.',
    tags:['HTML5','CSS3','JavaScript','Responsive'],
    stat:'Mobile-first design',
    github:'https://github.com',
    demo:'#'
  },
  {
    icon:'🌤️',
    iconBg:'rgba(0,180,216,.1)',
    name:'Weather Dashboard',
    desc:'Real-time weather app fetching data from OpenWeatherMap API. Displays current weather, 5-day forecast with animated icons.',
    tags:['JavaScript','API','CSS3','JSON'],
    stat:'Live API integration',
    github:'https://github.com',
    demo:'#'
  },
  {
    icon:'✅',
    iconBg:'rgba(6,214,160,.1)',
    name:'Task Manager App',
    desc:'A productivity app to create, edit, and manage daily tasks. Features drag-and-drop, local persistence, and priority levels.',
    tags:['React','CSS3','LocalStorage'],
    stat:'React SPA',
    github:'https://github.com',
    demo:'#'
  },
  {
    icon:'💬',
    iconBg:'rgba(56,176,0,.1)',
    name:'Portfolio Chat Bot',
    desc:'An interactive chatbot embedded in a portfolio page that answers visitor questions about skills, projects and contact info.',
    tags:['JavaScript','HTML5','CSS3','APIs'],
    stat:'Interactive UI',
    github:'https://github.com',
    demo:'#'
  }
];
const pg=document.getElementById('projGrid');
projects.forEach((p,i)=>{
  const c=document.createElement('div');
  c.className='proj-card';
  c.style.transitionDelay=(i*.1)+'s';
  c.innerHTML=`
    <div class="proj-top">
      <div class="proj-icon" style="background:${p.iconBg}">${p.icon}</div>
      <div class="proj-links">
        <a class="proj-link" href="${p.github}" target="_blank" title="GitHub">⌥</a>
        <a class="proj-link" href="${p.demo}" title="Live Demo">↗</a>
      </div>
    </div>
    <div class="proj-name">${p.name}</div>
    <div class="proj-desc">${p.desc}</div>
    <div class="proj-tags">${p.tags.map(t=>`<span class="tag">${t}</span>`).join('')}</div>
    <div class="proj-stat"><span class="pstat-dot"></span>${p.stat}</div>
  `;
  pg.appendChild(c);
});
const pObs=new IntersectionObserver(es=>{es.forEach(e=>{if(e.isIntersecting){e.target.classList.add('vis');pObs.unobserve(e.target)}})},{threshold:.1});
document.querySelectorAll('.proj-card').forEach(el=>pObs.observe(el));

/* ── SKILLS ── */
const skills=[
  {n:'HTML5',i:'🌐',l:92},{n:'CSS3',i:'🎨',l:88},
  {n:'JavaScript',i:'⚡',l:82},{n:'React',i:'⚛️',l:75},
  {n:'Bootstrap',i:'🅱️',l:85},{n:'MongoDB',i:'🍃',l:65},
  {n:'APIs',i:'🔗',l:72},{n:'Python',i:'🐍',l:60},
  {n:'Frontend Dev',i:'💻',l:90}
];
const sg=document.getElementById('skGrid');
skills.forEach((s,i)=>{
  const c=document.createElement('div');c.className='sk';c.style.transitionDelay=(i*.06)+'s';
  c.innerHTML=`<div class="sk-ico">${s.i}</div><div class="sk-nm">${s.n}</div><div class="sk-bg"><div class="sk-fill" data-l="${s.l}"></div></div>`;
  sg.appendChild(c);
});
const sObs=new IntersectionObserver(es=>{es.forEach(e=>{if(e.isIntersecting){
  e.target.classList.add('vis');
  setTimeout(()=>{const f=e.target.querySelector('.sk-fill');f.style.width=f.dataset.l+'%'},250);
  sObs.unobserve(e.target);
}})},{threshold:.15});
document.querySelectorAll('.sk').forEach(el=>sObs.observe(el));

/* ── TIMELINE ── */
document.querySelectorAll('.tl-it').forEach(el=>{
  const obs=new IntersectionObserver(es=>{es.forEach(e=>{if(e.isIntersecting){setTimeout(()=>el.classList.add('vis'),+el.dataset.d||0);obs.unobserve(el)}})},{threshold:.2});
  obs.observe(el);
});

/* ── PARALLAX ORBS ── */
document.addEventListener('mousemove',e=>{
  const x=(e.clientX/innerWidth-.5)*22,y=(e.clientY/innerHeight-.5)*22;
  document.querySelector('.o1').style.transform=`translate(${x}px,${y}px)`;
  document.querySelector('.o2').style.transform=`translate(${-x*.7}px,${-y*.7}px)`;
  document.querySelector('.o3').style.transform=`translate(${x*.4}px,${-y*.4}px)`;
});
</script>
</body>
</html>