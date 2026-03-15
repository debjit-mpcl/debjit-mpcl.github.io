<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Debjit Chowdhury — AI Solutions Architect</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=JetBrains+Mono:wght@300;400;500&family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet"/>
<style>
/* ══════════════════════════════════════════════════════════
   ROOT & RESET
══════════════════════════════════════════════════════════ */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --g:#76b900; --g2:#a8e000; --g3:#4a7800;
  --bg:#060a0d; --bg2:#0b1117; --bg3:#111820;
  --card:#0f1923; --card2:#131f2b;
  --border:#1a2d3a; --border2:#243545;
  --text:#dce8f0; --muted:#5d7d8f; --dim:#2a4050;
  --white:#ffffff;
  --font-display:'Syne',sans-serif;
  --font-body:'Outfit',sans-serif;
  --font-mono:'JetBrains Mono',monospace;
  --glow: 0 0 40px rgba(118,185,0,.18);
  --glow-sm: 0 0 16px rgba(118,185,0,.12);
}
html{scroll-behavior:smooth;font-size:16px}
body{font-family:var(--font-body);background:var(--bg);color:var(--text);overflow-x:hidden;line-height:1.6}

/* ── Animated background grid ─────────────────────────────── */
body::before{
  content:'';position:fixed;inset:0;z-index:0;
  background-image:
    linear-gradient(rgba(118,185,0,.028) 1px,transparent 1px),
    linear-gradient(90deg,rgba(118,185,0,.028) 1px,transparent 1px);
  background-size:52px 52px;
  animation:gridShift 20s linear infinite;
}
@keyframes gridShift{0%{background-position:0 0}100%{background-position:52px 52px}}

/* ── Scrollbar ─────────────────────────────────────────────── */
::-webkit-scrollbar{width:5px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--g3);border-radius:4px}

/* ══════════════════════════════════════════════════════════
   NAVBAR
══════════════════════════════════════════════════════════ */
#nav{
  position:fixed;top:0;left:0;right:0;z-index:100;
  display:flex;align-items:center;justify-content:space-between;
  padding:0 40px;height:60px;
  background:rgba(6,10,13,.85);
  backdrop-filter:blur(18px);-webkit-backdrop-filter:blur(18px);
  border-bottom:1px solid var(--border);
}
/* NVIDIA Logo SVG inline */
.nv-logo{display:flex;align-items:center;gap:10px;text-decoration:none}
.nv-logo svg{height:22px;width:auto}
.nv-divider{width:1px;height:22px;background:var(--border2)}
.nv-partner{font-family:var(--font-mono);font-size:.6rem;color:var(--muted);letter-spacing:.12em;text-transform:uppercase;line-height:1.2}
.nv-partner span{display:block;color:var(--g);font-size:.55rem}
.nav-right{display:flex;align-items:center;gap:28px}
.nav-link{font-family:var(--font-mono);font-size:.62rem;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);text-decoration:none;transition:color .2s}
.nav-link:hover{color:var(--g)}
.nav-badge{
  font-family:var(--font-mono);font-size:.6rem;letter-spacing:.08em;
  padding:5px 14px;border:1px solid var(--g);color:var(--g);
  border-radius:3px;text-transform:uppercase;
  background:rgba(118,185,0,.06);
  box-shadow:var(--glow-sm);
}

/* ══════════════════════════════════════════════════════════
   HERO
══════════════════════════════════════════════════════════ */
#hero{
  position:relative;min-height:100vh;
  display:flex;align-items:center;
  padding:100px 0 80px;overflow:hidden;
}
#hero-canvas{position:absolute;inset:0;z-index:0;opacity:.55}
.hero-glow{
  position:absolute;top:-10%;right:-8%;
  width:700px;height:700px;
  background:radial-gradient(circle,rgba(118,185,0,.09) 0%,transparent 65%);
  pointer-events:none;z-index:0;
}
.hero-glow2{
  position:absolute;bottom:-15%;left:-5%;
  width:500px;height:500px;
  background:radial-gradient(circle,rgba(0,80,140,.07) 0%,transparent 65%);
  pointer-events:none;z-index:0;
}
.container{max-width:1160px;margin:0 auto;padding:0 40px;position:relative;z-index:1}
.hero-grid{display:grid;grid-template-columns:1fr 320px;gap:60px;align-items:center}

/* eyebrow */
.eyebrow{
  display:inline-flex;align-items:center;gap:10px;
  font-family:var(--font-mono);font-size:.65rem;letter-spacing:.2em;
  color:var(--g);text-transform:uppercase;margin-bottom:20px;
}
.eyebrow::before,.eyebrow::after{content:'';flex-shrink:0;height:1px;background:var(--g)}
.eyebrow::before{width:24px}
.eyebrow::after{width:12px}

.hero-name{
  font-family:var(--font-display);
  font-size:clamp(3rem,6vw,5rem);
  font-weight:800;line-height:.95;
  letter-spacing:-.03em;color:var(--white);
  margin-bottom:6px;
}
.hero-name .accent{
  color:transparent;
  -webkit-text-stroke:2px var(--g);
  display:inline-block;
}
.hero-role{
  font-size:1.05rem;font-weight:500;
  color:var(--muted);margin-bottom:8px;
  letter-spacing:.01em;
}
.hero-company{
  display:inline-flex;align-items:center;gap:8px;
  font-family:var(--font-mono);font-size:.72rem;
  color:var(--g);letter-spacing:.05em;
  padding:5px 14px;border:1px solid rgba(118,185,0,.3);
  border-radius:3px;background:rgba(118,185,0,.05);
  margin-bottom:28px;
}
.hero-company::before{content:'▸';font-size:.8rem}
.hero-tags{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:32px}
.htag{
  font-family:var(--font-mono);font-size:.62rem;letter-spacing:.06em;
  text-transform:uppercase;padding:5px 13px;
  border-radius:3px;transition:all .25s;
}
.htag-dim{border:1px solid var(--border2);color:var(--muted)}
.htag-dim:hover{border-color:var(--g);color:var(--g)}
.htag-green{border:1px solid var(--g);color:var(--g);background:rgba(118,185,0,.08);box-shadow:var(--glow-sm)}

/* hero meta */
.hero-meta{display:flex;gap:20px;flex-wrap:wrap}
.hm{display:flex;align-items:center;gap:7px;font-size:.78rem;color:var(--muted)}
.hm svg{width:13px;height:13px;stroke:var(--g);fill:none;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;flex-shrink:0}

