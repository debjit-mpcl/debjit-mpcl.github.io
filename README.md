<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no"/>
<title>Debjit Chowdhury — AI Solutions Architect</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=JetBrains+Mono:wght@300;400;500;700&family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet"/>
<style>
/* ══════════════════════════════════════════════════════════
   ROOT & RESET
══════════════════════════════════════════════════════════ */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --g: #76b900;       /* NVIDIA Green */
  --g-glow: #88d400;  /* Lighter Green for Glow */
  --g-dark: #4a7800;
  
  --bg: #04070a;      /* Deep Carbon Black */
  --bg2: #0a1016;     /* Server Rack Dark */
  --bg3: #111a24;
  
  --card: rgba(15, 25, 35, 0.6);
  --card-hover: rgba(20, 32, 45, 0.85);
  --border: rgba(118, 185, 0, 0.2);
  --border-strong: rgba(118, 185, 0, 0.5);
  
  --text: #e2e8f0; 
  --muted: #8ba3b5; 
  --dim: #3a5060;
  --white: #ffffff;
  
  --font-display: 'Syne', sans-serif;
  --font-body: 'Outfit', sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
  
  --glow-lg: 0 0 60px rgba(118,185,0,0.25);
  --glow-md: 0 0 25px rgba(118,185,0,0.2);
  --glow-sm: 0 0 12px rgba(118,185,0,0.4);
}

html { scroll-behavior: smooth; font-size: 16px; cursor: none; }
body {
  font-family: var(--font-body);
  background: var(--bg);
  color: var(--text);
  overflow-x: hidden;
  line-height: 1.6;
  -webkit-font-smoothing: antialiased;
}

/* ── Custom Cursor ─────────────────────────────────────────── */
#cursor-dot, #cursor-ring {
  position: fixed;
  top: 0; left: 0;
  transform: translate(-50%, -50%);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9999;
}
#cursor-dot {
  width: 6px; height: 6px;
  background: var(--g);
  box-shadow: var(--glow-sm);
  transition: width 0.2s, height 0.2s;
}
#cursor-ring {
  width: 36px; height: 36px;
  border: 1px solid rgba(118,185,0,0.4);
  transition: width 0.2s, height 0.2s, background 0.2s, border-color 0.2s;
  transition-timing-function: ease-out;
}
.cursor-hover #cursor-ring {
  width: 50px; height: 50px;
  background: rgba(118,185,0,0.1);
  border-color: var(--g);
}
@media(max-width: 1024px){ html{cursor:auto} #cursor-dot, #cursor-ring{display:none;} }

/* ── Animated Background ───────────────────────────────────── */
body::before {
  content: ''; position: fixed; inset: 0; z-index: -2;
  background-image: 
    linear-gradient(rgba(118,185,0,.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(118,185,0,.03) 1px, transparent 1px);
  background-size: 40px 40px;
  background-position: center center;
  mask-image: radial-gradient(ellipse at center, black 40%, transparent 80%);
  -webkit-mask-image: radial-gradient(ellipse at center, black 40%, transparent 80%);
}

/* ── Scrollbar ─────────────────────────────────────────────── */
::-webkit-scrollbar { width: 6px; }
::-webkit-scrollbar-track { background: var(--bg); }
::-webkit-scrollbar-thumb { background: var(--dim); border-radius: 4px; }
::-webkit-scrollbar-thumb:hover { background: var(--g); }

/* ══════════════════════════════════════════════════════════
   NAVBAR & MOBILE MENU
══════════════════════════════════════════════════════════ */
#nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 0 40px; height: 70px;
  background: rgba(4, 7, 10, 0.7);
  backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(255,255,255,0.05);
  transition: all 0.3s ease;
}
#nav.scrolled {
  border-bottom-color: var(--border-strong);
  box-shadow: 0 4px 30px rgba(0,0,0,0.5);
}

.brand-group { display: flex; align-items: center; gap: 16px; text-decoration: none; }
.nv-logo svg { height: 26px; width: auto; filter: drop-shadow(0 0 8px rgba(118,185,0,0.3)); }
.nv-divider { width: 1px; height: 28px; background: rgba(255,255,255,0.15); }

/* Official-looking Partner Badge */
.partner-badge {
  display: flex; flex-direction: column;
  background: var(--bg2);
  border: 1px solid var(--g);
  border-radius: 4px; overflow: hidden;
}
.partner-badge .pn-top {
  background: var(--g); color: #000;
  font-family: var(--font-display); font-weight: 800; font-size: 0.55rem;
  padding: 3px 8px; letter-spacing: 0.1em;
}
.partner-badge .pn-bot {
  color: var(--white); background: #000;
  font-family: var(--font-mono); font-weight: 500; font-size: 0.45rem;
  padding: 3px 8px; letter-spacing: 0.15em; text-transform: uppercase;
}

.nav-right { display: flex; align-items: center; gap: 32px; }
.nav-link {
  font-family: var(--font-mono); font-size: 0.7rem; letter-spacing: 0.1em;
  text-transform: uppercase; color: var(--text); text-decoration: none;
  position: relative; padding: 5px 0; transition: color 0.3s;
}
.nav-link::after {
  content:''; position: absolute; bottom: 0; left: 0; width: 0; height: 1px;
  background: var(--g); transition: width 0.3s ease;
}
.nav-link:hover { color: var(--g); }
.nav-link:hover::after { width: 100%; }

.nav-badge {
  font-family: var(--font-mono); font-size: 0.65rem; letter-spacing: 0.1em;
  padding: 8px 18px; border: 1px solid var(--g); color: #000;
  border-radius: 4px; text-transform: uppercase; font-weight: 700;
  background: var(--g); box-shadow: var(--glow-sm);
  transition: all 0.3s; cursor: pointer;
}
.nav-badge:hover { background: transparent; color: var(--g); box-shadow: var(--glow-lg); }

