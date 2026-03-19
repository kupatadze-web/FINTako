<!DOCTYPE html>
<html lang="ka">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>თამარი კუპატაძე — ბუღალტერია & ფინანსები</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
/* ═══════════════════════════════════════════
   ROOT & RESET
═══════════════════════════════════════════ */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --navy:       #0d203f;
  --navy-light: #162d55;
  --navy-mid:   #1e3a6e;
  --black:      #07090f;
  --white:      #f4f3ef;
  --gold:       #c9a96e;
  --gold-light: #e0c898;
  --grey:       #7a8090;
  --border:     rgba(201,169,110,.18);
  --ff-display: 'Cormorant Garamond', Georgia, serif;
  --ff-body:    'DM Sans', system-ui, sans-serif;
  --ease:       cubic-bezier(.4,0,.2,1);
}

html { scroll-behavior: smooth; }

body {
  background: var(--black);
  color: var(--white);
  font-family: var(--ff-body);
  font-weight: 300;
  overflow-x: hidden;
  -webkit-font-smoothing: antialiased;
}

/* noise grain */
body::after {
  content: '';
  position: fixed; inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)' opacity='.045'/%3E%3C/svg%3E");
  pointer-events: none; z-index: 9998; opacity: .4;
}

a { text-decoration: none; color: inherit; }
img { display: block; max-width: 100%; }
button { cursor: pointer; font-family: var(--ff-body); }

/* ═══════════════════════════════════════════
   SCROLLBAR
═══════════════════════════════════════════ */
::-webkit-scrollbar { width: 5px; }
::-webkit-scrollbar-track { background: var(--black); }
::-webkit-scrollbar-thumb { background: var(--navy-light); border-radius: 3px; }

/* ═══════════════════════════════════════════
   UTILITIES
═══════════════════════════════════════════ */
.tag {
  display: inline-flex; align-items: center; gap: .65rem;
  font-size: .67rem; letter-spacing: .22em; text-transform: uppercase;
  color: var(--gold); margin-bottom: .9rem;
}
.tag::before { content:''; width: 26px; height: 1px; background: var(--gold); }

.sec-title {
  font-family: var(--ff-display);
  font-size: clamp(2rem,4vw,3.4rem);
  font-weight: 300; line-height: 1.12; color: var(--white);
}
.sec-title em { font-style: italic; color: var(--gold); }

.sec-sub {
  font-size: .92rem; color: var(--grey); line-height: 1.75;
  max-width: 480px; margin-top: .9rem;
}

.divider {
  height: 1px; margin: 0 4rem;
  background: linear-gradient(to right, transparent, var(--border) 25%, var(--border) 75%, transparent);
}

/* buttons */
.btn {
  display: inline-block;
  font-size: .76rem; font-weight: 500;
  letter-spacing: .12em; text-transform: uppercase;
  padding: .85rem 2rem;
  transition: transform .2s var(--ease), background .22s, color .22s, border-color .22s;
}
.btn:hover { transform: translateY(-2px); }

.btn-gold {
  background: var(--gold); color: var(--black); border: none;
}
.btn-gold:hover { background: var(--gold-light); }

.btn-outline {
  background: transparent; color: var(--white);
  border: 1px solid rgba(244,243,239,.22);
}
.btn-outline:hover { border-color: var(--gold); color: var(--gold); }

/* reveal animation */
.reveal {
  opacity: 0; transform: translateY(22px);
  transition: opacity .7s var(--ease), transform .7s var(--ease);
}
.reveal.on { opacity: 1; transform: none; }
.d1 { transition-delay: .1s; }
.d2 { transition-delay: .2s; }
.d3 { transition-delay: .3s; }
.d4 { transition-delay: .4s; }

/* ═══════════════════════════════════════════
   NAV
═══════════════════════════════════════════ */
#nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 500;
  display: flex; align-items: center; justify-content: space-between;
  padding: 1.3rem 4rem;
  background: rgba(7,9,15,.82);
  backdrop-filter: blur(18px);
  border-bottom: 1px solid var(--border);
  transition: padding .3s var(--ease);
}
#nav.scrolled { padding: .85rem 4rem; }

.nav-logo {
  font-family: var(--ff-display);
  font-size: 1.4rem; font-weight: 400; letter-spacing: .04em;
}
.nav-logo span { color: var(--gold); }

.nav-links {
  display: flex; list-style: none;
  align-items: center; gap: 2.2rem;
}
.nav-links a {
  font-size: .72rem; letter-spacing: .14em; text-transform: uppercase;
  color: var(--grey); transition: color .2s;
}
.nav-links a:hover { color: var(--gold); }

.nav-cta {
  font-size: .7rem !important; letter-spacing: .14em !important;
  color: var(--gold) !important;
  border: 1px solid var(--gold);
  padding: .4rem 1.1rem;
  transition: background .22s, color .22s !important;
}
.nav-cta:hover { background: var(--gold); color: var(--black) !important; }

/* hamburger */
.ham { display: none; flex-direction: column; gap: 5px; background: none; border: none; padding: 4px; }
.ham span { width: 22px; height: 1.5px; background: var(--white); display: block; transition: .3s; }
.ham.open span:nth-child(1) { transform: translateY(6.5px) rotate(45deg); }
.ham.open span:nth-child(2) { opacity: 0; }
.ham.open span:nth-child(3) { transform: translateY(-6.5px) rotate(-45deg); }

.mob-menu {
  display: none; position: fixed;
  top: 60px; left: 0; right: 0; z-index: 499;
  background: var(--black);
  border-bottom: 1px solid var(--border);
  flex-direction: column; padding: 1.5rem 2rem;
  gap: 1.2rem;
}
.mob-menu.open { display: flex; }
.mob-menu a {
  font-size: .85rem; letter-spacing: .12em; text-transform: uppercase;
  color: var(--grey); transition: color .2s; padding: .3rem 0;
  border-bottom: 1px solid var(--border);
}
.mob-menu a:hover { color: var(--gold); }

/* ═══════════════════════════════════════════
   HERO
═══════════════════════════════════════════ */
#home {
  min-height: 100vh;
  display: grid; grid-template-columns: 1fr 1fr;
  align-items: center; gap: 0;
  padding: 0 4rem; padding-top: 5rem;
  position: relative; overflow: hidden;
}

