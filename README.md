<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Debjit Chowdhury — AI Factory Architect · NVIDIA Elite Partner</title>
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:ital,wght@0,300;0,400;0,600;0,700;0,800;0,900;1,700&family=DM+Mono:wght@300;400;500&family=Barlow:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
/* ══════════════════════════════════════════════════════════
   ROOT
══════════════════════════════════════════════════════════ */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --g:#76b900;--g2:#a8e063;--g3:#3d6200;--g4:#1e3100;
  --cyan:#00e5ff;--cyan2:rgba(0,229,255,.12);
  --bg:#020507;--bg2:#050c10;--bg3:#080f14;
  --card:#08111a;--card2:#0c1824;
  --border:#0e2030;--border2:#162d40;
  --text:#d4eaf5;--muted:#8ab8cc;--dim:#3a6070;
  --white:#e8f4fa;
  --fd:'Barlow Condensed',sans-serif;
  --fb:'Barlow',sans-serif;
  --fm:'DM Mono',monospace;
  --glow:0 0 60px rgba(118,185,0,.2);
  --glow2:0 0 30px rgba(118,185,0,.15);
  --cglow:0 0 30px rgba(0,229,255,.15);
}
html{scroll-behavior:smooth;font-size:16px}
body{font-family:var(--fb);background:var(--bg);color:var(--text);overflow-x:hidden;line-height:1.6;cursor:default}
::selection{background:rgba(118,185,0,.25);color:var(--white)}
::-webkit-scrollbar{width:3px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:linear-gradient(var(--g3),var(--g));border-radius:2px}

/* ── Full-page background canvas ─── */
#bg-canvas{
  position:fixed;inset:0;z-index:0;
  pointer-events:none;opacity:.7;
}

/* ── Scanline overlay ─── */
body::after{
  content:'';position:fixed;inset:0;z-index:1;pointer-events:none;
  background:repeating-linear-gradient(0deg,transparent,transparent 3px,rgba(0,0,0,.04) 3px,rgba(0,0,0,.04) 4px);
}

/* ── Vignette ─── */
body::before{
  content:'';position:fixed;inset:0;z-index:0;pointer-events:none;
  background:radial-gradient(ellipse at 50% 0%,transparent 50%,rgba(2,5,7,.7) 100%);
}

/* ══════════════════════════════════════════════════════════
   NAV
══════════════════════════════════════════════════════════ */
#nav{
  position:fixed;top:0;left:0;right:0;z-index:1000;
  display:flex;align-items:center;justify-content:space-between;
  padding:0 36px;height:68px;
  background:rgba(2,5,7,.88);
  backdrop-filter:blur(28px);-webkit-backdrop-filter:blur(28px);
  border-bottom:1px solid var(--border);
  transition:border-color .4s,box-shadow .4s;
}
#nav::before{
  content:'';position:absolute;bottom:0;left:0;right:0;height:1px;
  background:linear-gradient(90deg,transparent,rgba(118,185,0,.4) 30%,rgba(0,229,255,.2) 70%,transparent);
  opacity:0;transition:opacity .4s;
}
#nav.scrolled{border-bottom-color:transparent}
#nav.scrolled::before{opacity:1}

.nav-logo{display:flex;align-items:center;height:40px}
.nav-logo img{height:38px;width:auto;filter:brightness(1.05)}

.nav-links{display:flex;align-items:center;gap:4px}
.nav-link{
  font-family:var(--fm);font-size:.58rem;letter-spacing:.12em;
  text-transform:uppercase;color:var(--muted);text-decoration:none;
  padding:6px 12px;border-radius:2px;transition:all .2s;white-space:nowrap;
  position:relative;
}
.nav-link::after{
  content:'';position:absolute;bottom:2px;left:12px;right:12px;
  height:1px;background:var(--g);transform:scaleX(0);transition:transform .2s;
}
.nav-link:hover{color:var(--g)}
.nav-link:hover::after,.nav-link.active::after{transform:scaleX(1)}
.nav-link.active{color:var(--g)}

.nav-status{
  display:flex;align-items:center;gap:8px;margin-left:12px;
  font-family:var(--fm);font-size:.58rem;letter-spacing:.1em;
  padding:6px 16px;border:1px solid rgba(118,185,0,.3);
  border-radius:2px;background:rgba(118,185,0,.05);color:var(--g);
  white-space:nowrap;
}
.nav-status .pulse-dot{
  width:6px;height:6px;border-radius:50%;background:var(--g);
  animation:pulseDot 1.8s ease-in-out infinite;
  box-shadow:0 0 8px var(--g);
}
@keyframes pulseDot{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.4;transform:scale(.7)}}

.hamburger{
  display:none;flex-direction:column;gap:5px;cursor:pointer;
  padding:6px;border:none;background:none;z-index:1001;
}
.hamburger span{display:block;width:22px;height:1.5px;background:var(--text);border-radius:1px;transition:all .3s}
.hamburger.open span:nth-child(1){transform:translateY(6.5px) rotate(45deg)}
.hamburger.open span:nth-child(2){opacity:0;transform:scaleX(0)}
.hamburger.open span:nth-child(3){transform:translateY(-6.5px) rotate(-45deg)}

.mobile-menu{
  display:none;position:fixed;inset:0;top:68px;z-index:999;
  background:rgba(2,5,7,.97);backdrop-filter:blur(24px);
  flex-direction:column;align-items:center;justify-content:center;
  gap:6px;padding:40px 24px;
}
.mobile-menu.open{display:flex}
.mobile-menu .nav-link{font-size:.8rem;padding:14px 32px;width:100%;text-align:center;border:1px solid var(--border);border-radius:3px}

/* ══════════════════════════════════════════════════════════
   HERO
══════════════════════════════════════════════════════════ */
#hero{
  position:relative;min-height:100vh;
  display:flex;align-items:center;
  padding:100px 0 80px;overflow:hidden;
}

/* HUD corner decorations */
#hero::before{
  content:'';position:absolute;top:80px;left:0;
  width:180px;height:180px;
  border-top:1px solid rgba(118,185,0,.2);
  border-left:1px solid rgba(118,185,0,.2);
  pointer-events:none;z-index:2;
}
#hero::after{
  content:'';position:absolute;bottom:20px;right:0;
  width:120px;height:120px;
  border-bottom:1px solid rgba(0,229,255,.15);
  border-right:1px solid rgba(0,229,255,.15);
  pointer-events:none;z-index:2;
}

.container{max-width:1240px;margin:0 auto;padding:0 36px;position:relative;z-index:3}

.hero-grid{display:grid;grid-template-columns:1fr 310px;gap:60px;align-items:center}

/* ─ Badge eyebrow ─ */
.hero-eyebrow{
  display:inline-flex;align-items:center;gap:10px;
  font-family:var(--fm);font-size:.7rem;letter-spacing:.2em;
  color:var(--g);text-transform:uppercase;margin-bottom:20px;
  padding:5px 14px;border:1px solid rgba(118,185,0,.2);
  border-radius:2px;background:rgba(118,185,0,.05);
}
.hero-eyebrow .blink{animation:blink 2s step-end infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}

/* ─ Name ─ */
.hero-name{
  font-family:var(--fd);
  font-size:clamp(3.8rem,7.5vw,6.5rem);
  font-weight:900;line-height:.88;
  letter-spacing:-.01em;color:var(--white);
  margin-bottom:4px;
  text-transform:uppercase;
}
.hero-name .green-stroke{
  color:transparent;
  -webkit-text-stroke:2px var(--g);
  text-shadow:0 0 60px rgba(118,185,0,.25);
}

/* ─ Role ─ */
.hero-role{
  font-family:var(--fd);font-size:1.55rem;font-weight:400;font-style:italic;
  color:var(--muted);margin-bottom:20px;letter-spacing:.03em;
}
.hero-role strong{color:var(--text);font-weight:600;font-style:normal}

/* ─ Company strip ─ */
.hero-co{
  display:flex;align-items:center;gap:0;
  margin-bottom:28px;overflow:hidden;width:fit-content;
}
.hero-co-inner{
  font-family:var(--fm);font-size:.65rem;letter-spacing:.1em;
  text-transform:uppercase;
  padding:7px 16px;
  border:1px solid rgba(118,185,0,.25);
  border-radius:2px;
  color:var(--g);
  background:rgba(118,185,0,.05);
  display:flex;align-items:center;gap:10px;
}
.hero-co-inner span{color:var(--g3)}

/* ─ Tags ─ */
.hero-tags{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:32px}
.htag{
  font-family:var(--fm);font-size:.7rem;letter-spacing:.06em;
  text-transform:uppercase;padding:5px 13px;border-radius:2px;
  transition:all .25s;cursor:default;
}
.htag-g{
  border:1px solid rgba(118,185,0,.4);color:var(--g);
  background:rgba(118,185,0,.07);
}
.htag-g:hover{background:rgba(118,185,0,.18);box-shadow:0 0 20px rgba(118,185,0,.2);transform:translateY(-2px)}
.htag-d{border:1px solid var(--border2);color:var(--muted)}
.htag-d:hover{border-color:var(--g);color:var(--g)}
.htag-c{border:1px solid rgba(0,229,255,.25);color:rgba(0,229,255,.7);background:rgba(0,229,255,.05)}
.htag-c:hover{background:rgba(0,229,255,.12);box-shadow:0 0 20px rgba(0,229,255,.1)}

/* ─ Meta ─ */
.hero-meta{display:flex;gap:22px;flex-wrap:wrap}
.hm{
  display:flex;align-items:center;gap:7px;
  font-size:.75rem;color:var(--muted);text-decoration:none;transition:color .2s;
}
.hm:hover{color:var(--g)}
.hm svg{width:12px;height:12px;stroke:var(--g);fill:none;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;flex-shrink:0}

/* ─ Stat column ─ */
.stat-col{display:flex;flex-direction:column;gap:10px}
.stat-card{
  position:relative;overflow:hidden;
  background:var(--card);border:1px solid var(--border);
  border-radius:4px;padding:18px 20px;
  transition:all .3s;cursor:default;
}
.stat-card::before{
  content:'';position:absolute;left:0;top:0;bottom:0;width:2px;
  background:linear-gradient(to bottom,var(--g),var(--g3));
}
.stat-card::after{
  content:'';position:absolute;top:-20px;right:-20px;
  width:80px;height:80px;
  background:radial-gradient(circle,rgba(118,185,0,.07),transparent 70%);
}
.stat-card:hover{border-color:rgba(118,185,0,.35);box-shadow:var(--glow);transform:translateX(-3px)}
.stat-n{
  font-family:var(--fd);font-size:2.8rem;font-weight:900;color:var(--g);
  line-height:1;margin-bottom:3px;text-shadow:0 0 30px rgba(118,185,0,.5);
}
.stat-l{font-family:var(--fm);font-size:.6rem;color:var(--muted);letter-spacing:.06em}
.stat-bar{height:2px;background:var(--bg3);margin-top:10px;border-radius:1px;overflow:hidden}
.stat-bar-fill{height:100%;background:linear-gradient(90deg,var(--g3),var(--g));border-radius:1px;width:0;transition:width 2s cubic-bezier(.16,1,.3,1);box-shadow:0 0 8px rgba(118,185,0,.5)}