/* Mobile Menu Toggle */
.menu-btn {
  display: none; flex-direction: column; justify-content: space-around;
  width: 30px; height: 24px; background: transparent; border: none;
  cursor: pointer; z-index: 101;
}
.menu-btn span {
  width: 100%; height: 2px; background: var(--g);
  transition: all 0.3s linear; transform-origin: 1px;
}
.menu-btn.open span:nth-child(1) { transform: rotate(45deg); }
.menu-btn.open span:nth-child(2) { opacity: 0; }
.menu-btn.open span:nth-child(3) { transform: rotate(-45deg); }

/* ══════════════════════════════════════════════════════════
   HERO & CANVAS
══════════════════════════════════════════════════════════ */
#hero {
  position: relative; min-height: 100vh; display: flex; align-items: center;
  padding: 120px 0 80px; overflow: hidden;
}
#hero-canvas { position: absolute; inset: 0; z-index: -1; opacity: 0.8; }
.hero-glow {
  position: absolute; top: 10%; right: -10%; width: 800px; height: 800px;
  background: radial-gradient(circle, rgba(118,185,0,.12) 0%, transparent 60%);
  pointer-events: none; z-index: -1;
}

.container { max-width: 1240px; margin: 0 auto; padding: 0 40px; position: relative; z-index: 1; width: 100%; }
.hero-grid { display: grid; grid-template-columns: 1.2fr 1fr; gap: 60px; align-items: center; }

.eyebrow {
  display: inline-flex; align-items: center; gap: 12px;
  font-family: var(--font-mono); font-size: 0.7rem; letter-spacing: 0.2em;
  color: var(--g); text-transform: uppercase; margin-bottom: 24px;
}
.eyebrow::before { content:''; width: 30px; height: 1px; background: var(--g); box-shadow: var(--glow-sm); }

.hero-name {
  font-family: var(--font-display); font-size: clamp(3.5rem, 7vw, 6rem);
  font-weight: 800; line-height: 0.9; letter-spacing: -0.04em;
  color: var(--white); margin-bottom: 12px; text-transform: uppercase;
}
.hero-name .accent {
  background: linear-gradient(90deg, var(--white), var(--g));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
}

.hero-role {
  font-family: var(--font-mono); font-size: 1.1rem; color: var(--g);
  margin-bottom: 16px; height: 28px;
}

.hero-company {
  display: inline-flex; align-items: center; gap: 10px;
  font-family: var(--font-mono); font-size: 0.75rem; color: var(--text);
  padding: 8px 16px; border: 1px solid rgba(255,255,255,0.1);
  border-radius: 4px; background: rgba(255,255,255,0.03);
  backdrop-filter: blur(10px); margin-bottom: 32px;
}
.hero-company::before { content:''; width: 8px; height: 8px; background: var(--g); border-radius: 50%; box-shadow: var(--glow-sm); }

.hero-tags { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 40px; }
.htag {
  font-family: var(--font-mono); font-size: 0.65rem; letter-spacing: 0.08em;
  text-transform: uppercase; padding: 6px 14px; border-radius: 4px;
  transition: all 0.3s; backdrop-filter: blur(5px);
}
.htag-green { border: 1px solid var(--g); color: var(--g); background: rgba(118,185,0,.08); box-shadow: var(--glow-sm); }
.htag-dim { border: 1px solid var(--border); color: var(--muted); background: rgba(255,255,255,0.02); }
.htag-dim:hover { border-color: var(--g); color: var(--white); background: rgba(118,185,0,.1); }

.hero-meta { display: flex; gap: 24px; flex-wrap: wrap; }
.hm { display: flex; align-items: center; gap: 8px; font-size: 0.85rem; color: var(--muted); }
.hm svg { width: 16px; height: 16px; stroke: var(--g); fill: none; stroke-width: 2; flex-shrink: 0; }
.hm a { color: var(--muted); text-decoration: none; transition: color 0.3s; }
.hm a:hover { color: var(--white); }

/* Server-blade Stats */
.stat-col { display: flex; flex-direction: column; gap: 20px; perspective: 1000px; }
.stat-card {
  background: var(--card); border: 1px solid var(--border);
  border-radius: 8px; padding: 30px; position: relative; overflow: hidden;
  backdrop-filter: blur(12px); -webkit-backdrop-filter: blur(12px);
  transform-style: preserve-3d; transition: border-color 0.3s, box-shadow 0.3s;
}
.stat-card::before {
  content:''; position: absolute; left: 0; top: 0; bottom: 0; width: 4px;
  background: var(--g); box-shadow: var(--glow-sm);
}
.stat-card::after { /* Scanning line effect */
  content:''; position: absolute; top: -50%; left: -50%; width: 200%; height: 2px;
  background: rgba(118,185,0,0.5); transform: rotate(30deg);
  animation: scanline 6s linear infinite; opacity: 0; transition: opacity 0.3s;
}
.stat-card:hover::after { opacity: 1; }
@keyframes scanline { 0% { top: -50%; } 100% { top: 150%; } }

.stat-card:hover { border-color: var(--border-strong); box-shadow: var(--glow-lg); }
.stat-n {
  font-family: var(--font-display); font-size: 3rem; font-weight: 800;
  color: var(--white); line-height: 1; margin-bottom: 8px;
  text-shadow: 0 0 20px rgba(118,185,0,0.5); transform: translateZ(20px);
}
.stat-l {
  font-family: var(--font-mono); font-size: 0.75rem; color: var(--muted);
  letter-spacing: 0.05em; text-transform: uppercase; transform: translateZ(10px);
}

/* ══════════════════════════════════════════════════════════
   SECTION STRUCTURE
══════════════════════════════════════════════════════════ */
section { padding: 100px 0; position: relative; }
section::before {
  content: ''; position: absolute; top: 0; left: 40px; right: 40px; height: 1px;
  background: linear-gradient(90deg, transparent, rgba(118,185,0,0.2), transparent);
}
.sec-hd { display: flex; align-items: center; gap: 20px; margin-bottom: 50px; }
.sec-num {
  font-family: var(--font-mono); font-size: 0.8rem; font-weight: 700;
  color: var(--g); letter-spacing: 0.1em;
  padding: 4px 10px; background: rgba(118,185,0,.1); border-radius: 4px;
}
.sec-title {
  font-family: var(--font-display); font-size: 2rem; font-weight: 700;
  color: var(--white); text-transform: uppercase; letter-spacing: -0.02em;
}
.sec-line { flex: 1; height: 1px; background: rgba(255,255,255,0.05); }
.sec-sub { font-family: var(--font-mono); font-size: 0.7rem; color: var(--muted); text-transform: uppercase; letter-spacing: 0.05em; }