.hero-bg {
  position: absolute; inset: 0; pointer-events: none;
  background:
    radial-gradient(ellipse 55% 85% at 62% 50%, rgba(13,32,63,.9) 0%, transparent 70%),
    radial-gradient(ellipse 35% 55% at 8% 85%, rgba(201,169,110,.05) 0%, transparent 60%);
}
.hero-vline {
  position: absolute; top: 0; bottom: 0; left: 50%;
  width: 1px;
  background: linear-gradient(to bottom, transparent, var(--border) 25%, var(--border) 75%, transparent);
  pointer-events: none;
}

.hero-left { position: relative; z-index: 2; padding-right: 3.5rem; }

.hero-eyebrow {
  display: inline-flex; align-items: center; gap: .7rem;
  font-size: .68rem; letter-spacing: .22em; text-transform: uppercase;
  color: var(--gold); margin-bottom: 1.8rem;
  opacity: 0; animation: fadeUp .7s .15s forwards;
}
.hero-eyebrow::before { content:''; width:28px; height:1px; background:var(--gold); }

.hero-name {
  font-family: var(--ff-display);
  font-size: clamp(3rem, 5.5vw, 5.2rem);
  font-weight: 300; line-height: 1.06; letter-spacing: -.01em;
  margin-bottom: 1.5rem;
  opacity: 0; animation: fadeUp .7s .3s forwards;
}
.hero-name em { font-style: italic; color: var(--gold); }

.hero-desc {
  font-size: .98rem; line-height: 1.78; color: var(--grey);
  max-width: 400px; margin-bottom: 2.5rem;
  opacity: 0; animation: fadeUp .7s .45s forwards;
}

.hero-btns {
  display: flex; gap: 1rem; flex-wrap: wrap;
  opacity: 0; animation: fadeUp .7s .6s forwards;
}

.hero-right {
  position: relative; z-index: 2;
  display: flex; justify-content: center; align-items: center;
  opacity: 0; animation: fadeIn 1.1s .5s forwards;
}

.portrait-wrap { position: relative; width: min(340px,90%); }

.portrait-card {
  width: 100%; aspect-ratio: 3/4;
  background: linear-gradient(150deg, var(--navy-light) 0%, var(--navy) 55%, #050810 100%);
  border: 1px solid var(--border);
  position: relative; overflow: hidden;
  display: flex; flex-direction: column;
  align-items: center; justify-content: flex-end;
  padding: 1.8rem;
}
.portrait-card::before {
  content:'';
  position: absolute; top: 0; left: 2rem; right: 2rem; height: 3px;
  background: linear-gradient(to right, transparent, var(--gold), transparent);
}
.portrait-initials {
  position: absolute; top: 50%; left: 50%;
  transform: translate(-50%,-52%);
  font-family: var(--ff-display);
  font-size: 7rem; font-weight: 300;
  color: rgba(201,169,110,.1);
  letter-spacing: -.04em; line-height: 1;
  user-select: none;
}
.portrait-badge {
  position: relative; z-index: 1;
  background: rgba(7,9,15,.65);
  backdrop-filter: blur(12px);
  border: 1px solid var(--border);
  padding: .55rem 1.1rem;
  font-size: .68rem; letter-spacing: .16em; text-transform: uppercase;
  color: var(--gold); text-align: center;
}

.stats-row {
  position: absolute; bottom: -2.2rem; left: 0; right: 0;
  display: flex; background: var(--navy); border: 1px solid var(--border);
}
.stat {
  flex: 1; padding: 1.1rem; text-align: center;
  border-right: 1px solid var(--border);
}
.stat:last-child { border-right: none; }
.stat-n {
  font-family: var(--ff-display); font-size: 1.75rem;
  font-weight: 300; color: var(--gold); line-height: 1;
}
.stat-l {
  font-size: .6rem; letter-spacing: .14em; text-transform: uppercase;
  color: var(--grey); margin-top: .25rem;
}

/* ═══════════════════════════════════════════
   COURSES
═══════════════════════════════════════════ */
#courses {
  padding: 7rem 4rem;
  background: var(--navy);
  position: relative;
}
#courses::before {
  content:''; position:absolute; top:0; left:0; right:0; height:1px;
  background: linear-gradient(to right, transparent, var(--border) 25%, var(--border) 75%, transparent);
}

.courses-hdr { margin-bottom: 3.5rem; }

.courses-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5px;
  background: var(--border);
  border: 1.5px solid var(--border);
}

.c-card {
  background: var(--navy);
  padding: 2.3rem;
  position: relative; overflow: hidden;
  transition: background .3s var(--ease);
  cursor: pointer;
}
.c-card:hover { background: var(--navy-mid); }
.c-card:hover .c-arrow { transform: translate(3px,-3px); }

.c-card::before {
  content:''; position:absolute; inset:0;
  background: radial-gradient(ellipse at 0% 0%, rgba(201,169,110,.06) 0%, transparent 65%);
  opacity:0; transition: opacity .4s;
}
.c-card:hover::before { opacity:1; }

.c-featured { border-left: 2.5px solid var(--gold); background: var(--navy-mid); }

.c-level {
  display: inline-block;
  font-size: .6rem; letter-spacing: .18em; text-transform: uppercase;
  color: var(--gold); border: 1px solid rgba(201,169,110,.28);
  padding: .22rem .55rem; margin-bottom: 1.4rem;
}
.c-icon { font-size: 1.7rem; margin-bottom: 1rem; display: block; }
.c-title {
  font-family: var(--ff-display);
  font-size: 1.38rem; font-weight: 400;
  color: var(--white); line-height: 1.25; margin-bottom: .75rem;
}
.c-desc {
  font-size: .83rem; color: var(--grey);
  line-height: 1.65; margin-bottom: 1.6rem;
}
.c-footer {
  display: flex; align-items: center; justify-content: space-between;
  padding-top: 1.1rem; border-top: 1px solid var(--border);
}
.c-price {
  font-family: var(--ff-display);
  font-size: 1.35rem; font-weight: 400; color: var(--gold);
}
.c-price small {
  font-family: var(--ff-body); font-size: .68rem;
  color: var(--grey); margin-left: .25rem;
}
.c-dur { font-size: .68rem; letter-spacing: .1em; text-transform: uppercase; color: var(--grey); }
.c-arrow {
  position: absolute; top: 2.2rem; right: 2.2rem;
  font-size: 1.1rem; color: var(--gold);
  transition: transform .25s var(--ease);
}