/* stat column */
.stat-col{display:flex;flex-direction:column;gap:14px}
.stat-card{
  position:relative;overflow:hidden;
  background:var(--card);border:1px solid var(--border);
  border-radius:14px;padding:22px 22px 20px;
  transition:all .3s;
}
.stat-card::before{
  content:'';position:absolute;left:0;top:0;bottom:0;
  width:3px;background:linear-gradient(to bottom,var(--g),var(--g3));
  border-radius:3px 0 0 3px;
}
.stat-card::after{
  content:'';position:absolute;top:0;right:0;
  width:80px;height:80px;
  background:radial-gradient(circle at top right,rgba(118,185,0,.08),transparent 70%);
}
.stat-card:hover{border-color:rgba(118,185,0,.5);box-shadow:var(--glow);transform:translateX(-3px)}
.stat-n{
  font-family:var(--font-display);
  font-size:2.4rem;font-weight:800;color:var(--g);
  line-height:1;margin-bottom:4px;
}
.stat-l{font-size:.7rem;color:var(--muted);letter-spacing:.05em;font-weight:500}

/* ══════════════════════════════════════════════════════════
   SECTION STRUCTURE
══════════════════════════════════════════════════════════ */
section{padding:80px 0;border-top:1px solid var(--border)}
.sec-hd{display:flex;align-items:center;gap:16px;margin-bottom:48px}
.sec-num{font-family:var(--font-mono);font-size:.6rem;color:var(--dim);letter-spacing:.12em}
.sec-title{font-family:var(--font-display);font-size:1.4rem;font-weight:700;letter-spacing:-.015em;color:var(--white)}
.sec-line{flex:1;height:1px;background:var(--border)}
.sec-sub{font-family:var(--font-mono);font-size:.62rem;color:var(--muted);white-space:nowrap}

/* ══════════════════════════════════════════════════════════
   CERTIFICATIONS
══════════════════════════════════════════════════════════ */
.cert-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:16px}
.cert-card{
  background:var(--card);border:1px solid var(--border);border-radius:14px;
  padding:22px 18px;position:relative;overflow:hidden;
  transition:all .35s cubic-bezier(.22,1,.36,1);cursor:default;
}
.cert-card::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(140deg,rgba(118,185,0,.07) 0%,transparent 55%);
  opacity:0;transition:opacity .35s;
}
.cert-card:hover{border-color:var(--g);transform:translateY(-6px) scale(1.01);box-shadow:0 20px 50px rgba(118,185,0,.12)}
.cert-card:hover::before{opacity:1}
.cc-icon{
  width:40px;height:40px;background:rgba(118,185,0,.1);border-radius:10px;
  display:flex;align-items:center;justify-content:center;margin-bottom:14px;
  transition:background .3s;
}
.cert-card:hover .cc-icon{background:rgba(118,185,0,.2)}
.cc-icon svg{width:20px;height:20px;stroke:var(--g);fill:none;stroke-width:1.8;stroke-linecap:round;stroke-linejoin:round}
.cc-name{font-family:var(--font-display);font-size:.82rem;font-weight:700;color:var(--white);line-height:1.35;margin-bottom:10px}
.cc-issuer{font-size:.67rem;color:var(--muted);margin-bottom:5px;font-weight:400}
.cc-date{font-family:var(--font-mono);font-size:.64rem;color:var(--g);letter-spacing:.05em}
.cc-badge{
  position:absolute;top:14px;right:14px;
  width:22px;height:22px;background:var(--g);border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  box-shadow:0 0 10px rgba(118,185,0,.4);
}
.cc-badge svg{width:11px;height:11px;stroke:#000;fill:none;stroke-width:3;stroke-linecap:round;stroke-linejoin:round}
.cert-card.featured{border-color:rgba(118,185,0,.35);background:linear-gradient(135deg,rgba(118,185,0,.06),var(--card))}

/* ══════════════════════════════════════════════════════════
   CORE SPECIALISATIONS (NEW SECTION)
══════════════════════════════════════════════════════════ */
.spec-hero{
  display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:20px;
}
.spec-card{
  border-radius:16px;padding:32px 30px;
  position:relative;overflow:hidden;
  border:1px solid var(--border);
  background:var(--card);
  transition:all .35s;
}
.spec-card::after{
  content:'';position:absolute;top:-60px;right:-60px;
  width:200px;height:200px;border-radius:50%;
  background:radial-gradient(circle,rgba(118,185,0,.1),transparent 70%);
  transition:opacity .3s;
}
.spec-card:hover{border-color:rgba(118,185,0,.5);box-shadow:0 20px 60px rgba(118,185,0,.1);transform:translateY(-4px)}
.spec-card.primary{
  border-color:rgba(118,185,0,.4);
  background:linear-gradient(135deg,rgba(118,185,0,.07) 0%,var(--card) 50%);
  grid-column:1/-1;
  display:grid;grid-template-columns:1fr 1fr;gap:30px;align-items:center;
}
.spec-icon-large{
  width:56px;height:56px;background:rgba(118,185,0,.12);border-radius:14px;
  display:flex;align-items:center;justify-content:center;margin-bottom:18px;
}
.spec-icon-large svg{width:28px;height:28px;stroke:var(--g);fill:none;stroke-width:1.6;stroke-linecap:round;stroke-linejoin:round}
.spec-label{
  font-family:var(--font-mono);font-size:.6rem;letter-spacing:.15em;
  color:var(--g);text-transform:uppercase;margin-bottom:10px;
}
.spec-title{
  font-family:var(--font-display);font-size:1.3rem;font-weight:700;
  color:var(--white);margin-bottom:12px;line-height:1.2;
}
.spec-body{font-size:.83rem;color:var(--muted);line-height:1.7}
.spec-chips{display:flex;flex-wrap:wrap;gap:7px;margin-top:16px}
.spec-chip{
  font-family:var(--font-mono);font-size:.6rem;letter-spacing:.05em;
  padding:4px 10px;background:rgba(118,185,0,.08);
  border:1px solid rgba(118,185,0,.2);color:var(--g);border-radius:3px;
}
.spec-visual{display:flex;flex-direction:column;gap:10px}
.spec-metric{
  background:rgba(118,185,0,.05);border:1px solid rgba(118,185,0,.15);
  border-radius:10px;padding:14px 18px;
  display:flex;align-items:center;gap:14px;
}
.sm-icon{font-size:1.3rem}
.sm-text{font-size:.78rem;color:var(--muted);line-height:1.4}
.sm-text strong{display:block;color:var(--white);font-size:.82rem;margin-bottom:1px}

/* sub-spec grid */
.spec-sub{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}
.spec-sub .spec-card::after{display:none}

/* ══════════════════════════════════════════════════════════
   SKILLS
══════════════════════════════════════════════════════════ */
.skills-wrap{display:grid;grid-template-columns:1.2fr 1fr;gap:50px;align-items:start}

/* bars */
.skill-group-label{
  font-family:var(--font-mono);font-size:.58rem;letter-spacing:.15em;
  text-transform:uppercase;color:var(--g);margin-bottom:14px;margin-top:24px;
  padding-bottom:6px;border-bottom:1px solid var(--border);
}
.skill-group-label:first-child{margin-top:0}
.skill-row{margin-bottom:13px}
.skill-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:5px}
.skill-name{font-size:.8rem;color:var(--text);font-weight:500}
.skill-name.core{color:var(--white);font-weight:600}
.skill-pct{font-family:var(--font-mono);font-size:.67rem;color:var(--g)}
.bar-track{height:5px;background:var(--bg3);border-radius:3px;overflow:hidden;position:relative}
.bar-fill{
  height:100%;border-radius:3px;width:0;
  background:linear-gradient(90deg,var(--g3),var(--g),var(--g2));
  transition:width 1.6s cubic-bezier(.16,1,.3,1);
  box-shadow:0 0 8px rgba(118,185,0,.3);
}
.bar-fill.core{background:linear-gradient(90deg,var(--g),var(--g2));box-shadow:0 0 12px rgba(168,224,0,.4)}
.bar-fill.dim{background:linear-gradient(90deg,var(--dim),var(--g3));box-shadow:none}