/* ══════════════════════════════════════════════════════════
   CERTIFICATIONS (3D Tilt Cards)
══════════════════════════════════════════════════════════ */
.cert-grid { display: grid; grid-template-columns: repeat(5, 1fr); gap: 20px; perspective: 1200px; }
.cert-card {
  background: var(--card); border: 1px solid var(--border); border-radius: 8px;
  padding: 24px; position: relative; transform-style: preserve-3d;
  backdrop-filter: blur(10px); cursor: pointer;
}
.cert-card::after {
  content: ''; position: absolute; inset: 0; border-radius: inherit;
  box-shadow: inset 0 0 20px rgba(118,185,0,0); transition: box-shadow 0.3s;
}
.cert-card:hover::after { box-shadow: inset 0 0 20px rgba(118,185,0,0.15); }
.cert-card:hover { border-color: var(--g); }

.cc-icon {
  width: 48px; height: 48px; background: rgba(118,185,0,.08); border-radius: 8px;
  display: flex; align-items: center; justify-content: center; margin-bottom: 20px;
  border: 1px solid rgba(118,185,0,.2); transform: translateZ(30px);
}
.cc-icon svg { width: 24px; height: 24px; stroke: var(--g); fill: none; stroke-width: 1.5; }
.cc-name {
  font-family: var(--font-body); font-size: 0.9rem; font-weight: 600;
  color: var(--white); line-height: 1.4; margin-bottom: 12px; transform: translateZ(20px);
}
.cc-issuer { font-family: var(--font-mono); font-size: 0.65rem; color: var(--muted); margin-bottom: 8px; transform: translateZ(10px); }
.cc-date { font-family: var(--font-mono); font-size: 0.7rem; color: var(--g); transform: translateZ(10px); }

.cc-badge {
  position: absolute; top: 16px; right: 16px; width: 24px; height: 24px;
  background: var(--g); border-radius: 50%; display: flex; align-items: center; justify-content: center;
  box-shadow: 0 0 12px rgba(118,185,0,.5); transform: translateZ(40px);
}
.cc-badge svg { width: 12px; height: 12px; stroke: #000; stroke-width: 3; }

/* ══════════════════════════════════════════════════════════
   CORE SPECIALISATIONS
══════════════════════════════════════════════════════════ */
.spec-hero { margin-bottom: 24px; perspective: 1000px; }
.spec-card {
  border-radius: 12px; padding: 40px; position: relative; overflow: hidden;
  border: 1px solid var(--border); background: var(--card);
  backdrop-filter: blur(10px); transform-style: preserve-3d; cursor: pointer;
}
.spec-card::before {
  content:''; position: absolute; inset: 0;
  background: radial-gradient(800px circle at var(--mouse-x, 50%) var(--mouse-y, 50%), rgba(118,185,0,0.06), transparent 40%);
  opacity: 0; transition: opacity 0.3s;
}
.spec-card:hover::before { opacity: 1; }
.spec-card:hover { border-color: var(--border-strong); box-shadow: var(--glow-md); }

.spec-card.primary {
  border-color: rgba(118,185,0,.4);
  background: linear-gradient(145deg, rgba(15,25,35,0.8), rgba(4,7,10,0.9));
  display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: center;
}
.spec-icon-large {
  width: 64px; height: 64px; background: rgba(118,185,0,.1); border: 1px solid rgba(118,185,0,.3);
  border-radius: 12px; display: flex; align-items: center; justify-content: center; margin-bottom: 24px;
  box-shadow: var(--glow-sm); transform: translateZ(30px);
}
.spec-icon-large svg { width: 32px; height: 32px; stroke: var(--g); fill: none; stroke-width: 1.5; }
.spec-label {
  font-family: var(--font-mono); font-size: 0.7rem; letter-spacing: 0.15em;
  color: var(--g); text-transform: uppercase; margin-bottom: 12px; transform: translateZ(20px);
}
.spec-title {
  font-family: var(--font-display); font-size: 1.8rem; font-weight: 700;
  color: var(--white); margin-bottom: 16px; line-height: 1.1; transform: translateZ(25px);
}
.spec-body { font-size: 0.95rem; color: var(--muted); line-height: 1.7; margin-bottom: 24px; transform: translateZ(15px); }
.spec-chips { display: flex; flex-wrap: wrap; gap: 10px; transform: translateZ(20px); }
.spec-chip {
  font-family: var(--font-mono); font-size: 0.65rem; letter-spacing: 0.05em;
  padding: 6px 12px; background: rgba(118,185,0,.08);
  border: 1px solid rgba(118,185,0,.2); color: var(--g); border-radius: 4px;
}

.spec-visual { display: flex; flex-direction: column; gap: 12px; transform: translateZ(20px); }
.spec-metric {
  background: rgba(0,0,0,0.4); border: 1px solid rgba(255,255,255,0.05);
  border-radius: 8px; padding: 16px 20px; display: flex; align-items: center; gap: 16px;
  transition: all 0.3s;
}
.spec-metric:hover { border-color: var(--border-strong); background: rgba(118,185,0,0.05); }
.sm-icon { font-size: 1.5rem; filter: drop-shadow(0 0 8px rgba(118,185,0,0.4)); }
.sm-text { font-size: 0.85rem; color: var(--muted); line-height: 1.4; }
.sm-text strong { display: block; color: var(--white); font-size: 0.95rem; margin-bottom: 4px; font-weight: 600; }

.spec-sub { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; perspective: 1000px; }

/* ══════════════════════════════════════════════════════════
   SKILLS & TECH STACK
══════════════════════════════════════════════════════════ */
.skills-wrap { display: grid; grid-template-columns: 1.2fr 1fr; gap: 60px; align-items: start; }

.skill-group-label {
  font-family: var(--font-mono); font-size: 0.7rem; letter-spacing: 0.15em;
  text-transform: uppercase; color: var(--white); margin-bottom: 24px;
  padding-bottom: 10px; border-bottom: 1px solid rgba(255,255,255,0.1);
  display: flex; align-items: center; gap: 10px;
}
.skill-group-label::before { content:''; width: 6px; height: 6px; background: var(--g); border-radius: 50%; box-shadow: var(--glow-sm); }

.skill-row { margin-bottom: 18px; }
.skill-top { display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px; }
.skill-name { font-size: 0.9rem; color: var(--text); font-weight: 500; font-family: var(--font-mono); }
.skill-name.core { color: var(--white); font-weight: 600; }
.skill-pct { font-family: var(--font-mono); font-size: 0.8rem; color: var(--g); }
.bar-track { height: 6px; background: rgba(255,255,255,0.05); border-radius: 3px; overflow: hidden; position: relative; }
.bar-fill {
  height: 100%; border-radius: 3px; width: 0;
  background: linear-gradient(90deg, var(--g-dark), var(--g), var(--g-glow));
  transition: width 1.5s cubic-bezier(.16,1,.3,1); box-shadow: var(--glow-md);
}

.tech-stack { margin-top: 40px; }
.stack-title { font-family: var(--font-mono); font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--muted); margin-bottom: 16px; }
.stack-pills { display: flex; flex-wrap: wrap; gap: 12px; }
.stack-pill {
  display: flex; align-items: center; gap: 8px; padding: 10px 18px;
  background: rgba(0,0,0,0.5); border: 1px solid rgba(255,255,255,0.1); border-radius: 6px;
  font-family: var(--font-mono); font-size: 0.8rem; color: var(--text);
  transition: all 0.3s; cursor: pointer;
}
.stack-pill:hover { border-color: var(--g); color: var(--white); box-shadow: 0 0 15px rgba(118,185,0,0.15); transform: translateY(-2px); }
.stack-pill .dot { width: 8px; height: 8px; border-radius: 50%; }
.dot-green { background: var(--g); box-shadow: var(--glow-sm); }
.dot-muted { background: var(--dim); }

