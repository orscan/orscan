<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ORSCAN — README</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,300;0,400;0,600;0,700;1,400&family=Bebas+Neue&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap" rel="stylesheet">
<style>
/* ─── RESET ─────────────────────────────────────── */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;font-size:16px}
body{
  background:#0d0d0d;
  color:#e8e7e2;
  font-family:'JetBrains Mono',monospace;
  font-size:14px;
  line-height:1.7;
  cursor:default;
  overflow-x:hidden;
}
::selection{background:#e8e7e2;color:#0d0d0d}
::-webkit-scrollbar{width:4px}
::-webkit-scrollbar-track{background:#0d0d0d}
::-webkit-scrollbar-thumb{background:#333}
a{color:#e8e7e2;text-decoration:none}
a:hover{text-decoration:underline;text-underline-offset:3px}

/* ─── VARIABLES ──────────────────────────────────── */
:root{
  --bg:#0d0d0d;
  --bg2:#111;
  --bg3:#161616;
  --wht:#e8e7e2;
  --gry:#666;
  --mgry:#999;
  --border:1px solid #222;
  --border2:1px solid #2a2a2a;
  --accent:#e8e7e2;
}

/* ─── NOISE TEXTURE ──────────────────────────────── */
body::before{
  content:'';
  position:fixed;inset:0;z-index:0;pointer-events:none;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
  opacity:.4;
}

/* ─── LAYOUT ─────────────────────────────────────── */
.page{position:relative;z-index:1;max-width:980px;margin:0 auto;padding:0 24px}

/* ─── TOP BAR ────────────────────────────────────── */
.topbar{
  position:sticky;top:0;z-index:100;
  background:rgba(13,13,13,.96);
  backdrop-filter:blur(8px);
  border-bottom:var(--border);
  padding:0 24px;
  display:flex;align-items:center;justify-content:space-between;
  height:48px;
  font-size:11px;letter-spacing:2px;
  color:var(--gry);
  text-transform:uppercase;
}
.topbar-logo{
  display:flex;align-items:center;gap:10px;
  color:var(--wht);font-weight:600;letter-spacing:4px;
}
.topbar-logo svg{width:20px;height:20px}
.topbar-nav{display:flex;gap:0}
.topbar-nav a{
  color:var(--gry);padding:0 14px;height:48px;
  display:flex;align-items:center;
  border-left:var(--border);
  transition:color .15s;
  font-size:10px;letter-spacing:2px;
}
.topbar-nav a:hover{color:var(--wht);text-decoration:none}

/* ─── HERO ───────────────────────────────────────── */
.hero{
  padding:80px 0 60px;
  border-bottom:var(--border);
}
.hero-badge{
  display:inline-flex;align-items:center;gap:8px;
  font-size:10px;letter-spacing:3px;text-transform:uppercase;
  color:var(--gry);border:var(--border);
  padding:5px 14px;margin-bottom:32px;
}
.hero-badge .dot{width:6px;height:6px;border-radius:50%;background:var(--wht);animation:blink 1.4s step-end infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
.hero-title{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(64px,9vw,108px);
  line-height:.9;letter-spacing:-1px;
  margin-bottom:6px;
}
.hero-title .out{-webkit-text-stroke:1.5px #e8e7e2;color:transparent}
.hero-sub{
  font-size:13px;color:var(--mgry);
  letter-spacing:3px;text-transform:uppercase;
  margin-bottom:36px;
  display:flex;align-items:center;gap:16px;
}
.hero-sub::before{content:'//';color:var(--gry)}
.hero-desc{
  font-family:'DM Sans',sans-serif;
  font-size:17px;color:#aaa;line-height:1.7;
  max-width:680px;margin-bottom:40px;
  font-weight:300;
}
.hero-desc strong{color:var(--wht);font-weight:500}

.badges-row{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:40px}
.badge{
  font-size:10px;letter-spacing:2px;text-transform:uppercase;
  padding:5px 12px;border:var(--border);color:var(--gry);
  transition:all .15s;
}
.badge:hover{border-color:var(--wht);color:var(--wht);text-decoration:none}
.badge-fill{background:var(--wht);color:#0d0d0d;border-color:var(--wht)}
.badge-fill:hover{background:#ccc;color:#0d0d0d}

.install-block{
  background:var(--bg2);border:var(--border);
  padding:18px 22px;
  display:flex;align-items:center;justify-content:space-between;
  gap:16px;max-width:600px;
}
.install-cmd{font-size:13px;color:#aaa;letter-spacing:1px}
.install-cmd span{color:var(--wht)}
.copy-btn{
  font-size:10px;letter-spacing:2px;text-transform:uppercase;
  color:var(--gry);background:none;border:var(--border);
  padding:5px 12px;cursor:pointer;transition:all .15s;
  white-space:nowrap;
}
.copy-btn:hover{color:var(--wht);border-color:var(--wht)}

/* ─── TOC ────────────────────────────────────────── */
.toc{
  border:var(--border);background:var(--bg2);
  margin:48px 0;
}
.toc-header{
  padding:14px 20px;border-bottom:var(--border);
  display:flex;align-items:center;gap:10px;
  font-size:10px;letter-spacing:3px;text-transform:uppercase;color:var(--gry);
}
.toc-header::before{content:'📋';font-size:13px}
.toc-grid{
  display:grid;grid-template-columns:repeat(3,1fr);
  gap:0;
}
.toc-item{
  padding:14px 20px;border-right:var(--border);border-bottom:var(--border);
  display:flex;align-items:center;gap:10px;
  transition:background .15s;
}
.toc-item:hover{background:var(--bg3);text-decoration:none}
.toc-item:nth-child(3n){border-right:none}
.toc-num{color:var(--gry);font-size:11px;min-width:22px}
.toc-label{font-size:12px;color:#bbb;letter-spacing:.5px}
.toc-item:hover .toc-label{color:var(--wht)}

/* ─── SECTION ────────────────────────────────────── */
.section{padding:60px 0;border-bottom:var(--border)}
.section:last-child{border-bottom:none}

.sec-kicker{
  font-size:10px;letter-spacing:4px;text-transform:uppercase;
  color:var(--gry);margin-bottom:8px;
  display:flex;align-items:center;gap:10px;
}
.sec-kicker::before{content:'';width:20px;height:1px;background:var(--gry)}

h2{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(32px,4vw,52px);
  line-height:.95;letter-spacing:-0.5px;
  margin-bottom:32px;
}
h2 .out{-webkit-text-stroke:1px #e8e7e2;color:transparent}

h3{
  font-family:'Bebas Neue',sans-serif;
  font-size:24px;letter-spacing:1px;
  margin-bottom:16px;margin-top:32px;
  color:var(--wht);
}
h3:first-child{margin-top:0}

h4{
  font-size:11px;letter-spacing:3px;text-transform:uppercase;
  color:var(--mgry);margin-bottom:12px;margin-top:24px;
}

p{font-family:'DM Sans',sans-serif;font-size:15px;color:#aaa;line-height:1.75;margin-bottom:16px}
p strong{color:var(--wht)}
p:last-child{margin-bottom:0}

/* ─── CODE BLOCKS ────────────────────────────────── */
pre{
  background:var(--bg2);border:var(--border);
  padding:20px 22px;margin:20px 0;
  overflow-x:auto;position:relative;
  border-left:3px solid #333;
}
pre::-webkit-scrollbar{height:3px}
pre::-webkit-scrollbar-thumb{background:#333}
code{
  font-family:'JetBrains Mono',monospace;
  font-size:12.5px;color:#ccc;line-height:1.7;
}
pre code{color:#ccc}
:not(pre)>code{
  background:#1a1a1a;border:var(--border);
  padding:2px 7px;font-size:12px;color:#e0dfda;
}
.code-lang{
  position:absolute;top:10px;right:14px;
  font-size:9px;letter-spacing:2px;text-transform:uppercase;color:#444;
}
/* syntax highlight colors */
.kw{color:#e8e7e2;font-weight:600}  /* keyword */
.st{color:#aaa}                      /* string */
.cm{color:#444;font-style:italic}    /* comment */
.nm{color:#ccc}                      /* number */
.fn{color:#ddd}                      /* function */
.vr{color:#bbb}                      /* variable */
.op{color:#888}                      /* operator */

/* ─── FEATURE GRID ───────────────────────────────── */
.feat-grid{
  display:grid;grid-template-columns:repeat(3,1fr);
  border:var(--border);border-right:none;border-bottom:none;
  margin:24px 0;
}
.feat-card{
  padding:24px 22px;border-right:var(--border);border-bottom:var(--border);
  transition:background .2s;
}
.feat-card:hover{background:var(--bg2)}
.feat-ico{font-size:22px;margin-bottom:12px;display:block}
.feat-title{font-family:'Bebas Neue',sans-serif;font-size:18px;letter-spacing:1px;margin-bottom:6px}
.feat-desc{font-family:'DM Sans',sans-serif;font-size:13px;color:#777;line-height:1.6}
.feat-tag{
  font-size:9px;letter-spacing:2px;text-transform:uppercase;
  padding:3px 8px;border:var(--border);display:inline-block;
  margin-top:10px;color:var(--gry);
}
.feat-tag.pm{border-style:dashed}

/* ─── TABLE ──────────────────────────────────────── */
.table-wrap{overflow-x:auto;margin:20px 0}
table{width:100%;border-collapse:collapse}
th{
  font-size:10px;letter-spacing:2px;text-transform:uppercase;
  padding:12px 16px;text-align:left;
  border-bottom:2px solid #222;color:var(--gry);
  background:var(--bg2);
}
td{
  font-family:'DM Sans',sans-serif;font-size:13px;
  padding:12px 16px;border-bottom:var(--border);color:#aaa;
  vertical-align:top;
}
tr:last-child td{border-bottom:none}
tr:hover td{background:var(--bg2)}
td code{font-size:11px}
.td-yes{color:var(--wht);font-weight:600}
.td-no{color:#444}
.td-badge{
  display:inline-block;font-size:9px;letter-spacing:1px;text-transform:uppercase;
  padding:2px 8px;border:var(--border);
}
.td-badge.ok{background:var(--wht);color:#0d0d0d;border-color:var(--wht)}
.td-badge.wn{border-style:dashed;color:var(--gry)}

/* ─── LIST ───────────────────────────────────────── */
ul,ol{margin:16px 0 16px 0;display:flex;flex-direction:column;gap:6px}
li{
  font-family:'DM Sans',sans-serif;font-size:14px;color:#aaa;
  padding-left:20px;position:relative;line-height:1.6;
}
li::before{content:'—';position:absolute;left:0;color:#444}
ol{counter-reset:li}
ol li::before{
  content:counter(li,decimal-leading-zero);counter-increment:li;
  font-family:'JetBrains Mono',monospace;font-size:10px;color:#555;
}
li strong{color:var(--wht)}

/* ─── CALLOUT ────────────────────────────────────── */
.callout{
  border:var(--border);background:var(--bg2);
  padding:18px 22px;margin:20px 0;
  display:flex;gap:14px;align-items:flex-start;
  border-left:3px solid var(--wht);
}
.callout-icon{font-size:16px;flex-shrink:0;margin-top:1px}
.callout-body{font-family:'DM Sans',sans-serif;font-size:13px;color:#999;line-height:1.6}
.callout-body strong{color:var(--wht)}
.callout.warn{border-left-color:#777}
.callout.info{border-left-color:#444}
.callout.tip{border-left-color:var(--wht)}

/* ─── STEP LIST ──────────────────────────────────── */
.steps{display:flex;flex-direction:column;gap:0;border:var(--border);margin:20px 0}
.step-item{display:flex;gap:0;border-bottom:var(--border)}
.step-item:last-child{border-bottom:none}
.step-num{
  width:52px;flex-shrink:0;
  display:flex;align-items:center;justify-content:center;
  border-right:var(--border);
  font-family:'Bebas Neue',sans-serif;font-size:26px;
  color:#333;
}
.step-body{padding:18px 22px}
.step-title{
  font-family:'Bebas Neue',sans-serif;font-size:17px;letter-spacing:1px;
  color:var(--wht);margin-bottom:6px;
}
.step-desc{font-family:'DM Sans',sans-serif;font-size:13px;color:#777;line-height:1.6}
.step-desc code{font-size:11px}

/* ─── API ENDPOINT ───────────────────────────────── */
.endpoint{
  border:var(--border);margin:16px 0;background:var(--bg2);
}
.endpoint-header{
  display:flex;align-items:center;gap:12px;
  padding:12px 18px;border-bottom:var(--border);
}
.method{
  font-size:10px;letter-spacing:2px;font-weight:700;
  padding:3px 10px;background:var(--wht);color:#0d0d0d;
}
.method.post{background:#555;color:var(--wht)}
.method.del{background:#333;color:var(--wht)}
.ep-path{font-size:13px;color:var(--wht);letter-spacing:.5px}
.ep-desc{font-family:'DM Sans',sans-serif;font-size:12px;color:#666;margin-left:auto}
.ep-body{padding:16px 18px}
.param-list{display:flex;flex-direction:column;gap:8px}
.param{display:flex;align-items:flex-start;gap:12px;padding:8px 0;border-bottom:var(--border2)}
.param:last-child{border-bottom:none}
.param-name{color:var(--wht);font-size:12px;min-width:130px;flex-shrink:0}
.param-type{color:#555;font-size:11px;min-width:70px;flex-shrink:0;margin-top:1px}
.param-req{
  font-size:9px;letter-spacing:1px;text-transform:uppercase;
  padding:1px 6px;border:var(--border);color:#555;min-width:60px;
  text-align:center;flex-shrink:0;margin-top:1px;
}
.param-req.r{border-color:#555;color:#999}
.param-desc{font-family:'DM Sans',sans-serif;font-size:12px;color:#777;line-height:1.5}

/* ─── SCORE DISPLAY ──────────────────────────────── */
.scores-row{
  display:grid;grid-template-columns:repeat(5,1fr);
  border:var(--border);border-right:none;margin:20px 0;
}
.score-item{
  padding:18px 14px;border-right:var(--border);text-align:center;
}
.score-num{
  font-family:'Bebas Neue',sans-serif;font-size:40px;line-height:1;
  display:block;
}
.score-lbl{font-size:9px;letter-spacing:2px;text-transform:uppercase;color:#555;margin-top:4px}
.score-item.hi .score-num{color:var(--wht)}
.score-item.md .score-num{color:#888}
.score-item.lo .score-num{color:#444}

/* ─── DIVIDER ────────────────────────────────────── */
.divider{
  border:none;border-top:var(--border);
  margin:40px 0;position:relative;
}
.divider-label{
  position:absolute;top:-9px;left:0;
  background:var(--bg);padding:0 14px;
  font-size:9px;letter-spacing:3px;text-transform:uppercase;color:#333;
}

/* ─── COMPARISON TABLE ───────────────────────────── */
.compare-grid{
  display:grid;grid-template-columns:2fr 1fr 1fr;
  border:var(--border);border-bottom:none;margin:20px 0;
}
.cg-cell{
  padding:12px 16px;border-right:var(--border);border-bottom:var(--border);
  font-family:'DM Sans',sans-serif;font-size:13px;color:#aaa;
}
.cg-cell:last-child{border-right:none}
.cg-header{
  background:var(--bg2);
  font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--gry);
  font-family:'JetBrains Mono',monospace;
}
.cg-header.active{background:var(--bg3);color:var(--wht)}
.cg-check-y{color:var(--wht);font-weight:700}
.cg-check-n{color:#333}

/* ─── ENV TABLE ──────────────────────────────────── */
.env-table{border:var(--border);margin:20px 0}
.env-row{display:flex;border-bottom:var(--border)}
.env-row:last-child{border-bottom:none}
.env-key{
  width:260px;flex-shrink:0;padding:12px 16px;
  border-right:var(--border);
  font-size:12px;color:var(--wht);
}
.env-val{
  flex:1;padding:12px 16px;
  font-size:12px;color:#555;font-family:'DM Sans',sans-serif;
}
.env-req{
  padding:12px 16px;
  font-size:9px;letter-spacing:1px;text-transform:uppercase;
  color:#333;flex-shrink:0;width:90px;text-align:center;
  border-left:var(--border);
}
.env-req.r{color:#888}

/* ─── CHANGELOG ──────────────────────────────────── */
.changelog{display:flex;flex-direction:column;gap:0;border:var(--border)}
.cl-item{display:flex;gap:0;border-bottom:var(--border)}
.cl-item:last-child{border-bottom:none}
.cl-ver{
  width:100px;flex-shrink:0;padding:16px;
  border-right:var(--border);
  font-family:'Bebas Neue',sans-serif;font-size:16px;letter-spacing:2px;
  color:var(--wht);
}
.cl-date{
  width:110px;flex-shrink:0;padding:16px;
  border-right:var(--border);
  font-size:11px;color:#555;
}
.cl-body{padding:16px 20px;flex:1}
.cl-title{font-size:13px;color:var(--wht);margin-bottom:6px;font-weight:600}
.cl-items{display:flex;flex-direction:column;gap:3px}
.cl-change{
  font-family:'DM Sans',sans-serif;font-size:12px;color:#777;
  padding-left:16px;position:relative;
}
.cl-change::before{content:'→';position:absolute;left:0;color:#444;font-size:10px}
.cl-tag{
  font-size:8px;letter-spacing:1px;text-transform:uppercase;
  padding:1px 6px;border:var(--border);margin-left:6px;color:#555;
  vertical-align:middle;
}
.cl-tag.new{border-color:#555;color:#aaa}
.cl-tag.fix{border-color:#333}

/* ─── FOOTER ─────────────────────────────────────── */
.readme-footer{
  border-top:var(--border);
  padding:40px 0;
  display:flex;align-items:center;justify-content:space-between;
  flex-wrap:wrap;gap:20px;
}
.footer-logo{display:flex;align-items:center;gap:10px}
.footer-logo svg{width:24px;height:24px}
.footer-brand{font-family:'Bebas Neue',sans-serif;font-size:22px;letter-spacing:4px}
.footer-links{display:flex;gap:20px;flex-wrap:wrap}
.footer-links a{font-size:11px;letter-spacing:2px;text-transform:uppercase;color:#444;transition:color .15s}
.footer-links a:hover{color:var(--wht);text-decoration:none}
.footer-copy{font-size:10px;color:#333;letter-spacing:2px;text-transform:uppercase}

/* ─── ANIMATIONS ─────────────────────────────────── */
.fade-in{animation:fadein .5s ease forwards}
@keyframes fadein{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:translateY(0)}}

/* ─── PRINT ──────────────────────────────────────── */
@media print{.topbar{display:none}}

/* ─── RESPONSIVE ─────────────────────────────────── */
@media(max-width:768px){
  .topbar-nav{display:none}
  .toc-grid{grid-template-columns:1fr 1fr}
  .feat-grid{grid-template-columns:1fr}
  .scores-row{grid-template-columns:repeat(3,1fr)}
  .compare-grid{grid-template-columns:1fr}
  .cg-header.active+.cg-header{display:none}
  .env-key{width:180px}
  .cl-date{display:none}
  pre{font-size:11px}
}
@media(max-width:480px){
  .toc-grid{grid-template-columns:1fr}
  .scores-row{grid-template-columns:1fr 1fr}
  .install-block{flex-direction:column;gap:10px}
}
</style>
</head>
<body>

<!-- TOP BAR -->
<div class="topbar">
  <div class="topbar-logo">
    <svg viewBox="0 0 22 22" fill="none">
      <circle cx="11" cy="11" r="8.5" stroke="#e8e7e2" stroke-width="1.5"/>
      <circle cx="11" cy="11" r="3.5" fill="#e8e7e2"/>
      <line x1="11" y1="0" x2="11" y2="2.5" stroke="#e8e7e2" stroke-width="1.5"/>
      <line x1="11" y1="19.5" x2="11" y2="22" stroke="#e8e7e2" stroke-width="1.5"/>
      <line x1="0" y1="11" x2="2.5" y2="11" stroke="#e8e7e2" stroke-width="1.5"/>
      <line x1="19.5" y1="11" x2="22" y2="11" stroke="#e8e7e2" stroke-width="1.5"/>
    </svg>
    ORSCAN
  </div>
  <div class="topbar-nav">
    <a href="#overview">Overview</a>
    <a href="#features">Features</a>
    <a href="#quickstart">Quickstart</a>
    <a href="#api">API</a>
    <a href="#pricing">Pricing</a>
    <a href="#changelog">Changelog</a>
  </div>
  <span style="font-size:10px;letter-spacing:2px;color:#333">README.md</span>
</div>

<div class="page">

  <!-- HERO -->
  <section class="hero fade-in" id="overview">
    <div class="hero-badge">
      <span class="dot"></span>
      v2.4 · Stable Release
    </div>

    <h1 class="hero-title">
      <span>ORS</span><span class="out">CAN</span>
    </h1>
    <div class="hero-sub">Website Intelligence Platform</div>

    <p class="hero-desc">
      <strong>ORSCAN</strong> is a brutally honest, AI-powered website scanner. Drop in any URL and get a deep analysis of SEO, performance, security, accessibility, and Core Web Vitals — in under 10 seconds. No login. No fluff. Just the truth your agency won't tell you.
    </p>

    <div class="badges-row">
      <span class="badge badge-fill">Free Tier</span>
      <span class="badge">MIT License</span>
      <span class="badge">AI-Powered</span>
      <span class="badge">REST API</span>
      <span class="badge">Mobile App</span>
      <span class="badge">v2.4 Stable</span>
    </div>

    <div class="install-block">
      <div class="install-cmd">
        <span style="color:#444">$</span> <span>curl -X POST https://api.orscan.io/v1/scan \</span><br>
        &nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#666">-d '{"url":"https://yourwebsite.com"}'</span>
      </div>
      <button class="copy-btn" onclick="copyInstall(this)">Copy</button>
    </div>
  </section>

  <!-- TABLE OF CONTENTS -->
  <nav class="toc" id="toc">
    <div class="toc-header">Table of Contents</div>
    <div class="toc-grid">
      <a href="#overview"    class="toc-item"><span class="toc-num">01</span><span class="toc-label">Overview</span></a>
      <a href="#features"    class="toc-item"><span class="toc-num">02</span><span class="toc-label">Features</span></a>
      <a href="#quickstart"  class="toc-item"><span class="toc-num">03</span><span class="toc-label">Quick Start</span></a>
      <a href="#api"         class="toc-item"><span class="toc-num">04</span><span class="toc-label">API Reference</span></a>
      <a href="#modules"     class="toc-item"><span class="toc-num">05</span><span class="toc-label">Scan Modules</span></a>
      <a href="#orbot"       class="toc-item"><span class="toc-num">06</span><span class="toc-label">ORBOT AI Agent</span></a>
      <a href="#env"         class="toc-item"><span class="toc-num">07</span><span class="toc-label">Configuration</span></a>
      <a href="#output"      class="toc-item"><span class="toc-num">08</span><span class="toc-label">Output Format</span></a>
      <a href="#pricing"     class="toc-item"><span class="toc-num">09</span><span class="toc-label">Pricing</span></a>
      <a href="#selfhost"    class="toc-item"><span class="toc-num">10</span><span class="toc-label">Self-Hosting</span></a>
      <a href="#contributing" class="toc-item"><span class="toc-num">11</span><span class="toc-label">Contributing</span></a>
      <a href="#changelog"   class="toc-item"><span class="toc-num">12</span><span class="toc-label">Changelog</span></a>
    </div>
  </nav>

  <!-- FEATURES -->
  <section class="section" id="features">
    <div class="sec-kicker">02 — Features</div>
    <h2>WHAT <span class="out">ORSCAN</span><br>DOES</h2>

    <p>ORSCAN's multi-module engine dissects any publicly accessible website across <strong>12 critical checkpoints</strong>. Every result is prioritized by impact and mapped to actionable fixes — not vague suggestions.</p>

    <div class="feat-grid">
      <div class="feat-card">
        <span class="feat-ico">📈</span>
        <div class="feat-title">SEO Deep Audit</div>
        <p class="feat-desc">Meta tags, title optimization, keyword density, canonical issues, structured data, XML sitemaps, robots.txt validation.</p>
        <span class="feat-tag">Free</span>
      </div>
      <div class="feat-card">
        <span class="feat-ico">⚡</span>
        <div class="feat-title">Core Web Vitals</div>
        <p class="feat-desc">LCP, FID, CLS, TTFB, FCP measurement with Google PageSpeed integration. Render-blocking resource detection.</p>
        <span class="feat-tag">Free</span>
      </div>
      <div class="feat-card">
        <span class="feat-ico">🔒</span>
        <div class="feat-title">Security Headers</div>
        <p class="feat-desc">SSL certificate check, HTTPS enforcement, CSP, HSTS, X-Frame-Options, XSS protection header analysis.</p>
        <span class="feat-tag">Free</span>
      </div>
      <div class="feat-card">
        <span class="feat-ico">📱</span>
        <div class="feat-title">Mobile Optimization</div>
        <p class="feat-desc">Responsive design check, touch target sizes, viewport configuration, mobile-first indexing readiness score.</p>
        <span class="feat-tag">Free</span>
      </div>
      <div class="feat-card">
        <span class="feat-ico">♿</span>
        <div class="feat-title">Accessibility WCAG</div>
        <p class="feat-desc">WCAG 2.2 compliance, color contrast ratios, ARIA labels, keyboard navigation, screen reader compatibility.</p>
        <span class="feat-tag pm">Premium</span>
      </div>
      <div class="feat-card">
        <span class="feat-ico">🤖</span>
        <div class="feat-title">AI Critique (ORBOT)</div>
        <p class="feat-desc">GPT-powered brutally honest analysis of content quality, copy tone, UX patterns, and conversion optimization.</p>
        <span class="feat-tag pm">Premium</span>
      </div>
      <div class="feat-card">
        <span class="feat-ico">🎯</span>
        <div class="feat-title">Competitor Analysis</div>
        <p class="feat-desc">Stack your scores against top 3 competitors. Keyword gap analysis, DA/PA comparison, content benchmarking.</p>
        <span class="feat-tag pm">Premium</span>
      </div>
      <div class="feat-card">
        <span class="feat-ico">🔗</span>
        <div class="feat-title">Link Audit</div>
        <p class="feat-desc">Broken internal and external links, redirect chains, anchor text optimization, link authority mapping.</p>
        <span class="feat-tag pm">Premium</span>
      </div>
      <div class="feat-card">
        <span class="feat-ico">📊</span>
        <div class="feat-title">Schema Markup</div>
        <p class="feat-desc">JSON-LD validation, Open Graph tags, Twitter Cards, structured data for Articles, Products, FAQs, Reviews.</p>
        <span class="feat-tag">Free</span>
      </div>
    </div>

    <div class="scores-row">
      <div class="score-item hi"><span class="score-num">86</span><span class="score-lbl">SEO</span></div>
      <div class="score-item md"><span class="score-num">72</span><span class="score-lbl">Performance</span></div>
      <div class="score-item hi"><span class="score-num">94</span><span class="score-lbl">Security</span></div>
      <div class="score-item lo"><span class="score-num">64</span><span class="score-lbl">Accessibility</span></div>
      <div class="score-item md"><span class="score-num">78</span><span class="score-lbl">UX Score</span></div>
    </div>
    <p style="font-size:11px;color:#444;margin-top:-8px;letter-spacing:1px">// Example scan output for https://example.com</p>
  </section>

  <!-- QUICKSTART -->
  <section class="section" id="quickstart">
    <div class="sec-kicker">03 — Quick Start</div>
    <h2>UP & RUNNING<br>IN <span class="out">60 SECONDS</span></h2>

    <h3>Option A — Web Interface</h3>
    <p>The fastest way. No setup required. Just go to <code>orscan.io</code> and paste your URL.</p>

    <div class="callout tip">
      <span class="callout-icon">💡</span>
      <div class="callout-body"><strong>Free tier</strong> allows 3 scans per day covering SEO, Performance, Security, Mobile, and Schema modules. No account required.</div>
    </div>

    <h3>Option B — REST API</h3>

    <div class="steps">
      <div class="step-item">
        <div class="step-num">01</div>
        <div class="step-body">
          <div class="step-title">Get Your API Key</div>
          <div class="step-desc">Sign up at <code>orscan.io/signup</code> and navigate to Dashboard → API Keys → Generate New Key. Your key starts with <code>orsk_</code>.</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">02</div>
        <div class="step-body">
          <div class="step-title">Make Your First Scan</div>
          <div class="step-desc">Send a POST request to the scan endpoint with your target URL and desired modules.</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">03</div>
        <div class="step-body">
          <div class="step-title">Handle the Response</div>
          <div class="step-desc">Scan results return synchronously for standard scans (&lt;30s). For deep scans with all modules, poll the results endpoint using the returned <code>scan_id</code>.</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">04</div>
        <div class="step-body">
          <div class="step-title">Set Up Webhooks (Optional)</div>
          <div class="step-desc">Premium users can configure webhooks at <code>orscan.io/dashboard/webhooks</code> to receive real-time results pushed to your endpoint.</div>
        </div>
      </div>
    </div>

    <h3>cURL Example</h3>
    <pre><code><span class="cm"># Basic scan — free tier</span>
<span class="kw">curl</span> -X POST https://api.orscan.io/v1/scan \
  -H <span class="st">"Content-Type: application/json"</span> \
  -H <span class="st">"Authorization: Bearer orsk_your_api_key"</span> \
  -d <span class="st">'{
    "url": "https://yourwebsite.com",
    "modules": ["seo", "performance", "security"]
  }'</span>
<div class="code-lang">BASH</div></code></pre>

    <h3>JavaScript / Node.js</h3>
    <pre><code><span class="kw">const</span> <span class="vr">response</span> <span class="op">=</span> <span class="kw">await</span> <span class="fn">fetch</span>(<span class="st">'https://api.orscan.io/v1/scan'</span>, {
  <span class="vr">method</span>: <span class="st">'POST'</span>,
  <span class="vr">headers</span>: {
    <span class="st">'Content-Type'</span>: <span class="st">'application/json'</span>,
    <span class="st">'Authorization'</span>: <span class="st">`Bearer ${</span><span class="vr">process.env.ORSCAN_API_KEY</span><span class="st">}`</span>
  },
  <span class="vr">body</span>: <span class="fn">JSON.stringify</span>({
    <span class="vr">url</span>: <span class="st">'https://yourwebsite.com'</span>,
    <span class="vr">modules</span>: [<span class="st">'seo'</span>, <span class="st">'performance'</span>, <span class="st">'security'</span>, <span class="st">'accessibility'</span>],
    <span class="vr">options</span>: {
      <span class="vr">depth</span>: <span class="nm">3</span>,           <span class="cm">// crawl depth (1-10)</span>
      <span class="vr">screenshots</span>: <span class="kw">true</span>,  <span class="cm">// capture page screenshots</span>
      <span class="vr">ai_critique</span>: <span class="kw">true</span>   <span class="cm">// enable ORBOT analysis (Premium)</span>
    }
  })
});

<span class="kw">const</span> <span class="vr">scan</span> <span class="op">=</span> <span class="kw">await</span> <span class="vr">response</span>.<span class="fn">json</span>();
<span class="vr">console</span>.<span class="fn">log</span>(<span class="vr">scan</span>.<span class="vr">scores</span>.<span class="vr">seo</span>); <span class="cm">// → 86</span>
<div class="code-lang">JAVASCRIPT</div></code></pre>

    <h3>Python</h3>
    <pre><code><span class="kw">import</span> requests

<span class="vr">response</span> <span class="op">=</span> requests.<span class="fn">post</span>(
    <span class="st">"https://api.orscan.io/v1/scan"</span>,
    <span class="vr">headers</span><span class="op">=</span>{<span class="st">"Authorization"</span>: <span class="st">f"Bearer {api_key}"</span>},
    <span class="vr">json</span><span class="op">=</span>{
        <span class="st">"url"</span>: <span class="st">"https://yourwebsite.com"</span>,
        <span class="st">"modules"</span>: [<span class="st">"seo"</span>, <span class="st">"performance"</span>, <span class="st">"security"</span>]
    }
)

<span class="vr">scan</span> <span class="op">=</span> <span class="vr">response</span>.<span class="fn">json</span>()
<span class="fn">print</span>(<span class="vr">scan</span>[<span class="st">"scores"</span>][<span class="st">"seo"</span>])      <span class="cm"># 86</span>
<span class="fn">print</span>(<span class="kw">len</span>(<span class="vr">scan</span>[<span class="st">"issues"</span>]))          <span class="cm"># 5</span>
<span class="fn">print</span>(<span class="vr">scan</span>[<span class="st">"ai_critique"</span>][<span class="st">"summary"</span>]) <span class="cm"># ORBOT response</span>
<div class="code-lang">PYTHON</div></code></pre>
  </section>

  <!-- API REFERENCE -->
  <section class="section" id="api">
    <div class="sec-kicker">04 — API Reference</div>
    <h2>REST API<br><span class="out">REFERENCE</span></h2>

    <p>Base URL: <code>https://api.orscan.io/v1</code><br>
    All requests require <code>Authorization: Bearer &lt;your_api_key&gt;</code> header.</p>

    <h3>Endpoints</h3>

    <!-- POST /scan -->
    <div class="endpoint">
      <div class="endpoint-header">
        <span class="method">POST</span>
        <span class="ep-path">/scan</span>
        <span class="ep-desc">Initiate a website scan</span>
      </div>
      <div class="ep-body">
        <h4>Request Parameters</h4>
        <div class="param-list">
          <div class="param">
            <span class="param-name">url</span>
            <span class="param-type">string</span>
            <span class="param-req r">required</span>
            <span class="param-desc">Target URL to scan. Must include protocol (https://). Supports up to 10,000 pages per crawl.</span>
          </div>
          <div class="param">
            <span class="param-name">modules</span>
            <span class="param-type">string[]</span>
            <span class="param-req r">required</span>
            <span class="param-desc">Array of modules to run. Options: <code>seo</code>, <code>performance</code>, <code>security</code>, <code>accessibility</code>, <code>mobile</code>, <code>schema</code>, <code>links</code>, <code>competitor</code>, <code>ai_critique</code>.</span>
          </div>
          <div class="param">
            <span class="param-name">options.depth</span>
            <span class="param-type">integer</span>
            <span class="param-req">optional</span>
            <span class="param-desc">Crawl depth. Range: 1–10. Default: <code>3</code>. Higher depth = longer scan time.</span>
          </div>
          <div class="param">
            <span class="param-name">options.screenshots</span>
            <span class="param-type">boolean</span>
            <span class="param-req">optional</span>
            <span class="param-desc">Capture full-page screenshots for each scanned URL. Default: <code>false</code>.</span>
          </div>
          <div class="param">
            <span class="param-name">options.ai_critique</span>
            <span class="param-type">boolean</span>
            <span class="param-req">optional</span>
            <span class="param-desc">Enable ORBOT AI analysis. Requires Premium plan. Default: <code>false</code>.</span>
          </div>
          <div class="param">
            <span class="param-name">webhook_url</span>
            <span class="param-type">string</span>
            <span class="param-req">optional</span>
            <span class="param-desc">URL to receive scan completion webhook. POST request with full scan result JSON.</span>
          </div>
        </div>
      </div>
    </div>

    <!-- GET /scan/:id -->
    <div class="endpoint">
      <div class="endpoint-header">
        <span class="method">GET</span>
        <span class="ep-path">/scan/:scan_id</span>
        <span class="ep-desc">Get scan results by ID</span>
      </div>
      <div class="ep-body">
        <h4>Path Parameters</h4>
        <div class="param-list">
          <div class="param">
            <span class="param-name">scan_id</span>
            <span class="param-type">string</span>
            <span class="param-req r">required</span>
            <span class="param-desc">Scan ID returned from POST /scan. Format: <code>scan_xxxxxxxxxxxxxxxx</code>.</span>
          </div>
        </div>
      </div>
    </div>

    <!-- GET /scans -->
    <div class="endpoint">
      <div class="endpoint-header">
        <span class="method">GET</span>
        <span class="ep-path">/scans</span>
        <span class="ep-desc">List all scans (paginated)</span>
      </div>
      <div class="ep-body">
        <h4>Query Parameters</h4>
        <div class="param-list">
          <div class="param">
            <span class="param-name">limit</span>
            <span class="param-type">integer</span>
            <span class="param-req">optional</span>
            <span class="param-desc">Results per page. Default: <code>20</code>. Max: <code>100</code>.</span>
          </div>
          <div class="param">
            <span class="param-name">cursor</span>
            <span class="param-type">string</span>
            <span class="param-req">optional</span>
            <span class="param-desc">Pagination cursor from previous response.</span>
          </div>
        </div>
      </div>
    </div>

    <!-- POST /orbot/chat -->
    <div class="endpoint">
      <div class="endpoint-header">
        <span class="method post">POST</span>
        <span class="ep-path">/orbot/chat</span>
        <span class="ep-desc">Chat with ORBOT AI Agent — Premium only</span>
      </div>
      <div class="ep-body">
        <h4>Request Parameters</h4>
        <div class="param-list">
          <div class="param">
            <span class="param-name">scan_id</span>
            <span class="param-type">string</span>
            <span class="param-req r">required</span>
            <span class="param-desc">Scan ID to provide context for ORBOT's analysis.</span>
          </div>
          <div class="param">
            <span class="param-name">message</span>
            <span class="param-type">string</span>
            <span class="param-req r">required</span>
            <span class="param-desc">Natural language question or instruction for ORBOT. Max 2,000 characters.</span>
          </div>
          <div class="param">
            <span class="param-name">history</span>
            <span class="param-type">object[]</span>
            <span class="param-req">optional</span>
            <span class="param-desc">Previous conversation turns for multi-turn context. Format: <code>[{role, content}]</code>.</span>
          </div>
        </div>
      </div>
    </div>

    <h3>Response Format</h3>
    <pre><code>{
  <span class="st">"scan_id"</span>:    <span class="st">"scan_k2m9x7dn4qfp"</span>,
  <span class="st">"url"</span>:        <span class="st">"https://yourwebsite.com"</span>,
  <span class="st">"status"</span>:     <span class="st">"complete"</span>,         <span class="cm">// pending | running | complete | failed</span>
  <span class="st">"scanned_at"</span>: <span class="st">"2025-04-12T08:22:14Z"</span>,
  <span class="st">"duration_ms"</span>: <span class="nm">2340</span>,

  <span class="st">"scores"</span>: {
    <span class="st">"seo"</span>:           <span class="nm">86</span>,
    <span class="st">"performance"</span>:   <span class="nm">72</span>,
    <span class="st">"security"</span>:      <span class="nm">94</span>,
    <span class="st">"accessibility"</span>: <span class="nm">64</span>,
    <span class="st">"ux"</span>:            <span class="nm">78</span>
  },

  <span class="st">"issues"</span>: [
    {
      <span class="st">"id"</span>:       <span class="st">"seo_meta_missing"</span>,
      <span class="st">"module"</span>:   <span class="st">"seo"</span>,
      <span class="st">"severity"</span>: <span class="st">"critical"</span>,         <span class="cm">// critical | warning | info | pass</span>
      <span class="st">"title"</span>:    <span class="st">"Missing meta descriptions"</span>,
      <span class="st">"detail"</span>:   <span class="st">"4 pages have no meta description"</span>,
      <span class="st">"pages"</span>:    [<span class="st">"/about"</span>, <span class="st">"/services"</span>, <span class="st">"/blog"</span>, <span class="st">"/contact"</span>],
      <span class="st">"fix"</span>:      <span class="st">"Add unique meta descriptions under 160 chars"</span>
    }
  ],

  <span class="st">"vitals"</span>: {
    <span class="st">"lcp"</span>:  <span class="nm">3.4</span>,   <span class="st">"ttfb"</span>: <span class="nm">820</span>,
    <span class="st">"fid"</span>:  <span class="nm">45</span>,    <span class="st">"cls"</span>:  <span class="nm">0.04</span>,
    <span class="st">"fcp"</span>:  <span class="nm">1.9</span>
  },

  <span class="st">"tech_stack"</span>: {
    <span class="st">"cms"</span>: <span class="st">"WordPress"</span>, <span class="st">"server"</span>: <span class="st">"Nginx"</span>,
    <span class="st">"cdn"</span>: <span class="kw">null</span>,         <span class="st">"ssl_days"</span>: <span class="nm">284</span>
  },

  <span class="st">"ai_critique"</span>: {          <span class="cm">// only if ai_critique: true</span>
    <span class="st">"summary"</span>:  <span class="st">"Strong security posture. SEO needs work..."</span>,
    <span class="st">"roadmap"</span>:  [<span class="st">"Fix meta descriptions (1h)"</span>, ...],
    <span class="st">"orbot_id"</span>: <span class="st">"orb_9xdk2m"</span>
  }
}
<div class="code-lang">JSON</div></code></pre>

    <h3>HTTP Status Codes</h3>
    <div class="table-wrap">
      <table>
        <thead><tr><th>Code</th><th>Meaning</th><th>Notes</th></tr></thead>
        <tbody>
          <tr><td><code>200</code></td><td class="td-yes">OK</td><td>Scan completed successfully</td></tr>
          <tr><td><code>202</code></td><td>Accepted</td><td>Scan queued — poll results with <code>scan_id</code></td></tr>
          <tr><td><code>400</code></td><td>Bad Request</td><td>Invalid URL or missing required fields</td></tr>
          <tr><td><code>401</code></td><td>Unauthorized</td><td>Invalid or missing API key</td></tr>
          <tr><td><code>402</code></td><td>Payment Required</td><td>Premium-only module requested on free plan</td></tr>
          <tr><td><code>429</code></td><td>Rate Limited</td><td>Free: 3/day · Pro: 500/day · Enterprise: custom</td></tr>
          <tr><td><code>500</code></td><td>Server Error</td><td>Check <code>status.orscan.io</code></td></tr>
        </tbody>
      </table>
    </div>
  </section>

  <!-- MODULES -->
  <section class="section" id="modules">
    <div class="sec-kicker">05 — Scan Modules</div>
    <h2>SCAN<br><span class="out">MODULES</span></h2>

    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Module</th>
            <th>Key</th>
            <th>Checks</th>
            <th>Free</th>
            <th>Pro</th>
            <th>Avg Time</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><strong>SEO Audit</strong></td>
            <td><code>seo</code></td>
            <td>18 checks</td>
            <td class="td-yes">✓</td>
            <td class="td-yes">✓</td>
            <td>~0.8s</td>
          </tr>
          <tr>
            <td><strong>Performance</strong></td>
            <td><code>performance</code></td>
            <td>12 checks</td>
            <td class="td-yes">✓</td>
            <td class="td-yes">✓</td>
            <td>~1.4s</td>
          </tr>
          <tr>
            <td><strong>Security</strong></td>
            <td><code>security</code></td>
            <td>9 checks</td>
            <td class="td-yes">✓</td>
            <td class="td-yes">✓</td>
            <td>~0.6s</td>
          </tr>
          <tr>
            <td><strong>Mobile UX</strong></td>
            <td><code>mobile</code></td>
            <td>7 checks</td>
            <td class="td-yes">✓</td>
            <td class="td-yes">✓</td>
            <td>~0.9s</td>
          </tr>
          <tr>
            <td><strong>Schema Markup</strong></td>
            <td><code>schema</code></td>
            <td>6 checks</td>
            <td class="td-yes">✓</td>
            <td class="td-yes">✓</td>
            <td>~0.5s</td>
          </tr>
          <tr>
            <td><strong>Accessibility</strong></td>
            <td><code>accessibility</code></td>
            <td>22 checks (WCAG 2.2)</td>
            <td class="td-no">—</td>
            <td class="td-yes">✓</td>
            <td>~1.1s</td>
          </tr>
          <tr>
            <td><strong>Link Audit</strong></td>
            <td><code>links</code></td>
            <td>5 checks</td>
            <td class="td-no">—</td>
            <td class="td-yes">✓</td>
            <td>~2.0s</td>
          </tr>
          <tr>
            <td><strong>Competitor</strong></td>
            <td><code>competitor</code></td>
            <td>Top 3 rivals</td>
            <td class="td-no">—</td>
            <td class="td-yes">✓</td>
            <td>~3.5s</td>
          </tr>
          <tr>
            <td><strong>AI Critique</strong></td>
            <td><code>ai_critique</code></td>
            <td>ORBOT LLM analysis</td>
            <td class="td-no">—</td>
            <td class="td-yes">✓</td>
            <td>~4.2s</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="callout info">
      <span class="callout-icon">ℹ️</span>
      <div class="callout-body">Running all modules simultaneously is supported and recommended for comprehensive audits. Total scan time with all modules: approximately <strong>8–12 seconds</strong> for a standard website.</div>
    </div>
  </section>

  <!-- ORBOT -->
  <section class="section" id="orbot">
    <div class="sec-kicker">06 — ORBOT AI Agent</div>
    <h2>ORBOT<br><span class="out">AI AGENT</span></h2>

    <p>ORBOT is ORSCAN's built-in AI analyst. It reads your full scan report and answers questions in natural language — explaining issues, generating fix plans, rewriting your copy, and building prioritized roadmaps.</p>

    <div class="callout warn">
      <span class="callout-icon">⚠️</span>
      <div class="callout-body"><strong>Premium feature.</strong> ORBOT is available on Pro ($19/mo) and above. Demo mode available in the web UI for free users.</div>
    </div>

    <h3>ORBOT Capabilities</h3>
    <ul>
      <li><strong>Natural Language Q&A</strong> — Ask "Why is my SEO score low?" and get a specific, data-backed answer from your actual scan results.</li>
      <li><strong>Copy Rewriter</strong> — Request new meta descriptions, H1 tags, page headlines, or full copy rewrites optimized for keywords and conversion.</li>
      <li><strong>Fix Roadmap Generator</strong> — ORBOT creates a prioritized, time-estimated action plan to fix every issue found in your scan.</li>
      <li><strong>Competitor Breakdown</strong> — Ask "How does my SEO compare to competitor X?" and get a gap analysis with specific recommendations.</li>
      <li><strong>API Integration</strong> — Feed ORBOT into your own AI pipeline. Works with OpenAI, Anthropic, Gemini, or any custom LLM backend.</li>
    </ul>

    <h3>Chat API Example</h3>
    <pre><code><span class="cm">// Chat with ORBOT about a specific scan</span>
<span class="kw">const</span> <span class="vr">chat</span> <span class="op">=</span> <span class="kw">await</span> <span class="fn">fetch</span>(<span class="st">'https://api.orscan.io/v1/orbot/chat'</span>, {
  <span class="vr">method</span>: <span class="st">'POST'</span>,
  <span class="vr">headers</span>: { <span class="st">'Authorization'</span>: <span class="st">`Bearer ${</span><span class="vr">apiKey</span><span class="st">}`</span> },
  <span class="vr">body</span>: <span class="fn">JSON.stringify</span>({
    <span class="vr">scan_id</span>: <span class="st">'scan_k2m9x7dn4qfp'</span>,
    <span class="vr">message</span>: <span class="st">'What is the single biggest issue hurting my SEO ranking?'</span>
  })
});
<span class="cm">// → { reply: "Your biggest issue is missing meta descriptions on 4 pages..." }</span>
<div class="code-lang">JAVASCRIPT</div></code></pre>

    <h3>Connect Your Own LLM</h3>
    <pre><code><span class="cm"># Use ORSCAN scan data with your own OpenAI/Anthropic integration</span>
<span class="vr">scan_data</span> <span class="op">=</span> orscan_client.<span class="fn">scan</span>(<span class="st">"https://yoursite.com"</span>)

<span class="cm"># Feed into your LLM</span>
<span class="vr">prompt</span> <span class="op">=</span> <span class="st">f"""
You are a website optimization expert.
Scan results: {scan_data}
Question: What is the highest-impact fix I should do first?
"""</span>
<span class="vr">response</span> <span class="op">=</span> anthropic.<span class="fn">messages.create</span>(<span class="vr">model</span><span class="op">=</span><span class="st">"claude-opus-4-5"</span>, <span class="vr">messages</span><span class="op">=</span>[...])
<div class="code-lang">PYTHON</div></code></pre>
  </section>

  <!-- CONFIGURATION -->
  <section class="section" id="env">
    <div class="sec-kicker">07 — Configuration</div>
    <h2>CONFIG &<br><span class="out">ENV VARS</span></h2>

    <p>Configuration is managed via environment variables. For self-hosted deployments, create a <code>.env</code> file in the project root.</p>

    <div class="env-table">
      <div class="env-row" style="background:#111;border-bottom:var(--border)">
        <div class="env-key" style="font-size:10px;letter-spacing:2px;color:#444;text-transform:uppercase">Variable</div>
        <div class="env-val" style="font-size:10px;letter-spacing:2px;color:#444;text-transform:uppercase">Default / Example</div>
        <div class="env-req" style="font-size:10px;letter-spacing:2px;color:#444;text-transform:uppercase">Required</div>
      </div>
      <div class="env-row"><div class="env-key">ORSCAN_API_KEY</div><div class="env-val">orsk_xxxxxxxxxxxxxxxxxx</div><div class="env-req r">Yes</div></div>
      <div class="env-row"><div class="env-key">ORSCAN_BASE_URL</div><div class="env-val">https://api.orscan.io/v1</div><div class="env-req">No</div></div>
      <div class="env-row"><div class="env-key">ORSCAN_TIMEOUT</div><div class="env-val">30000 (ms)</div><div class="env-req">No</div></div>
      <div class="env-row"><div class="env-key">ORSCAN_DEFAULT_MODULES</div><div class="env-val">seo,performance,security</div><div class="env-req">No</div></div>
      <div class="env-row"><div class="env-key">ORSCAN_WEBHOOK_SECRET</div><div class="env-val">whsec_xxxxxxxxxxxxxxxxxx</div><div class="env-req">No</div></div>
      <div class="env-row"><div class="env-key">ORBOT_ENABLED</div><div class="env-val">false</div><div class="env-req">No</div></div>
      <div class="env-row"><div class="env-key">ORBOT_LLM_PROVIDER</div><div class="env-val">anthropic | openai | custom</div><div class="env-req">No</div></div>
      <div class="env-row"><div class="env-key">ORBOT_LLM_API_KEY</div><div class="env-val">sk-xxxxxxxx</div><div class="env-req">No</div></div>
      <div class="env-row"><div class="env-key">SCAN_CRAWL_DEPTH</div><div class="env-val">3</div><div class="env-req">No</div></div>
      <div class="env-row"><div class="env-key">SCAN_MAX_PAGES</div><div class="env-val">100</div><div class="env-req">No</div></div>
    </div>

    <h3>Sample .env File</h3>
    <pre><code><span class="cm"># ORSCAN Configuration</span>
<span class="vr">ORSCAN_API_KEY</span><span class="op">=</span><span class="st">orsk_your_api_key_here</span>
<span class="vr">ORSCAN_BASE_URL</span><span class="op">=</span><span class="st">https://api.orscan.io/v1</span>
<span class="vr">ORSCAN_TIMEOUT</span><span class="op">=</span><span class="nm">30000</span>

<span class="cm"># Scan defaults</span>
<span class="vr">SCAN_CRAWL_DEPTH</span><span class="op">=</span><span class="nm">3</span>
<span class="vr">SCAN_MAX_PAGES</span><span class="op">=</span><span class="nm">100</span>
<span class="vr">ORSCAN_DEFAULT_MODULES</span><span class="op">=</span><span class="st">seo,performance,security,mobile,schema</span>

<span class="cm"># ORBOT AI Agent (Premium)</span>
<span class="vr">ORBOT_ENABLED</span><span class="op">=</span><span class="kw">true</span>
<span class="vr">ORBOT_LLM_PROVIDER</span><span class="op">=</span><span class="st">anthropic</span>
<span class="vr">ORBOT_LLM_API_KEY</span><span class="op">=</span><span class="st">sk-ant-your-key-here</span>

<span class="cm"># Webhooks</span>
<span class="vr">ORSCAN_WEBHOOK_SECRET</span><span class="op">=</span><span class="st">whsec_your_webhook_secret</span>
<div class="code-lang">.ENV</div></code></pre>
  </section>

  <!-- OUTPUT FORMAT -->
  <section class="section" id="output">
    <div class="sec-kicker">08 — Output Format</div>
    <h2>OUTPUT<br><span class="out">FORMATS</span></h2>

    <p>ORSCAN supports multiple output formats for different use cases:</p>

    <div class="compare-grid">
      <div class="cg-cell cg-header">Format</div>
      <div class="cg-cell cg-header">Free</div>
      <div class="cg-cell cg-header active">Pro</div>

      <div class="cg-cell"><strong>JSON</strong> — Raw scan data via API</div>
      <div class="cg-cell cg-check-y">✓</div>
      <div class="cg-cell cg-check-y">✓</div>

      <div class="cg-cell"><strong>HTML Report</strong> — Interactive web report</div>
      <div class="cg-cell cg-check-y">✓</div>
      <div class="cg-cell cg-check-y">✓</div>

      <div class="cg-cell"><strong>PDF Export</strong> — Branded downloadable report</div>
      <div class="cg-cell cg-check-n">—</div>
      <div class="cg-cell cg-check-y">✓</div>

      <div class="cg-cell"><strong>CSV Export</strong> — Issues list in spreadsheet format</div>
      <div class="cg-cell cg-check-n">—</div>
      <div class="cg-cell cg-check-y">✓</div>

      <div class="cg-cell"><strong>White-label PDF</strong> — Custom branding for agencies</div>
      <div class="cg-cell cg-check-n">—</div>
      <div class="cg-cell cg-check-y">✓</div>

      <div class="cg-cell"><strong>Webhooks</strong> — Real-time POST to your endpoint</div>
      <div class="cg-cell cg-check-n">—</div>
      <div class="cg-cell cg-check-y">✓</div>
    </div>

    <h3>Export via API</h3>
    <pre><code><span class="cm"># Export scan as PDF</span>
<span class="kw">curl</span> https://api.orscan.io/v1/scan/scan_k2m9x7dn4qfp/export \
  -H <span class="st">"Authorization: Bearer orsk_your_key"</span> \
  -G -d <span class="st">"format=pdf"</span> \
  --output report.pdf

<span class="cm"># Export as CSV (issues list)</span>
<span class="kw">curl</span> https://api.orscan.io/v1/scan/scan_k2m9x7dn4qfp/export \
  -H <span class="st">"Authorization: Bearer orsk_your_key"</span> \
  -G -d <span class="st">"format=csv"</span> \
  --output issues.csv
<div class="code-lang">BASH</div></code></pre>
  </section>

  <!-- PRICING -->
  <section class="section" id="pricing">
    <div class="sec-kicker">09 — Pricing</div>
    <h2>PLANS &<br><span class="out">PRICING</span></h2>

    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Feature</th>
            <th>Free</th>
            <th>Pro — $19/mo</th>
            <th>Enterprise</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Scans per day</td><td>3</td><td class="td-yes">Unlimited</td><td class="td-yes">Unlimited</td></tr>
          <tr><td>Scan modules</td><td>5 modules</td><td class="td-yes">All 12</td><td class="td-yes">All 12 + custom</td></tr>
          <tr><td>API access</td><td class="td-no">—</td><td class="td-yes">✓</td><td class="td-yes">✓</td></tr>
          <tr><td>ORBOT AI Agent</td><td>Demo only</td><td class="td-yes">Full access</td><td class="td-yes">Custom model</td></tr>
          <tr><td>PDF export</td><td class="td-no">—</td><td class="td-yes">✓</td><td class="td-yes">White-label</td></tr>
          <tr><td>Webhooks</td><td class="td-no">—</td><td class="td-yes">✓</td><td class="td-yes">✓</td></tr>
          <tr><td>Competitor analysis</td><td class="td-no">—</td><td>Top 3 rivals</td><td class="td-yes">Unlimited</td></tr>
          <tr><td>Rate limit</td><td>3/day</td><td>500/day</td><td>Custom</td></tr>
          <tr><td>Support</td><td>Community</td><td>Email priority</td><td>Dedicated SLA</td></tr>
          <tr><td>SLA uptime</td><td class="td-no">—</td><td>99.5%</td><td>99.9%</td></tr>
        </tbody>
      </table>
    </div>

    <div class="callout tip">
      <span class="callout-icon">💳</span>
      <div class="callout-body"><strong>No credit card required</strong> for the free tier. Pro plan billed monthly, cancel anytime. Enterprise pricing available at <code><a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="335b565f5f5c735c414050525d1d5a5c">[email&#160;protected]</a></code>.</div>
    </div>
  </section>

  <!-- SELF-HOSTING -->
  <section class="section" id="selfhost">
    <div class="sec-kicker">10 — Self-Hosting</div>
    <h2>SELF<br><span class="out">HOSTING</span></h2>

    <p>ORSCAN can be self-hosted on your own infrastructure. The Docker image is available on GitHub Container Registry.</p>

    <div class="callout warn">
      <span class="callout-icon">⚠️</span>
      <div class="callout-body">Self-hosted instances require a valid ORSCAN license key. The free community license allows up to <strong>100 scans/month</strong>. Contact sales for production licenses.</div>
    </div>

    <h3>Docker</h3>
    <pre><code><span class="cm"># Pull the latest image</span>
docker pull ghcr.io/orscan/orscan:latest

<span class="cm"># Run with environment variables</span>
docker run -d \
  --name orscan \
  -p <span class="nm">3000</span>:<span class="nm">3000</span> \
  -e ORSCAN_API_KEY<span class="op">=</span>orsk_your_key \
  -e ORBOT_ENABLED<span class="op">=</span><span class="kw">true</span> \
  -e ORBOT_LLM_API_KEY<span class="op">=</span>sk-ant-xxx \
  ghcr.io/orscan/orscan:latest
<div class="code-lang">BASH</div></code></pre>

    <h3>Docker Compose</h3>
    <pre><code><span class="vr">version</span>: <span class="st">'3.9'</span>
<span class="vr">services</span>:
  <span class="vr">orscan</span>:
    <span class="vr">image</span>: ghcr.io/orscan/orscan:<span class="kw">latest</span>
    <span class="vr">ports</span>:
      - <span class="st">"3000:3000"</span>
    <span class="vr">environment</span>:
      - ORSCAN_API_KEY<span class="op">=</span><span class="st">${ORSCAN_API_KEY}</span>
      - SCAN_CRAWL_DEPTH<span class="op">=</span><span class="nm">3</span>
      - ORBOT_ENABLED<span class="op">=</span><span class="kw">true</span>
      - ORBOT_LLM_PROVIDER<span class="op">=</span>anthropic
      - ORBOT_LLM_API_KEY<span class="op">=</span><span class="st">${ORBOT_LLM_API_KEY}</span>
    <span class="vr">volumes</span>:
      - orscan_data:/data
    <span class="vr">restart</span>: unless-stopped
  <span class="vr">redis</span>:
    <span class="vr">image</span>: redis:7-alpine
    <span class="vr">restart</span>: unless-stopped
<span class="vr">volumes</span>:
  orscan_data:
<div class="code-lang">YAML</div></code></pre>

    <h3>System Requirements</h3>
    <ul>
      <li><strong>CPU:</strong> 2+ vCPU recommended for concurrent scans</li>
      <li><strong>RAM:</strong> 2GB minimum, 4GB recommended</li>
      <li><strong>Storage:</strong> 10GB minimum for scan data and screenshots</li>
      <li><strong>Node.js:</strong> v20+ or Docker (recommended)</li>
      <li><strong>Redis:</strong> Required for scan queue and caching</li>
    </ul>
  </section>

  <!-- CONTRIBUTING -->
  <section class="section" id="contributing">
    <div class="sec-kicker">11 — Contributing</div>
    <h2>CONTRI<span class="out">BUTING</span></h2>

    <p>ORSCAN welcomes contributions. Please read the guidelines before opening a PR.</p>

    <div class="steps">
      <div class="step-item">
        <div class="step-num">01</div>
        <div class="step-body">
          <div class="step-title">Fork & Clone</div>
          <div class="step-desc"><code>git clone https://github.com/orscan/orscan.git && cd orscan</code></div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">02</div>
        <div class="step-body">
          <div class="step-title">Install Dependencies</div>
          <div class="step-desc"><code>npm install</code> — Node.js v20+ required. Optionally copy <code>.env.example</code> to <code>.env</code> and add your API key.</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">03</div>
        <div class="step-body">
          <div class="step-title">Create a Feature Branch</div>
          <div class="step-desc"><code>git checkout -b feature/your-feature-name</code> — Keep branches focused on a single feature or fix.</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">04</div>
        <div class="step-body">
          <div class="step-title">Run Tests</div>
          <div class="step-desc"><code>npm test</code> — All tests must pass before submitting a PR. Add tests for any new scan module logic.</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">05</div>
        <div class="step-body">
          <div class="step-title">Open a Pull Request</div>
          <div class="step-desc">Submit your PR against the <code>main</code> branch with a clear description of what changed and why. Reference any related issues.</div>
        </div>
      </div>
    </div>

    <h3>Code Style</h3>
    <ul>
      <li>ESLint + Prettier enforced. Run <code>npm run lint</code> before committing.</li>
      <li>Commit messages follow Conventional Commits: <code>feat:</code> / <code>fix:</code> / <code>docs:</code> / <code>chore:</code></li>
      <li>New scan modules must include unit tests with at least 80% coverage.</li>
      <li>Document new environment variables in <code>README.md</code> and <code>.env.example</code>.</li>
    </ul>

    <h3>Reporting Bugs</h3>
    <p>Open a GitHub issue at <code>github.com/orscan/orscan/issues</code> using the bug report template. Include your Node.js version, the URL scanned (if possible), and the full error output.</p>

    <div class="callout tip">
      <span class="callout-icon">⭐</span>
      <div class="callout-body">Found ORSCAN useful? <strong>Star the repo</strong> at <code>github.com/orscan/orscan</code> — it helps more than you think.</div>
    </div>
  </section>

  <!-- CHANGELOG -->
  <section class="section" id="changelog">
    <div class="sec-kicker">12 — Changelog</div>
    <h2>CHANGE<br><span class="out">LOG</span></h2>

    <div class="changelog">
      <div class="cl-item">
        <div class="cl-ver">v2.4</div>
        <div class="cl-date">Apr 2025</div>
        <div class="cl-body">
          <div class="cl-title">Current Stable Release</div>
          <div class="cl-items">
            <div class="cl-change">ORBOT AI Agent v2 with multi-turn conversation context <span class="cl-tag new">New</span></div>
            <div class="cl-change">Competitor analysis module — top 3 rival comparison</div>
            <div class="cl-change">White-label PDF reports for agencies</div>
            <div class="cl-change">Custom LLM provider support (OpenAI, Anthropic, Gemini)</div>
            <div class="cl-change">Webhook signature verification with HMAC-SHA256</div>
          </div>
        </div>
      </div>
      <div class="cl-item">
        <div class="cl-ver">v2.3</div>
        <div class="cl-date">Feb 2025</div>
        <div class="cl-body">
          <div class="cl-title">Accessibility & Performance</div>
          <div class="cl-items">
            <div class="cl-change">Full WCAG 2.2 accessibility audit module <span class="cl-tag new">New</span></div>
            <div class="cl-change">Core Web Vitals now uses live CrUX data from Google</div>
            <div class="cl-change">API rate limit headers added to all responses</div>
            <div class="cl-change">Fixed false positives in CSP header detection <span class="cl-tag fix">Fix</span></div>
          </div>
        </div>
      </div>
      <div class="cl-item">
        <div class="cl-ver">v2.2</div>
        <div class="cl-date">Dec 2024</div>
        <div class="cl-body">
          <div class="cl-title">API & Webhooks</div>
          <div class="cl-items">
            <div class="cl-change">REST API v1 public release <span class="cl-tag new">New</span></div>
            <div class="cl-change">Webhook support with retry logic (3 attempts)</div>
            <div class="cl-change">CSV and JSON export endpoints</div>
            <div class="cl-change">Improved scan speed — 40% faster average scan time</div>
          </div>
        </div>
      </div>
      <div class="cl-item">
        <div class="cl-ver">v2.0</div>
        <div class="cl-date">Oct 2024</div>
        <div class="cl-body">
          <div class="cl-title">ORBOT First Release</div>
          <div class="cl-items">
            <div class="cl-change">ORBOT AI Agent v1 — initial release <span class="cl-tag new">New</span></div>
            <div class="cl-change">Dashboard redesign — brutalist B&W interface</div>
            <div class="cl-change">Pro plan launch at $19/month</div>
            <div class="cl-change">Mobile web app (PWA)</div>
          </div>
        </div>
      </div>
      <div class="cl-item">
        <div class="cl-ver">v1.0</div>
        <div class="cl-date">Jun 2024</div>
        <div class="cl-body">
          <div class="cl-title">Initial Public Launch</div>
          <div class="cl-items">
            <div class="cl-change">Public launch — free tier with 5 scan modules <span class="cl-tag new">New</span></div>
            <div class="cl-change">SEO, Performance, Security, Mobile, Schema modules</div>
            <div class="cl-change">50,000 websites scanned in first 30 days</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer class="readme-footer">
    <div class="footer-logo">
      <svg viewBox="0 0 22 22" fill="none">
        <circle cx="11" cy="11" r="8.5" stroke="#e8e7e2" stroke-width="1.5"/>
        <circle cx="11" cy="11" r="3.5" fill="#e8e7e2"/>
        <line x1="11" y1="0" x2="11" y2="2.5" stroke="#e8e7e2" stroke-width="1.5"/>
        <line x1="11" y1="19.5" x2="11" y2="22" stroke="#e8e7e2" stroke-width="1.5"/>
        <line x1="0" y1="11" x2="2.5" y2="11" stroke="#e8e7e2" stroke-width="1.5"/>
        <line x1="19.5" y1="11" x2="22" y2="11" stroke="#e8e7e2" stroke-width="1.5"/>
      </svg>
      <span class="footer-brand">ORSCAN</span>
    </div>
    <div class="footer-links">
      <a href="https://orscan.io">Website</a>
      <a href="https://docs.orscan.io">Docs</a>
      <a href="https://github.com/orscan/orscan">GitHub</a>
      <a href="https://status.orscan.io">Status</a>
      <a href="/cdn-cgi/l/email-protection#4129242d2d2e012e333222202f6f282e">Contact</a>
    </div>
    <div class="footer-copy">MIT License · © 2025 ORSCAN</div>
  </footer>

</div><!-- /page -->

<script data-cfasync="false" src="/cdn-cgi/scripts/5c5dd728/cloudflare-static/email-decode.min.js"></script><script>
// ─── COPY BUTTON ──────────────────────────────────────────
function copyInstall(btn) {
  const cmd = `curl -X POST https://api.orscan.io/v1/scan \\\n  -H "Content-Type: application/json" \\\n  -d '{"url":"https://yourwebsite.com"}'`;
  navigator.clipboard.writeText(cmd).then(() => {
    btn.textContent = 'Copied!';
    setTimeout(() => btn.textContent = 'Copy', 2000);
  });
}

// ─── CODE BLOCK COPY ──────────────────────────────────────
document.querySelectorAll('pre').forEach(pre => {
  const btn = document.createElement('button');
  btn.textContent = 'Copy';
  btn.style.cssText = `
    position:absolute;top:10px;right:${pre.querySelector('.code-lang') ? '70px' : '12px'};
    background:none;border:1px solid #333;color:#555;padding:3px 10px;
    font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:2px;
    text-transform:uppercase;cursor:pointer;transition:all .15s;
  `;
  btn.addEventListener('mouseenter', () => { btn.style.color='#e8e7e2';btn.style.borderColor='#555'; });
  btn.addEventListener('mouseleave', () => { btn.style.color='#555';btn.style.borderColor='#333'; });
  btn.addEventListener('click', () => {
    navigator.clipboard.writeText(pre.innerText.replace(/Copy\n?/,'').replace(/[A-Z]+\n?$/,'').trim());
    btn.textContent = 'Copied!';
    btn.style.color = '#e8e7e2';
    setTimeout(() => { btn.textContent = 'Copy'; btn.style.color = '#555'; }, 1800);
  });
  pre.appendChild(btn);
});

// ─── ACTIVE NAV ───────────────────────────────────────────
const sections = document.querySelectorAll('.section, .hero');
const navLinks = document.querySelectorAll('.topbar-nav a');
const observer = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const id = entry.target.id;
      navLinks.forEach(a => {
        a.style.color = a.getAttribute('href') === '#'+id ? '#e8e7e2' : '';
      });
    }
  });
}, { rootMargin: '-40% 0px -50% 0px' });
sections.forEach(s => s.id && observer.observe(s));

// ─── SMOOTH SCROLL ────────────────────────────────────────
document.querySelectorAll('a[href^="#"]').forEach(a => {
  a.addEventListener('click', e => {
    const el = document.querySelector(a.getAttribute('href'));
    if (el) { e.preventDefault(); el.scrollIntoView({ behavior:'smooth', block:'start' }); }
  });
});

// ─── FADE IN ON SCROLL ────────────────────────────────────
const fader = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.style.opacity = '1';
      entry.target.style.transform = 'translateY(0)';
      fader.unobserve(entry.target);
    }
  });
}, { threshold: 0.05 });
document.querySelectorAll('.feat-card, .step-item, .cl-item, .endpoint').forEach(el => {
  el.style.opacity = '0';
  el.style.transform = 'translateY(14px)';
  el.style.transition = 'opacity .4s ease, transform .4s ease';
  fader.observe(el);
});
</script>
</body>
</html>