/* ── AI PIPELINE FLOW ─────────────────────────────────────── */
/* Divider between hero and main — animated pipeline arrow */
.pipeline-bar{
  position:relative;z-index:3;
  background:var(--bg2);
  border-top:1px solid var(--border2);
  border-bottom:1px solid var(--border2);
  padding:18px 0;overflow:hidden;
}
.pipeline-bar::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(90deg,transparent,rgba(118,185,0,.04) 30%,rgba(0,229,255,.03) 70%,transparent);
  animation:barShimmer 4s ease-in-out infinite;
}
@keyframes barShimmer{0%,100%{transform:translateX(-100%)}100%{transform:translateX(200%)}}
.pipeline-inner{
  max-width:1240px;margin:0 auto;padding:0 36px;
  display:flex;align-items:center;justify-content:space-between;
  gap:0;
}
.pipe-stage{
  display:flex;flex-direction:column;align-items:center;gap:5px;
  position:relative;flex:1;
}
.pipe-stage-icon{
  font-size:1.3rem;
  filter:drop-shadow(0 0 6px rgba(118,185,0,.4));
}
.pipe-stage-label{
  font-family:var(--fm);font-size:.53rem;letter-spacing:.15em;
  text-transform:uppercase;color:var(--muted);
}
.pipe-stage-sub{
  font-family:var(--fd);font-size:1rem;font-weight:700;
  text-transform:uppercase;color:var(--g);letter-spacing:.05em;
}
.pipe-arrow{
  display:flex;align-items:center;
  color:rgba(118,185,0,.3);font-size:1rem;
  padding:0 8px;flex-shrink:0;
}
.pipe-flow-dot{
  width:6px;height:6px;border-radius:50%;background:var(--g);
  box-shadow:0 0 8px var(--g);
  animation:flowAlong 3s linear infinite;
}
@keyframes flowAlong{
  0%{transform:translateX(-80px);opacity:0}
  10%{opacity:1}
  90%{opacity:1}
  100%{transform:translateX(80px);opacity:0}
}

/* ══════════════════════════════════════════════════════════
   SECTION STRUCTURE
══════════════════════════════════════════════════════════ */
section{padding:92px 0;border-top:1px solid var(--border);position:relative;z-index:3}

/* Section corner HUD marks */
section::before{
  content:'';position:absolute;top:0;left:36px;
  width:60px;height:1px;
  background:linear-gradient(to right,var(--g),transparent);
}

.sec-hd{display:flex;align-items:center;gap:14px;margin-bottom:56px}
.sec-num{font-family:var(--fm);font-size:.55rem;color:var(--g3);letter-spacing:.2em;flex-shrink:0}
.sec-title{
  font-family:var(--fd);font-size:2.1rem;font-weight:800;
  letter-spacing:.04em;color:var(--white);flex-shrink:0;
  text-transform:uppercase;
}
.sec-line{flex:1;height:1px;background:linear-gradient(to right,var(--border2),transparent)}
.sec-sub{font-family:var(--fm);font-size:.72rem;color:var(--muted);white-space:nowrap;letter-spacing:.05em}

/* ══════════════════════════════════════════════════════════
   CERTIFICATIONS
══════════════════════════════════════════════════════════ */
.cert-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:12px}

.cert-card{
  background:var(--card);border:1px solid var(--border);
  border-radius:4px;padding:22px 16px;
  position:relative;overflow:hidden;
  transition:all .4s cubic-bezier(.22,1,.36,1);cursor:default;
}
/* Circuit trace top border animation */
.cert-card::before{
  content:'';position:absolute;top:0;left:-100%;
  width:100%;height:1px;
  background:linear-gradient(90deg,transparent,var(--g),transparent);
  transition:left .5s ease;
}
.cert-card:hover::before{left:100%}
.cert-card:hover{
  border-color:rgba(118,185,0,.5);
  transform:translateY(-8px) scale(1.015);
  box-shadow:0 24px 60px rgba(118,185,0,.15),0 0 0 1px rgba(118,185,0,.08),inset 0 0 30px rgba(118,185,0,.03);
}
.cert-card.featured{
  border-color:rgba(118,185,0,.2);
  background:linear-gradient(145deg,rgba(118,185,0,.04) 0%,var(--card) 65%);
}
.cc-badge{
  position:absolute;top:10px;right:10px;
  width:18px;height:18px;background:var(--g);border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  box-shadow:0 0 14px rgba(118,185,0,.6);
}
.cc-badge svg{width:9px;height:9px;stroke:#000;fill:none;stroke-width:3;stroke-linecap:round;stroke-linejoin:round}
.cc-icon{
  width:38px;height:38px;border-radius:6px;
  display:flex;align-items:center;justify-content:center;margin-bottom:12px;
  background:rgba(118,185,0,.07);border:1px solid rgba(118,185,0,.12);
  transition:all .3s;
}
.cert-card:hover .cc-icon{background:rgba(118,185,0,.18);border-color:rgba(118,185,0,.4);box-shadow:0 0 20px rgba(118,185,0,.2)}
.cc-icon svg{width:18px;height:18px;stroke:var(--g);fill:none;stroke-width:1.8;stroke-linecap:round;stroke-linejoin:round}
.cc-name{font-family:var(--fd);font-size:1.05rem;font-weight:700;color:var(--white);line-height:1.3;margin-bottom:8px;text-transform:uppercase;letter-spacing:.02em}
.cc-issuer{font-family:var(--fm);font-size:.72rem;color:var(--muted);margin-bottom:4px}
.cc-date{font-family:var(--fm);font-size:.72rem;color:var(--g);letter-spacing:.06em}

/* ══════════════════════════════════════════════════════════
   SPECIALISATIONS
══════════════════════════════════════════════════════════ */
.spec-primary{
  display:grid;grid-template-columns:1fr 1fr;gap:0;
  border:1px solid rgba(118,185,0,.3);border-radius:4px;
  overflow:hidden;margin-bottom:14px;
  background:linear-gradient(135deg,rgba(118,185,0,.05),var(--card));
  position:relative;
  transition:all .35s;
}
.spec-primary::before{
  content:'';position:absolute;top:0;left:0;right:0;height:1px;
  background:linear-gradient(90deg,var(--g),rgba(0,229,255,.5),transparent);
}
.spec-primary:hover{box-shadow:0 20px 60px rgba(118,185,0,.1);border-color:rgba(118,185,0,.5)}
.spec-p-left{padding:36px 36px;border-right:1px solid rgba(118,185,0,.15)}
.spec-p-right{padding:36px 32px;display:flex;flex-direction:column;gap:12px;justify-content:center}

.spec-tag{
  display:inline-flex;align-items:center;gap:6px;
  font-family:var(--fm);font-size:.68rem;letter-spacing:.16em;
  color:var(--g);text-transform:uppercase;margin-bottom:12px;
}
.spec-tag::before{content:'▸';font-size:.7rem}

.spec-icon{
  width:50px;height:50px;background:rgba(118,185,0,.09);
  border-radius:6px;border:1px solid rgba(118,185,0,.18);
  display:flex;align-items:center;justify-content:center;margin-bottom:16px;
  transition:all .3s;
}
.spec-primary:hover .spec-icon{background:rgba(118,185,0,.2);border-color:rgba(118,185,0,.4);box-shadow:0 0 20px rgba(118,185,0,.2)}
.spec-icon svg{width:24px;height:24px;stroke:var(--g);fill:none;stroke-width:1.6;stroke-linecap:round;stroke-linejoin:round}

.spec-h{
  font-family:var(--fd);font-size:1.8rem;font-weight:800;
  color:var(--white);margin-bottom:12px;
  line-height:1.1;text-transform:uppercase;letter-spacing:.02em;
}
.spec-body{font-size:.97rem;color:var(--muted);line-height:1.78;font-weight:300}
.spec-chips{display:flex;flex-wrap:wrap;gap:6px;margin-top:16px}
.chip{
  font-family:var(--fm);font-size:.7rem;letter-spacing:.05em;
  padding:4px 10px;background:rgba(118,185,0,.06);
  border:1px solid rgba(118,185,0,.16);color:var(--g);border-radius:2px;
  transition:all .2s;cursor:default;
}
.chip:hover{background:rgba(118,185,0,.15);border-color:var(--g);transform:translateY(-1px)}

.spec-metric{
  background:rgba(118,185,0,.04);border:1px solid rgba(118,185,0,.1);
  border-radius:4px;padding:13px 15px;
  display:flex;align-items:flex-start;gap:11px;
  transition:all .2s;
}
.spec-metric:hover{background:rgba(118,185,0,.09);border-color:rgba(118,185,0,.22)}
.sm-ico{font-size:1.1rem;flex-shrink:0;margin-top:1px}
.sm-t{font-size:.88rem;color:var(--muted);line-height:1.45}
.sm-t strong{display:block;color:var(--white);font-size:.9rem;margin-bottom:1px;font-weight:600}

/* Sub spec grid */
.spec-sub{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
.spec-sub-card{
  background:var(--card);border:1px solid var(--border);
  border-radius:4px;padding:26px 22px;
  position:relative;overflow:hidden;transition:all .35s;cursor:default;
}
.spec-sub-card::after{
  content:'';position:absolute;bottom:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,transparent,var(--g),transparent);
  transform:scaleX(0);transition:transform .3s;
}
.spec-sub-card:hover{border-color:rgba(118,185,0,.4);transform:translateY(-5px);box-shadow:0 20px 40px rgba(118,185,0,.1)}
.spec-sub-card:hover::after{transform:scaleX(1)}

/* ══════════════════════════════════════════════════════════
   SKILLS
══════════════════════════════════════════════════════════ */
.skills-wrap{display:grid;grid-template-columns:1.35fr 1fr;gap:60px;align-items:start}

.sg-label{
  font-family:var(--fm);font-size:.68rem;letter-spacing:.16em;
  text-transform:uppercase;color:var(--g);
  display:flex;align-items:center;gap:10px;
  margin-bottom:14px;margin-top:28px;
}
.sg-label::after{content:'';flex:1;height:1px;background:var(--border)}
.sg-label:first-child{margin-top:0}

.skill-row{margin-bottom:13px}
.skill-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:5px}
.skill-name{font-size:.91rem;color:var(--text);font-weight:400}
.skill-name.core{color:var(--white);font-weight:600}
.skill-pct{font-family:var(--fm);font-size:.78rem;color:var(--g)}
.bar-track{
  height:3px;background:var(--bg3);border-radius:2px;overflow:hidden;
  position:relative;
}
.bar-fill{
  height:100%;border-radius:2px;width:0;
  background:linear-gradient(90deg,var(--g3),var(--g),var(--g2));
  transition:width 1.7s cubic-bezier(.16,1,.3,1);
  box-shadow:0 0 10px rgba(118,185,0,.45);position:relative;z-index:1;
}
.bar-fill.core{box-shadow:0 0 14px rgba(168,224,0,.6)}
.bar-fill.dim{background:linear-gradient(90deg,var(--dim),var(--g3));box-shadow:none}