.domain-matrix { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; }
.dm-cell {
  background: var(--card); border: 1px solid rgba(255,255,255,0.05); border-radius: 8px;
  padding: 24px 16px; text-align: center; transition: all 0.3s; cursor: pointer;
}
.dm-cell:hover { transform: translateY(-5px); }
.dm-cell.highlight { border-color: var(--border); background: rgba(118,185,0,.03); }
.dm-cell.highlight:hover { border-color: var(--g); box-shadow: var(--glow-md); background: rgba(118,185,0,.08); }
.dm-icon { font-size: 1.8rem; margin-bottom: 12px; display: block; filter: grayscale(1); transition: filter 0.3s; }
.dm-cell.highlight .dm-icon { filter: drop-shadow(0 0 10px rgba(118,185,0,0.5)) grayscale(0); }
.dm-name { font-family: var(--font-mono); font-size: 0.75rem; color: var(--muted); text-transform: uppercase; }
.dm-cell.highlight .dm-name { color: var(--white); font-weight: 600; }

/* ══════════════════════════════════════════════════════════
   EXPERIENCE
══════════════════════════════════════════════════════════ */
.timeline { position: relative; padding-left: 40px; }
.timeline::before {
  content:''; position: absolute; left: 8px; top: 10px; bottom: 10px; width: 2px;
  background: linear-gradient(to bottom, var(--g) 0%, rgba(118,185,0,0.2) 70%, transparent 100%);
}
.tl-item { position: relative; margin-bottom: 48px; }
.tl-dot {
  position: absolute; left: -41px; top: 4px; width: 18px; height: 18px; border-radius: 50%;
  background: var(--bg); border: 3px solid var(--g); transition: all 0.3s;
}
.tl-item:hover .tl-dot { background: var(--g); box-shadow: var(--glow-md); }
.tl-period {
  font-family: var(--font-mono); font-size: 0.75rem; color: var(--g);
  letter-spacing: 0.1em; text-transform: uppercase; margin-bottom: 8px;
}
.tl-title { font-family: var(--font-display); font-size: 1.3rem; font-weight: 700; color: var(--white); margin-bottom: 4px; }
.tl-co { font-family: var(--font-mono); font-size: 0.85rem; color: var(--muted); margin-bottom: 16px; }
.tl-desc { font-size: 0.95rem; color: var(--text); line-height: 1.8; margin-bottom: 16px; }
.tl-chips { display: flex; flex-wrap: wrap; gap: 10px; }
.tl-chip {
  font-family: var(--font-mono); font-size: 0.65rem; letter-spacing: 0.05em; text-transform: uppercase;
  padding: 6px 12px; background: rgba(255,255,255,0.03); border: 1px solid rgba(255,255,255,0.1); color: var(--text); border-radius: 4px;
}

/* ══════════════════════════════════════════════════════════
   VALUE PROPOSITION
══════════════════════════════════════════════════════════ */
.value-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 24px; perspective: 1000px; }
.vcard {
  background: var(--card); border: 1px solid rgba(255,255,255,0.05);
  border-radius: 8px; padding: 32px 24px; position: relative; overflow: hidden;
  transform-style: preserve-3d; cursor: pointer; backdrop-filter: blur(10px);
}
.vcard::before {
  content:''; position: absolute; bottom: 0; left: 0; right: 0; height: 3px;
  background: linear-gradient(90deg, transparent, var(--g), transparent);
  opacity: 0; transition: opacity 0.3s;
}
.vcard:hover { border-color: rgba(118,185,0,.3); box-shadow: 0 15px 30px rgba(0,0,0,0.5); }
.vcard:hover::before { opacity: 1; box-shadow: var(--glow-md); }
.vnum { font-family: var(--font-mono); font-size: 0.7rem; color: var(--dim); letter-spacing: 0.15em; margin-bottom: 16px; transform: translateZ(10px); }
.vtitle { font-family: var(--font-display); font-size: 1.1rem; font-weight: 700; color: var(--white); margin-bottom: 12px; line-height: 1.3; transform: translateZ(20px); }
.vcard:hover .vtitle { color: var(--g); }
.vbody { font-size: 0.9rem; color: var(--muted); line-height: 1.7; transform: translateZ(15px); }