/* ═══════════════════════════════════════════
   BLOG
═══════════════════════════════════════════ */
#blog { padding: 7rem 4rem; background: var(--black); }

.blog-grid {
  display: grid;
  grid-template-columns: 1.65fr 1fr 1fr;
  grid-template-rows: auto auto;
  gap: 1.5px;
  background: var(--border);
  border: 1.5px solid var(--border);
  margin-top: 3.5rem;
}

.b-card {
  background: var(--black);
  padding: 2.1rem;
  cursor: pointer;
  transition: background .3s;
  position: relative;
}
.b-card:hover { background: #0c1120; }
.b-card:hover .b-title { color: var(--gold); }

.b-featured {
  grid-row: span 2;
  background: var(--navy);
  border-right: 1px solid var(--border);
  display: flex; flex-direction: column;
}
.b-featured:hover { background: var(--navy-light); }

.b-cat {
  font-size: .62rem; letter-spacing: .2em; text-transform: uppercase;
  color: var(--gold); margin-bottom: .9rem;
  display: flex; align-items: center; gap: .5rem;
}
.b-cat::before { content:''; width:16px; height:1px; background:var(--gold); }

.b-title {
  font-family: var(--ff-display);
  font-size: 1.2rem; font-weight: 400;
  color: var(--white); line-height: 1.3;
  margin-bottom: .7rem; transition: color .25s;
}
.b-featured .b-title { font-size: 1.85rem; font-weight: 300; flex-grow:1; }

.b-excerpt {
  font-size: .82rem; color: var(--grey);
  line-height: 1.65; margin-bottom: 1.5rem;
}
.b-meta {
  display: flex; align-items: center; gap: .8rem;
  font-size: .68rem; letter-spacing: .07em; color: var(--grey);
  padding-top: .9rem; border-top: 1px solid var(--border); margin-top: auto;
}
.b-dot { width:3px; height:3px; border-radius:50%; background:var(--gold); flex-shrink:0; }

/* ═══════════════════════════════════════════
   AI ASSISTANT
═══════════════════════════════════════════ */
#ai {
  padding: 7rem 4rem;
  background: var(--navy);
  position: relative; overflow: hidden;
}
#ai::before {
  content:''; position:absolute;
  top:-25%; right:-15%;
  width:550px; height:550px;
  background: radial-gradient(circle, rgba(201,169,110,.045) 0%, transparent 68%);
  pointer-events:none;
}
#ai::after { display:none; } /* override body grain for this section */

.ai-wrap {
  display: grid; grid-template-columns: 1fr 1.25fr;
  gap: 5rem; align-items: start;
}

.ai-features { list-style:none; margin-top:2.2rem; display:flex; flex-direction:column; gap:1rem; }
.ai-feat {
  display: flex; align-items: flex-start; gap: 1rem;
  padding: 1.1rem; border: 1px solid var(--border);
  background: rgba(7,9,15,.35); transition: border-color .3s, background .3s;
}
.ai-feat:hover { border-color: rgba(201,169,110,.4); background: rgba(7,9,15,.6); }
.ai-feat-icon { font-size: 1.15rem; flex-shrink:0; margin-top:.05rem; }
.ai-feat h4 { font-family: var(--ff-display); font-size:1rem; font-weight:400; color:var(--white); margin-bottom:.22rem; }
.ai-feat p  { font-size:.78rem; color:var(--grey); line-height:1.5; }

/* chat */
.chat-box {
  border: 1px solid var(--border);
  background: var(--black);
  display: flex; flex-direction: column;
  height: 530px;
}