.tech-stack{margin-top:26px}
.stack-title{font-family:var(--fm);font-size:.68rem;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);margin-bottom:11px}
.stack-pills{display:flex;flex-wrap:wrap;gap:7px}
.stack-pill{
  display:flex;align-items:center;gap:7px;
  padding:7px 13px;background:var(--card2);
  border:1px solid var(--border2);border-radius:3px;
  font-size:.85rem;color:var(--text);font-weight:400;
  transition:all .25s;cursor:default;
}
.stack-pill:hover{border-color:var(--g);color:var(--white);background:rgba(118,185,0,.07)}
.dot{width:5px;height:5px;border-radius:50%;flex-shrink:0}
.dot-g{background:var(--g);box-shadow:0 0 6px rgba(118,185,0,.7)}
.dot-d{background:var(--dim)}

/* Domain matrix */
.domain-matrix{display:grid;grid-template-columns:repeat(3,1fr);gap:9px}
.dm-cell{
  background:var(--card);border:1px solid var(--border);
  border-radius:4px;padding:15px 10px;text-align:center;
  transition:all .25s;cursor:default;overflow:hidden;position:relative;
}
.dm-cell::before{
  content:'';position:absolute;inset:0;
  background:radial-gradient(circle,rgba(118,185,0,.08),transparent 70%);
  opacity:0;transition:opacity .25s;
}
.dm-cell:hover{border-color:var(--g);transform:scale(1.04)}
.dm-cell:hover::before{opacity:1}
.dm-cell.hi{border-color:rgba(118,185,0,.2);background:rgba(118,185,0,.04)}
.dm-icon{font-size:1.3rem;margin-bottom:5px;display:block}
.dm-name{font-family:var(--fm);font-size:.72rem;color:var(--muted);line-height:1.3;letter-spacing:.03em}
.dm-cell.hi .dm-name{color:var(--g)}

/* ══════════════════════════════════════════════════════════
   TIMELINE
══════════════════════════════════════════════════════════ */
.timeline{position:relative;padding-left:28px}
.timeline::before{
  content:'';position:absolute;left:4px;top:10px;bottom:10px;width:1px;
  background:linear-gradient(to bottom,var(--g) 0%,var(--g3) 60%,transparent 100%);
}
.tl-item{position:relative;margin-bottom:38px}
.tl-dot{
  position:absolute;left:-28px;top:7px;
  width:9px;height:9px;border-radius:50%;
  background:var(--bg);border:1.5px solid var(--g);transition:all .25s;
}
.tl-item:hover .tl-dot{background:var(--g);box-shadow:0 0 0 5px rgba(118,185,0,.12)}
.tl-period{font-family:var(--fm);font-size:.72rem;color:var(--g);letter-spacing:.12em;text-transform:uppercase;margin-bottom:4px}
.tl-title{font-family:var(--fd);font-size:1.35rem;font-weight:800;color:var(--white);margin-bottom:2px;text-transform:uppercase;letter-spacing:.03em}
.tl-co{font-size:.9rem;color:var(--muted);margin-bottom:10px;font-weight:300}
.tl-desc{font-size:.97rem;color:var(--muted);line-height:1.76;font-weight:300}
.tl-chips{display:flex;flex-wrap:wrap;gap:7px;margin-top:12px}
.tl-chip{font-family:var(--fm);font-size:.7rem;letter-spacing:.05em;padding:5px 11px;background:rgba(118,185,0,.06);border:1px solid rgba(118,185,0,.15);color:var(--g);border-radius:2px}

/* ══════════════════════════════════════════════════════════
   VALUE
══════════════════════════════════════════════════════════ */
.value-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:12px}
.vcard{
  background:var(--card);border:1px solid var(--border);
  border-radius:4px;padding:24px 20px;
  transition:all .3s;position:relative;overflow:hidden;cursor:default;
}
.vcard::before{
  content:'';position:absolute;bottom:0;left:0;right:0;height:1px;
  background:linear-gradient(90deg,transparent,var(--g),transparent);
  opacity:0;transition:opacity .3s;
}
.vcard:hover{border-color:rgba(118,185,0,.3);transform:translateY(-5px);box-shadow:0 18px 40px rgba(118,185,0,.09)}
.vcard:hover::before{opacity:1}
.vnum{font-family:var(--fm);font-size:.52rem;color:var(--dim);letter-spacing:.15em;margin-bottom:12px}
.vtitle{font-family:var(--fd);font-size:1.15rem;font-weight:800;color:var(--g);margin-bottom:10px;line-height:1.2;text-transform:uppercase;letter-spacing:.02em}
.vbody{font-size:.93rem;color:var(--muted);line-height:1.72;font-weight:300}

/* ══════════════════════════════════════════════════════════
   FOOTER
══════════════════════════════════════════════════════════ */
#footer{
  padding:26px 36px;
  background:var(--card);border-top:1px solid var(--border);
  display:flex;align-items:center;justify-content:space-between;
  flex-wrap:wrap;gap:16px;position:relative;z-index:3;
}
#footer::before{
  content:'';position:absolute;top:0;left:0;right:0;height:1px;
  background:linear-gradient(90deg,transparent,rgba(118,185,0,.3) 30%,rgba(0,229,255,.2) 70%,transparent);
}
.footer-left{display:flex;align-items:center;gap:14px}
.footer-logo{height:32px;width:auto;filter:brightness(.7)}
.footer-text{font-family:var(--fm);font-size:.55rem;color:var(--dim);letter-spacing:.06em;line-height:1.7}
.footer-badge{font-family:var(--fm);font-size:.56rem;letter-spacing:.1em;padding:6px 16px;border:1px solid rgba(118,185,0,.25);color:var(--g);border-radius:2px;background:rgba(118,185,0,.04)}

/* ══════════════════════════════════════════════════════════
   REVEAL
══════════════════════════════════════════════════════════ */
.reveal{opacity:0;transform:translateY(18px);transition:opacity .6s ease,transform .6s ease}
.reveal.vis{opacity:1;transform:none}
.stagger>*{opacity:0;transform:translateY(14px);transition:opacity .45s ease,transform .45s ease}
.stagger.vis>*:nth-child(1){opacity:1;transform:none;transition-delay:.0s}
.stagger.vis>*:nth-child(2){opacity:1;transform:none;transition-delay:.07s}
.stagger.vis>*:nth-child(3){opacity:1;transform:none;transition-delay:.14s}
.stagger.vis>*:nth-child(4){opacity:1;transform:none;transition-delay:.21s}
.stagger.vis>*:nth-child(5){opacity:1;transform:none;transition-delay:.28s}

/* ══════════════════════════════════════════════════════════
   RESPONSIVE
══════════════════════════════════════════════════════════ */
@media(max-width:1080px){
  .cert-grid{grid-template-columns:repeat(3,1fr)}
  .value-grid{grid-template-columns:repeat(2,1fr)}
  .spec-primary{grid-template-columns:1fr}
  .spec-p-left{border-right:none;border-bottom:1px solid rgba(118,185,0,.15)}
}
@media(max-width:768px){
  #nav{padding:0 20px}
  .nav-links,.nav-status{display:none}
  .hamburger{display:flex}
  .container{padding:0 20px}
  .hero-grid{grid-template-columns:1fr;gap:32px}
  .stat-col{flex-direction:row;flex-wrap:wrap}
  .stat-card{flex:1;min-width:120px}
  .cert-grid{grid-template-columns:repeat(2,1fr)}
  .spec-sub{grid-template-columns:1fr}
  .skills-wrap{grid-template-columns:1fr;gap:36px}
  .value-grid{grid-template-columns:1fr}
  .pipeline-inner{gap:4px}
  .pipe-stage-sub{font-size:.7rem}
  .pipe-stage-label{display:none}
  #footer{flex-direction:column;align-items:flex-start;padding:20px}
  section{padding:60px 0}
  section::before{left:20px}
  #hero::before,#hero::after{display:none}
  .sec-sub{display:none}
}
@media(max-width:480px){
  .cert-grid{grid-template-columns:1fr}
  .stat-col{flex-direction:column}
  .hero-tags{gap:6px}
  .pipeline-inner{justify-content:center;gap:6px}
  .pipe-arrow{display:none}
}

/* AI Factory Architecture Diagram */
.aif-diagram-wrap{
  border:1px solid rgba(118,185,0,.2);border-radius:6px;
  overflow:hidden;background:rgba(8,17,26,.8);
  margin-bottom:14px;
}
.aif-diagram-label{
  font-family:var(--fm);font-size:.7rem;letter-spacing:.18em;
  text-transform:uppercase;color:var(--g);
  padding:10px 20px;
  border-bottom:1px solid rgba(118,185,0,.15);
  background:rgba(118,185,0,.04);
  display:flex;align-items:center;gap:8px;
}
.aif-diagram-label::before{content:'◆';font-size:.6rem}
.aif-svg{
  width:100%;height:auto;display:block;
  max-height:300px;
}

</style>
</head>
<body>

<!-- FULL-PAGE BACKGROUND CANVAS -->
<canvas id="bg-canvas"></canvas>

<!-- ══════════════════════════════════════════
     NAVBAR
═══════════════════════════════════════════ -->
<nav id="nav">
  <div class="nav-logo">
    <img src="data:image/png;base64,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" alt="NVIDIA Elite Partner · Micropoint Computers"/>
  </div>
  <div class="nav-links">
    <a class="nav-link" href="#certs">Certifications</a>
    <a class="nav-link" href="#specialisations">Specialisations</a>
    <a class="nav-link" href="#skills">Skills</a>
    <a class="nav-link" href="#experience">Experience</a>
    <div class="nav-status">
      <span class="pulse-dot"></span>AI Factory Active
    </div>
  </div>
  <button class="hamburger" id="hamburger" aria-label="Menu" aria-expanded="false">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- Mobile menu -->
<div class="mobile-menu" id="mobile-menu">
  <a class="nav-link" href="#certs">Certifications</a>
  <a class="nav-link" href="#specialisations">Specialisations</a>
  <a class="nav-link" href="#skills">Skills</a>
  <a class="nav-link" href="#experience">Experience</a>
</div>

<!-- ══════════════════════════════════════════
     HERO