/* ══════════════════════════════════════════════════════════
   FOOTER
══════════════════════════════════════════════════════════ */
#footer {
  padding: 40px; background: rgba(4,7,10,0.9); border-top: 1px solid rgba(255,255,255,0.05);
  display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 20px;
  position: relative; z-index: 10;
}
.footer-left { display: flex; align-items: center; gap: 24px; }
.footer-left svg { height: 24px; width: auto; opacity: 0.8; }
.footer-text { font-family: var(--font-mono); font-size: 0.7rem; color: var(--muted); letter-spacing: 0.05em; line-height: 1.6; }
.footer-badge {
  font-family: var(--font-mono); font-size: 0.65rem; letter-spacing: 0.1em;
  padding: 8px 20px; border: 1px solid var(--border-strong); color: var(--g);
  border-radius: 4px; background: rgba(118,185,0,.05); text-transform: uppercase;
}

/* ══════════════════════════════════════════════════════════
   REVEAL ANIMATIONS
══════════════════════════════════════════════════════════ */
.reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.8s cubic-bezier(.16,1,.3,1), transform 0.8s cubic-bezier(.16,1,.3,1); }
.reveal.vis { opacity: 1; transform: none; }
.typewriter { border-right: 2px solid var(--g); white-space: nowrap; overflow: hidden; animation: typing 3s steps(40, end), blink .75s step-end infinite; }
@keyframes typing { from { width: 0 } to { width: 100% } }
@keyframes blink { from, to { border-color: transparent } 50% { border-color: var(--g); } }

/* ══════════════════════════════════════════════════════════
   RESPONSIVE (Mobile Friendly)
══════════════════════════════════════════════════════════ */
@media(max-width: 1200px){
  .cert-grid { grid-template-columns: repeat(3, 1fr); }
  .value-grid { grid-template-columns: repeat(2, 1fr); }
}
@media(max-width: 992px){
  #nav { padding: 0 20px; }
  .nav-right { display: none; }
  .nav-right.active {
    display: flex; flex-direction: column; position: fixed; top: 70px; left: 0; right: 0;
    background: rgba(4,7,10,0.95); backdrop-filter: blur(20px); padding: 30px; border-bottom: 1px solid var(--border);
    animation: slideDown 0.3s ease forwards;
  }
  @keyframes slideDown { from { opacity: 0; transform: translateY(-10px); } to { opacity: 1; transform: translateY(0); } }
  .menu-btn { display: flex; }
  
  .hero-grid { grid-template-columns: 1fr; gap: 40px; }
  .stat-col { flex-direction: row; flex-wrap: wrap; }
  .stat-card { flex: 1; min-width: 250px; }
  .skills-wrap { grid-template-columns: 1fr; }
  .domain-matrix { grid-template-columns: repeat(3, 1fr); }
  .spec-sub { grid-template-columns: 1fr; }
  .spec-card.primary { grid-template-columns: 1fr; }
  .container { padding: 0 20px; }
  section { padding: 60px 0; }
  .hero-name { font-size: 3.5rem; }
}
@media(max-width: 600px){
  .cert-grid { grid-template-columns: 1fr; }
  .value-grid { grid-template-columns: 1fr; }
  .stat-col { flex-direction: column; }
  .domain-matrix { grid-template-columns: repeat(2, 1fr); }
  .sec-hd { flex-direction: column; align-items: flex-start; gap: 10px; }
  .sec-title { font-size: 1.5rem; }
  .sec-sub { white-space: normal; }
  .hero-meta { flex-direction: column; gap: 12px; }
  .footer-left { flex-direction: column; align-items: flex-start; }
}
</style>
</head>
<body>

<!-- Custom Cursor -->
<div id="cursor-dot"></div>
<div id="cursor-ring"></div>

<!-- ══════════════════════════════════════════
     NAVBAR