/* tech stack logos/pills */
.tech-stack{margin-top:24px}
.stack-title{font-family:var(--font-mono);font-size:.58rem;letter-spacing:.15em;text-transform:uppercase;color:var(--muted);margin-bottom:14px}
.stack-pills{display:flex;flex-wrap:wrap;gap:9px}
.stack-pill{
  display:flex;align-items:center;gap:7px;
  padding:8px 14px;background:var(--card2);
  border:1px solid var(--border2);border-radius:8px;
  font-size:.75rem;color:var(--text);font-weight:500;
  transition:all .25s;
}
.stack-pill:hover{border-color:var(--g);color:var(--white)}
.stack-pill .dot{width:7px;height:7px;border-radius:50%;flex-shrink:0}
.dot-green{background:var(--g);box-shadow:0 0 6px var(--g)}
.dot-muted{background:var(--dim)}

/* domain matrix */
.domain-matrix{display:grid;grid-template-columns:repeat(3,1fr);gap:10px}
.dm-cell{
  background:var(--card);border:1px solid var(--border);border-radius:11px;
  padding:18px 12px;text-align:center;transition:all .25s;
}
.dm-cell:hover{border-color:var(--g);background:rgba(118,185,0,.06)}
.dm-cell.highlight{border-color:rgba(118,185,0,.3);background:rgba(118,185,0,.05)}
.dm-icon{font-size:1.5rem;margin-bottom:6px;display:block}
.dm-name{font-size:.7rem;color:var(--muted);line-height:1.3;font-weight:500}
.dm-cell.highlight .dm-name{color:var(--g)}

/* ══════════════════════════════════════════════════════════
   EXPERIENCE TIMELINE
══════════════════════════════════════════════════════════ */
.timeline{position:relative;padding-left:32px}
.timeline::before{
  content:'';position:absolute;left:7px;top:10px;bottom:10px;width:1px;
  background:linear-gradient(to bottom,var(--g) 0%,var(--dim) 70%,transparent 100%);
}
.tl-item{position:relative;margin-bottom:36px}
.tl-dot{
  position:absolute;left:-32px;top:6px;
  width:15px;height:15px;border-radius:50%;
  background:var(--bg);border:2px solid var(--g);
  transition:all .25s;box-shadow:0 0 0 0 rgba(118,185,0,0);
}
.tl-item:hover .tl-dot{background:var(--g);box-shadow:0 0 0 5px rgba(118,185,0,.15)}
.tl-period{
  font-family:var(--font-mono);font-size:.62rem;color:var(--g);
  letter-spacing:.1em;text-transform:uppercase;margin-bottom:4px;
}
.tl-header{display:flex;align-items:flex-start;justify-content:space-between;gap:10px;flex-wrap:wrap;margin-bottom:3px}
.tl-title{font-family:var(--font-display);font-size:1rem;font-weight:700;color:var(--white)}
.tl-co{font-size:.78rem;color:var(--muted);margin-bottom:10px}
.tl-desc{font-size:.81rem;color:var(--muted);line-height:1.72}
.tl-chips{display:flex;flex-wrap:wrap;gap:7px;margin-top:12px}
.tl-chip{
  font-family:var(--font-mono);font-size:.6rem;letter-spacing:.04em;
  padding:4px 10px;background:rgba(118,185,0,.07);
  border:1px solid rgba(118,185,0,.2);color:var(--g);border-radius:3px;
}

/* ══════════════════════════════════════════════════════════
   VALUE PROPOSITION
══════════════════════════════════════════════════════════ */
.value-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:16px}
.vcard{
  background:var(--card);border:1px solid var(--border);
  border-radius:14px;padding:26px 22px;
  transition:all .3s;position:relative;overflow:hidden;
}
.vcard::before{
  content:'';position:absolute;bottom:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,transparent,var(--g),transparent);
  opacity:0;transition:opacity .3s;
}
.vcard:hover{border-color:rgba(118,185,0,.35);transform:translateY(-4px);box-shadow:0 16px 40px rgba(118,185,0,.08)}
.vcard:hover::before{opacity:1}
.vnum{font-family:var(--font-mono);font-size:.58rem;color:var(--dim);letter-spacing:.12em;margin-bottom:12px}
.vtitle{font-family:var(--font-display);font-size:.9rem;font-weight:700;color:var(--g);margin-bottom:10px;line-height:1.3}
.vbody{font-size:.77rem;color:var(--muted);line-height:1.68}