═══════════════════════════════════════════ -->
<section id="hero">
  <div class="container">
    <div class="hero-grid">
      <div>
        <div class="hero-eyebrow">
          <span class="blink">◆</span>&nbsp; AI Factory Solution Architect Profile
        </div>

        <h1 class="hero-name reveal">
          Debjit<br>
          <span class="green-stroke">Chowdhury</span>
        </h1>

        <p class="hero-role reveal" style="transition-delay:.06s">
          <strong>AI Solutions Architect</strong> &nbsp;·&nbsp; NVIDIA Certified Partner Specialist
        </p>

        <div class="hero-co reveal" style="transition-delay:.1s">
          <div class="hero-co-inner">
            <span>▸</span>
            Micropoint Computers Pvt. Ltd. &nbsp;—&nbsp; NVIDIA Partner Network
          </div>
        </div>

        <div class="hero-tags reveal" style="transition-delay:.14s">
          <span class="htag htag-g">NVIDIA Elite Partner</span>
          <span class="htag htag-g">Generative AI</span>
          <span class="htag htag-g">Deep Learning / CUDA</span>
          <span class="htag htag-g">AI Factory Design</span>
          <span class="htag htag-c">DGX Infrastructure</span>
          <span class="htag htag-c">Distributed Training</span>
          <span class="htag htag-d">LLM Inference</span>
          <span class="htag htag-d">HPC / GPU</span>
        </div>

        <div class="hero-meta reveal" style="transition-delay:.18s">
          <span class="hm">
            <svg viewBox="0 0 24 24"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
            Bengaluru, India
          </span>
          <a class="hm" href="https://linkedin.com/in/debjit-chowdhury-298772191" target="_blank" rel="noopener">
            <svg viewBox="0 0 24 24"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
            linkedin.com/in/debjit-chowdhury
          </a>
        </div>
      </div>

      <div class="stat-col">
        <div class="stat-card reveal">
          <div class="stat-n" data-count="5">0</div>
          <div class="stat-l">NVIDIA Certifications (2025)</div>
          <div class="stat-bar"><div class="stat-bar-fill" data-w="100"></div></div>
        </div>
        <div class="stat-card reveal" style="transition-delay:.09s">
          <div class="stat-n" data-count="3">0</div>
          <div class="stat-l">Years in AI / ML Engineering</div>
          <div class="stat-bar"><div class="stat-bar-fill" data-w="75"></div></div>
        </div>
        <div class="stat-card reveal" style="transition-delay:.18s">
          <div class="stat-n" style="font-size:1.9rem;letter-spacing:-.02em">360°</div>
          <div class="stat-l">Full-Stack AI Factory Coverage</div>
          <div class="stat-bar"><div class="stat-bar-fill" data-w="100"></div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════════
     AI FACTORY PIPELINE BAR
═══════════════════════════════════════════ -->
<div class="pipeline-bar">
  <div class="pipeline-inner">
    <div class="pipe-stage">
      <div class="pipe-stage-icon">📥</div>
      <div class="pipe-stage-label">Stage 01</div>
      <div class="pipe-stage-sub">Data Ingest</div>
    </div>
    <div class="pipe-arrow">
      <div class="pipe-flow-dot" style="animation-delay:0s"></div>
      <span style="margin:0 4px;font-family:var(--fm);font-size:.8rem;color:rgba(118,185,0,.3)">──▶</span>
    </div>
    <div class="pipe-stage">
      <div class="pipe-stage-icon">🏋</div>
      <div class="pipe-stage-label">Stage 02</div>
      <div class="pipe-stage-sub">Distributed Train</div>
    </div>
    <div class="pipe-arrow">
      <div class="pipe-flow-dot" style="animation-delay:.6s"></div>
      <span style="margin:0 4px;font-family:var(--fm);font-size:.8rem;color:rgba(118,185,0,.3)">──▶</span>
    </div>
    <div class="pipe-stage">
      <div class="pipe-stage-icon">🔬</div>
      <div class="pipe-stage-label">Stage 03</div>
      <div class="pipe-stage-sub">Fine-tune / PEFT</div>
    </div>
    <div class="pipe-arrow">
      <div class="pipe-flow-dot" style="animation-delay:1.2s"></div>
      <span style="margin:0 4px;font-family:var(--fm);font-size:.8rem;color:rgba(118,185,0,.3)">──▶</span>
    </div>
    <div class="pipe-stage">
      <div class="pipe-stage-icon">⚡</div>
      <div class="pipe-stage-label">Stage 04</div>
      <div class="pipe-stage-sub">TensorRT Optimise</div>
    </div>
    <div class="pipe-arrow">
      <div class="pipe-flow-dot" style="animation-delay:1.8s"></div>
      <span style="margin:0 4px;font-family:var(--fm);font-size:.8rem;color:rgba(118,185,0,.3)">──▶</span>
    </div>
    <div class="pipe-stage">
      <div class="pipe-stage-icon">📡</div>
      <div class="pipe-stage-label">Stage 05</div>
      <div class="pipe-stage-sub">Triton Serve</div>
    </div>
    <div class="pipe-arrow">
      <div class="pipe-flow-dot" style="animation-delay:2.4s"></div>
      <span style="margin:0 4px;font-family:var(--fm);font-size:.8rem;color:rgba(118,185,0,.3)">──▶</span>
    </div>
    <div class="pipe-stage">
      <div class="pipe-stage-icon">🏭</div>
      <div class="pipe-stage-label">Stage 06</div>
      <div class="pipe-stage-sub">AI Factory Live</div>
    </div>
  </div>
</div>

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
  <div class="cert-grid stagger reveal">

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

    <div class="cert-card" style="opacity:.68">
      <div class="cc-badge"><svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg></div>
      <div class="cc-icon" style="background:rgba(118,185,0,.03)"><svg viewBox="0 0 24 24"><path d="M5 12.55a11 11 0 0114.08 0"/><path d="M1.42 9a16 16 0 0121.16 0"/><path d="M8.53 16.11a6 6 0 016.95 0"/><circle cx="12" cy="20" r="1" fill="currentColor"/></svg></div>
      <div class="cc-name" style="color:var(--muted)">Networking Technical Curriculum</div>
      <div class="cc-issuer">NVIDIA Partner Network</div>
      <div class="cc-date">Jun 23, 2025</div>
    </div>

  </div>
</div>
</section>

<!-- ══════════════════════════════════════════
     SPECIALISATIONS