.chat-hdr {
  padding: .9rem 1.4rem;
  border-bottom: 1px solid var(--border);
  background: var(--navy);
  display: flex; align-items: center; gap: .75rem;
}
.chat-av {
  width:36px; height:36px; background:var(--gold);
  display:flex; align-items:center; justify-content:center;
  font-family:var(--ff-display); font-size:.9rem; font-weight:600;
  color:var(--black); flex-shrink:0;
}
.chat-nm { font-family:var(--ff-display); font-size:1rem; font-weight:400; }
.chat-nm small {
  display:block; font-family:var(--ff-body);
  font-size:.6rem; letter-spacing:.13em; text-transform:uppercase; color:var(--gold);
}
.chat-online {
  margin-left:auto; display:flex; align-items:center; gap:.4rem;
  font-size:.62rem; letter-spacing:.1em; text-transform:uppercase; color:#4ade80;
}
.online-dot { width:6px;height:6px;border-radius:50%;background:#4ade80;animation:pulse 2s infinite; }

.chat-msgs {
  flex:1; overflow-y:auto; padding:1.3rem;
  display:flex; flex-direction:column; gap:.9rem;
  scrollbar-width:thin; scrollbar-color: var(--navy) transparent;
}
.chat-msgs::-webkit-scrollbar { width:4px; }
.chat-msgs::-webkit-scrollbar-thumb { background:var(--navy-light); }

.msg { max-width:82%; display:flex; flex-direction:column; gap:.25rem; }
.msg.u { align-self:flex-end; align-items:flex-end; }
.msg.b { align-self:flex-start; }

.bubble {
  padding: .8rem 1rem; font-size:.83rem; line-height:1.6;
}
.b .bubble {
  background:var(--navy); border:1px solid var(--border);
  color:var(--white); border-radius:0 8px 8px 8px;
}
.u .bubble {
  background:var(--gold); color:var(--black);
  border-radius:8px 0 8px 8px;
}
.msg-t { font-size:.6rem; color:var(--grey); letter-spacing:.05em; }

.typing-wrap { display:flex; flex-direction:column; gap:.25rem; align-self:flex-start; }
.typing {
  display:flex; align-items:center; gap:4px;
  padding:.8rem 1rem; background:var(--navy);
  border:1px solid var(--border); border-radius:0 8px 8px 8px;
}
.typing span { width:6px;height:6px;border-radius:50%;background:var(--gold);animation:typing 1.2s infinite; }
.typing span:nth-child(2) { animation-delay:.2s; }
.typing span:nth-child(3) { animation-delay:.4s; }

.chip-row {
  display:flex; flex-wrap:wrap; gap:.45rem;
  padding:.75rem 1.4rem; background:var(--navy);
  border-top:1px solid var(--border);
}
.chip {
  font-size:.68rem; letter-spacing:.07em; color:var(--gold);
  border:1px solid rgba(201,169,110,.25); padding:.28rem .65rem;
  background:transparent; transition:background .2s,border-color .2s;
  font-family:var(--ff-body);
}
.chip:hover { background:rgba(201,169,110,.09); border-color:var(--gold); }

.chat-input-row {
  padding:.85rem 1.4rem;
  border-top:1px solid var(--border);
  display:flex; gap:.7rem; align-items:center;
  background:var(--navy);
}
.chat-inp {
  flex:1; background:var(--black); border:1px solid var(--border);
  color:var(--white); padding:.65rem .9rem;
  font-family:var(--ff-body); font-size:.83rem;
  outline:none; transition:border-color .2s;
}
.chat-inp:focus { border-color:rgba(201,169,110,.5); }
.chat-inp::placeholder { color:rgba(122,128,144,.45); }
.chat-send {
  width:38px;height:38px; background:var(--gold); border:none;
  color:var(--black); font-size:1rem;
  display:flex;align-items:center;justify-content:center;
  transition:background .2s,transform .2s; flex-shrink:0;
}
.chat-send:hover { background:var(--gold-light); transform:scale(1.06); }

/* ═══════════════════════════════════════════
   CONTACT
═══════════════════════════════════════════ */
#contact { padding: 7rem 4rem; background: var(--black); }

.contact-wrap {
  display:grid; grid-template-columns:1fr 1.5fr;
  gap:5.5rem; align-items:start;
}

.c-info-item {
  display:flex; align-items:flex-start; gap:.9rem;
  padding:1.3rem 0; border-bottom:1px solid var(--border);
}
.c-info-icon { font-size:1rem; flex-shrink:0; margin-top:.1rem; }
.c-info-lbl { font-size:.62rem;letter-spacing:.18em;text-transform:uppercase;color:var(--gold);margin-bottom:.28rem; }
.c-info-val { font-size:.88rem; color:var(--white); }

.form { display:flex; flex-direction:column; gap:1.1rem; }
.form-row-2 { display:grid; grid-template-columns:1fr 1fr; gap:1.1rem; }
.fg { display:flex; flex-direction:column; gap:.42rem; }
.flbl { font-size:.62rem;letter-spacing:.18em;text-transform:uppercase;color:var(--grey); }
.finp, .fsel, .ftxt {
  background:var(--navy); border:1px solid var(--border);
  color:var(--white); padding:.78rem .95rem;
  font-family:var(--ff-body); font-size:.86rem;
  outline:none; width:100%; transition:border-color .2s;
}
.finp:focus, .fsel:focus, .ftxt:focus { border-color:rgba(201,169,110,.5); }
.finp::placeholder, .ftxt::placeholder { color:rgba(122,128,144,.38); }
.fsel { appearance:none; cursor:pointer; }
.fsel option { background:var(--navy); }
.ftxt { resize:vertical; min-height:108px; }
.form-note {
  font-size:.7rem; color:var(--grey); line-height:1.5;
  padding:.7rem .9rem; border-left:2px solid var(--gold);
  background:rgba(13,32,63,.4);
}

/* ═══════════════════════════════════════════
   FOOTER
═══════════════════════════════════════════ */
footer {
  padding:2.2rem 4rem;
  border-top:1px solid var(--border);
  background:var(--black);
  display:flex; align-items:center; justify-content:space-between;
  flex-wrap:wrap; gap:1.2rem;
}
.foot-logo { font-family:var(--ff-display); font-size:1.05rem; color:var(--grey); }
.foot-logo span { color:var(--gold); }
.foot-copy { font-size:.7rem;letter-spacing:.08em;color:var(--grey); }
.foot-links { display:flex; gap:1.8rem; }
.foot-links a { font-size:.66rem;letter-spacing:.14em;text-transform:uppercase;color:var(--grey);transition:color .2s; }
.foot-links a:hover { color:var(--gold); }

/* ═══════════════════════════════════════════
   KEYFRAMES
═══════════════════════════════════════════ */
@keyframes fadeUp { from{opacity:0;transform:translateY(18px)} to{opacity:1;transform:none} }
@keyframes fadeIn { from{opacity:0} to{opacity:1} }
@keyframes pulse  { 0%,100%{opacity:1} 50%{opacity:.35} }
@keyframes typing { 0%,100%{transform:translateY(0);opacity:.4} 50%{transform:translateY(-4px);opacity:1} }

/* ═══════════════════════════════════════════
   RESPONSIVE
═══════════════════════════════════════════ */
@media(max-width:1080px){
  #home       { grid-template-columns:1fr; padding:7rem 2.5rem 4rem; }
  .hero-vline { display:none; }
  .hero-left  { padding-right:0; text-align:center; }
  .hero-desc  { max-width:100%; }
  .hero-btns  { justify-content:center; }
  .hero-eyebrow{ justify-content:center; }
  .hero-right { order:-1; margin-bottom:3rem; }
  .portrait-wrap{ width:min(260px,80%); }
  .stats-row  { position:static; margin-top:2rem; }
  .courses-grid{ grid-template-columns:1fr 1fr; }
  .blog-grid  { grid-template-columns:1fr 1fr; }
  .b-featured { grid-row:auto; grid-column:span 2; border-right:none; border-bottom:1px solid var(--border); }
  .ai-wrap    { grid-template-columns:1fr; gap:3rem; }
  .contact-wrap{ grid-template-columns:1fr; gap:3.5rem; }
  .divider    { margin:0 2.5rem; }
  #nav        { padding:1.2rem 2rem; }
  #nav.scrolled{ padding:.8rem 2rem; }
  #courses,#blog,#ai,#contact { padding:5.5rem 2.5rem; }
  footer      { padding:2rem 2.5rem; }
}

@media(max-width:680px){
  #nav        { padding:1rem 1.5rem; }
  #nav.scrolled{ padding:.75rem 1.5rem; }
  .nav-links  { display:none !important; }
  .ham        { display:flex; }
  .courses-grid{ grid-template-columns:1fr; }
  .blog-grid  { grid-template-columns:1fr; }
  .b-featured { grid-column:auto; }
  .form-row-2 { grid-template-columns:1fr; }
  #home,#courses,#blog,#ai,#contact { padding-left:1.5rem; padding-right:1.5rem; }
  .divider    { margin:0 1.5rem; }
  footer      { flex-direction:column; align-items:flex-start; padding:2rem 1.5rem; }
}
</style>
</head>
<body>

<!-- ══════════ NAV ══════════ -->
<nav id="nav">
  <a class="nav-logo" href="#home">თამარ <span>.</span></a>
  <ul class="nav-links" id="navLinks">
    <li><a href="#home"   onclick="closeMob()">მთავარი</a></li>
    <li><a href="#courses" onclick="closeMob()">კურსები</a></li>
    <li><a href="#blog"   onclick="closeMob()">ბლოგი</a></li>
    <li><a href="#ai"     onclick="closeMob()">AI ასისტენტი</a></li>
    <li><a href="#contact" onclick="closeMob()" class="nav-cta">კონტაქტი</a></li>
  </ul>
  <button class="ham" id="ham" onclick="toggleMob()" aria-label="მენიუ">
    <span></span><span></span><span></span>
  </button>
</nav>

<div class="mob-menu" id="mobMenu">
  <a href="#home"    onclick="closeMob()">მთავარი</a>
  <a href="#courses" onclick="closeMob()">კურსები</a>
  <a href="#blog"    onclick="closeMob()">ბლოგი</a>
  <a href="#ai"      onclick="closeMob()">AI ასისტენტი</a>
  <a href="#contact" onclick="closeMob()">კონტაქტი</a>
</div>

<!-- ══════════ HERO ══════════ -->
<section id="home">
  <div class="hero-bg"></div>
  <div class="hero-vline"></div>

  <div class="hero-left">
    <div class="hero-eyebrow">სერტიფიცირებული ბუღალტერი · CPA</div>
    <h1 class="hero-name">
      გამარჯობა,<br>
      მე ვარ <em>თამარ</em><br>
      კუპატაძე
    </h1>
    <p class="hero-desc">
      ბუღალტერიასა და ფინანსებში 10+ წლის გამოცდილებით,
      ვასწავლი ბიზნეს-ფინანსებს, გადასახადებს
      და AI-ის გამოყენებას ფინანსურ ანალიზში.
    </p>
    <div class="hero-btns">
      <a href="#courses" class="btn btn-gold">კურსები იხილე</a>
      <a href="#ai"      class="btn btn-outline">FinGPT-ს სცადე</a>
    </div>
  </div>

  <div class="hero-right">
    <div class="portrait-wrap">
      <div class="portrait-card">
        <div class="portrait-initials">ТК</div>
        <div class="portrait-badge">CPA &nbsp;·&nbsp; MBA ფინანსები</div>
      </div>
      <div class="stats-row">
        <div class="stat"><div class="stat-n">10+</div><div class="stat-l">წელი</div></div>
        <div class="stat"><div class="stat-n">800+</div><div class="stat-l">სტუდენტი</div></div>
        <div class="stat"><div class="stat-n">12</div><div class="stat-l">კურსი</div></div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ══════════ COURSES ══════════ -->
<section id="courses">
  <div class="courses-hdr reveal">
    <div class="tag">სასწავლო პროგრამები</div>
    <h2 class="sec-title">კურსები, რომლებიც<br><em>კარიერას შეცვლის</em></h2>
    <p class="sec-sub">პრაქტიკული ბუღალტრული განათლება — დამწყებიდან პროფესიონალამდე</p>
  </div>

  <div class="courses-grid reveal d1">

    <div class="c-card c-featured">
      <span class="c-arrow">↗</span>
      <span class="c-icon">📊</span>
      <span class="c-level">⭐ Featured</span>
      <div class="c-title">ბუღალტრული აღრიცხვა — სრული კურსი</div>
      <div class="c-desc">საფუძვლებიდან IFRS სტანდარტებამდე. ბალანსი, მოგება-ზარალი, ფულის ნაკადები და ფინანსური ანალიზი.</div>
      <div class="c-footer">
        <div class="c-price">₾ 490<small>/ სრული</small></div>
        <div class="c-dur">8 კვირა</div>
      </div>
    </div>

    <div class="c-card">
      <span class="c-arrow">↗</span>
      <span class="c-icon">💰</span>
      <span class="c-level">Beginner</span>
      <div class="c-title">პირადი ფინანსების მართვა</div>
      <div class="c-desc">ბიუჯეტირება, დაზოგვა, ინვესტიციები და ფინანსური თავისუფლება — ნებისმიერისთვის.</div>
      <div class="c-footer">
        <div class="c-price">₾ 190<small>/ სრული</small></div>
        <div class="c-dur">4 კვირა</div>
      </div>
    </div>

    <div class="c-card">
      <span class="c-arrow">↗</span>
      <span class="c-icon">🤖</span>
      <span class="c-level">Advanced</span>
      <div class="c-title">AI ბუღალტერიაში</div>
      <div class="c-desc">GPT, Copilot და ავტომატიზაციის ხელსაწყოები ფინანსური ანალიტიკოსებისთვის.</div>
      <div class="c-footer">
        <div class="c-price">₾ 350<small>/ სრული</small></div>
        <div class="c-dur">5 კვირა</div>
      </div>
    </div>

    <div class="c-card">
      <span class="c-arrow">↗</span>
      <span class="c-icon">🏢</span>
      <span class="c-level">Business</span>
      <div class="c-title">ბიზნეს-გეგმა & ფინანსური პროგნოზი</div>
      <div class="c-desc">Excel ფინანსური მოდელები, DCF, Break-even ანალიზი და სტარტაპ-ბიუჯეტირება.</div>
      <div class="c-footer">
        <div class="c-price">₾ 280<small>/ სრული</small></div>
        <div class="c-dur">3 კვირა</div>
      </div>
    </div>

    <div class="c-card">
      <span class="c-arrow">↗</span>
      <span class="c-icon">📋</span>
      <span class="c-level">Intermediate</span>
      <div class="c-title">საგადასახადო დეკლარაციები</div>
      <div class="c-desc">საქართველოს საგადასახადო კოდექსი, დღგ, საშემოსავლო გადასახადი და ყოველთვიური ანგარიშობა.</div>
      <div class="c-footer">
        <div class="c-price">₾ 240<small>/ სრული</small></div>
        <div class="c-dur">3 კვირა</div>
      </div>
    </div>

    <div class="c-card">
      <span class="c-arrow">↗</span>
      <span class="c-icon">📈</span>
      <span class="c-level">All Levels</span>
      <div class="c-title">Excel ფინანსებისთვის</div>
      <div class="c-desc">Pivot Tables, VLOOKUP, ფინანსური ფუნქციები, დაშბორდები. პრაქტიკული პროექტებით.</div>
      <div class="c-footer">
        <div class="c-price">₾ 160<small>/ სრული</small></div>
        <div class="c-dur">2 კვირა</div>
      </div>
    </div>

  </div>
</section>

<div class="divider"></div>

<!-- ══════════ BLOG ══════════ -->
<section id="blog">
  <div class="reveal">
    <div class="tag">სტატიები & ინსაიტები</div>
    <h2 class="sec-title">ბლოგი — <em>ცოდნა</em><br>რომელსაც ვიყენებ</h2>
    <p class="sec-sub">ბუღალტერია, ფინანსები და AI — ყოველ კვირა ახალი სტატია</p>
  </div>

  <div class="blog-grid reveal d1">

    <div class="b-card b-featured">
      <div class="b-cat">AI & ფინანსები</div>
      <div class="b-title">როგორ იცვლება ბუღალტერია AI-ის ეპოქაში — 5 ყველაზე მნიშვნელოვანი ტენდენცია 2025 წლისთვის</div>
      <div class="b-excerpt">ხელოვნური ინტელექტი აღარ არის მხოლოდ ტექნოლოგიური ფენომენი — ის ხდება ყოველდღიური ბუღალტრული სამუშაოს ნაწილი. განვიხილავთ, რა იცვლება და როგორ მოვემზადოთ პროფესიონალებმა ახალი რეალობისთვის...</div>
      <div class="b-meta">
        <span>თამარ კ.</span><div class="b-dot"></div>
        <span>12 მარტი, 2025</span><div class="b-dot"></div>
        <span>8 წთ</span>
      </div>
    </div>

    <div class="b-card">
      <div class="b-cat">გადასახადები</div>
      <div class="b-title">2025 — ახალი საგადასახადო ცვლილებები: რა უნდა ვიცოდეთ</div>
      <div class="b-meta">
        <span>5 მარტი</span><div class="b-dot"></div><span>5 წთ</span>
      </div>
    </div>

    <div class="b-card">
      <div class="b-cat">ფინანსური ანალიზი</div>
      <div class="b-title">P&L vs Cash Flow — ფინანსური ანგარიშების სწორი წაკითხვა</div>
      <div class="b-meta">
        <span>28 თებ.</span><div class="b-dot"></div><span>6 წთ</span>
      </div>
    </div>

    <div class="b-card">
      <div class="b-cat">Excel & ავტომატიზაცია</div>
      <div class="b-title">10 Excel ფორმულა, რომელიც ბუღალტერს დრო დაუზოგავს</div>
      <div class="b-meta">
        <span>20 თებ.</span><div class="b-dot"></div><span>4 წთ</span>
      </div>
    </div>

    <div class="b-card">
      <div class="b-cat">IFRS</div>
      <div class="b-title">IFRS 15 — შემოსავლების აღიარება: პრაქტიკული გზამკვლევი</div>
      <div class="b-meta">
        <span>14 თებ.</span><div class="b-dot"></div><span>7 წთ</span>
      </div>
    </div>

  </div>
</section>

<div class="divider"></div>

<!-- ══════════ AI ASSISTANT ══════════ -->
<section id="ai">
  <div class="ai-wrap">

    <div class="reveal">
      <div class="tag">FinGPT by Tamari</div>
      <h2 class="sec-title">AI ასისტენტი<br><em>ფინანსებში</em></h2>
      <p class="sec-sub">დასვი ნებისმიერი კითხვა ბუღალტერიაზე, გადასახადებზე ან ფინანსებზე — FinGPT გიპასუხებს.</p>

      <ul class="ai-features">
        <li class="ai-feat">
          <div class="ai-feat-icon">⚡</div>
          <div>
            <h4>სწრაფი პასუხები</h4>
            <p>ბუღალტრული კონცეფციები, IFRS სტანდარტები, კალკულაციები — წამებში</p>
          </div>
        </li>
        <li class="ai-feat">
          <div class="ai-feat-icon">🇬🇪</div>
          <div>
            <h4>ქართული კონტექსტი</h4>
            <p>საქართველოს საგადასახადო კოდექსი, RS.ge, ეროვნული ბანკის რეგულაციები</p>
          </div>
        </li>
        <li class="ai-feat">
          <div class="ai-feat-icon">📚</div>
          <div>
            <h4>სასწავლო რეჟიმი</h4>
            <p>ნებისმიერ კონცეფციას ახსნის მარტივი ენით, მაგალითთან ერთად</p>
          </div>
        </li>
        <li class="ai-feat">
          <div class="ai-feat-icon">🔐</div>
          <div>
            <h4>კონფიდენციალურობა</h4>
            <p>შენი მონაცემები დაცულია — პერსონალური ფინანსური ინფო ჩვენთან რჩება</p>
          </div>
        </li>
      </ul>
    </div>

    <div class="reveal d2">
      <div class="chat-box">

        <div class="chat-hdr">
          <div class="chat-av">FG</div>
          <div class="chat-nm">
            FinGPT
            <small>by Tamari · AI ასისტენტი</small>
          </div>
          <div class="chat-online">
            <div class="online-dot"></div>Online
          </div>
        </div>

        <div class="chat-msgs" id="chatMsgs">
          <div class="msg b">
            <div class="bubble">გამარჯობა! 👋 მე ვარ <strong>FinGPT</strong> — თამარის AI ასისტენტი ბუღალტერიასა და ფინანსებში.<br><br>დამისვი ნებისმიერი კითხვა — ვუპასუხებ ქართულ კონტექსტში!</div>
            <div class="msg-t">ახლა</div>
          </div>
        </div>

        <div class="chip-row" id="chipRow">
          <button class="chip" onclick="chip(this)">რა არის IFRS?</button>
          <button class="chip" onclick="chip(this)">დღგ-ს ახსნა</button>
          <button class="chip" onclick="chip(this)">P&amp;L vs Balance Sheet</button>
          <button class="chip" onclick="chip(this)">ROE გაანგარიშება</button>
          <button class="chip" onclick="chip(this)">Depreciation მეთოდები</button>
        </div>

        <div class="chat-input-row">
          <input class="chat-inp" id="chatInp" type="text"
            placeholder="კითხვა ბუღალტერიაზე..."
            onkeydown="if(event.key==='Enter')sendMsg()"/>
          <button class="chat-send" onclick="sendMsg()">→</button>
        </div>

      </div>
    </div>

  </div>
</section>

<div class="divider"></div>

<!-- ══════════ CONTACT ══════════ -->
<section id="contact">
  <div class="contact-wrap">

    <div class="reveal">
      <div class="tag">კონტაქტი</div>
      <h2 class="sec-title">მოდი<br><em>ვისაუბროთ</em></h2>
      <p class="sec-sub" style="margin-bottom:2.5rem">კონსულტაცია, კურსებზე ჩარიცხვა ან უბრალოდ კითხვა — ყოველთვის ხელმისაწვდომი ვარ.</p>

      <div class="c-info-item">
        <div class="c-info-icon">✉️</div>
        <div><div class="c-info-lbl">ელ-ფოსტა</div><div class="c-info-val">tamar@fingeorgia.ge</div></div>
      </div>
      <div class="c-info-item">
        <div class="c-info-icon">📱</div>
        <div><div class="c-info-lbl">ტელეფონი / WhatsApp</div><div class="c-info-val">+995 555 00 00 00</div></div>
      </div>
      <div class="c-info-item">
        <div class="c-info-icon">📍</div>
        <div><div class="c-info-lbl">მდებარეობა</div><div class="c-info-val">თბილისი, საქართველო</div></div>
      </div>
      <div class="c-info-item">
        <div class="c-info-icon">💼</div>
        <div><div class="c-info-lbl">LinkedIn</div><div class="c-info-val">linkedin.com/in/tamari-fin</div></div>
      </div>
    </div>

    <div class="reveal d2">
      <form class="form" onsubmit="submitForm(event)">
        <div class="form-row-2">
          <div class="fg">
            <label class="flbl">სახელი *</label>
            <input class="finp" type="text" placeholder="შენი სახელი" required/>
          </div>
          <div class="fg">
            <label class="flbl">ელ-ფოსტა *</label>
            <input class="finp" type="email" placeholder="example@gmail.com" required/>
          </div>
        </div>
        <div class="fg">
          <label class="flbl">ტელეფონი</label>
          <input class="finp" type="tel" placeholder="+995 5XX XX XX XX"/>
        </div>
        <div class="fg">
          <label class="flbl">თემა</label>
          <select class="fsel">
            <option value="">— აირჩიე —</option>
            <option>კურსზე ჩარიცხვა</option>
            <option>კორპორატიული ტრენინგი</option>
            <option>AI კონსულტაცია</option>
            <option>ბუღალტრული სერვისი</option>
            <option>სხვა</option>
          </select>
        </div>
        <div class="fg">
          <label class="flbl">შეტყობინება *</label>
          <textarea class="ftxt" placeholder="გვიამბე შენი კითხვის ან პროექტის შესახებ..." required></textarea>
        </div>
        <div class="form-note">
          ჩვეულებრივ ვპასუხობ 24 საათის განმავლობაში. კორპორატიული შეკითხვებისთვის — მოიცადე 48 საათამდე.
        </div>
        <div>
          <button type="submit" class="btn btn-gold" id="submitBtn">შეტყობინების გაგზავნა →</button>
        </div>
      </form>
    </div>

  </div>
</section>

<!-- ══════════ FOOTER ══════════ -->
<footer>
  <div class="foot-logo">თამარ <span>კუპატაძე</span></div>
  <div class="foot-copy">© 2025 · ყველა უფლება დაცულია</div>
  <div class="foot-links">
    <a href="#">LinkedIn</a>
    <a href="#">YouTube</a>
    <a href="#">Instagram</a>
    <a href="#">Telegram</a>
  </div>
</footer>

<!-- ══════════════════════════════════════════
     JAVASCRIPT
══════════════════════════════════════════ -->
<script>
/* ─── NAV ─── */
const nav = document.getElementById('nav');
window.addEventListener('scroll', () => {
  nav.classList.toggle('scrolled', window.scrollY > 50);
});

function toggleMob() {
  const h = document.getElementById('ham');
  const m = document.getElementById('mobMenu');
  h.classList.toggle('open');
  m.classList.toggle('open');
}
function closeMob() {
  document.getElementById('ham').classList.remove('open');
  document.getElementById('mobMenu').classList.remove('open');
}

/* ─── REVEAL ─── */
const ro = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) { e.target.classList.add('on'); ro.unobserve(e.target); }
  });
}, { threshold: 0.1 });
document.querySelectorAll('.reveal').forEach(el => ro.observe(el));