/* ══════════════════════════════════════════════════════════
   FOOTER
══════════════════════════════════════════════════════════ */
#footer{
  padding:32px 40px;
  background:var(--card);border-top:1px solid var(--border);
  display:flex;align-items:center;justify-content:space-between;
  flex-wrap:wrap;gap:16px;
}
.footer-left{display:flex;align-items:center;gap:16px}
.footer-left svg{height:18px;width:auto;opacity:.6}
.footer-text{font-family:var(--font-mono);font-size:.6rem;color:var(--dim);letter-spacing:.08em;line-height:1.6}
.footer-badge{
  font-family:var(--font-mono);font-size:.6rem;letter-spacing:.08em;
  padding:6px 16px;border:1px solid var(--g);color:var(--g);
  border-radius:3px;background:rgba(118,185,0,.05);
}

/* ══════════════════════════════════════════════════════════
   REVEAL ANIMATION
══════════════════════════════════════════════════════════ */
.reveal{opacity:0;transform:translateY(24px);transition:opacity .7s ease,transform .7s ease}
.reveal.vis{opacity:1;transform:none}
.reveal-left{opacity:0;transform:translateX(-20px);transition:opacity .7s ease,transform .7s ease}
.reveal-left.vis{opacity:1;transform:none}

/* ══════════════════════════════════════════════════════════
   RESPONSIVE
══════════════════════════════════════════════════════════ */
@media(max-width:1000px){
  .cert-grid{grid-template-columns:repeat(3,1fr)}
  .value-grid{grid-template-columns:repeat(2,1fr)}
  .spec-hero{grid-template-columns:1fr}
  .spec-card.primary{grid-template-columns:1fr}
}
@media(max-width:760px){
  .hero-grid{grid-template-columns:1fr}
  .skills-wrap{grid-template-columns:1fr}
  .cert-grid{grid-template-columns:repeat(2,1fr)}
  .spec-sub{grid-template-columns:1fr}
  #nav .nav-right{display:none}
}
</style>
</head>
<body>

<!-- ══════════════════════════════════════════
     NAVBAR
═══════════════════════════════════════════ -->
<nav id="nav">
  <a class="nv-logo" href="#hero">
    <!-- NVIDIA SVG Wordmark + Eye Logo -->
    <svg viewBox="0 0 120 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <!-- The NVIDIA eye icon -->
      <path d="M10.2 5.4C6.9 5.4 4 7.1 2.4 9.7C3.8 8.5 5.7 7.8 7.8 7.8C12 7.8 15.5 11.1 15.8 15.2C14.5 11.9 11.6 9.5 8.1 9.5C5.7 9.5 3.6 10.6 2.2 12.3L2.2 12.5C2.2 17 5.8 20.6 10.2 20.6C14.6 20.6 18.2 17 18.2 12.5V12.4C18.2 8.6 14.6 5.4 10.2 5.4Z" fill="#76b900"/>
      <path d="M7.8 7.8C5.7 7.8 3.8 8.5 2.4 9.7C2.3 10 2.2 10.2 2.2 10.5V12.3C3.6 10.6 5.7 9.5 8.1 9.5C11.6 9.5 14.5 11.9 15.8 15.2C15.5 11.1 12 7.8 7.8 7.8Z" fill="#76b900" opacity="0.5"/>
      <!-- NVIDIA wordmark -->
      <path d="M22 7.5H24.5L28.5 16.5L32.5 7.5H35L29.5 19H27.5L22 7.5Z" fill="#76b900"/>
      <path d="M37 7.5H39.5V19H37V7.5Z" fill="#76b900"/>
      <path d="M42 7.5H45L51 15.5V7.5H53.5V19H51L45 11V19H42V7.5Z" fill="#76b900"/>
      <path d="M56 7.5H62C66 7.5 68.5 10 68.5 13.2C68.5 16.5 66 19 62 19H56V7.5ZM61.8 16.5C64.3 16.5 65.8 15 65.8 13.2C65.8 11.4 64.3 10 61.8 10H58.5V16.5H61.8Z" fill="#76b900"/>
      <path d="M71 7.5H80.5V10H73.5V12H79.5V14.5H73.5V16.5H80.5V19H71V7.5Z" fill="#76b900"/>
      <path d="M83 7.5H90C92.5 7.5 94 9 94 11C94 12.6 93 13.8 91.5 14.3L94.5 19H91.5L88.8 14.8H85.5V19H83V7.5ZM89.5 12.5C90.8 12.5 91.5 11.8 91.5 11C91.5 10.2 90.8 9.8 89.5 9.8H85.5V12.5H89.5Z" fill="#76b900"/>
      <path d="M97 7.5H99.5L105 14.5V7.5H107.5V19H105L99.5 12V19H97V7.5Z" fill="#76b900"/>
    </svg>
  </a>
  <div style="display:flex;align-items:center;gap:10px">
    <div class="nv-divider"></div>
    <div class="nv-partner">Partner Network<span>Certified Specialist</span></div>
  </div>
  <div class="nav-right">
    <a class="nav-link" href="#certs">Certifications</a>
    <a class="nav-link" href="#specialisations">Specialisations</a>
    <a class="nav-link" href="#skills">Skills</a>
    <a class="nav-link" href="#experience">Experience</a>
    <span class="nav-badge">AI Factory Profile</span>
  </div>
</nav>

<!-- ══════════════════════════════════════════
     HERO
═══════════════════════════════════════════ -->
<section id="hero">
  <canvas id="hero-canvas"></canvas>
  <div class="hero-glow"></div>
  <div class="hero-glow2"></div>
  <div class="container">
    <div class="hero-grid">
      <div>
        <div class="eyebrow">AI Factory Solution Architect Profile</div>
        <h1 class="hero-name">
          Debjit<br>
          <span class="accent">Chowdhury</span>
        </h1>
        <p class="hero-role">AI Solutions Architect &nbsp;·&nbsp; NVIDIA Certified Partner Specialist</p>
        <div class="hero-company">Micropoint Computers Pvt. Ltd. — NVIDIA Partner Network</div>
        <div class="hero-tags">
          <span class="htag htag-green">NVIDIA Partner</span>
          <span class="htag htag-green">Generative AI</span>
          <span class="htag htag-green">Deep Learning / CUDA</span>
          <span class="htag htag-green">AI Factory Design</span>
          <span class="htag htag-dim">DGX Infrastructure</span>
          <span class="htag htag-dim">Distributed Training</span>
          <span class="htag htag-dim">LLM Inference</span>
          <span class="htag htag-dim">HPC / GPU</span>
        </div>
        <div class="hero-meta">
          <span class="hm">
            <svg viewBox="0 0 24 24"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
            Bengaluru, India
          </span>
          <span class="hm">
            <svg viewBox="0 0 24 24"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
            linkedin.com/in/debjit-chowdhury-298772191
          </span>
        </div>
      </div>
      <div class="stat-col">
        <div class="stat-card reveal">
          <div class="stat-n" data-count="5">0</div>
          <div class="stat-l">NVIDIA Certifications (2025)</div>
        </div>
        <div class="stat-card reveal" style="transition-delay:.1s">
          <div class="stat-n" data-count="3">0</div>
          <div class="stat-l">Years in AI / ML</div>
        </div>
        <div class="stat-card reveal" style="transition-delay:.2s">
          <div class="stat-n" style="font-size:1.9rem">360°</div>
          <div class="stat-l">Full-Stack AI Factory Coverage</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════════
     CERTIFICATIONS