═══════════════════════════════════════════ -->
<section id="specialisations">
<div class="container">
  <div class="sec-hd reveal">
    <span class="sec-num">02</span>
    <h2 class="sec-title">Core Specialisations</h2>
    <div class="sec-line"></div>
    <span class="sec-sub">Primary technical focus areas for AI Factory delivery</span>
  </div>

  <!-- Primary card -->
  <div class="spec-primary reveal">
    <div class="spec-p-left">
      <div class="spec-tag">Primary Specialisation</div>
      <div class="spec-icon">
        <svg viewBox="0 0 24 24"><rect x="2" y="3" width="6" height="6" rx="1"/><rect x="16" y="3" width="6" height="6" rx="1"/><rect x="9" y="15" width="6" height="6" rx="1"/><path d="M5 9v3a1 1 0 001 1h12a1 1 0 001-1V9"/><path d="M12 13v2"/></svg>
      </div>
      <div class="spec-h">Distributed Training &amp;<br>Inference of LLMs</div>
      <div class="spec-body">
        Expert in designing and deploying large-scale distributed training pipelines and optimised inference stacks for Large Language Models on NVIDIA GPU clusters. Leverages NVIDIA's NeMo Framework, TensorRT-LLM, Triton Inference Server, and multi-node DGX infrastructure to achieve maximum throughput and minimal latency for production AI Factory workloads.
      </div>
      <div class="spec-chips">
        <span class="chip">NeMo Framework</span>
        <span class="chip">TensorRT-LLM</span>
        <span class="chip">Triton Inference Server</span>
        <span class="chip">Multi-GPU / Multi-Node</span>
        <span class="chip">NCCL</span>
        <span class="chip">Model Parallelism</span>
        <span class="chip">DGX H100 / H200</span>
      </div>
    </div>
    <div class="spec-p-right">
      <div class="spec-metric"><span class="sm-ico">🧩</span><div class="sm-t"><strong>Model Parallelism</strong>Tensor, pipeline &amp; sequence parallelism across DGX nodes</div></div>
      <div class="spec-metric"><span class="sm-ico">⚡</span><div class="sm-t"><strong>TensorRT-LLM Optimisation</strong>Quantisation, kernel fusion &amp; batching for low-latency inference</div></div>
      <div class="spec-metric"><span class="sm-ico">🏭</span><div class="sm-t"><strong>AI Factory Integration</strong>Full stack from raw GPU compute to production LLM endpoints</div></div>
      <div class="spec-metric"><span class="sm-ico">📡</span><div class="sm-t"><strong>Triton Inference Server</strong>Scalable model serving with dynamic batching &amp; ensemble pipelines</div></div>
    </div>
  </div>


  <!-- AI FACTORY ARCHITECTURE DIAGRAM -->
  <div class="aif-diagram-wrap reveal" style="margin-bottom:14px">
    <div class="aif-diagram-label">AI Factory — Full Stack Architecture</div>
    <svg class="aif-svg" viewBox="0 0 1100 280" fill="none" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="AI Factory Architecture Diagram">
      <defs>
        <linearGradient id="gG" x1="0" y1="0" x2="1" y2="0"><stop offset="0%" stop-color="#3d6200"/><stop offset="100%" stop-color="#76b900"/></linearGradient>
        <linearGradient id="gC" x1="0" y1="0" x2="1" y2="0"><stop offset="0%" stop-color="#005566"/><stop offset="100%" stop-color="#00c4dc"/></linearGradient>
        <linearGradient id="gB" x1="0" y1="0" x2="0" y2="1"><stop offset="0%" stop-color="#0d1f2d"/><stop offset="100%" stop-color="#091520"/></linearGradient>
        <filter id="glow"><feGaussianBlur stdDeviation="3" result="blur"/><feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge></filter>
      </defs>

      <!-- Background -->
      <rect width="1100" height="280" fill="url(#gB)" rx="6"/>
      <rect width="1100" height="280" fill="none" stroke="rgba(118,185,0,0.2)" stroke-width="1" rx="6"/>

      <!-- Layer labels on left -->
      <text x="14" y="56" fill="rgba(118,185,0,0.5)" font-family="DM Mono,monospace" font-size="9" letter-spacing="2">APPS</text>
      <text x="14" y="118" fill="rgba(118,185,0,0.5)" font-family="DM Mono,monospace" font-size="9" letter-spacing="2">SW</text>
      <text x="14" y="182" fill="rgba(118,185,0,0.5)" font-family="DM Mono,monospace" font-size="9" letter-spacing="2">PLATFORM</text>
      <text x="14" y="244" fill="rgba(118,185,0,0.5)" font-family="DM Mono,monospace" font-size="9" letter-spacing="2">HW</text>

      <!-- Vertical separator -->
      <line x1="55" y1="10" x2="55" y2="270" stroke="rgba(118,185,0,0.12)" stroke-width="1"/>

      <!-- LAYER 1: Applications (y=30..76) -->
      <rect x="66" y="28" width="150" height="40" rx="4" fill="rgba(118,185,0,0.08)" stroke="rgba(118,185,0,0.35)" stroke-width="1"/>
      <text x="141" y="44" fill="#a8e063" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">GENERATIVE AI</text>
      <text x="141" y="58" fill="rgba(168,224,99,0.6)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">LLM · RAG · Agents</text>

      <rect x="228" y="28" width="140" height="40" rx="4" fill="rgba(118,185,0,0.06)" stroke="rgba(118,185,0,0.25)" stroke-width="1"/>
      <text x="298" y="44" fill="#a8e063" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">AGENTIC AI</text>
      <text x="298" y="58" fill="rgba(168,224,99,0.6)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">LangChain · AutoGen</text>

      <rect x="380" y="28" width="140" height="40" rx="4" fill="rgba(118,185,0,0.06)" stroke="rgba(118,185,0,0.25)" stroke-width="1"/>
      <text x="450" y="44" fill="#a8e063" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">ROBOTICS / SIM</text>
      <text x="450" y="58" fill="rgba(168,224,99,0.6)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Omniverse · Isaac</text>

      <rect x="532" y="28" width="140" height="40" rx="4" fill="rgba(118,185,0,0.06)" stroke="rgba(118,185,0,0.25)" stroke-width="1"/>
      <text x="602" y="44" fill="#a8e063" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">CV / PERCEPTION</text>
      <text x="602" y="58" fill="rgba(168,224,99,0.6)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">DeepStream · TAO</text>

      <rect x="684" y="28" width="140" height="40" rx="4" fill="rgba(118,185,0,0.06)" stroke="rgba(118,185,0,0.25)" stroke-width="1"/>
      <text x="754" y="44" fill="#a8e063" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">HPC / SCIENCE</text>
      <text x="754" y="58" fill="rgba(168,224,99,0.6)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">CUDA · cuBLAS</text>

      <!-- AI Factory label in top right -->
      <rect x="854" y="28" width="220" height="40" rx="4" fill="rgba(118,185,0,0.15)" stroke="rgba(118,185,0,0.6)" stroke-width="1.5"/>
      <text x="964" y="43" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="13" font-weight="900" text-anchor="middle" letter-spacing="2">🏭 AI FACTORY</text>
      <text x="964" y="58" fill="rgba(118,185,0,0.7)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">NVIDIA Partner Stack</text>

      <!-- Horizontal separator line -->
      <line x1="66" y1="80" x2="1080" y2="80" stroke="rgba(118,185,0,0.15)" stroke-width="1" stroke-dasharray="4,3"/>

      <!-- LAYER 2: Software (y=88..134) -->
      <rect x="66" y="88" width="206" height="40" rx="4" fill="rgba(0,180,200,0.06)" stroke="rgba(0,180,200,0.3)" stroke-width="1"/>
      <text x="169" y="104" fill="#00c4dc" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">NEMO FRAMEWORK</text>
      <text x="169" y="118" fill="rgba(0,196,220,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Training · Fine-tuning · PEFT</text>

      <rect x="284" y="88" width="186" height="40" rx="4" fill="rgba(0,180,200,0.06)" stroke="rgba(0,180,200,0.25)" stroke-width="1"/>
      <text x="377" y="104" fill="#00c4dc" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">TENSORRT-LLM</text>
      <text x="377" y="118" fill="rgba(0,196,220,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Quant · Kernel Fusion · Batch</text>

      <rect x="482" y="88" width="186" height="40" rx="4" fill="rgba(0,180,200,0.06)" stroke="rgba(0,180,200,0.25)" stroke-width="1"/>
      <text x="575" y="104" fill="#00c4dc" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">TRITON SERVER</text>
      <text x="575" y="118" fill="rgba(0,196,220,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Dynamic Batch · Ensemble</text>

      <rect x="680" y="88" width="186" height="40" rx="4" fill="rgba(0,180,200,0.06)" stroke="rgba(0,180,200,0.25)" stroke-width="1"/>
      <text x="773" y="104" fill="#00c4dc" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">NVIDIA NIM</text>
      <text x="773" y="118" fill="rgba(0,196,220,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Microservices · APIs</text>

      <rect x="878" y="88" width="196" height="40" rx="4" fill="rgba(0,180,200,0.06)" stroke="rgba(0,180,200,0.25)" stroke-width="1"/>
      <text x="976" y="104" fill="#00c4dc" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">KUBERNETES/SLURM</text>
      <text x="976" y="118" fill="rgba(0,196,220,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Orchestration · Scheduling</text>

      <!-- Separator -->
      <line x1="66" y1="142" x2="1080" y2="142" stroke="rgba(118,185,0,0.15)" stroke-width="1" stroke-dasharray="4,3"/>

      <!-- LAYER 3: Platform (y=150..196) -->
      <rect x="66" y="150" width="290" height="40" rx="4" fill="rgba(118,185,0,0.05)" stroke="rgba(118,185,0,0.2)" stroke-width="1"/>
      <text x="211" y="166" fill="#a8e063" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">BASE COMMAND PLATFORM</text>
      <text x="211" y="180" fill="rgba(168,224,99,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">AI Workload Management</text>

      <rect x="368" y="150" width="220" height="40" rx="4" fill="rgba(118,185,0,0.05)" stroke="rgba(118,185,0,0.2)" stroke-width="1"/>
      <text x="478" y="166" fill="#a8e063" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">CUDA / CUDNN</text>
      <text x="478" y="180" fill="rgba(168,224,99,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">GPU Acceleration Layer</text>

      <rect x="600" y="150" width="220" height="40" rx="4" fill="rgba(118,185,0,0.05)" stroke="rgba(118,185,0,0.2)" stroke-width="1"/>
      <text x="710" y="166" fill="#a8e063" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">HIGH-SPEED FABRIC</text>
      <text x="710" y="180" fill="rgba(168,224,99,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">InfiniBand · NVLink · NVSwitch</text>

      <rect x="832" y="150" width="242" height="40" rx="4" fill="rgba(118,185,0,0.05)" stroke="rgba(118,185,0,0.2)" stroke-width="1"/>
      <text x="953" y="166" fill="#a8e063" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="700" text-anchor="middle" letter-spacing="1">PARALLEL FILE SYSTEM</text>
      <text x="953" y="180" fill="rgba(168,224,99,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">GPFS · Lustre · NFS</text>

      <!-- Separator -->
      <line x1="66" y1="204" x2="1080" y2="204" stroke="rgba(118,185,0,0.15)" stroke-width="1" stroke-dasharray="4,3"/>

      <!-- LAYER 4: Hardware (y=212..258) -->
      <!-- DGX H100/H200 nodes -->
      <rect x="66" y="212" width="140" height="52" rx="4" fill="rgba(118,185,0,0.12)" stroke="url(#gG)" stroke-width="1.5"/>
      <text x="136" y="230" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="12" font-weight="900" text-anchor="middle" letter-spacing="1">DGX H200</text>
      <text x="136" y="244" fill="rgba(118,185,0,0.65)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">8× H200 SXM · 141GB</text>
      <text x="136" y="255" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">NVLink 4 · NVSwitch</text>

      <rect x="218" y="212" width="140" height="52" rx="4" fill="rgba(118,185,0,0.09)" stroke="rgba(118,185,0,0.4)" stroke-width="1"/>
      <text x="288" y="230" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="12" font-weight="900" text-anchor="middle" letter-spacing="1">DGX H100</text>
      <text x="288" y="244" fill="rgba(118,185,0,0.65)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">8× H100 SXM · 80GB</text>
      <text x="288" y="255" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">NVLink 4 · 600GB/s</text>

      <rect x="370" y="212" width="140" height="52" rx="4" fill="rgba(118,185,0,0.07)" stroke="rgba(118,185,0,0.3)" stroke-width="1"/>
      <text x="440" y="230" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="12" font-weight="900" text-anchor="middle" letter-spacing="1">DGX A100</text>
      <text x="440" y="244" fill="rgba(118,185,0,0.65)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">8× A100 SXM · 80GB</text>
      <text x="440" y="255" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">NVLink 3.0</text>

      <!-- GPU count diagram right side -->
      <text x="560" y="230" fill="rgba(118,185,0,0.4)" font-family="DM Mono,monospace" font-size="9" letter-spacing="1">MULTI-NODE CLUSTER</text>

      <!-- GPU grid diagram -->
      <g transform="translate(555,238)">
        <!-- Row 1 -->
        <rect x="0"  y="0" width="16" height="16" rx="2" fill="rgba(118,185,0,0.3)" stroke="rgba(118,185,0,0.6)" stroke-width=".8"/>
        <rect x="20" y="0" width="16" height="16" rx="2" fill="rgba(118,185,0,0.3)" stroke="rgba(118,185,0,0.6)" stroke-width=".8"/>
        <rect x="40" y="0" width="16" height="16" rx="2" fill="rgba(118,185,0,0.3)" stroke="rgba(118,185,0,0.6)" stroke-width=".8"/>
        <rect x="60" y="0" width="16" height="16" rx="2" fill="rgba(118,185,0,0.3)" stroke="rgba(118,185,0,0.6)" stroke-width=".8"/>
        <!-- Row 2 -->
        <rect x="0"  y="20" width="16" height="16" rx="2" fill="rgba(118,185,0,0.2)" stroke="rgba(118,185,0,0.4)" stroke-width=".8"/>
        <rect x="20" y="20" width="16" height="16" rx="2" fill="rgba(118,185,0,0.2)" stroke="rgba(118,185,0,0.4)" stroke-width=".8"/>
        <rect x="40" y="20" width="16" height="16" rx="2" fill="rgba(118,185,0,0.2)" stroke="rgba(118,185,0,0.4)" stroke-width=".8"/>
        <rect x="60" y="20" width="16" height="16" rx="2" fill="rgba(118,185,0,0.2)" stroke="rgba(118,185,0,0.4)" stroke-width=".8"/>
        <!-- connect lines -->
        <line x1="16" y1="8" x2="20" y2="8" stroke="rgba(118,185,0,0.5)" stroke-width=".8"/>
        <line x1="36" y1="8" x2="40" y2="8" stroke="rgba(118,185,0,0.5)" stroke-width=".8"/>
        <line x1="56" y1="8" x2="60" y2="8" stroke="rgba(118,185,0,0.5)" stroke-width=".8"/>
        <line x1="16" y1="28" x2="20" y2="28" stroke="rgba(118,185,0,0.3)" stroke-width=".8"/>
        <line x1="36" y1="28" x2="40" y2="28" stroke="rgba(118,185,0,0.3)" stroke-width=".8"/>
        <line x1="56" y1="28" x2="60" y2="28" stroke="rgba(118,185,0,0.3)" stroke-width=".8"/>
        <!-- vertical connect between rows -->
        <line x1="8"  y1="16" x2="8"  y2="20" stroke="rgba(118,185,0,0.4)" stroke-width=".8"/>
        <line x1="28" y1="16" x2="28" y2="20" stroke="rgba(118,185,0,0.4)" stroke-width=".8"/>
        <line x1="48" y1="16" x2="48" y2="20" stroke="rgba(118,185,0,0.4)" stroke-width=".8"/>
        <line x1="68" y1="16" x2="68" y2="20" stroke="rgba(118,185,0,0.4)" stroke-width=".8"/>
        <text x="38" y="52" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">GPU NODES</text>
      </g>

      <!-- InfiniBand / NVLink arrows -->
      <g transform="translate(670,215)">
        <rect x="0" y="0" width="120" height="50" rx="4" fill="rgba(0,180,200,0.05)" stroke="rgba(0,180,200,0.25)" stroke-width="1"/>
        <text x="60" y="16" fill="#00c4dc" font-family="Barlow Condensed,sans-serif" font-size="10" font-weight="700" text-anchor="middle" letter-spacing="1">INTERCONNECT</text>
        <text x="60" y="28" fill="rgba(0,196,220,0.6)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">InfiniBand NDR 400G</text>
        <text x="60" y="39" fill="rgba(0,196,220,0.6)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">NVLink 900GB/s</text>
      </g>

      <!-- Power/Cooling -->
      <g transform="translate(806,215)">
        <rect x="0" y="0" width="120" height="50" rx="4" fill="rgba(118,185,0,0.04)" stroke="rgba(118,185,0,0.18)" stroke-width="1"/>
        <text x="60" y="16" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="10" font-weight="700" text-anchor="middle" letter-spacing="1">FACILITY</text>
        <text x="60" y="28" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">Power · Cooling</text>
        <text x="60" y="39" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">10-30kW per rack</text>
      </g>

      <!-- Micropoint / Partner -->
      <g transform="translate(942,215)">
        <rect x="0" y="0" width="132" height="50" rx="4" fill="rgba(118,185,0,0.1)" stroke="rgba(118,185,0,0.45)" stroke-width="1.5"/>
        <text x="66" y="16" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="10" font-weight="800" text-anchor="middle" letter-spacing="1">MICROPOINT</text>
        <text x="66" y="28" fill="rgba(118,185,0,0.65)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">NVIDIA Elite Partner</text>
        <text x="66" y="39" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">Design · Deploy · Support</text>
      </g>

      <!-- Vertical flow arrows between layers -->
      <g stroke="rgba(118,185,0,0.25)" stroke-width="1" marker-end="none">
        <line x1="200" y1="80" x2="200" y2="88" stroke-dasharray="3,2"/>
        <line x1="400" y1="80" x2="400" y2="88" stroke-dasharray="3,2"/>
        <line x1="600" y1="80" x2="600" y2="88" stroke-dasharray="3,2"/>
        <line x1="200" y1="142" x2="200" y2="150" stroke-dasharray="3,2"/>
        <line x1="400" y1="142" x2="400" y2="150" stroke-dasharray="3,2"/>
        <line x1="200" y1="204" x2="200" y2="212" stroke-dasharray="3,2"/>
        <line x1="400" y1="204" x2="400" y2="212" stroke-dasharray="3,2"/>
      </g>
    </svg>
  </div>

  <!-- Sub cards -->
  <div class="spec-sub stagger reveal" style="transition-delay:.1s">
    <div class="spec-sub-card">
      <div class="spec-tag">Specialisation</div>
      <div class="spec-icon" style="margin-bottom:14px"><svg viewBox="0 0 24 24"><path d="M12 2a2 2 0 012 2v4a2 2 0 01-2 2H8a2 2 0 01-2-2V4a2 2 0 012-2h4z"/><path d="M16 14a2 2 0 012 2v4a2 2 0 01-2 2h-8a2 2 0 01-2-2v-4a2 2 0 012-2h8z"/><path d="M12 8v6"/></svg></div>
      <div class="spec-h" style="font-size:1.15rem">Generative AI on NVIDIA Stack</div>
      <div class="spec-body">End-to-end deployment of Generative AI workloads using NVIDIA NIM microservices, NeMo, and cuDNN — from foundation model fine-tuning through to production serving inside an AI Factory.</div>
      <div class="spec-chips">
        <span class="chip">NVIDIA NIM</span><span class="chip">NeMo</span><span class="chip">cuDNN</span><span class="chip">Fine-tuning</span>
      </div>
    </div>
    <div class="spec-sub-card">
      <div class="spec-tag">Specialisation</div>
      <div class="spec-icon" style="margin-bottom:14px"><svg viewBox="0 0 24 24"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg></div>
      <div class="spec-h" style="font-size:1.15rem">Deep Learning &amp; CUDA Engineering</div>
      <div class="spec-body">Proficient in GPU-native Python and CUDA programming for high-performance deep learning model development, custom kernel optimisation, and accelerated data pipelines on NVIDIA hardware.</div>
      <div class="spec-chips">
        <span class="chip">CUDA</span><span class="chip">Python</span><span class="chip">PyTorch</span><span class="chip">cuBLAS / cuDNN</span>
      </div>
    </div>
    <div class="spec-sub-card">
      <div class="spec-tag">Specialisation</div>
      <div class="spec-icon" style="margin-bottom:14px"><svg viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/></svg></div>
      <div class="spec-h" style="font-size:1.15rem">AI Factory Architecture &amp; DGX Infrastructure</div>
      <div class="spec-body">Designs the full compute, storage, and networking blueprint of large-scale AI Factories — integrating DGX systems, high-speed fabrics, and software orchestration layers into a unified, scalable platform.</div>
      <div class="spec-chips">
        <span class="chip">DGX Systems</span><span class="chip">AI Factory Blueprint</span><span class="chip">Kubernetes / Slurm</span>
      </div>
    </div>
  </div>