/* ─── CHAT ─── */
const BOT = {
  'ifrs':         'IFRS (International Financial Reporting Standards) — საერთაშორისო ფინანსური ანგარიშგების სტანდარტები. 📊\n\nეს არის წესების ერთობლიობა, რომელიც განსაზღვრავს ფინანსური ანგარიშების შედგენის წესს. საქართველოში სავალდებულოა სახელმწიფო ინტერესსა და საჯარო კომპანიებში.\n\nძირითადი სტანდარტები: IFRS 15 (შემოსავლები), IFRS 16 (იჯარა), IAS 36 (აქტივების გაუფასურება).',
  'დღგ':          'დღგ — დამატებული ღირებულების გადასახადი, 18% საქართველოში. 💰\n\n✅ 100 000 ₾-ზე მეტი ბრუნვა → სავალდებულო რეგისტრაცია RS.ge-ზე\n✅ დღგ-ს დეკლარაცია → ყოველთვიური (მომდევნო თვის 15-მდე)\n✅ გამოქვითვა → შეძენილ საქონელ/მომსახურებაზე გადახდილი დღგ',
  'p&l':          'P&L vs Balance Sheet — ორი სხვადასხვა "სურათი": 📋\n\n📈 P&L (მოგება-ზარალი): გვიჩვენებს შემოსავლებს, ხარჯებს, მოგებას ᲞᲔᲠᲘᲝᲓᲘᲡᲗᲕᲘᲡ\n\n📋 Balance Sheet (ბალანსი): გვიჩვენებს აქტივებს, ვალდებულებებს, კაპიტალს ᲙᲝᲜᲙᲠᲔᲢᲣᲚ ᲗᲐᲠᲘᲦᲖᲔ\n\nP&L → "კარგად ვიმუშავეთ?" / Balance Sheet → "რა გვაქვს ხელში?"',
  'roe':          'ROE (Return on Equity) — კაპიტალის რენტაბელობა: 💪\n\n📐 ფორმულა: ROE = წმინდა მოგება ÷ საკუთარი კაპიტალი × 100%\n\n📌 მაგ: მოგება 50 000 ₾, კაპიტალი 250 000 ₾\n→ ROE = 50 000 ÷ 250 000 × 100% = 20%\n\n📊 ROE > 15% — კარგი\nROE > 25% — ძალიან ძლიერი ბიზნესი',
  'depreciation': 'Depreciation (ცვეთა/ამორტიზაცია) — ძირითადი მეთოდები: 🔧\n\n1️⃣ Straight-Line: ყოველ წელს ერთნაირი თანხა\n   → (ღირ. - სანარჩ.) ÷ სიცოცხლე\n\n2️⃣ Declining Balance: ყოველ წელს % ნარჩენი ღირებულებიდან\n   → სწრაფი ცვეთა პირველ წლებში\n\n3️⃣ Units of Production: გამოყენების მიხედვით\n   → მანქანებისა და ტექნიკისთვის იდეალური',
};