═══════════════════════════════════════════ -->
<section id="certs">
<div class="container">
  <div class="sec-hd reveal">
    <span class="sec-num">01</span>
    <h2 class="sec-title">NVIDIA Certifications</h2>
    <div class="sec-line"></div>
    <span class="sec-sub">All issued June 2025 · Darrin Chen, VP NVIDIA Partner Network</span>
  </div>
  <div class="cert-grid reveal">

    <div class="cert-card featured">
      <div class="cc-badge"><svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg></div>
      <div class="cc-icon"><svg viewBox="0 0 24 24"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg></div>
      <div class="cc-name">NVIDIA AI Technical Curriculum</div>
      <div class="cc-issuer">NVIDIA Partner Network</div>
      <div class="cc-date">Jun 23, 2025</div>
    </div>

    <div class="cert-card featured">
      <div class="cc-badge"><svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg></div>
      <div class="cc-icon"><svg viewBox="0 0 24 24"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg></div>
      <div class="cc-name">Compute Technical Curriculum</div>
      <div class="cc-issuer">NVIDIA Partner Network</div>
      <div class="cc-date">Jun 24, 2025</div>
    </div>

    <div class="cert-card featured">
      <div class="cc-badge"><svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg></div>
      <div class="cc-icon"><svg viewBox="0 0 24 24"><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></svg></div>
      <div class="cc-name">DGX AI Compute Systems Technical Curriculum</div>
      <div class="cc-issuer">NVIDIA Partner Network</div>
      <div class="cc-date">Jun 23, 2025</div>
    </div>

    <div class="cert-card featured">
      <div class="cc-badge"><svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg></div>
      <div class="cc-icon"><svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="3"/><path d="M12 1v4M12 19v4M4.22 4.22l2.83 2.83M16.95 16.95l2.83 2.83M1 12h4M19 12h4M4.22 19.78l2.83-2.83M16.95 7.05l2.83-2.83"/></svg></div>
      <div class="cc-name">DGX AI Compute Systems Installation Curriculum</div>
      <div class="cc-issuer">NVIDIA Partner Network</div>
      <div class="cc-date">Jun 25, 2025</div>
    </div>

    <!-- Networking kept but visually de-emphasised -->
    <div class="cert-card" style="opacity:.75">
      <div class="cc-badge"><svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg></div>
      <div class="cc-icon" style="background:rgba(118,185,0,.06)"><svg viewBox="0 0 24 24"><path d="M5 12.55a11 11 0 0114.08 0"/><path d="M1.42 9a16 16 0 0121.16 0"/><path d="M8.53 16.11a6 6 0 016.95 0"/><circle cx="12" cy="20" r="1" fill="currentColor"/></svg></div>
      <div class="cc-name" style="color:var(--muted)">Networking Technical Curriculum</div>
      <div class="cc-issuer">NVIDIA Partner Network</div>
      <div class="cc-date">Jun 23, 2025</div>
    </div>

  </div>
</div>
</section>

<!-- ══════════════════════════════════════════
     CORE SPECIALISATIONS