</div>
</section>

<!-- ══════════════════════════════════════════
     SKILLS
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
      <div class="sg-label">Core AI · Deep Learning · Generative AI</div>
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
      <div class="sg-label">AI Factory · Compute Infrastructure</div>
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
      <div class="sg-label" style="color:var(--dim)">Supporting Infrastructure</div>
      <div class="skill-row">
        <div class="skill-top"><span class="skill-name" style="color:var(--muted)">High-Speed Networking (InfiniBand / Ethernet)</span><span class="skill-pct" style="color:var(--dim)">72%</span></div>
        <div class="bar-track"><div class="bar-fill dim" data-w="72"></div></div>
      </div>
      <div class="tech-stack">
        <div class="stack-title">Key Technologies</div>
        <div class="stack-pills">
          <div class="stack-pill"><span class="dot dot-g"></span>CUDA / C++</div>
          <div class="stack-pill"><span class="dot dot-g"></span>TensorRT-LLM</div>
          <div class="stack-pill"><span class="dot dot-g"></span>NVIDIA NIM</div>
          <div class="stack-pill"><span class="dot dot-g"></span>NeMo Framework</div>
          <div class="stack-pill"><span class="dot dot-g"></span>Triton Server</div>
          <div class="stack-pill"><span class="dot dot-g"></span>PyTorch</div>
          <div class="stack-pill"><span class="dot dot-g"></span>Python</div>
          <div class="stack-pill"><span class="dot dot-g"></span>DGX H100/H200</div>
          <div class="stack-pill"><span class="dot dot-d"></span>InfiniBand</div>
          <div class="stack-pill"><span class="dot dot-d"></span>Kubernetes</div>
          <div class="stack-pill"><span class="dot dot-d"></span>Slurm</div>
        </div>
      </div>

    <!-- LLM Training & Inference Pipeline Diagram -->
    <div class="aif-diagram-wrap reveal" style="margin-top:28px;transition-delay:.15s">
      <div class="aif-diagram-label">Distributed LLM Training & Inference Pipeline</div>
      <svg viewBox="0 0 900 160" fill="none" xmlns="http://www.w3.org/2000/svg" style="width:100%;height:auto;display:block">
        <rect width="900" height="160" fill="rgba(8,17,26,.8)" rx="0"/>

        <!-- Stage boxes -->
        <!-- 1: Raw Data -->
        <rect x="18" y="40" width="118" height="80" rx="4" fill="rgba(118,185,0,0.07)" stroke="rgba(118,185,0,0.3)" stroke-width="1"/>
        <text x="77" y="72" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="12" font-weight="800" text-anchor="middle" letter-spacing=".5">DATA</text>
        <text x="77" y="86" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Tokenise</text>
        <text x="77" y="97" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Preprocess</text>
        <text x="77" y="108" fill="rgba(118,185,0,0.45)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">NEMO DataLoader</text>
        <!-- flow dot 1 -->
        <circle cx="160" cy="80" r="4" fill="#76b900" opacity="0.9">
          <animate attributeName="cx" values="148;164;148" dur="2.4s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="0;1;0" dur="2.4s" repeatCount="indefinite"/>
        </circle>
        <line x1="136" y1="80" x2="162" y2="80" stroke="rgba(118,185,0,0.35)" stroke-width="1.2" stroke-dasharray="4,3"/>

        <!-- 2: Distributed Training -->
        <rect x="166" y="40" width="142" height="80" rx="4" fill="rgba(118,185,0,0.1)" stroke="rgba(118,185,0,0.45)" stroke-width="1.5"/>
        <text x="237" y="68" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="12" font-weight="800" text-anchor="middle" letter-spacing=".5">DIST. TRAIN</text>
        <text x="237" y="82" fill="rgba(118,185,0,0.65)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">NeMo + NCCL</text>
        <text x="237" y="93" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Tensor / Pipeline</text>
        <text x="237" y="104" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Parallelism</text>
        <text x="237" y="115" fill="rgba(118,185,0,0.4)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">DGX H100/H200</text>

        <circle cx="322" cy="80" r="4" fill="#76b900" opacity="0.9">
          <animate attributeName="cx" values="310;326;310" dur="2.4s" begin="0.5s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="0;1;0" dur="2.4s" begin="0.5s" repeatCount="indefinite"/>
        </circle>
        <line x1="308" y1="80" x2="330" y2="80" stroke="rgba(118,185,0,0.35)" stroke-width="1.2" stroke-dasharray="4,3"/>

        <!-- 3: Fine-Tune -->
        <rect x="334" y="40" width="118" height="80" rx="4" fill="rgba(118,185,0,0.07)" stroke="rgba(118,185,0,0.3)" stroke-width="1"/>
        <text x="393" y="72" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="12" font-weight="800" text-anchor="middle" letter-spacing=".5">FINE-TUNE</text>
        <text x="393" y="86" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">LoRA · PEFT</text>
        <text x="393" y="97" fill="rgba(118,185,0,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">SFT · RLHF</text>
        <text x="393" y="108" fill="rgba(118,185,0,0.45)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">NeMo Customise</text>

        <circle cx="466" cy="80" r="4" fill="#00c4dc" opacity="0.9">
          <animate attributeName="cx" values="454;470;454" dur="2.4s" begin="1s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="0;1;0" dur="2.4s" begin="1s" repeatCount="indefinite"/>
        </circle>
        <line x1="452" y1="80" x2="474" y2="80" stroke="rgba(0,196,220,0.35)" stroke-width="1.2" stroke-dasharray="4,3"/>

        <!-- 4: TRT-LLM Optimise -->
        <rect x="478" y="40" width="142" height="80" rx="4" fill="rgba(0,180,200,0.07)" stroke="rgba(0,180,200,0.35)" stroke-width="1.2"/>
        <text x="549" y="68" fill="#00c4dc" font-family="Barlow Condensed,sans-serif" font-size="12" font-weight="800" text-anchor="middle" letter-spacing=".5">TENSORRT-LLM</text>
        <text x="549" y="82" fill="rgba(0,196,220,0.6)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">INT4/FP8 Quant</text>
        <text x="549" y="93" fill="rgba(0,196,220,0.6)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Kernel Fusion</text>
        <text x="549" y="104" fill="rgba(0,196,220,0.6)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">In-flight Batching</text>
        <text x="549" y="115" fill="rgba(0,196,220,0.4)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">Max Throughput</text>

        <circle cx="634" cy="80" r="4" fill="#00c4dc" opacity="0.9">
          <animate attributeName="cx" values="622;638;622" dur="2.4s" begin="1.5s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="0;1;0" dur="2.4s" begin="1.5s" repeatCount="indefinite"/>
        </circle>
        <line x1="620" y1="80" x2="642" y2="80" stroke="rgba(0,196,220,0.35)" stroke-width="1.2" stroke-dasharray="4,3"/>

        <!-- 5: Triton Serve -->
        <rect x="646" y="40" width="118" height="80" rx="4" fill="rgba(0,180,200,0.05)" stroke="rgba(0,180,200,0.25)" stroke-width="1"/>
        <text x="705" y="72" fill="#00c4dc" font-family="Barlow Condensed,sans-serif" font-size="12" font-weight="800" text-anchor="middle" letter-spacing=".5">TRITON</text>
        <text x="705" y="86" fill="rgba(0,196,220,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Model Serving</text>
        <text x="705" y="97" fill="rgba(0,196,220,0.55)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Dyn Batching</text>
        <text x="705" y="108" fill="rgba(0,196,220,0.45)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">gRPC · REST · KV</text>

        <circle cx="778" cy="80" r="4" fill="#76b900" opacity="0.9">
          <animate attributeName="cx" values="766;782;766" dur="2.4s" begin="2s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="0;1;0" dur="2.4s" begin="2s" repeatCount="indefinite"/>
        </circle>
        <line x1="764" y1="80" x2="786" y2="80" stroke="rgba(118,185,0,0.35)" stroke-width="1.2" stroke-dasharray="4,3"/>

        <!-- 6: Production API -->
        <rect x="790" y="40" width="94" height="80" rx="4" fill="rgba(118,185,0,0.12)" stroke="rgba(118,185,0,0.5)" stroke-width="1.5"/>
        <text x="837" y="70" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="12" font-weight="800" text-anchor="middle" letter-spacing=".5">PROD</text>
        <text x="837" y="83" fill="rgba(118,185,0,0.7)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">NIM APIs</text>
        <text x="837" y="94" fill="rgba(118,185,0,0.7)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">Enterprise</text>
        <text x="837" y="105" fill="rgba(118,185,0,0.6)" font-family="DM Mono,monospace" font-size="8" text-anchor="middle">SLA · Scale</text>

        <!-- Stage labels at bottom -->
        <text x="77"  y="148" fill="rgba(118,185,0,0.3)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">01</text>
        <text x="237" y="148" fill="rgba(118,185,0,0.4)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">02</text>
        <text x="393" y="148" fill="rgba(118,185,0,0.3)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">03</text>
        <text x="549" y="148" fill="rgba(0,196,220,0.35)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">04</text>
        <text x="705" y="148" fill="rgba(0,196,220,0.3)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">05</text>
        <text x="837" y="148" fill="rgba(118,185,0,0.4)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">06</text>
      </svg>
    </div>
    </div>
    <div class="domain-matrix reveal" style="transition-delay:.12s">
      <div class="dm-cell hi"><span class="dm-icon">🧠</span><div class="dm-name">Deep Learning</div></div>
      <div class="dm-cell hi"><span class="dm-icon">⚡</span><div class="dm-name">CUDA / GPU</div></div>
      <div class="dm-cell hi"><span class="dm-icon">🤖</span><div class="dm-name">Generative AI</div></div>
      <div class="dm-cell hi"><span class="dm-icon">🔀</span><div class="dm-name">Dist. Training</div></div>
      <div class="dm-cell hi"><span class="dm-icon">🚀</span><div class="dm-name">LLM Inference</div></div>
      <div class="dm-cell hi"><span class="dm-icon">🏭</span><div class="dm-name">AI Factory</div></div>
      <div class="dm-cell"><span class="dm-icon">📦</span><div class="dm-name">DGX Systems</div></div>
      <div class="dm-cell"><span class="dm-icon">🔬</span><div class="dm-name">Fine-tuning</div></div>
      <div class="dm-cell"><span class="dm-icon">🦾</span><div class="dm-name">Agentic AI</div></div>
      <div class="dm-cell"><span class="dm-icon">🎯</span><div class="dm-name">Solution Design</div></div>
      <div class="dm-cell"><span class="dm-icon">🔭</span><div class="dm-name">Omniverse</div></div>
      <div class="dm-cell" style="opacity:.35"><span class="dm-icon">🌐</span><div class="dm-name">Networking</div></div>
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
      <div class="tl-desc">Leads end-to-end design and deployment of large-scale AI Factory solutions, with a primary focus on Generative AI workloads, distributed LLM training pipelines, and high-performance inference infrastructure built on NVIDIA's DGX systems and software stack. Manages pre-sales technical engagements, proof-of-concept implementations, and architecture reviews for enterprise customers. Operates in close collaboration with NVIDIA's Partner Network, providing direct access to NVIDIA engineering tools, product roadmaps, and support channels essential for complex AI Factory builds.</div>
      <div class="tl-chips">
        <span class="tl-chip">NVIDIA DGX</span><span class="tl-chip">Distributed Training</span><span class="tl-chip">LLM Inference</span><span class="tl-chip">NIM / NeMo</span><span class="tl-chip">CUDA / Python</span><span class="tl-chip">AI Factory Architecture</span><span class="tl-chip">Pre-Sales Engineering</span>
      </div>
    </div>
    <div class="tl-item">
      <div class="tl-dot"></div>
      <div class="tl-period">Prior Roles</div>
      <div class="tl-title">Technical &amp; Solutions Roles</div>
      <div class="tl-co">LG Electronics · Viga Entertainment Technology · Eigenlytics Data Solutions · MedTourEasy</div>
      <div class="tl-desc">Cross-industry background spanning consumer electronics, entertainment platforms, data analytics, and healthtech — building a versatile foundation in systems integration, data pipelines, and solution architecture. This breadth provides the real-world business context necessary for designing AI infrastructure that addresses genuine enterprise challenges.</div>
      <div class="tl-chips">
        <span class="tl-chip">Data Analytics</span><span class="tl-chip">Systems Integration</span><span class="tl-chip">Enterprise Technology</span>
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
  <!-- GPU Cluster Visual Accent -->
  <div class="gpu-cluster-row reveal" style="margin-bottom:32px">
    <svg viewBox="0 0 1160 90" fill="none" xmlns="http://www.w3.org/2000/svg" style="width:100%;height:auto;display:block">
      <rect width="1160" height="90" fill="rgba(8,17,26,.6)" rx="4"/>
      <rect width="1160" height="90" fill="none" stroke="rgba(118,185,0,.15)" stroke-width="1" rx="4"/>
      <!-- Row of 8 GPU chips representing DGX node -->
      <text x="18" y="20" fill="rgba(118,185,0,.4)" font-family="DM Mono,monospace" font-size="8" letter-spacing="2">DGX NODE — 8× H200 TENSOR CORE GPUs — 1.13 EXAFLOPS AI PERFORMANCE</text>
      <!-- GPU chips -->
      <g transform="translate(18,26)">
        <!-- 8 GPU chips with labels -->
        <!-- GPU 0 -->
        <rect x="0"   y="0" width="120" height="50" rx="3" fill="rgba(118,185,0,.12)" stroke="rgba(118,185,0,.5)" stroke-width="1.2"/>
        <text x="60"  y="17" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="900" text-anchor="middle">H200 · GPU 0</text>
        <text x="60"  y="29" fill="rgba(118,185,0,.6)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">141GB HBM3e</text>
        <text x="60"  y="40" fill="rgba(118,185,0,.5)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">3.35TB/s BW</text>
        <!-- GPU 1 -->
        <rect x="131" y="0" width="120" height="50" rx="3" fill="rgba(118,185,0,.09)" stroke="rgba(118,185,0,.4)" stroke-width="1"/>
        <text x="191" y="17" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="900" text-anchor="middle">H200 · GPU 1</text>
        <text x="191" y="29" fill="rgba(118,185,0,.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">141GB HBM3e</text>
        <text x="191" y="40" fill="rgba(118,185,0,.45)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">3.35TB/s BW</text>
        <!-- GPU 2 -->
        <rect x="262" y="0" width="120" height="50" rx="3" fill="rgba(118,185,0,.09)" stroke="rgba(118,185,0,.35)" stroke-width="1"/>
        <text x="322" y="17" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="900" text-anchor="middle">H200 · GPU 2</text>
        <text x="322" y="29" fill="rgba(118,185,0,.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">141GB HBM3e</text>
        <text x="322" y="40" fill="rgba(118,185,0,.45)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">3.35TB/s BW</text>
        <!-- GPU 3 -->
        <rect x="393" y="0" width="120" height="50" rx="3" fill="rgba(118,185,0,.09)" stroke="rgba(118,185,0,.35)" stroke-width="1"/>
        <text x="453" y="17" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="900" text-anchor="middle">H200 · GPU 3</text>
        <text x="453" y="29" fill="rgba(118,185,0,.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">141GB HBM3e</text>
        <text x="453" y="40" fill="rgba(118,185,0,.45)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">3.35TB/s BW</text>
        <!-- NVSwitch center label -->
        <rect x="524" y="10" width="90" height="30" rx="3" fill="rgba(0,180,200,.08)" stroke="rgba(0,180,200,.3)" stroke-width="1"/>
        <text x="569" y="21" fill="#00c4dc" font-family="Barlow Condensed,sans-serif" font-size="9" font-weight="700" text-anchor="middle">NVSwitch</text>
        <text x="569" y="33" fill="rgba(0,196,220,.5)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">900GB/s</text>
        <!-- GPU 4 -->
        <rect x="624" y="0" width="120" height="50" rx="3" fill="rgba(118,185,0,.09)" stroke="rgba(118,185,0,.35)" stroke-width="1"/>
        <text x="684" y="17" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="900" text-anchor="middle">H200 · GPU 4</text>
        <text x="684" y="29" fill="rgba(118,185,0,.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">141GB HBM3e</text>
        <text x="684" y="40" fill="rgba(118,185,0,.45)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">3.35TB/s BW</text>
        <!-- GPU 5 -->
        <rect x="755" y="0" width="120" height="50" rx="3" fill="rgba(118,185,0,.09)" stroke="rgba(118,185,0,.35)" stroke-width="1"/>
        <text x="815" y="17" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="900" text-anchor="middle">H200 · GPU 5</text>
        <text x="815" y="29" fill="rgba(118,185,0,.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">141GB HBM3e</text>
        <text x="815" y="40" fill="rgba(118,185,0,.45)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">3.35TB/s BW</text>
        <!-- GPU 6 -->
        <rect x="886" y="0" width="120" height="50" rx="3" fill="rgba(118,185,0,.09)" stroke="rgba(118,185,0,.35)" stroke-width="1"/>
        <text x="946" y="17" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="900" text-anchor="middle">H200 · GPU 6</text>
        <text x="946" y="29" fill="rgba(118,185,0,.55)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">141GB HBM3e</text>
        <text x="946" y="40" fill="rgba(118,185,0,.45)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">3.35TB/s BW</text>
        <!-- GPU 7 -->
        <rect x="1017" y="0" width="120" height="50" rx="3" fill="rgba(118,185,0,.12)" stroke="rgba(118,185,0,.5)" stroke-width="1.2"/>
        <text x="1077" y="17" fill="#76b900" font-family="Barlow Condensed,sans-serif" font-size="11" font-weight="900" text-anchor="middle">H200 · GPU 7</text>
        <text x="1077" y="29" fill="rgba(118,185,0,.6)" font-family="DM Mono,monospace" font-size="7.5" text-anchor="middle">141GB HBM3e</text>
        <text x="1077" y="40" fill="rgba(118,185,0,.5)" font-family="DM Mono,monospace" font-size="7" text-anchor="middle">3.35TB/s BW</text>
        <!-- NVLink connections (simplified lines) -->
        <line x1="120" y1="25" x2="131" y2="25" stroke="rgba(118,185,0,.4)" stroke-width="1.5"/>
        <line x1="251" y1="25" x2="262" y2="25" stroke="rgba(118,185,0,.35)" stroke-width="1.5"/>
        <line x1="382" y1="25" x2="393" y2="25" stroke="rgba(118,185,0,.35)" stroke-width="1.5"/>
        <line x1="513" y1="25" x2="524" y2="25" stroke="rgba(0,196,220,.4)" stroke-width="1.5"/>
        <line x1="614" y1="25" x2="624" y2="25" stroke="rgba(0,196,220,.4)" stroke-width="1.5"/>
        <line x1="744" y1="25" x2="755" y2="25" stroke="rgba(118,185,0,.35)" stroke-width="1.5"/>
        <line x1="875" y1="25" x2="886" y2="25" stroke="rgba(118,185,0,.35)" stroke-width="1.5"/>
        <line x1="1006" y1="25" x2="1017" y2="25" stroke="rgba(118,185,0,.4)" stroke-width="1.5"/>
      </g>
    </svg>
  </div>
  <div class="value-grid stagger reveal">
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
    <img class="footer-logo" src="data:image/png;base64,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" alt="NVIDIA Elite Partner · Micropoint Computers"/>
    <div class="footer-text">
      NVIDIA certifications verified · Darrin Chen, VP – NVIDIA Partner Network<br>
      Micropoint Computers Pvt. Ltd. · Bengaluru, India
    </div>
  </div>
  <div class="footer-badge">Confidential — AI Factory Engagement Profile</div>