═══════════════════════════════════════════ -->
<nav id="nav">
  <a class="brand-group" href="#hero">
    <div class="nv-logo">
      <svg viewBox="0 0 120 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M10.2 5.4C6.9 5.4 4 7.1 2.4 9.7C3.8 8.5 5.7 7.8 7.8 7.8C12 7.8 15.5 11.1 15.8 15.2C14.5 11.9 11.6 9.5 8.1 9.5C5.7 9.5 3.6 10.6 2.2 12.3L2.2 12.5C2.2 17 5.8 20.6 10.2 20.6C14.6 20.6 18.2 17 18.2 12.5V12.4C18.2 8.6 14.6 5.4 10.2 5.4Z" fill="#76b900"/>
        <path d="M7.8 7.8C5.7 7.8 3.8 8.5 2.4 9.7C2.3 10 2.2 10.2 2.2 10.5V12.3C3.6 10.6 5.7 9.5 8.1 9.5C11.6 9.5 14.5 11.9 15.8 15.2C15.5 11.1 12 7.8 7.8 7.8Z" fill="#76b900" opacity="0.5"/>
        <path d="M22 7.5H24.5L28.5 16.5L32.5 7.5H35L29.5 19H27.5L22 7.5Z" fill="#76b900"/>
        <path d="M37 7.5H39.5V19H37V7.5Z" fill="#76b900"/>
        <path d="M42 7.5H45L51 15.5V7.5H53.5V19H51L45 11V19H42V7.5Z" fill="#76b900"/>
        <path d="M56 7.5H62C66 7.5 68.5 10 68.5 13.2C68.5 16.5 66 19 62 19H56V7.5ZM61.8 16.5C64.3 16.5 65.8 15 65.8 13.2C65.8 11.4 64.3 10 61.8 10H58.5V16.5H61.8Z" fill="#76b900"/>
        <path d="M71 7.5H80.5V10H73.5V12H79.5V14.5H73.5V16.5H80.5V19H71V7.5Z" fill="#76b900"/>
        <path d="M83 7.5H90C92.5 7.5 94 9 94 11C94 12.6 93 13.8 91.5 14.3L94.5 19H91.5L88.8 14.8H85.5V19H83V7.5ZM89.5 12.5C90.8 12.5 91.5 11.8 91.5 11C91.5 10.2 90.8 9.8 89.5 9.8H85.5V12.5H89.5Z" fill="#76b900"/>
        <path d="M97 7.5H99.5L105 14.5V7.5H107.5V19H105L99.5 12V19H97V7.5Z" fill="#76b900"/>
      </svg>
    </div>
    <div class="nv-divider"></div>
    <div class="partner-badge">
      <span class="pn-top">NVIDIA</span>
      <span class="pn-bot">PARTNER NETWORK</span>
    </div>
  </a>
  <div class="nav-right" id="nav-links">
    <a class="nav-link" href="#certs">Certifications</a>
    <a class="nav-link" href="#specialisations">Specialisations</a>
    <a class="nav-link" href="#skills">Skills</a>
    <a class="nav-link" href="#experience">Experience</a>
    <span class="nav-badge">AI Factory Profile</span>
  </div>
  <button class="menu-btn" id="menu-toggle" aria-label="Toggle menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- ══════════════════════════════════════════
     HERO