═══════════════════════════════════════════ -->
<section id="specialisations">
<div class="container">
  <div class="sec-hd reveal">
    <span class="sec-num">02</span>
    <h2 class="sec-title">Core Specialisations</h2>
    <div class="sec-line"></div>
    <span class="sec-sub">Primary technical focus areas for AI Factory delivery</span>
  </div>

  <!-- Hero spec card: Distributed Training & Inference -->
  <div class="spec-hero reveal">
    <div class="spec-card primary">
      <div>
        <div class="spec-label">Primary Specialisation</div>
        <div class="spec-icon-large"><svg viewBox="0 0 24 24"><rect x="2" y="3" width="6" height="6" rx="1"/><rect x="16" y="3" width="6" height="6" rx="1"/><rect x="9" y="15" width="6" height="6" rx="1"/><path d="M5 9v3a1 1 0 001 1h12a1 1 0 001-1V9"/><path d="M12 13v2"/></svg></div>
        <div class="spec-title">Distributed Training &amp;<br>Inference of LLMs</div>
        <div class="spec-body">
          Expert in designing and deploying large-scale distributed training pipelines and optimised inference stacks for Large Language Models on NVIDIA GPU clusters. Leverages NVIDIA's NeMo Framework, TensorRT-LLM, Triton Inference Server, and multi-node DGX infrastructure to achieve maximum throughput and minimal latency for production AI Factory workloads.
        </div>
        <div class="spec-chips">
          <span class="spec-chip">NeMo Framework</span>
          <span class="spec-chip">TensorRT-LLM</span>
          <span class="spec-chip">Triton Inference Server</span>
          <span class="spec-chip">Multi-GPU / Multi-Node</span>
          <span class="spec-chip">NCCL</span>
          <span class="spec-chip">Model Parallelism</span>
          <span class="spec-chip">DGX H100 / H200</span>
        </div>
      </div>
      <div class="spec-visual">
        <div class="spec-metric"><span class="sm-icon">🧩</span><div class="sm-text"><strong>Model Parallelism</strong>Tensor, pipeline &amp; sequence parallelism across DGX nodes</div></div>
        <div class="spec-metric"><span class="sm-icon">⚡</span><div class="sm-text"><strong>TensorRT-LLM Optimisation</strong>Quantisation, kernel fusion &amp; batching for low-latency inference</div></div>
        <div class="spec-metric"><span class="sm-icon">🏭</span><div class="sm-text"><strong>AI Factory Integration</strong>Full stack from raw GPU compute to production LLM endpoints</div></div>
        <div class="spec-metric"><span class="sm-icon">📡</span><div class="sm-text"><strong>Triton Inference Server</strong>Scalable model serving with dynamic batching &amp; ensemble pipelines</div></div>
      </div>
    </div>
  </div>

  <!-- Sub spec grid -->
  <div class="spec-sub reveal" style="transition-delay:.1s">
    <div class="spec-card">
      <div class="spec-label">Specialisation</div>
      <div class="spec-icon-large"><svg viewBox="0 0 24 24"><path d="M12 2a2 2 0 012 2v4a2 2 0 01-2 2H8a2 2 0 01-2-2V4a2 2 0 012-2h4z"/><path d="M16 14a2 2 0 012 2v4a2 2 0 01-2 2h-8a2 2 0 01-2-2v-4a2 2 0 012-2h8z"/><path d="M12 8v6"/></svg></div>
      <div class="spec-title">Generative AI on NVIDIA Stack</div>
      <div class="spec-body">End-to-end deployment of Generative AI workloads using NVIDIA NIM microservices, NeMo, and cuDNN — from foundation model fine-tuning through to production serving inside an AI Factory.</div>
      <div class="spec-chips">
        <span class="spec-chip">NVIDIA NIM</span>
        <span class="spec-chip">NeMo</span>
        <span class="spec-chip">cuDNN</span>
        <span class="spec-chip">Fine-tuning</span>
      </div>
    </div>
    <div class="spec-card">
      <div class="spec-label">Specialisation</div>
      <div class="spec-icon-large"><svg viewBox="0 0 24 24"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg></div>
      <div class="spec-title">Deep Learning &amp; CUDA Engineering</div>
      <div class="spec-body">Proficient in GPU-native Python and CUDA programming for high-performance deep learning model development, custom kernel optimisation, and accelerated data pipelines on NVIDIA hardware.</div>
      <div class="spec-chips">
        <span class="spec-chip">CUDA</span>
        <span class="spec-chip">Python</span>
        <span class="spec-chip">PyTorch</span>
        <span class="spec-chip">cuBLAS / cuDNN</span>
      </div>
    </div>
    <div class="spec-card">
      <div class="spec-label">Specialisation</div>
      <div class="spec-icon-large"><svg viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/></svg></div>
      <div class="spec-title">AI Factory Architecture &amp; DGX Infrastructure</div>
      <div class="spec-body">Designs the full compute, storage, and networking blueprint of large-scale AI Factories — integrating DGX systems, high-speed fabrics, and software orchestration layers into a unified, scalable platform.</div>
      <div class="spec-chips">
        <span class="spec-chip">DGX Systems</span>
        <span class="spec-chip">AI Factory Blueprint</span>
        <span class="spec-chip">Kubernetes / Slurm</span>
      </div>
    </div>
  </div>
</div>
</section>

<!-- ══════════════════════════════════════════
     TECHNICAL SKILLS
═══════════════════════════════════════════ -->
<section id="skills">
<div class="container">
  <div class="sec-hd reveal">
    <span class="sec-num">03</span>
    <h2 class="sec-title">Technical Skills</h2>
    <div class="sec-line"></div>
  </div>
  <div class="skills-wrap">
    <div class="reveal">
      <!-- Core AI/ML skills -->
      <div class="skill-group-label">Core AI · Deep Learning · Generative AI</div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name core">Deep Learning &amp; CUDA Programming</span><span class="skill-pct">97%</span></div>
        <div class="bar-track"><div class="bar-fill core" data-w="97"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name core">Generative AI (NIM / NeMo / TensorRT)</span><span class="skill-pct">96%</span></div>
        <div class="bar-track"><div class="bar-fill core" data-w="96"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name core">Distributed LLM Training &amp; Inference</span><span class="skill-pct">95%</span></div>
        <div class="bar-track"><div class="bar-fill core" data-w="95"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name core">Python · PyTorch · cuBLAS / cuDNN</span><span class="skill-pct">94%</span></div>
        <div class="bar-track"><div class="bar-fill core" data-w="94"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name core">Agentic AI &amp; LLM Systems</span><span class="skill-pct">94%</span></div>
        <div class="bar-track"><div class="bar-fill core" data-w="94"></div></div>
      </div>

      <!-- Infrastructure -->
      <div class="skill-group-label" style="margin-top:20px">AI Factory · Compute Infrastructure</div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name">AI Factory Architecture &amp; Design</span><span class="skill-pct">95%</span></div>
        <div class="bar-track"><div class="bar-fill" data-w="95"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name">DGX AI Compute Infrastructure</span><span class="skill-pct">93%</span></div>
        <div class="bar-track"><div class="bar-fill" data-w="93"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name">HPC &amp; GPU-Accelerated Computing</span><span class="skill-pct">91%</span></div>
        <div class="bar-track"><div class="bar-fill" data-w="91"></div></div>
      </div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name">NVIDIA Omniverse &amp; Robotics Simulation</span><span class="skill-pct">80%</span></div>
        <div class="bar-track"><div class="bar-fill" data-w="80"></div></div>
      </div>

      <!-- Networking de-emphasised -->
      <div class="skill-group-label" style="margin-top:20px;color:var(--dim)">Supporting Infrastructure</div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name" style="color:var(--muted)">High-Speed Networking (InfiniBand / Ethernet)</span><span class="skill-pct" style="color:var(--dim)">72%</span></div>
        <div class="bar-track"><div class="bar-fill dim" data-w="72"></div></div>
      </div>

      <!-- Tech stack pills -->
      <div class="tech-stack" style="margin-top:22px">
        <div class="stack-title">Key Technologies</div>
        <div class="stack-pills">
          <div class="stack-pill"><span class="dot dot-green"></span>CUDA / C++</div>
          <div class="stack-pill"><span class="dot dot-green"></span>TensorRT-LLM</div>
          <div class="stack-pill"><span class="dot dot-green"></span>NVIDIA NIM</div>
          <div class="stack-pill"><span class="dot dot-green"></span>NeMo Framework</div>
          <div class="stack-pill"><span class="dot dot-green"></span>Triton Server</div>
          <div class="stack-pill"><span class="dot dot-green"></span>PyTorch</div>
          <div class="stack-pill"><span class="dot dot-green"></span>Python</div>
          <div class="stack-pill"><span class="dot dot-green"></span>DGX H100/H200</div>
          <div class="stack-pill"><span class="dot dot-muted"></span>InfiniBand</div>
          <div class="stack-pill"><span class="dot dot-muted"></span>Kubernetes</div>
          <div class="stack-pill"><span class="dot dot-muted"></span>Slurm</div>
        </div>
      </div>
    </div>

    <div class="domain-matrix reveal" style="transition-delay:.12s">
      <div class="dm-cell highlight"><span class="dm-icon">🧠</span><div class="dm-name">Deep Learning</div></div>
      <div class="dm-cell highlight"><span class="dm-icon">⚡</span><div class="dm-name">CUDA / GPU</div></div>
      <div class="dm-cell highlight"><span class="dm-icon">🤖</span><div class="dm-name">Generative AI</div></div>
      <div class="dm-cell highlight"><span class="dm-icon">🔀</span><div class="dm-name">Dist. Training</div></div>
      <div class="dm-cell highlight"><span class="dm-icon">🚀</span><div class="dm-name">LLM Inference</div></div>
      <div class="dm-cell highlight"><span class="dm-icon">🏭</span><div class="dm-name">AI Factory</div></div>
      <div class="dm-cell"><span class="dm-icon">📦</span><div class="dm-name">DGX Systems</div></div>
      <div class="dm-cell"><span class="dm-icon">🔬</span><div class="dm-name">Fine-tuning</div></div>
      <div class="dm-cell"><span class="dm-icon">🦾</span><div class="dm-name">Agentic AI</div></div>
      <div class="dm-cell"><span class="dm-icon">🎯</span><div class="dm-name">Solution Design</div></div>
      <div class="dm-cell"><span class="dm-icon">🔭</span><div class="dm-name">Omniverse</div></div>
      <div class="dm-cell" style="opacity:.5"><span class="dm-icon">🌐</span><div class="dm-name">Networking</div></div>
    </div>
  </div>