</footer>


<script>
/* ════════════════════════════════════════════════════
   NEURAL NETWORK + CIRCUIT HYBRID BACKGROUND
════════════════════════════════════════════════════ */
(function(){
  const canvas = document.getElementById('bg-canvas');
  const ctx = canvas.getContext('2d');
  let W, H, nodes=[], packets=[];
  const G='118,185,0', C='0,229,255';

  function resize(){
    W = canvas.width  = window.innerWidth;
    H = canvas.height = window.innerHeight;
    init();
  }

  function init(){
    nodes=[]; packets=[];
    const count = window.innerWidth < 600 ? 45 : 80;
    for(let i=0;i<count;i++){
      nodes.push({
        x:Math.random()*W, y:Math.random()*H,
        vx:(Math.random()-.5)*.28, vy:(Math.random()-.5)*.28,
        r:1.4+Math.random()*2.2,
        pulse:Math.random()*Math.PI*2,
        speed:.014+Math.random()*.012,
        core: i < Math.floor(count*.12) // 12% are "core" GPU nodes
      });
    }
    for(let i=0;i<18;i++) spawnPacket();
  }

  function spawnPacket(){
    const a=nodes[Math.floor(Math.random()*nodes.length)];
    const b=nodes[Math.floor(Math.random()*nodes.length)];
    if(a===b) return;
    packets.push({
      from:a, to:b, t:Math.random(),
      speed:.004+Math.random()*.004,
      isCyan:Math.random()<.15, size:1.8+Math.random()*1.5
    });
  }

  function draw(){
    ctx.clearRect(0,0,W,H);

    // Update node positions
    nodes.forEach(n=>{
      n.x+=n.vx; n.y+=n.vy; n.pulse+=n.speed;
      if(n.x<0||n.x>W) n.vx*=-1;
      if(n.y<0||n.y>H) n.vy*=-1;
    });

    // Draw proximity edges (neural network style)
    const maxDist = 150;
    for(let i=0;i<nodes.length;i++){
      for(let j=i+1;j<nodes.length;j++){
        const dx=nodes[i].x-nodes[j].x, dy=nodes[i].y-nodes[j].y;
        const d=Math.sqrt(dx*dx+dy*dy);
        if(d<maxDist){
          const a=(1-d/maxDist)*.18;
          // Slightly cyan for long connections, green for short
          const col = d>100 ? C : G;
          ctx.strokeStyle=`rgba(${col},${a})`;
          ctx.lineWidth=.65;
          ctx.beginPath(); ctx.moveTo(nodes[i].x,nodes[i].y); ctx.lineTo(nodes[j].x,nodes[j].y); ctx.stroke();
        }
      }
    }

    // Draw nodes
    nodes.forEach(n=>{
      const p=.5+.5*Math.sin(n.pulse);
      if(n.core){
        // Core GPU chip — small glowing square with crosshair
        const s=5+p*2.5;
        ctx.fillStyle=`rgba(${G},${.1+p*.08})`;
        ctx.strokeStyle=`rgba(${G},${.35+p*.25})`;
        ctx.lineWidth=.8;
        ctx.fillRect(n.x-s/2,n.y-s/2,s,s);
        ctx.strokeRect(n.x-s/2,n.y-s/2,s,s);
        // crosshair
        ctx.strokeStyle=`rgba(${G},${.12+p*.08})`;
        ctx.lineWidth=.5;
        ctx.beginPath();ctx.moveTo(n.x-s*1.6,n.y);ctx.lineTo(n.x+s*1.6,n.y);ctx.stroke();
        ctx.beginPath();ctx.moveTo(n.x,n.y-s*1.6);ctx.lineTo(n.x,n.y+s*1.6);ctx.stroke();
        // outer glow
        const grd=ctx.createRadialGradient(n.x,n.y,0,n.x,n.y,s*4);
        grd.addColorStop(0,`rgba(${G},${.12*p})`); grd.addColorStop(1,'transparent');
        ctx.beginPath();ctx.arc(n.x,n.y,s*4,0,Math.PI*2);ctx.fillStyle=grd;ctx.fill();
      } else {
        // Regular neuron node
        ctx.beginPath();
        ctx.arc(n.x,n.y,n.r*(1+p*.4),0,Math.PI*2);
        ctx.fillStyle=`rgba(${G},${.3+p*.3})`;
        ctx.fill();
        // soft glow halo
        const g=ctx.createRadialGradient(n.x,n.y,0,n.x,n.y,n.r*5);
        g.addColorStop(0,`rgba(${G},${.1*p})`); g.addColorStop(1,'transparent');
        ctx.beginPath();ctx.arc(n.x,n.y,n.r*5,0,Math.PI*2);
        ctx.fillStyle=g;ctx.fill();
      }
    });

    // Draw data packets
    for(let i=packets.length-1;i>=0;i--){
      const pk=packets[i];
      pk.t+=pk.speed;
      if(pk.t>=1){ packets.splice(i,1); if(packets.length<24) spawnPacket(); continue; }
      const x=pk.from.x+(pk.to.x-pk.from.x)*pk.t;
      const y=pk.from.y+(pk.to.y-pk.from.y)*pk.t;
      const col=pk.isCyan?C:G;
      // glow
      const gp=ctx.createRadialGradient(x,y,0,x,y,pk.size*4);
      gp.addColorStop(0,`rgba(${col},.6)`); gp.addColorStop(1,'transparent');
      ctx.beginPath();ctx.arc(x,y,pk.size*4,0,Math.PI*2);ctx.fillStyle=gp;ctx.fill();
      // core
      ctx.beginPath();ctx.arc(x,y,pk.size,0,Math.PI*2);
      ctx.fillStyle=`rgba(${col},.95)`;ctx.fill();
    }

    requestAnimationFrame(draw);
  }

  window.addEventListener('resize',()=>{clearTimeout(window._rsznn);window._rsznn=setTimeout(resize,150);});
  resize();
  draw();
})();