═══════════════════════════════════════════ -->
<section id="hero">
  <canvas id="hero-canvas"></canvas>
  <div class="hero-glow"></div>
  <div class="container">
    <div class="hero-grid">
      <div>
        <div class="eyebrow reveal">AI Factory Solution Architect Profile</div>
        <h1 class="hero-name reveal" style="transition-delay:0.1s">
          Debjit<br>
          <span class="accent">Chowdhury</span>
        </h1>
        <div class="hero-role reveal" style="transition-delay:0.2s">
          <span class="typewriter" style="display:inline-block">AI Solutions Architect &nbsp;·&nbsp; NVIDIA Certified Specialist</span>
        </div>
        <div class="hero-company reveal" style="transition-delay:0.3s">Micropoint Computers Pvt. Ltd. — NVIDIA Partner Network</div>
        <div class="hero-tags reveal" style="transition-delay:0.4s">
          <span class="htag htag-green">NVIDIA Partner</span>
          <span class="htag htag-green">Generative AI</span>
          <span class="htag htag-green">Deep Learning / CUDA</span>
          <span class="htag htag-green">AI Factory Design</span>
          <span class="htag htag-dim">DGX Infrastructure</span>
          <span class="htag htag-dim">Distributed Training</span>
          <span class="htag htag-dim">LLM Inference</span>
          <span class="htag htag-dim">HPC / GPU</span>
        </div>
        <div class="hero-meta reveal" style="transition-delay:0.5s">
          <span class="hm">
            <svg viewBox="0 0 24 24"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
            Bengaluru, India
          </span>
          <span class="hm">
            <svg viewBox="0 0 24 24"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
            <a href="https://linkedin.com/in/debjit-chowdhury-298772191" target="_blank">linkedin.com/in/debjit-chowdhury</a>
          </span>
        </div>
      </div>
      <div class="stat-col">
        <div class="stat-card tilt-card reveal" style="transition-delay:0.3s">
          <div class="stat-n" data-count="5">0</div>
          <div class="stat-l">NVIDIA Certifications (2025)</div>
        </div>
        <div class="stat-card tilt-card reveal" style="transition-delay:0.4s">
          <div class="stat-n" data-count="3">0</div>
          <div class="stat-l">Years in AI / ML</div>
        </div>
        <div class="stat-card tilt-card reveal" style="transition-delay:0.5s">
          <div class="stat-n" style="font-size:2.4rem">360°</div>
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
    <span class="sec-sub">All issued June 2025 · Verified Partner</span>
  </div>
  <div class="cert-grid reveal">

    <div class="cert-card tilt-card featured">
      <div class="cc-badge"><svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg></div>
      <div class="cc-icon"><svg viewBox="0 0 24 24"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg></div>
      <div class="cc-name">NVIDIA AI Technical Curriculum</div>
      <div class="cc-issuer">NVIDIA Partner Network</div>
      <div class="cc-date">Jun 23, 2025</div>
    </div>

    <div class="cert-card tilt-card featured">
      <div class="cc-badge"><svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg></div>
      <div class="cc-icon"><svg viewBox="0 0 24 24"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg></div>
      <div class="cc-name">Compute Technical Curriculum</div>
      <div class="cc-issuer">NVIDIA Partner Network</div>
      <div class="cc-date">Jun 24, 2025</div>
    </div>

    <div class="cert-card tilt-card featured">
      <div class="cc-badge"><svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg></div>
      <div class="cc-icon"><svg viewBox="0 0 24 24"><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></svg></div>
      <div class="cc-name">DGX AI Compute Systems Technical</div>
      <div class="cc-issuer">NVIDIA Partner Network</div>
      <div class="cc-date">Jun 23, 2025</div>
    </div>

    <div class="cert-card tilt-card featured">
      <div class="cc-badge"><svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg></div>
      <div class="cc-icon"><svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="3"/><path d="M12 1v4M12 19v4M4.22 4.22l2.83 2.83M16.95 16.95l2.83 2.83M1 12h4M19 12h4M4.22 19.78l2.83-2.83M16.95 7.05l2.83-2.83"/></svg></div>
      <div class="cc-name">DGX AI Compute Systems Installation</div>
      <div class="cc-issuer">NVIDIA Partner Network</div>
      <div class="cc-date">Jun 25, 2025</div>
    </div>

    <div class="cert-card tilt-card" style="opacity:.8">
      <div class="cc-badge"><svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg></div>
      <div class="cc-icon" style="background:rgba(255,255,255,.03); border-color:rgba(255,255,255,0.1)"><svg style="stroke:var(--muted)" viewBox="0 0 24 24"><path d="M5 12.55a11 11 0 0114.08 0"/><path d="M1.42 9a16 16 0 0121.16 0"/><path d="M8.53 16.11a6 6 0 016.95 0"/><circle cx="12" cy="20" r="1" fill="currentColor"/></svg></div>
      <div class="cc-name" style="color:var(--muted)">Networking Technical Curriculum</div>
      <div class="cc-issuer">NVIDIA Partner Network</div>
      <div class="cc-date" style="color:var(--dim)">Jun 23, 2025</div>
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
    <span class="sec-sub">AI Factory Delivery Focus</span>
  </div>

  <div class="spec-hero reveal">
    <div class="spec-card tilt-card primary">
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

  <div class="spec-sub reveal" style="transition-delay:.1s">
    <div class="spec-card tilt-card">
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
    <div class="spec-card tilt-card">
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
    <div class="spec-card tilt-card">
      <div class="spec-label">Specialisation</div>
      <div class="spec-icon-large"><svg viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/></svg></div>
      <div class="spec-title">AI Factory Architecture &amp; DGX</div>
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
    <h2 class="sec-title">Technical Matrix</h2>
    <div class="sec-line"></div>
  </div>
  <div class="skills-wrap">
    <div class="reveal">
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

      <div class="skill-group-label" style="margin-top:32px">AI Factory · Compute Infrastructure</div>
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

      <div class="skill-group-label" style="margin-top:32px;color:var(--dim)">Supporting Infrastructure</div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name" style="color:var(--muted)">High-Speed Networking (InfiniBand / Ethernet)</span><span class="skill-pct" style="color:var(--dim)">72%</span></div>
        <div class="bar-track"><div class="bar-fill dim" style="background:var(--dim);box-shadow:none" data-w="72"></div></div>
      </div>

      <div class="tech-stack">
        <div class="stack-title">Key Technologies</div>
        <div class="stack-pills">
          <div class="stack-pill hoverable"><span class="dot dot-green"></span>CUDA / C++</div>
          <div class="stack-pill hoverable"><span class="dot dot-green"></span>TensorRT-LLM</div>
          <div class="stack-pill hoverable"><span class="dot dot-green"></span>NVIDIA NIM</div>
          <div class="stack-pill hoverable"><span class="dot dot-green"></span>NeMo Framework</div>
          <div class="stack-pill hoverable"><span class="dot dot-green"></span>Triton Server</div>
          <div class="stack-pill hoverable"><span class="dot dot-green"></span>PyTorch</div>
          <div class="stack-pill hoverable"><span class="dot dot-green"></span>Python</div>
          <div class="stack-pill hoverable"><span class="dot dot-green"></span>DGX H100/H200</div>
          <div class="stack-pill hoverable"><span class="dot dot-muted"></span>InfiniBand</div>
          <div class="stack-pill hoverable"><span class="dot dot-muted"></span>Kubernetes</div>
          <div class="stack-pill hoverable"><span class="dot dot-muted"></span>Slurm</div>
        </div>
      </div>
    </div>

    <div class="domain-matrix reveal" style="transition-delay:.2s">
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
      <div class="dm-cell" style="opacity:.6"><span class="dm-icon">🌐</span><div class="dm-name">Networking</div></div>
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
    <div class="vcard tilt-card">
      <div class="vnum">01 / 04</div>
      <div class="vtitle">NVIDIA-Certified Across the Full AI Stack</div>
      <div class="vbody">Five NVIDIA-issued credentials covering AI, compute, DGX systems, and installation — the most comprehensive partner certification coverage available from a single specialist, directly validating AI Factory readiness.</div>
    </div>
    <div class="vcard tilt-card">
      <div class="vnum">02 / 04</div>
      <div class="vtitle">Deep Learning &amp; CUDA at Core</div>
      <div class="vbody">Brings genuine GPU-native engineering depth — CUDA programming, PyTorch, TensorRT-LLM, and cuDNN — ensuring AI Factory infrastructure is not just deployed but optimised for real-world workload performance.</div>
    </div>
    <div class="vcard tilt-card">
      <div class="vnum">03 / 04</div>
      <div class="vtitle">Distributed Training &amp; Inference Expertise</div>
      <div class="vbody">Specialist knowledge in multi-node LLM training with NeMo and scalable inference with Triton Server and TensorRT-LLM — the exact capabilities required to maximise the ROI of a large-scale AI investment.</div>
    </div>
    <div class="vcard tilt-card">
      <div class="vnum">04 / 04</div>
      <div class="vtitle">Direct NVIDIA Partner-Level Access</div>
      <div class="vbody">Operating within an official NVIDIA Partner Network organisation with direct access to NVIDIA engineering teams, product roadmaps, and technical support channels — providing the inside edge.</div>
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
      <path d="M10.2 5.4C6.9 5.4 4 7.1 2.4 9.7C3.8 8.5 5.7 7.8 7.8 7.8C12 7.8 15.5 11.1 15.8 15.2C14.5 11.9 11.6 9.5 8.1 9.5C5.7 9.5 3.6 10.6 2.2 12.3L2.2 12.5C2.2 17 5.8 20.6 10.2 20.6C14.6 20.6 18.2 17 18.2 12.5V12.4C18.2 8.6 14.6 5.4 10.2 5.4Z" fill="#76b900" opacity="0.6"/>
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
/* ── Interactive Custom Cursor ─────────────────────────────── */
const dot = document.getElementById('cursor-dot');
const ring = document.getElementById('cursor-ring');
let mouseX = window.innerWidth / 2, mouseY = window.innerHeight / 2;
let ringX = mouseX, ringY = mouseY;

window.addEventListener('mousemove', e => {
  mouseX = e.clientX; mouseY = e.clientY;
  dot.style.left = mouseX + 'px'; dot.style.top = mouseY + 'px';
});