function getReply(text) {
  const t = text.toLowerCase();
  if (t.includes('ifrs') || t.includes('iffrs')) return BOT['ifrs'];
  if (t.includes('დღგ') || t.includes('vat')) return BOT['დღგ'];
  if (t.includes('p&l') || t.includes('balance') || t.includes('ბალანს')) return BOT['p&l'];
  if (t.includes('roe') || t.includes('roi') || t.includes('რენტაბ')) return BOT['roe'];
  if (t.includes('depreciation') || t.includes('ცვეთ') || t.includes('ამორ')) return BOT['depreciation'];
  const fallback = [
    'კარგი კითხვა! ეს თემა ჩვენს კურსებში დეტალურად არის განხილული. 📚\n\nუფრო კონკრეტული ახსნისთვის — მიმართე თამარს პირდაპირ კონტაქტის გვერდზე.',
    'საინტერესო საკითხია! FinGPT-ის სრული ვერსია მალე ხელმისაწვდომი გახდება. 🚀\n\nამ კონკრეტულ კითხვაზე პასუხი კი კურსებში გაქვს — შეამოწმე Courses სექცია.',
    'პასუხი დამოკიდებულია კონკრეტულ სიტუაციაზე. 💬\n\nპერსონალური კონსულტაციისთვის — დაუკავშირდი თამარს: tamari@fingeorgia.ge',
  ];
  return fallback[Math.floor(Math.random() * fallback.length)];
}