/* ════════════════════════════════════════════════════
   HAMBURGER
════════════════════════════════════════════════════ */
const ham = document.getElementById('hamburger');
const mMenu = document.getElementById('mobile-menu');
ham.addEventListener('click', () => {
  const open = mMenu.classList.toggle('open');
  ham.classList.toggle('open', open);
  ham.setAttribute('aria-expanded', open);
  document.body.style.overflow = open ? 'hidden' : '';
});
mMenu.querySelectorAll('.nav-link').forEach(l => l.addEventListener('click', () => {
  mMenu.classList.remove('open');
  ham.classList.remove('open');
  document.body.style.overflow = '';
}));

/* ════════════════════════════════════════════════════
   SCROLL REVEAL
════════════════════════════════════════════════════ */
const revObs = new IntersectionObserver(es => {
  es.forEach(e => { if(e.isIntersecting) e.target.classList.add('vis'); });
}, { threshold: 0.06 });
document.querySelectorAll('.reveal, .stagger').forEach(el => revObs.observe(el));

/* ════════════════════════════════════════════════════
   COUNTERS
════════════════════════════════════════════════════ */
const cntObs = new IntersectionObserver(es => {
  es.forEach(e => {
    if(e.isIntersecting){
      const v = parseInt(e.target.dataset.count);
      if(!isNaN(v)){
        const start = performance.now();
        const dur = 1900;
        (function step(t){
          const p = Math.min((t-start)/dur,1);
          e.target.textContent = Math.round((1-Math.pow(1-p,4))*v);
          if(p<1) requestAnimationFrame(step);
        })(start);
      }
      cntObs.unobserve(e.target);
    }
  });
}, { threshold: .5 });
document.querySelectorAll('[data-count]').forEach(el => cntObs.observe(el));

/* ════════════════════════════════════════════════════
   STAT BARS
════════════════════════════════════════════════════ */
const sbObs = new IntersectionObserver(es => {
  es.forEach(e => {
    if(e.isIntersecting){
      e.target.querySelectorAll('.stat-bar-fill').forEach(b => b.style.width = b.dataset.w + '%');
      sbObs.unobserve(e.target);
    }
  });
}, { threshold: .3 });
document.querySelectorAll('.stat-card').forEach(el => sbObs.observe(el));

/* ════════════════════════════════════════════════════
   SKILL BARS
════════════════════════════════════════════════════ */
const bObs = new IntersectionObserver(es => {
  es.forEach(e => {
    if(e.isIntersecting){
      e.target.querySelectorAll('.bar-fill').forEach(b => b.style.width = b.dataset.w + '%');
      bObs.unobserve(e.target);
    }
  });
}, { threshold: .08 });
document.querySelectorAll('.skills-wrap').forEach(el => bObs.observe(el));

/* ════════════════════════════════════════════════════
   NAV ACTIVE STATE
════════════════════════════════════════════════════ */
const nav = document.getElementById('nav');
const navLinks = document.querySelectorAll('#nav .nav-link');
const sections = document.querySelectorAll('section[id]');
function updateNav(){
  const st = window.scrollY;
  nav.classList.toggle('scrolled', st > 50);
  let cur = '';
  sections.forEach(s => { if(st >= s.offsetTop - 110) cur = s.id; });
  navLinks.forEach(l => l.classList.toggle('active', l.getAttribute('href') === '#'+cur));
}
window.addEventListener('scroll', updateNav, { passive: true });
updateNav();
</script>
</body>
</html>