</div>
</section>

<!-- ══════════════════════════════════════════
     EXPERIENCE
═══════════════════════════════════════════ -->
<section id="experience">
<div class="container">
  <div class="sec-hd reveal">
    <span class="sec-num">04</span>
    <h2 class="sec-title">Experience &amp; Education</h2>
    <div class="sec-line"></div>
  </div>
  <div class="timeline reveal">
    <div class="tl-item">
      <div class="tl-dot"></div>
      <div class="tl-period">Current Position</div>
      <div class="tl-title">AI Solutions Architect</div>
      <div class="tl-co">Micropoint Computers Pvt. Ltd. · NVIDIA Partner Network · Bengaluru</div>
      <div class="tl-desc">
        Leads end-to-end design and deployment of large-scale AI Factory solutions, with a primary focus on Generative AI workloads, distributed LLM training pipelines, and high-performance inference infrastructure built on NVIDIA's DGX systems and software stack. Manages pre-sales technical engagements, proof-of-concept implementations, and architecture reviews for enterprise customers. Operates in close collaboration with NVIDIA's Partner Network, providing direct access to NVIDIA engineering tools, product roadmaps, and support channels essential for complex AI Factory builds.
      </div>
      <div class="tl-chips">
        <span class="tl-chip">NVIDIA DGX</span>
        <span class="tl-chip">Distributed Training</span>
        <span class="tl-chip">LLM Inference</span>
        <span class="tl-chip">NIM / NeMo</span>
        <span class="tl-chip">CUDA / Python</span>
        <span class="tl-chip">AI Factory Architecture</span>
        <span class="tl-chip">Pre-Sales Engineering</span>
      </div>
    </div>
    <div class="tl-item">
      <div class="tl-dot"></div>
      <div class="tl-period">Prior Roles</div>
      <div class="tl-title">Technical &amp; Solutions Roles</div>
      <div class="tl-co">LG Electronics · Viga Entertainment Technology · Eigenlytics Data Solutions · MedTourEasy</div>
      <div class="tl-desc">
        Cross-industry background spanning consumer electronics, entertainment platforms, data analytics, and healthtech — building a versatile foundation in systems integration, data pipelines, and solution architecture. This breadth provides the real-world business context necessary for designing AI infrastructure that addresses genuine enterprise challenges.
      </div>
      <div class="tl-chips">
        <span class="tl-chip">Data Analytics</span>
        <span class="tl-chip">Systems Integration</span>
        <span class="tl-chip">Enterprise Technology</span>
      </div>
    </div>
    <div class="tl-item">
      <div class="tl-dot"></div>
      <div class="tl-period">2018 – 2022</div>
      <div class="tl-title">B.Tech — Computer Science &amp; Systems Engineering</div>
      <div class="tl-co">Kalinga Institute of Industrial Technology (KIIT), Bhubaneswar</div>
      <div class="tl-desc">Strong foundational training in computer science, algorithms, systems engineering, and software design — the academic bedrock underlying a career built on deep technical architecture work with GPU and AI systems.</div>
    </div>
  </div>
</div>
</section>

<!-- ══════════════════════════════════════════
     VALUE PROPOSITION
═══════════════════════════════════════════ -->
<section id="value">
<div class="container">
  <div class="sec-hd reveal">
    <span class="sec-num">05</span>
    <h2 class="sec-title">Why Debjit for Your AI Factory</h2>
    <div class="sec-line"></div>
  </div>
  <div class="value-grid reveal">
    <div class="vcard">
      <div class="vnum">01 / 04</div>
      <div class="vtitle">NVIDIA-Certified Across the Full AI Stack</div>
      <div class="vbody">Five NVIDIA-issued 2025 credentials covering AI, compute, DGX systems, and installation — the most comprehensive partner certification coverage available from a single specialist, directly validating AI Factory readiness.</div>
    </div>
    <div class="vcard">
      <div class="vnum">02 / 04</div>
      <div class="vtitle">Deep Learning &amp; CUDA at Core</div>
      <div class="vbody">Brings genuine GPU-native engineering depth — CUDA programming, PyTorch, TensorRT-LLM, and cuDNN — ensuring AI Factory infrastructure is not just deployed but optimised for real-world deep learning workload performance.</div>
    </div>
    <div class="vcard">
      <div class="vnum">03 / 04</div>
      <div class="vtitle">Distributed Training &amp; Inference Expertise</div>
      <div class="vbody">Specialist knowledge in multi-node LLM training with NeMo and scalable inference with Triton Server and TensorRT-LLM — the exact capabilities required to maximise the ROI of a large-scale AI Factory investment.</div>
    </div>
    <div class="vcard">
      <div class="vnum">04 / 04</div>
      <div class="vtitle">Direct NVIDIA Partner-Level Access</div>
      <div class="vbody">Operating within an official NVIDIA Partner Network organisation with direct access to NVIDIA engineering teams, product roadmaps, and technical support channels — providing the inside edge that sets this AI Factory engagement apart.</div>
    </div>
  </div>