function now() {
  return new Date().toLocaleTimeString('ka-GE',{hour:'2-digit',minute:'2-digit'});
}

function appendMsg(text, type) {
  const box = document.getElementById('chatMsgs');
  const div = document.createElement('div');
  div.className = 'msg ' + type;
  div.innerHTML = `<div class="bubble">${text.replace(/\n/g,'<br>')}</div><div class="msg-t">${now()}</div>`;
  box.appendChild(div);
  box.scrollTop = box.scrollHeight;
}

function showTyping() {
  const box = document.getElementById('chatMsgs');
  const div = document.createElement('div');
  div.className = 'typing-wrap'; div.id = 'typingIndicator';
  div.innerHTML = `<div class="typing"><span></span><span></span><span></span></div><div class="msg-t">${now()}</div>`;
  box.appendChild(div);
  box.scrollTop = box.scrollHeight;
}

function sendMsg() {
  const inp = document.getElementById('chatInp');
  const text = inp.value.trim();
  if (!text) return;
  appendMsg(text, 'u');
  inp.value = '';
  document.getElementById('chipRow').style.display = 'none';
  showTyping();
  setTimeout(() => {
    document.getElementById('typingIndicator')?.remove();
    appendMsg(getReply(text), 'b');
  }, 900 + Math.random() * 500);
}

function chip(btn) {
  document.getElementById('chatInp').value = btn.textContent;
  sendMsg();
}

/* ─── CONTACT FORM ─── */
function submitForm(e) {
  e.preventDefault();
  const btn = document.getElementById('submitBtn');
  btn.textContent = '✓ გაიგზავნა!';
  btn.style.background = '#4ade80';
  btn.style.color = '#07090f';
  btn.disabled = true;
  setTimeout(() => {
    btn.textContent = 'შეტყობინების გაგზავნა →';
    btn.style.background = '';
    btn.style.color = '';
    btn.disabled = false;
    e.target.reset();
  }, 3500);
}
</script>
</body>
</html>