function animateRing() {
  ringX += (mouseX - ringX) * 0.15; // smooth trailing effect
  ringY += (mouseY - ringY) * 0.15;
  ring.style.left = ringX + 'px';
  ring.style.top = ringY + 'px';
  requestAnimationFrame(animateRing);
}
animateRing();

// Hover effects for cursor
const hoverElements = document.querySelectorAll('a, button, .nav-badge, .tilt-card, .hoverable, .dm-cell');
hoverElements.forEach(el => {
  el.addEventListener('mouseenter', () => document.body.classList.add('cursor-hover'));
  el.addEventListener('mouseleave', () => document.body.classList.remove('cursor-hover'));
});

/* ── Interactive GPU Node Canvas (Reacts to Mouse) ─────────── */
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
    for(let i=0;i<70;i++){
      nodes.push({
        x: Math.random()*W, y: Math.random()*H,
        vx:(Math.random()-.5)*0.5, vy:(Math.random()-.5)*0.5,
        r: Math.random()*2+1.5, pulse: Math.random()*Math.PI*2, speed: 0.02+Math.random()*0.02,
        baseVx: 0, baseVy: 0
      });
      nodes[i].baseVx = nodes[i].vx;
      nodes[i].baseVy = nodes[i].vy;
    }
  }

  function draw(){
    ctx.clearRect(0,0,W,H);
    // Mouse Interaction
    const mX = mouseX || -1000;
    const mY = mouseY || -1000;

    nodes.forEach(n=>{
      // Repel logic
      const dxMouse = n.x - mX; const dyMouse = n.y - mY;
      const distMouse = Math.sqrt(dxMouse*dxMouse + dyMouse*dyMouse);
      
      if(distMouse < 150) {
        const force = (150 - distMouse) / 150;
        n.vx += (dxMouse / distMouse) * force * 0.1;
        n.vy += (dyMouse / distMouse) * force * 0.1;
        // Draw line to mouse
        ctx.strokeStyle=`rgba(${GREEN},${force * 0.3})`;
        ctx.lineWidth=1;
        ctx.beginPath();
        ctx.moveTo(n.x, n.y);
        ctx.lineTo(mX, mY);
        ctx.stroke();
      } else {
        // Return to base velocity
        n.vx += (n.baseVx - n.vx) * 0.05;
        n.vy += (n.baseVy - n.vy) * 0.05;
      }

      n.x+=n.vx; n.y+=n.vy; n.pulse+=n.speed;
      if(n.x<0||n.x>W) { n.vx*=-1; n.baseVx*=-1; }
      if(n.y<0||n.y>H) { n.vy*=-1; n.baseVy*=-1; }
    });

    // edges
    for(let i=0;i<nodes.length;i++){
      for(let j=i+1;j<nodes.length;j++){
        const dx=nodes[i].x-nodes[j].x, dy=nodes[i].y-nodes[j].y;
        const d=Math.sqrt(dx*dx+dy*dy);
        if(d<120){
          const a=(1-d/120)*0.3;
          ctx.strokeStyle=`rgba(${GREEN},${a})`;
          ctx.lineWidth=0.8;
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
      ctx.fillStyle=`rgba(${GREEN},${0.4+pulse*0.4})`;
      ctx.fill();
    });
    requestAnimationFrame(draw);
  }

  window.addEventListener('resize', resize);
  resize(); draw();
})();

/* ── 3D Tilt Cards Physics ─────────────────────────────────── */
document.querySelectorAll('.tilt-card').forEach(card => {
  card.addEventListener('mousemove', e => {
    const rect = card.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    
    // Set custom properties for localized radial gradients (used in spec-cards)
    card.style.setProperty('--mouse-x', `${(x / rect.width) * 100}%`);
    card.style.setProperty('--mouse-y', `${(y / rect.height) * 100}%`);

    // 3D Tilt Calculations
    const centerX = rect.width / 2;
    const centerY = rect.height / 2;
    const rotateX = ((y - centerY) / centerY) * -6; // Max 6 deg tilt
    const rotateY = ((x - centerX) / centerX) * 6;
    
    card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale3d(1.02, 1.02, 1.02)`;
  });

  card.addEventListener('mouseleave', () => {
    card.style.transform = `perspective(1000px) rotateX(0deg) rotateY(0deg) scale3d(1, 1, 1)`;
  });
});

/* ── Scroll Reveals & Counters ─────────────────────────────── */
const obs = new IntersectionObserver(es=>{
  es.forEach(e=>{ if(e.isIntersecting) e.target.classList.add('vis') });
},{threshold:0.1});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));

function animCount(el,target){
  let s=null;
  (function step(t){
    if(!s) s=t;
    const p=Math.min((t-s)/1700,1);
    const e=1-Math.pow(1-p,4); // ease out quartic
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

/* ── Skill Bars ────────────────────────────────────────────── */
const bObs=new IntersectionObserver(es=>{
  es.forEach(e=>{
    if(e.isIntersecting){
      e.target.querySelectorAll('.bar-fill').forEach(b=>b.style.width=b.dataset.w+'%');
      bObs.unobserve(e.target);
    }
  });
},{threshold:0.15});
document.querySelectorAll('.skills-wrap').forEach(el=>bObs.observe(el));

/* ── Navbar Scrolled & Mobile Menu ─────────────────────────── */
const nav=document.getElementById('nav');
window.addEventListener('scroll',()=>{
  if(window.scrollY > 40) nav.classList.add('scrolled');
  else nav.classList.remove('scrolled');
});

const menuToggle = document.getElementById('menu-toggle');
const navLinks = document.getElementById('nav-links');

menuToggle.addEventListener('click', () => {
  menuToggle.classList.toggle('open');
  navLinks.classList.toggle('active');
});

// Close mobile menu on link click
document.querySelectorAll('.nav-link').forEach(link => {
  link.addEventListener('click', () => {
    menuToggle.classList.remove('open');
    navLinks.classList.remove('active');
  });
});
</script>
</body>
</html>