</div>
</section>

<!-- ══════════════════════════════════════════
     FOOTER
═══════════════════════════════════════════ -->
<footer id="footer">
  <div class="footer-left">
    <svg viewBox="0 0 120 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M10.2 5.4C6.9 5.4 4 7.1 2.4 9.7C3.8 8.5 5.7 7.8 7.8 7.8C12 7.8 15.5 11.1 15.8 15.2C14.5 11.9 11.6 9.5 8.1 9.5C5.7 9.5 3.6 10.6 2.2 12.3L2.2 12.5C2.2 17 5.8 20.6 10.2 20.6C14.6 20.6 18.2 17 18.2 12.5V12.4C18.2 8.6 14.6 5.4 10.2 5.4Z" fill="#76b900" opacity="0.5"/>
      <path d="M22 7.5H24.5L28.5 16.5L32.5 7.5H35L29.5 19H27.5L22 7.5Z" fill="#76b900" opacity="0.4"/>
    </svg>
    <div class="footer-text">
      NVIDIA certifications verified · Darrin Chen, VP – NVIDIA Partner Network<br>
      Micropoint Computers Pvt. Ltd. · Bengaluru, India
    </div>
  </div>
  <div class="footer-badge">Confidential — AI Factory Engagement Profile</div>
</footer>

<!-- ══════════════════════════════════════════
     SCRIPTS
═══════════════════════════════════════════ -->
<script>
/* ── GPU node canvas animation ─────────────────────────────── */
(function(){
  const canvas = document.getElementById('hero-canvas');
  const ctx = canvas.getContext('2d');
  let W, H, nodes=[], edges=[];
  const GREEN = '118,185,0';

  function resize(){
    W = canvas.width  = canvas.offsetWidth;
    H = canvas.height = canvas.offsetHeight;
    init();
  }

  function init(){
    nodes = [];
    for(let i=0;i<55;i++){
      nodes.push({
        x: Math.random()*W, y: Math.random()*H,
        vx:(Math.random()-.5)*0.35, vy:(Math.random()-.5)*0.35,
        r: Math.random()*2+1.5,
        pulse: Math.random()*Math.PI*2,
        speed: 0.02+Math.random()*0.015
      });
    }
  }

  function draw(){
    ctx.clearRect(0,0,W,H);
    // update
    nodes.forEach(n=>{
      n.x+=n.vx; n.y+=n.vy; n.pulse+=n.speed;
      if(n.x<0||n.x>W) n.vx*=-1;
      if(n.y<0||n.y>H) n.vy*=-1;
    });
    // edges
    for(let i=0;i<nodes.length;i++){
      for(let j=i+1;j<nodes.length;j++){
        const dx=nodes[i].x-nodes[j].x, dy=nodes[i].y-nodes[j].y;
        const d=Math.sqrt(dx*dx+dy*dy);
        if(d<130){
          const a=(1-d/130)*0.25;
          ctx.strokeStyle=`rgba(${GREEN},${a})`;
          ctx.lineWidth=0.7;
          ctx.beginPath();
          ctx.moveTo(nodes[i].x,nodes[i].y);
          ctx.lineTo(nodes[j].x,nodes[j].y);
          ctx.stroke();
        }
      }
    }
    // nodes
    nodes.forEach(n=>{
      const pulse = 0.5+0.5*Math.sin(n.pulse);
      ctx.beginPath();
      ctx.arc(n.x,n.y,n.r*(1+pulse*0.4),0,Math.PI*2);
      ctx.fillStyle=`rgba(${GREEN},${0.4+pulse*0.35})`;
      ctx.fill();
      // glow
      const g=ctx.createRadialGradient(n.x,n.y,0,n.x,n.y,n.r*4);
      g.addColorStop(0,`rgba(${GREEN},${0.15*pulse})`);
      g.addColorStop(1,'transparent');
      ctx.beginPath();
      ctx.arc(n.x,n.y,n.r*4,0,Math.PI*2);
      ctx.fillStyle=g;
      ctx.fill();
    });
    requestAnimationFrame(draw);
  }

  window.addEventListener('resize', resize);
  resize();
  draw();
})();

/* ── Scroll reveal ─────────────────────────────────────────── */
const obs = new IntersectionObserver(es=>{
  es.forEach(e=>{ if(e.isIntersecting) e.target.classList.add('vis') });
},{threshold:0.08});
document.querySelectorAll('.reveal,.reveal-left').forEach(el=>obs.observe(el));

/* ── Animated counters ─────────────────────────────────────── */
function animCount(el,target){
  let s=null;
  (function step(t){
    if(!s) s=t;
    const p=Math.min((t-s)/1700,1);
    const e=1-Math.pow(1-p,4);
    el.textContent=Math.round(e*target);
    if(p<1) requestAnimationFrame(step);
  })(performance.now());
}
const cObs=new IntersectionObserver(es=>{
  es.forEach(e=>{
    if(e.isIntersecting){
      const v=parseInt(e.target.dataset.count);
      if(!isNaN(v)) animCount(e.target,v);
      cObs.unobserve(e.target);
    }
  });
},{threshold:0.5});
document.querySelectorAll('[data-count]').forEach(el=>cObs.observe(el));

/* ── Skill bars ────────────────────────────────────────────── */
const bObs=new IntersectionObserver(es=>{
  es.forEach(e=>{
    if(e.isIntersecting){
      e.target.querySelectorAll('.bar-fill').forEach(b=>b.style.width=b.dataset.w+'%');
      bObs.unobserve(e.target);
    }
  });
},{threshold:0.15});
document.querySelectorAll('.skill-bars,.skills-wrap').forEach(el=>bObs.observe(el));

/* ── Navbar scroll effect ──────────────────────────────────── */
const nav=document.getElementById('nav');
window.addEventListener('scroll',()=>{
  nav.style.borderBottomColor = window.scrollY>40 ? 'rgba(118,185,0,.2)' : 'var(--border)';
});
</script>
</body>
</html>
