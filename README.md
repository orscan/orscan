<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ORSCAN — README</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,300;0,400;0,600;0,700;1,400&family=Bebas+Neue&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500;9..40,600&display=swap" rel="stylesheet">
<style>
/* ── RESET ──────────────────────────────────────────── */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;font-size:16px}
body{
  background:#f7f5f0;
  color:#2c2a26;
  font-family:'JetBrains Mono',monospace;
  font-size:14px;
  line-height:1.75;
  overflow-x:hidden;
}
::selection{background:#2c2a26;color:#f7f5f0}
::-webkit-scrollbar{width:4px}
::-webkit-scrollbar-track{background:#f7f5f0}
::-webkit-scrollbar-thumb{background:#c8c5bc}
a{color:#2c2a26;text-decoration:none}
a:hover{text-decoration:underline;text-underline-offset:3px;color:#5a5750}

/* ── VARIABLES ──────────────────────────────────────── */
:root{
  --ink:      #2c2a26;
  --paper:    #f7f5f0;
  --warm:     #ede9e0;
  --stone:    #e2ded6;
  --mist:     #d0ccc4;
  --slate:    #8c8880;
  --dim:      #b8b4ac;
  --charcoal: #3a3731;
  --mid:      #4a4740;
  --soft:     #5a5750;
  --border:   1px solid #d8d4cc;
  --border-dk:1px solid #c0bcb4;
  --shadow:   0 1px 3px rgba(44,42,38,.06),0 4px 12px rgba(44,42,38,.04);
  --shadow-md:0 2px 8px rgba(44,42,38,.09),0 8px 24px rgba(44,42,38,.06);
}

/* ── NOISE ──────────────────────────────────────────── */
body::before{
  content:'';position:fixed;inset:0;z-index:0;pointer-events:none;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.8' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.02'/%3E%3C/svg%3E");
  opacity:.5;
}

/* ── LAYOUT ─────────────────────────────────────────── */
.wrap{position:relative;z-index:1;max-width:960px;margin:0 auto;padding:0 28px}

/* ── TOP BAR ────────────────────────────────────────── */
.topbar{
  position:sticky;top:0;z-index:100;
  background:rgba(247,245,240,.95);
  backdrop-filter:blur(10px);
  border-bottom:var(--border);
  padding:0 28px;
  display:flex;align-items:center;justify-content:space-between;
  height:50px;
}
.tb-logo{
  display:flex;align-items:center;gap:9px;
  font-family:'Bebas Neue',sans-serif;font-size:20px;letter-spacing:4px;
  color:var(--ink);
}
.tb-logo svg{width:20px;height:20px}
.tb-nav{display:flex;gap:0}
.tb-nav a{
  font-size:10px;letter-spacing:2px;text-transform:uppercase;
  color:var(--slate);padding:0 14px;height:50px;
  display:flex;align-items:center;border-left:var(--border);
  transition:color .15s;
}
.tb-nav a:hover{color:var(--ink);text-decoration:none}
.tb-right{font-size:10px;letter-spacing:2px;color:var(--dim);text-transform:uppercase}

/* ── HERO ───────────────────────────────────────────── */
.hero{
  padding:64px 0 52px;
  border-bottom:var(--border);
}
.hero-top{display:flex;align-items:flex-start;justify-content:space-between;gap:32px;flex-wrap:wrap;margin-bottom:32px}
.hero-badge{
  display:inline-flex;align-items:center;gap:8px;
  font-size:10px;letter-spacing:3px;text-transform:uppercase;
  color:var(--slate);border:var(--border);
  padding:5px 13px;margin-bottom:20px;border-radius:20px;
  background:var(--warm);
}
.hero-badge .pulse{width:7px;height:7px;border-radius:50%;background:#8a9a80;animation:pulse 1.8s ease infinite}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.5;transform:scale(.8)}}
.hero-title{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(56px,8vw,96px);
  line-height:.9;letter-spacing:-1px;
  color:var(--ink);margin-bottom:6px;
}
.hero-title .out{-webkit-text-stroke:1.5px var(--ink);color:transparent;display:block}
.hero-sub{
  font-size:11px;letter-spacing:4px;text-transform:uppercase;
  color:var(--slate);margin-bottom:28px;
  display:flex;align-items:center;gap:14px;
}
.hero-sub::before{content:'//';color:var(--dim);font-size:10px}
.hero-desc{
  font-family:'DM Sans',sans-serif;
  font-size:16px;color:var(--slate);line-height:1.8;
  max-width:640px;margin-bottom:32px;font-weight:400;
}
.hero-desc strong{color:var(--ink);font-weight:600}

.badge-row{display:flex;flex-wrap:wrap;gap:7px;margin-bottom:32px}
.bdg{
  font-size:10px;letter-spacing:1.5px;text-transform:uppercase;
  padding:4px 11px;border:var(--border);color:var(--slate);
  border-radius:3px;background:var(--warm);
  transition:all .15s;
}
.bdg:hover{border-color:var(--mist);color:var(--ink);text-decoration:none}
.bdg-fill{background:var(--ink);color:var(--paper);border-color:var(--ink)}
.bdg-fill:hover{background:var(--charcoal);color:var(--paper)}

.install-box{
  background:var(--charcoal);
  border:1px solid var(--mid);border-radius:5px;
  padding:16px 20px;
  display:flex;align-items:center;justify-content:space-between;
  gap:16px;max-width:620px;
  box-shadow:var(--shadow-md);
}
.install-cmd{font-size:12.5px;color:#c8c4b8;letter-spacing:.5px;line-height:1.6}
.install-cmd .cmt{color:#6a6660}
.install-cmd .val{color:#d8d4c8}
.copy-btn{
  font-size:10px;letter-spacing:2px;text-transform:uppercase;
  color:#8a8680;background:none;border:1px solid #5a5750;border-radius:3px;
  padding:5px 12px;cursor:pointer;transition:all .15s;white-space:nowrap;
}
.copy-btn:hover{color:#e8e4da;border-color:#9a9690}

/* ── TOC ────────────────────────────────────────────── */
.toc{
  border:var(--border);background:var(--warm);
  border-radius:5px;margin:44px 0;overflow:hidden;
  box-shadow:var(--shadow);
}
.toc-hd{
  padding:13px 20px;border-bottom:var(--border);
  display:flex;align-items:center;gap:10px;
  font-size:10px;letter-spacing:3px;text-transform:uppercase;color:var(--slate);
  background:var(--stone);
}
.toc-grid{display:grid;grid-template-columns:repeat(3,1fr)}
.toc-item{
  padding:13px 20px;border-right:var(--border);border-bottom:var(--border);
  display:flex;align-items:center;gap:10px;
  transition:background .15s;color:var(--slate);
}
.toc-item:hover{background:var(--stone);color:var(--ink);text-decoration:none}
.toc-item:nth-child(3n){border-right:none}
.toc-n{color:var(--dim);font-size:10px;min-width:22px}
.toc-l{font-size:12px;letter-spacing:.5px}

/* ── SECTION ────────────────────────────────────────── */
.section{padding:56px 0;border-bottom:var(--border)}
.section:last-child{border-bottom:none}

.kicker{
  font-size:10px;letter-spacing:4px;text-transform:uppercase;
  color:var(--slate);margin-bottom:8px;
  display:flex;align-items:center;gap:10px;
}
.kicker::before{content:'';width:20px;height:1px;background:var(--mist)}

h2{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(30px,4vw,48px);
  line-height:.95;color:var(--ink);
  margin-bottom:28px;letter-spacing:-.5px;
}
h2 .out{-webkit-text-stroke:1px var(--ink);color:transparent}

h3{
  font-family:'Bebas Neue',sans-serif;
  font-size:22px;letter-spacing:1px;
  color:var(--ink);margin-bottom:14px;margin-top:32px;
}
h3:first-child{margin-top:0}

h4{
  font-size:10px;letter-spacing:3px;text-transform:uppercase;
  color:var(--slate);margin-bottom:10px;margin-top:22px;
}

p{
  font-family:'DM Sans',sans-serif;
  font-size:15px;color:var(--slate);line-height:1.8;margin-bottom:16px;
}
p strong{color:var(--ink)}
p:last-child{margin-bottom:0}

/* ── CODE ───────────────────────────────────────────── */
pre{
  background:var(--charcoal);border:1px solid var(--mid);
  border-radius:5px;padding:20px 22px;margin:20px 0;
  overflow-x:auto;position:relative;
  box-shadow:var(--shadow-md);
}
pre::-webkit-scrollbar{height:3px}
pre::-webkit-scrollbar-thumb{background:var(--mid)}
code{
  font-family:'JetBrains Mono',monospace;
  font-size:12.5px;color:#c8c4b8;line-height:1.75;
}
pre code{color:#c8c4b8}
:not(pre)>code{
  background:var(--stone);border:var(--border);border-radius:3px;
  padding:2px 7px;font-size:12px;color:var(--ink);
}
.code-lang{
  position:absolute;top:10px;right:14px;
  font-size:9px;letter-spacing:2px;text-transform:uppercase;color:var(--soft);
}

/* syntax */
.kw{color:#e8e4da;font-weight:600}
.st{color:#b8c4a8}
.cm{color:#6a6660;font-style:italic}
.nm{color:#c8b898}
.fn{color:#d4ccc0}
.vr{color:#c0bcb0}
.op{color:#8a8680}

/* ── FEATURE GRID ───────────────────────────────────── */
.feat-grid{
  display:grid;grid-template-columns:repeat(3,1fr);
  border:var(--border);border-right:none;border-bottom:none;
  margin:24px 0;border-radius:4px 0 0 0;overflow:hidden;
}
.fc{
  padding:24px 22px;border-right:var(--border);border-bottom:var(--border);
  transition:background .2s;background:var(--paper);
}
.fc:hover{background:var(--warm)}
.fc-ico{font-size:20px;margin-bottom:10px;display:block}
.fc-ttl{font-family:'Bebas Neue',sans-serif;font-size:17px;letter-spacing:1px;margin-bottom:6px;color:var(--ink)}
.fc-desc{font-family:'DM Sans',sans-serif;font-size:13px;color:var(--slate);line-height:1.6}
.fc-tag{
  font-size:9px;letter-spacing:1.5px;text-transform:uppercase;
  padding:3px 9px;border:var(--border);border-radius:2px;
  display:inline-block;margin-top:10px;color:var(--slate);
}
.fc-tag.pm{border-style:dashed;color:var(--dim)}

/* ── TABLE ──────────────────────────────────────────── */
.table-wrap{overflow-x:auto;margin:20px 0;border-radius:4px;box-shadow:var(--shadow)}
table{width:100%;border-collapse:collapse}
th{
  font-size:10px;letter-spacing:2px;text-transform:uppercase;
  padding:11px 16px;text-align:left;
  border-bottom:var(--border-dk);color:var(--slate);
  background:var(--stone);
}
td{
  font-family:'DM Sans',sans-serif;font-size:13px;
  padding:11px 16px;border-bottom:var(--border);color:var(--slate);
  vertical-align:top;background:var(--paper);
}
tr:hover td{background:var(--warm)}
td code{font-size:11px}
.y{color:var(--ink);font-weight:700}
.n{color:var(--dim)}

/* ── LIST ───────────────────────────────────────────── */
ul,ol{margin:16px 0;display:flex;flex-direction:column;gap:7px}
li{
  font-family:'DM Sans',sans-serif;font-size:14px;color:var(--slate);
  padding-left:20px;position:relative;line-height:1.65;
}
li::before{content:'—';position:absolute;left:0;color:var(--mist)}
li strong{color:var(--ink)}

/* ── CALLOUT ────────────────────────────────────────── */
.callout{
  border:var(--border);background:var(--warm);
  border-radius:4px;padding:16px 20px;margin:20px 0;
  display:flex;gap:13px;align-items:flex-start;
  border-left:3px solid var(--mist);
}
.callout.tip{border-left-color:var(--ink)}
.callout.warn{border-left-color:#c8a060}
.callout.info{border-left-color:var(--mist)}
.callout-ico{font-size:15px;flex-shrink:0;margin-top:1px}
.callout-body{font-family:'DM Sans',sans-serif;font-size:13px;color:var(--slate);line-height:1.65}
.callout-body strong{color:var(--ink)}

/* ── STEPS ──────────────────────────────────────────── */
.steps{display:flex;flex-direction:column;gap:0;border:var(--border);border-radius:4px;overflow:hidden;margin:20px 0}
.step-item{display:flex;gap:0;border-bottom:var(--border)}
.step-item:last-child{border-bottom:none}
.step-num{
  width:52px;flex-shrink:0;
  display:flex;align-items:center;justify-content:center;
  border-right:var(--border);background:var(--stone);
  font-family:'Bebas Neue',sans-serif;font-size:24px;color:var(--dim);
}
.step-body{padding:18px 22px;background:var(--paper)}
.step-title{
  font-family:'Bebas Neue',sans-serif;font-size:16px;letter-spacing:1px;
  color:var(--ink);margin-bottom:5px;
}
.step-desc{font-family:'DM Sans',sans-serif;font-size:13px;color:var(--slate);line-height:1.6}
.step-desc code{font-size:11px}

/* ── ENDPOINT ───────────────────────────────────────── */
.endpoint{
  border:var(--border);margin:16px 0;background:var(--paper);
  border-radius:4px;overflow:hidden;box-shadow:var(--shadow);
}
.endpoint-hd{
  display:flex;align-items:center;gap:12px;
  padding:12px 18px;border-bottom:var(--border);
  background:var(--warm);
}
.method{
  font-size:10px;letter-spacing:2px;font-weight:700;
  padding:3px 10px;border-radius:3px;
  background:var(--ink);color:var(--paper);
}
.method.post{background:#7a8870;color:var(--paper)}
.ep-path{font-size:13px;color:var(--ink);letter-spacing:.5px}
.ep-desc{font-family:'DM Sans',sans-serif;font-size:12px;color:var(--slate);margin-left:auto}
.ep-body{padding:16px 18px}
.param-list{display:flex;flex-direction:column;gap:8px}
.param{display:flex;align-items:flex-start;gap:12px;padding:8px 0;border-bottom:var(--border)}
.param:last-child{border-bottom:none}
.p-name{color:var(--ink);font-size:12px;min-width:130px;flex-shrink:0}
.p-type{color:var(--slate);font-size:11px;min-width:70px;flex-shrink:0;margin-top:1px}
.p-req{
  font-size:9px;letter-spacing:1px;text-transform:uppercase;
  padding:2px 7px;border:var(--border);border-radius:2px;
  color:var(--dim);min-width:60px;text-align:center;flex-shrink:0;margin-top:1px;
}
.p-req.r{border-color:var(--mist);color:var(--slate);background:var(--stone)}
.p-desc{font-family:'DM Sans',sans-serif;font-size:12px;color:var(--slate);line-height:1.55}

/* ── SCORE ROW ──────────────────────────────────────── */
.scores{
  display:grid;grid-template-columns:repeat(5,1fr);
  border:var(--border);border-right:none;margin:20px 0;
  border-radius:4px 0 0 4px;overflow:hidden;
}
.sc{padding:18px 12px;border-right:var(--border);text-align:center;background:var(--warm)}
.sc-n{font-family:'Bebas Neue',sans-serif;font-size:36px;line-height:1;display:block;color:var(--ink)}
.sc-l{font-size:9px;letter-spacing:2px;text-transform:uppercase;color:var(--slate);margin-top:4px}
.sc.hi{background:var(--ink)}.sc.hi .sc-n,.sc.hi .sc-l{color:var(--paper)}
.sc.md{background:var(--stone)}
.sc.lo{background:var(--warm)}.sc.lo .sc-n{color:var(--dim)}

/* ── ENV TABLE ──────────────────────────────────────── */
.env-t{border:var(--border);border-radius:4px;overflow:hidden;margin:20px 0;box-shadow:var(--shadow)}
.env-hd{display:flex;border-bottom:var(--border-dk);background:var(--stone)}
.env-hd div{padding:10px 16px;font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--slate)}
.env-row{display:flex;border-bottom:var(--border)}
.env-row:last-child{border-bottom:none}
.env-k{width:260px;flex-shrink:0;padding:11px 16px;border-right:var(--border);font-size:12px;color:var(--ink);background:var(--warm)}
.env-v{flex:1;padding:11px 16px;font-size:12px;color:var(--slate);background:var(--paper);font-family:'DM Sans',sans-serif}
.env-r{padding:11px 16px;font-size:9px;letter-spacing:1px;text-transform:uppercase;color:var(--dim);flex-shrink:0;width:90px;text-align:center;border-left:var(--border);background:var(--warm)}
.env-r.r{color:var(--slate)}

/* ── COMPARE ────────────────────────────────────────── */
.compare{display:grid;grid-template-columns:2fr 1fr 1fr;border:var(--border);border-bottom:none;border-radius:4px 4px 0 0;overflow:hidden;margin:20px 0}
.cg{padding:11px 16px;border-right:var(--border);border-bottom:var(--border);font-family:'DM Sans',sans-serif;font-size:13px;color:var(--slate);background:var(--paper)}
.cg:last-child{border-right:none}
.cg-hd{background:var(--stone);font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--slate);font-family:'JetBrains Mono',monospace}
.cg-hd.active{background:var(--ink);color:var(--paper)}
.cy{color:var(--ink);font-weight:700}
.cn{color:var(--dim)}

/* ── CHANGELOG ──────────────────────────────────────── */
.cl{display:flex;flex-direction:column;border:var(--border);border-radius:4px;overflow:hidden;margin:20px 0}
.cl-row{display:flex;border-bottom:var(--border)}
.cl-row:last-child{border-bottom:none}
.cl-v{width:90px;flex-shrink:0;padding:16px;border-right:var(--border);font-family:'Bebas Neue',sans-serif;font-size:15px;letter-spacing:2px;color:var(--ink);background:var(--warm)}
.cl-d{width:100px;flex-shrink:0;padding:16px;border-right:var(--border);font-size:11px;color:var(--dim);background:var(--warm)}
.cl-b{padding:16px 20px;flex:1;background:var(--paper)}
.cl-ttl{font-size:13px;color:var(--ink);margin-bottom:7px;font-weight:600;font-family:'DM Sans',sans-serif}
.cl-items{display:flex;flex-direction:column;gap:4px}
.cl-ch{font-family:'DM Sans',sans-serif;font-size:12px;color:var(--slate);padding-left:16px;position:relative}
.cl-ch::before{content:'→';position:absolute;left:0;color:var(--mist);font-size:10px}
.tag-new{font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:1px 6px;border:var(--border);border-radius:2px;margin-left:6px;color:var(--ink);vertical-align:middle}
.tag-fix{font-size:8px;letter-spacing:1px;text-transform:uppercase;padding:1px 6px;border:var(--border);border-style:dashed;border-radius:2px;margin-left:6px;color:var(--slate);vertical-align:middle}

/* ── DIVIDER ────────────────────────────────────────── */
hr{border:none;border-top:var(--border);margin:32px 0;position:relative}

/* ── FOOTER ─────────────────────────────────────────── */
.readme-footer{
  border-top:var(--border);padding:36px 0;
  display:flex;align-items:center;justify-content:space-between;
  flex-wrap:wrap;gap:20px;
}
.ft-logo{display:flex;align-items:center;gap:9px}
.ft-logo svg{width:22px;height:22px}
.ft-brand{font-family:'Bebas Neue',sans-serif;font-size:20px;letter-spacing:4px;color:var(--ink)}
.ft-links{display:flex;gap:20px;flex-wrap:wrap}
.ft-links a{font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--slate);transition:color .15s}
.ft-links a:hover{color:var(--ink);text-decoration:none}
.ft-copy{font-size:10px;color:var(--dim);letter-spacing:2px;text-transform:uppercase}

/* ── RESPONSIVE ─────────────────────────────────────── */
@media(max-width:768px){
  .tb-nav{display:none}
  .toc-grid{grid-template-columns:1fr 1fr}
  .feat-grid{grid-template-columns:1fr}
  .scores{grid-template-columns:repeat(3,1fr)}
  .compare{grid-template-columns:1fr}
  .env-k{width:180px}
  .cl-d{display:none}
  pre{font-size:11.5px}
  .install-box{flex-direction:column;gap:10px}
  .hero-title{font-size:clamp(48px,12vw,80px)}
}
@media(max-width:480px){
  .toc-grid{grid-template-columns:1fr}
  .scores{grid-template-columns:1fr 1fr}
  .wrap{padding:0 18px}
}
</style>
</head>
<body>

<!-- TOP BAR -->
<div class="topbar">
  <div class="tb-logo">
    <svg viewBox="0 0 22 22" fill="none">
      <circle cx="11" cy="11" r="8.5" stroke="#2c2a26" stroke-width="1.5"/>
      <circle cx="11" cy="11" r="3.5" fill="#2c2a26"/>
      <line x1="11" y1="0" x2="11" y2="2.5" stroke="#2c2a26" stroke-width="1.5"/>
      <line x1="11" y1="19.5" x2="11" y2="22" stroke="#2c2a26" stroke-width="1.5"/>
      <line x1="0" y1="11" x2="2.5" y2="11" stroke="#2c2a26" stroke-width="1.5"/>
      <line x1="19.5" y1="11" x2="22" y2="11" stroke="#2c2a26" stroke-width="1.5"/>
    </svg>
    ORSCAN
  </div>
  <div class="tb-nav">
    <a href="#overview">Overview</a>
    <a href="#features">Features</a>
    <a href="#quickstart">Quickstart</a>
    <a href="#api">API</a>
    <a href="#pricing">Pricing</a>
    <a href="#changelog">Changelog</a>
  </div>
  <span class="tb-right">README.md</span>
</div>

<div class="wrap">

<!-- HERO -->
<section class="hero" id="overview">
  <div class="hero-badge">
    <span class="pulse"></span>
    v2.4 · Stable Release
  </div>
  <h1 class="hero-title">
    <span>ORS</span><span class="out">CAN</span>
  </h1>
  <div class="hero-sub">Website Intelligence Platform</div>
  <p class="hero-desc">
    <strong>ORSCAN</strong> is an AI-powered website scanner that delivers brutally honest results. Drop in any URL and get a comprehensive analysis of SEO, performance, security, accessibility, and Core Web Vitals — in under 10 seconds. No login required. No vague suggestions. Just the truth your agency won't tell you.
  </p>
  <div class="badge-row">
    <span class="bdg bdg-fill">Free Tier</span>
    <span class="bdg">MIT License</span>
    <span class="bdg">AI-Powered</span>
    <span class="bdg">REST API</span>
    <span class="bdg">Mobile App</span>
    <span class="bdg">v2.4 Stable</span>
  </div>
  <div class="install-box">
    <div class="install-cmd">
      <span class="cmt">$</span> <span class="val">curl -X POST https://api.orscan.io/v1/scan \</span><br>
      &nbsp;&nbsp;&nbsp;&nbsp;<span class="cmt">-d '{"url":"https://yourwebsite.com"}'</span>
    </div>
    <button class="copy-btn" onclick="doCopy(this)">Copy</button>
  </div>
</section>

<!-- TOC -->
<nav class="toc" id="toc">
  <div class="toc-hd">📋 &nbsp;Table of Contents</div>
  <div class="toc-grid">
    <a href="#overview"     class="toc-item"><span class="toc-n">01</span><span class="toc-l">Overview</span></a>
    <a href="#features"     class="toc-item"><span class="toc-n">02</span><span class="toc-l">Features</span></a>
    <a href="#quickstart"   class="toc-item"><span class="toc-n">03</span><span class="toc-l">Quick Start</span></a>
    <a href="#api"          class="toc-item"><span class="toc-n">04</span><span class="toc-l">API Reference</span></a>
    <a href="#modules"      class="toc-item"><span class="toc-n">05</span><span class="toc-l">Scan Modules</span></a>
    <a href="#orbot"        class="toc-item"><span class="toc-n">06</span><span class="toc-l">ORBOT AI Agent</span></a>
    <a href="#config"       class="toc-item"><span class="toc-n">07</span><span class="toc-l">Configuration</span></a>
    <a href="#output"       class="toc-item"><span class="toc-n">08</span><span class="toc-l">Output Format</span></a>
    <a href="#pricing"      class="toc-item"><span class="toc-n">09</span><span class="toc-l">Pricing</span></a>
    <a href="#selfhost"     class="toc-item"><span class="toc-n">10</span><span class="toc-l">Self-Hosting</span></a>
    <a href="#contributing" class="toc-item"><span class="toc-n">11</span><span class="toc-l">Contributing</span></a>
    <a href="#changelog"    class="toc-item"><span class="toc-n">12</span><span class="toc-l">Changelog</span></a>
  </div>
</nav>

<!-- 02 FEATURES -->
<section class="section" id="features">
  <div class="kicker">02 — Features</div>
  <h2>WHAT <span class="out">ORSCAN</span> DOES</h2>

  <p>ORSCAN's multi-module engine dissects any publicly accessible website across <strong>12 critical checkpoints</strong>. Every result is ranked by impact and paired with a specific, actionable fix — not generic advice.</p>

  <div class="feat-grid">
    <div class="fc"><span class="fc-ico">📈</span><div class="fc-ttl">SEO Deep Audit</div><p class="fc-desc">Meta tags, title optimization, keyword density, canonical issues, structured data, XML sitemaps, robots.txt validation.</p><span class="fc-tag">Free</span></div>
    <div class="fc"><span class="fc-ico">⚡</span><div class="fc-ttl">Core Web Vitals</div><p class="fc-desc">LCP, FID, CLS, TTFB, FCP measurement with live Google CrUX data. Render-blocking resource detection.</p><span class="fc-tag">Free</span></div>
    <div class="fc"><span class="fc-ico">🔒</span><div class="fc-ttl">Security Headers</div><p class="fc-desc">SSL certificate, HTTPS enforcement, CSP, HSTS, X-Frame-Options, XSS protection header analysis.</p><span class="fc-tag">Free</span></div>
    <div class="fc"><span class="fc-ico">📱</span><div class="fc-ttl">Mobile Optimization</div><p class="fc-desc">Responsive design, touch targets, viewport config, font sizes, mobile-first indexing readiness score.</p><span class="fc-tag">Free</span></div>
    <div class="fc"><span class="fc-ico">♿</span><div class="fc-ttl">Accessibility WCAG</div><p class="fc-desc">WCAG 2.2 compliance, color contrast ratios, ARIA labels, keyboard navigation, screen reader support.</p><span class="fc-tag pm">Premium</span></div>
    <div class="fc"><span class="fc-ico">🤖</span><div class="fc-ttl">AI Critique (ORBOT)</div><p class="fc-desc">GPT-powered analysis of content quality, copy tone, UX patterns, and conversion optimization suggestions.</p><span class="fc-tag pm">Premium</span></div>
    <div class="fc"><span class="fc-ico">🎯</span><div class="fc-ttl">Competitor Analysis</div><p class="fc-desc">Stack your scores vs. top 3 competitors. Keyword gap analysis, DA/PA comparison, content benchmarking.</p><span class="fc-tag pm">Premium</span></div>
    <div class="fc"><span class="fc-ico">🔗</span><div class="fc-ttl">Link Audit</div><p class="fc-desc">Broken internal and external links, redirect chains, anchor text optimization, link authority mapping.</p><span class="fc-tag pm">Premium</span></div>
    <div class="fc"><span class="fc-ico">📊</span><div class="fc-ttl">Schema Markup</div><p class="fc-desc">JSON-LD validation, Open Graph, Twitter Cards, structured data for Articles, Products, FAQs, Reviews.</p><span class="fc-tag">Free</span></div>
  </div>

  <p style="font-size:11px;color:var(--dim);letter-spacing:1px;margin-top:4px">// Example output scores for https://example.com</p>
  <div class="scores">
    <div class="sc hi"><span class="sc-n">86</span><span class="sc-l">SEO</span></div>
    <div class="sc md"><span class="sc-n">72</span><span class="sc-l">Performance</span></div>
    <div class="sc hi"><span class="sc-n">94</span><span class="sc-l">Security</span></div>
    <div class="sc lo"><span class="sc-n">64</span><span class="sc-l">Accessibility</span></div>
    <div class="sc md"><span class="sc-n">78</span><span class="sc-l">UX Score</span></div>
  </div>
</section>

<!-- 03 QUICKSTART -->
<section class="section" id="quickstart">
  <div class="kicker">03 — Quick Start</div>
  <h2>UP & RUNNING<br>IN <span class="out">60 SECONDS</span></h2>

  <h3>Option A — Web Interface</h3>
  <p>The fastest path. No setup, no account needed. Visit <code>orscan.io</code>, paste your URL, and get results instantly.</p>
  <div class="callout tip">
    <span class="callout-ico">💡</span>
    <div class="callout-body"><strong>Free tier</strong> allows 3 scans per day across SEO, Performance, Security, Mobile, and Schema modules. No credit card required.</div>
  </div>

  <h3>Option B — REST API</h3>
  <div class="steps">
    <div class="step-item">
      <div class="step-num">01</div>
      <div class="step-body">
        <div class="step-title">Get Your API Key</div>
        <div class="step-desc">Sign up at <code>orscan.io/signup</code> → Dashboard → API Keys → Generate New Key. Your key begins with <code>orsk_</code>.</div>
      </div>
    </div>
    <div class="step-item">
      <div class="step-num">02</div>
      <div class="step-body">
        <div class="step-title">Make Your First Scan</div>
        <div class="step-desc">Send a POST request with your target URL and the modules you want to run. Free tier: up to 5 modules. Pro: all 12.</div>
      </div>
    </div>
    <div class="step-item">
      <div class="step-num">03</div>
      <div class="step-body">
        <div class="step-title">Handle the Response</div>
        <div class="step-desc">Standard scans return synchronously in ~10s. Deep scans with all modules poll via <code>scan_id</code> on the results endpoint.</div>
      </div>
    </div>
    <div class="step-item">
      <div class="step-num">04</div>
      <div class="step-body">
        <div class="step-title">Set Up Webhooks (Optional)</div>
        <div class="step-desc">Premium users can configure webhooks at <code>orscan.io/dashboard/webhooks</code> to receive results pushed to your endpoint in real-time.</div>
      </div>
    </div>
  </div>

  <h3>cURL</h3>
<pre><code><span class="cm"># Basic scan — free tier</span>
<span class="kw">curl</span> -X POST https://api.orscan.io/v1/scan \
  -H <span class="st">"Content-Type: application/json"</span> \
  -H <span class="st">"Authorization: Bearer orsk_your_api_key"</span> \
  -d <span class="st">'{
    "url": "https://yourwebsite.com",
    "modules": ["seo", "performance", "security"]
  }'</span><div class="code-lang">BASH</div></code></pre>

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
      <span class="vr">depth</span>: <span class="nm">3</span>,           <span class="cm">// crawl depth 1–10</span>
      <span class="vr">screenshots</span>: <span class="kw">true</span>,  <span class="cm">// capture full-page screenshots</span>
      <span class="vr">ai_critique</span>: <span class="kw">true</span>   <span class="cm">// enable ORBOT (Premium)</span>
    }
  })
});

<span class="kw">const</span> <span class="vr">scan</span> <span class="op">=</span> <span class="kw">await</span> <span class="vr">response</span>.<span class="fn">json</span>();
<span class="vr">console</span>.<span class="fn">log</span>(<span class="vr">scan</span>.<span class="vr">scores</span>.<span class="vr">seo</span>); <span class="cm">// → 86</span><div class="code-lang">JS</div></code></pre>

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
<span class="vr">data</span> <span class="op">=</span> <span class="vr">response</span>.<span class="fn">json</span>()
<span class="fn">print</span>(<span class="vr">data</span>[<span class="st">"scores"</span>][<span class="st">"seo"</span>])        <span class="cm"># 86</span>
<span class="fn">print</span>(<span class="kw">len</span>(<span class="vr">data</span>[<span class="st">"issues"</span>]))            <span class="cm"># 5</span>
<span class="fn">print</span>(<span class="vr">data</span>[<span class="st">"ai_critique"</span>][<span class="st">"summary"</span>]) <span class="cm"># ORBOT response</span><div class="code-lang">PYTHON</div></code></pre>
</section>

<!-- 04 API -->
<section class="section" id="api">
  <div class="kicker">04 — API Reference</div>
  <h2>REST API<br><span class="out">REFERENCE</span></h2>
  <p>Base URL: <code>https://api.orscan.io/v1</code><br>All requests require the header <code>Authorization: Bearer &lt;api_key&gt;</code>.</p>

  <h3>Endpoints</h3>

  <div class="endpoint">
    <div class="endpoint-hd">
      <span class="method">POST</span>
      <span class="ep-path">/scan</span>
      <span class="ep-desc">Initiate a new website scan</span>
    </div>
    <div class="ep-body">
      <h4>Request Parameters</h4>
      <div class="param-list">
        <div class="param"><span class="p-name">url</span><span class="p-type">string</span><span class="p-req r">required</span><span class="p-desc">Target URL including protocol (https://). Supports any publicly accessible website.</span></div>
        <div class="param"><span class="p-name">modules</span><span class="p-type">string[]</span><span class="p-req r">required</span><span class="p-desc">Modules to run: <code>seo</code>, <code>performance</code>, <code>security</code>, <code>accessibility</code>, <code>mobile</code>, <code>schema</code>, <code>links</code>, <code>competitor</code>, <code>ai_critique</code>.</span></div>
        <div class="param"><span class="p-name">options.depth</span><span class="p-type">integer</span><span class="p-req">optional</span><span class="p-desc">Crawl depth 1–10. Default: <code>3</code>. Higher = slower but more thorough.</span></div>
        <div class="param"><span class="p-name">options.screenshots</span><span class="p-type">boolean</span><span class="p-req">optional</span><span class="p-desc">Capture full-page screenshots per URL. Default: <code>false</code>.</span></div>
        <div class="param"><span class="p-name">options.ai_critique</span><span class="p-type">boolean</span><span class="p-req">optional</span><span class="p-desc">Enable ORBOT AI analysis. Requires Premium plan. Default: <code>false</code>.</span></div>
        <div class="param"><span class="p-name">webhook_url</span><span class="p-type">string</span><span class="p-req">optional</span><span class="p-desc">Endpoint to receive completed scan via POST. Payload is the full scan JSON.</span></div>
      </div>
    </div>
  </div>

  <div class="endpoint">
    <div class="endpoint-hd">
      <span class="method">GET</span>
      <span class="ep-path">/scan/:scan_id</span>
      <span class="ep-desc">Retrieve scan results by ID</span>
    </div>
    <div class="ep-body">
      <div class="param-list">
        <div class="param"><span class="p-name">scan_id</span><span class="p-type">string</span><span class="p-req r">required</span><span class="p-desc">Scan ID returned from POST /scan. Format: <code>scan_xxxxxxxxxxxxxxxx</code>.</span></div>
      </div>
    </div>
  </div>

  <div class="endpoint">
    <div class="endpoint-hd">
      <span class="method">GET</span>
      <span class="ep-path">/scans</span>
      <span class="ep-desc">List all scans (paginated)</span>
    </div>
    <div class="ep-body">
      <div class="param-list">
        <div class="param"><span class="p-name">limit</span><span class="p-type">integer</span><span class="p-req">optional</span><span class="p-desc">Results per page. Default: <code>20</code>. Max: <code>100</code>.</span></div>
        <div class="param"><span class="p-name">cursor</span><span class="p-type">string</span><span class="p-req">optional</span><span class="p-desc">Pagination cursor from previous response <code>next_cursor</code> field.</span></div>
      </div>
    </div>
  </div>

  <div class="endpoint">
    <div class="endpoint-hd">
      <span class="method post">POST</span>
      <span class="ep-path">/orbot/chat</span>
      <span class="ep-desc">Chat with ORBOT AI Agent — Premium only</span>
    </div>
    <div class="ep-body">
      <div class="param-list">
        <div class="param"><span class="p-name">scan_id</span><span class="p-type">string</span><span class="p-req r">required</span><span class="p-desc">Scan ID to provide context for ORBOT's analysis and answers.</span></div>
        <div class="param"><span class="p-name">message</span><span class="p-type">string</span><span class="p-req r">required</span><span class="p-desc">Natural language question or instruction. Max 2,000 characters.</span></div>
        <div class="param"><span class="p-name">history</span><span class="p-type">object[]</span><span class="p-req">optional</span><span class="p-desc">Previous conversation turns for multi-turn context. Format: <code>[{role, content}]</code>.</span></div>
      </div>
    </div>
  </div>

  <h3>Response Format</h3>
<pre><code>{
  <span class="st">"scan_id"</span>:     <span class="st">"scan_k2m9x7dn4qfp"</span>,
  <span class="st">"url"</span>:         <span class="st">"https://yourwebsite.com"</span>,
  <span class="st">"status"</span>:      <span class="st">"complete"</span>,    <span class="cm">// pending | running | complete | failed</span>
  <span class="st">"scanned_at"</span>:  <span class="st">"2025-04-12T08:22:14Z"</span>,
  <span class="st">"duration_ms"</span>: <span class="nm">2340</span>,

  <span class="st">"scores"</span>: {
    <span class="st">"seo"</span>: <span class="nm">86</span>, <span class="st">"performance"</span>: <span class="nm">72</span>, <span class="st">"security"</span>: <span class="nm">94</span>,
    <span class="st">"accessibility"</span>: <span class="nm">64</span>, <span class="st">"ux"</span>: <span class="nm">78</span>
  },

  <span class="st">"issues"</span>: [
    {
      <span class="st">"id"</span>:       <span class="st">"seo_meta_missing"</span>,
      <span class="st">"module"</span>:   <span class="st">"seo"</span>,
      <span class="st">"severity"</span>: <span class="st">"critical"</span>,    <span class="cm">// critical | warning | info | pass</span>
      <span class="st">"title"</span>:    <span class="st">"Missing meta descriptions"</span>,
      <span class="st">"detail"</span>:   <span class="st">"4 pages have no meta description"</span>,
      <span class="st">"pages"</span>:    [<span class="st">"/about"</span>, <span class="st">"/services"</span>, <span class="st">"/blog"</span>, <span class="st">"/contact"</span>],
      <span class="st">"fix"</span>:      <span class="st">"Add unique meta descriptions under 160 chars"</span>
    }
  ],

  <span class="st">"vitals"</span>: {
    <span class="st">"lcp"</span>: <span class="nm">3.4</span>, <span class="st">"fid"</span>: <span class="nm">45</span>, <span class="st">"cls"</span>: <span class="nm">0.04</span>,
    <span class="st">"ttfb"</span>: <span class="nm">820</span>, <span class="st">"fcp"</span>: <span class="nm">1.9</span>
  },

  <span class="st">"tech_stack"</span>: {
    <span class="st">"cms"</span>: <span class="st">"WordPress"</span>, <span class="st">"server"</span>: <span class="st">"Nginx"</span>,
    <span class="st">"cdn"</span>: <span class="kw">null</span>, <span class="st">"ssl_days"</span>: <span class="nm">284</span>
  },

  <span class="st">"ai_critique"</span>: {       <span class="cm">// only when ai_critique: true</span>
    <span class="st">"summary"</span>:  <span class="st">"Strong security. SEO needs work on meta and H1..."</span>,
    <span class="st">"roadmap"</span>:  [<span class="st">"Fix meta descriptions (1h)"</span>, <span class="st">"Compress images (2h)"</span>],
    <span class="st">"orbot_id"</span>: <span class="st">"orb_9xdk2m"</span>
  }
}<div class="code-lang">JSON</div></code></pre>

  <h3>HTTP Status Codes</h3>
  <div class="table-wrap">
    <table>
      <thead><tr><th>Code</th><th>Status</th><th>Notes</th></tr></thead>
      <tbody>
        <tr><td><code>200</code></td><td class="y">OK</td><td>Scan completed successfully</td></tr>
        <tr><td><code>202</code></td><td>Accepted</td><td>Scan queued — poll with <code>scan_id</code></td></tr>
        <tr><td><code>400</code></td><td>Bad Request</td><td>Invalid URL or missing required fields</td></tr>
        <tr><td><code>401</code></td><td>Unauthorized</td><td>Invalid or missing API key</td></tr>
        <tr><td><code>402</code></td><td>Payment Required</td><td>Premium-only module on free plan</td></tr>
        <tr><td><code>429</code></td><td>Rate Limited</td><td>Free: 3/day · Pro: 500/day · Enterprise: custom</td></tr>
        <tr><td><code>500</code></td><td>Server Error</td><td>Check <code>status.orscan.io</code></td></tr>
      </tbody>
    </table>
  </div>
</section>

<!-- 05 MODULES -->
<section class="section" id="modules">
  <div class="kicker">05 — Scan Modules</div>
  <h2>SCAN<br><span class="out">MODULES</span></h2>
  <div class="table-wrap">
    <table>
      <thead><tr><th>Module</th><th>Key</th><th>Checks</th><th>Free</th><th>Pro</th><th>Avg Time</th></tr></thead>
      <tbody>
        <tr><td><strong>SEO Audit</strong></td><td><code>seo</code></td><td>18 checks</td><td class="y">✓</td><td class="y">✓</td><td>~0.8s</td></tr>
        <tr><td><strong>Performance</strong></td><td><code>performance</code></td><td>12 checks</td><td class="y">✓</td><td class="y">✓</td><td>~1.4s</td></tr>
        <tr><td><strong>Security</strong></td><td><code>security</code></td><td>9 checks</td><td class="y">✓</td><td class="y">✓</td><td>~0.6s</td></tr>
        <tr><td><strong>Mobile UX</strong></td><td><code>mobile</code></td><td>7 checks</td><td class="y">✓</td><td class="y">✓</td><td>~0.9s</td></tr>
        <tr><td><strong>Schema Markup</strong></td><td><code>schema</code></td><td>6 checks</td><td class="y">✓</td><td class="y">✓</td><td>~0.5s</td></tr>
        <tr><td><strong>Accessibility</strong></td><td><code>accessibility</code></td><td>22 (WCAG 2.2)</td><td class="n">—</td><td class="y">✓</td><td>~1.1s</td></tr>
        <tr><td><strong>Link Audit</strong></td><td><code>links</code></td><td>5 checks</td><td class="n">—</td><td class="y">✓</td><td>~2.0s</td></tr>
        <tr><td><strong>Competitor</strong></td><td><code>competitor</code></td><td>Top 3 rivals</td><td class="n">—</td><td class="y">✓</td><td>~3.5s</td></tr>
        <tr><td><strong>AI Critique</strong></td><td><code>ai_critique</code></td><td>ORBOT LLM analysis</td><td class="n">—</td><td class="y">✓</td><td>~4.2s</td></tr>
      </tbody>
    </table>
  </div>
  <div class="callout info">
    <span class="callout-ico">ℹ️</span>
    <div class="callout-body">All modules can run simultaneously. Full scan with all 9 modules takes approximately <strong>8–12 seconds</strong> for a standard site.</div>
  </div>
</section>

<!-- 06 ORBOT -->
<section class="section" id="orbot">
  <div class="kicker">06 — ORBOT AI Agent</div>
  <h2>ORBOT<br><span class="out">AI AGENT</span></h2>
  <p>ORBOT is ORSCAN's built-in AI analyst. It reads your full scan report and answers questions in natural language — explaining issues, generating fix plans, rewriting your copy, and building prioritized roadmaps on demand.</p>
  <div class="callout warn">
    <span class="callout-ico">⚠️</span>
    <div class="callout-body"><strong>Premium feature.</strong> ORBOT is available on Pro ($19/mo) and above. Demo mode available in the web UI for free users.</div>
  </div>

  <h3>Capabilities</h3>
  <ul>
    <li><strong>Natural Language Q&A</strong> — Ask "Why is my SEO score low?" and get a specific, data-backed answer from your actual scan results.</li>
    <li><strong>Copy Rewriter</strong> — Request new meta descriptions, H1 tags, page headlines, or full copy rewrites optimized for keywords and conversion.</li>
    <li><strong>Fix Roadmap Generator</strong> — ORBOT creates a prioritized, time-estimated action plan for every issue found in your scan.</li>
    <li><strong>Competitor Breakdown</strong> — "How does my SEO compare to competitor X?" — get a detailed gap analysis with targeted recommendations.</li>
    <li><strong>API Integration</strong> — Feed ORBOT into your own pipeline. Compatible with OpenAI, Anthropic, Gemini, or any custom LLM backend.</li>
  </ul>

  <h3>Chat API Example</h3>
<pre><code><span class="cm">// Ask ORBOT about a specific scan result</span>
<span class="kw">const</span> <span class="vr">chat</span> <span class="op">=</span> <span class="kw">await</span> <span class="fn">fetch</span>(<span class="st">'https://api.orscan.io/v1/orbot/chat'</span>, {
  <span class="vr">method</span>: <span class="st">'POST'</span>,
  <span class="vr">headers</span>: { <span class="st">'Authorization'</span>: <span class="st">`Bearer ${</span><span class="vr">apiKey</span><span class="st">}`</span> },
  <span class="vr">body</span>: <span class="fn">JSON.stringify</span>({
    <span class="vr">scan_id</span>: <span class="st">'scan_k2m9x7dn4qfp'</span>,
    <span class="vr">message</span>: <span class="st">'What is the single biggest issue hurting my SEO right now?'</span>
  })
});
<span class="cm">// → { reply: "Your biggest issue is missing meta descriptions on 4 pages..." }</span><div class="code-lang">JS</div></code></pre>

  <h3>Connect Your Own LLM</h3>
<pre><code><span class="cm"># Use ORSCAN data with your own Anthropic/OpenAI integration</span>
<span class="vr">scan_data</span> <span class="op">=</span> orscan_client.<span class="fn">scan</span>(<span class="st">"https://yoursite.com"</span>)

<span class="vr">prompt</span> <span class="op">=</span> <span class="st">f"""
You are a website optimization expert.
Scan results: {scan_data}
Q: What is the highest-impact fix I should do first?
"""</span>
<span class="vr">response</span> <span class="op">=</span> anthropic.<span class="fn">messages.create</span>(
    <span class="vr">model</span><span class="op">=</span><span class="st">"claude-opus-4-5"</span>,
    <span class="vr">messages</span><span class="op">=</span>[{<span class="st">"role"</span>: <span class="st">"user"</span>, <span class="st">"content"</span>: <span class="vr">prompt</span>}]
)<div class="code-lang">PYTHON</div></code></pre>
</section>

<!-- 07 CONFIG -->
<section class="section" id="config">
  <div class="kicker">07 — Configuration</div>
  <h2>CONFIG &<br><span class="out">ENV VARS</span></h2>
  <p>Configuration is managed through environment variables. For self-hosted deployments, create a <code>.env</code> file in the project root.</p>

  <div class="env-t">
    <div class="env-hd">
      <div style="flex:1;min-width:260px">Variable</div>
      <div style="flex:1">Default / Example</div>
      <div style="width:90px;text-align:center">Required</div>
    </div>
    <div class="env-row"><div class="env-k">ORSCAN_API_KEY</div><div class="env-v">orsk_xxxxxxxxxxxxxxxxxx</div><div class="env-r r">Yes</div></div>
    <div class="env-row"><div class="env-k">ORSCAN_BASE_URL</div><div class="env-v">https://api.orscan.io/v1</div><div class="env-r">No</div></div>
    <div class="env-row"><div class="env-k">ORSCAN_TIMEOUT</div><div class="env-v">30000 (ms)</div><div class="env-r">No</div></div>
    <div class="env-row"><div class="env-k">ORSCAN_DEFAULT_MODULES</div><div class="env-v">seo,performance,security</div><div class="env-r">No</div></div>
    <div class="env-row"><div class="env-k">ORSCAN_WEBHOOK_SECRET</div><div class="env-v">whsec_xxxxxxxxxxxxxxxxxx</div><div class="env-r">No</div></div>
    <div class="env-row"><div class="env-k">ORBOT_ENABLED</div><div class="env-v">false</div><div class="env-r">No</div></div>
    <div class="env-row"><div class="env-k">ORBOT_LLM_PROVIDER</div><div class="env-v">anthropic | openai | custom</div><div class="env-r">No</div></div>
    <div class="env-row"><div class="env-k">ORBOT_LLM_API_KEY</div><div class="env-v">sk-xxxxxxxx</div><div class="env-r">No</div></div>
    <div class="env-row"><div class="env-k">SCAN_CRAWL_DEPTH</div><div class="env-v">3</div><div class="env-r">No</div></div>
    <div class="env-row"><div class="env-k">SCAN_MAX_PAGES</div><div class="env-v">100</div><div class="env-r">No</div></div>
  </div>

  <h3>Sample .env</h3>
<pre><code><span class="cm"># ORSCAN Configuration</span>
<span class="vr">ORSCAN_API_KEY</span><span class="op">=</span><span class="st">orsk_your_api_key_here</span>
<span class="vr">ORSCAN_TIMEOUT</span><span class="op">=</span><span class="nm">30000</span>
<span class="vr">SCAN_CRAWL_DEPTH</span><span class="op">=</span><span class="nm">3</span>
<span class="vr">SCAN_MAX_PAGES</span><span class="op">=</span><span class="nm">100</span>
<span class="vr">ORSCAN_DEFAULT_MODULES</span><span class="op">=</span><span class="st">seo,performance,security,mobile,schema</span>

<span class="cm"># ORBOT AI Agent (Premium)</span>
<span class="vr">ORBOT_ENABLED</span><span class="op">=</span><span class="kw">true</span>
<span class="vr">ORBOT_LLM_PROVIDER</span><span class="op">=</span><span class="st">anthropic</span>
<span class="vr">ORBOT_LLM_API_KEY</span><span class="op">=</span><span class="st">sk-ant-your-key-here</span>

<span class="cm"># Webhooks</span>
<span class="vr">ORSCAN_WEBHOOK_SECRET</span><span class="op">=</span><span class="st">whsec_your_webhook_secret</span><div class="code-lang">.ENV</div></code></pre>
</section>

<!-- 08 OUTPUT -->
<section class="section" id="output">
  <div class="kicker">08 — Output Format</div>
  <h2>OUTPUT<br><span class="out">FORMATS</span></h2>
  <p>ORSCAN supports multiple output formats depending on your use case and plan tier.</p>

  <div class="compare">
    <div class="cg cg-hd">Format</div>
    <div class="cg cg-hd">Free</div>
    <div class="cg cg-hd active">Pro</div>
    <div class="cg"><strong>JSON</strong> — Raw data via API</div><div class="cg cy">✓</div><div class="cg cy">✓</div>
    <div class="cg"><strong>HTML Report</strong> — Interactive web report</div><div class="cg cy">✓</div><div class="cg cy">✓</div>
    <div class="cg"><strong>PDF Export</strong> — Branded downloadable report</div><div class="cg cn">—</div><div class="cg cy">✓</div>
    <div class="cg"><strong>CSV Export</strong> — Issues in spreadsheet format</div><div class="cg cn">—</div><div class="cg cy">✓</div>
    <div class="cg"><strong>White-label PDF</strong> — Custom branding for agencies</div><div class="cg cn">—</div><div class="cg cy">✓</div>
    <div class="cg"><strong>Webhooks</strong> — Real-time POST to your endpoint</div><div class="cg cn">—</div><div class="cg cy">✓</div>
  </div>

  <h3>Export via API</h3>
<pre><code><span class="cm"># Export as PDF</span>
<span class="kw">curl</span> https://api.orscan.io/v1/scan/scan_k2m9x7dn4qfp/export \
  -H <span class="st">"Authorization: Bearer orsk_your_key"</span> \
  -G -d <span class="st">"format=pdf"</span> --output report.pdf

<span class="cm"># Export as CSV</span>
<span class="kw">curl</span> https://api.orscan.io/v1/scan/scan_k2m9x7dn4qfp/export \
  -H <span class="st">"Authorization: Bearer orsk_your_key"</span> \
  -G -d <span class="st">"format=csv"</span> --output issues.csv<div class="code-lang">BASH</div></code></pre>
</section>

<!-- 09 PRICING -->
<section class="section" id="pricing">
  <div class="kicker">09 — Pricing</div>
  <h2>PLANS &<br><span class="out">PRICING</span></h2>
  <div class="table-wrap">
    <table>
      <thead><tr><th>Feature</th><th>Free</th><th>Pro — $19/mo</th><th>Enterprise</th></tr></thead>
      <tbody>
        <tr><td>Scans per day</td><td>3</td><td class="y">Unlimited</td><td class="y">Unlimited</td></tr>
        <tr><td>Scan modules</td><td>5 modules</td><td class="y">All 12</td><td class="y">All 12 + custom</td></tr>
        <tr><td>API access</td><td class="n">—</td><td class="y">✓</td><td class="y">✓</td></tr>
        <tr><td>ORBOT AI Agent</td><td>Demo only</td><td class="y">Full access</td><td class="y">Custom model</td></tr>
        <tr><td>PDF export</td><td class="n">—</td><td class="y">✓</td><td class="y">White-label</td></tr>
        <tr><td>Webhooks</td><td class="n">—</td><td class="y">✓</td><td class="y">✓</td></tr>
        <tr><td>Competitor analysis</td><td class="n">—</td><td>Top 3 rivals</td><td class="y">Unlimited</td></tr>
        <tr><td>Rate limit</td><td>3/day</td><td>500/day</td><td>Custom</td></tr>
        <tr><td>Support</td><td>Community</td><td>Email priority</td><td>Dedicated SLA</td></tr>
        <tr><td>Uptime SLA</td><td class="n">—</td><td>99.5%</td><td>99.9%</td></tr>
      </tbody>
    </table>
  </div>
  <div class="callout tip">
    <span class="callout-ico">💳</span>
    <div class="callout-body"><strong>No credit card required</strong> for the free tier. Pro plan is billed monthly, cancel anytime. For team and agency pricing email <code>hello@orscan.io</code>.</div>
  </div>
</section>

<!-- 10 SELF-HOST -->
<section class="section" id="selfhost">
  <div class="kicker">10 — Self-Hosting</div>
  <h2>SELF<br><span class="out">HOSTING</span></h2>
  <p>ORSCAN can be self-hosted on your own infrastructure. The Docker image is available via GitHub Container Registry.</p>
  <div class="callout warn">
    <span class="callout-ico">⚠️</span>
    <div class="callout-body">Self-hosted instances require a valid license key. The free community license allows up to <strong>100 scans/month</strong>. Contact sales for production licenses.</div>
  </div>

  <h3>Docker</h3>
<pre><code><span class="cm"># Pull latest image</span>
docker pull ghcr.io/orscan/orscan:<span class="kw">latest</span>

<span class="cm"># Run</span>
docker run -d \
  --name orscan \
  -p <span class="nm">3000</span>:<span class="nm">3000</span> \
  -e ORSCAN_API_KEY<span class="op">=</span>orsk_your_key \
  -e ORBOT_ENABLED<span class="op">=</span><span class="kw">true</span> \
  -e ORBOT_LLM_API_KEY<span class="op">=</span>sk-ant-xxx \
  ghcr.io/orscan/orscan:<span class="kw">latest</span><div class="code-lang">BASH</div></code></pre>

  <h3>Docker Compose</h3>
<pre><code><span class="vr">version</span>: <span class="st">'3.9'</span>
<span class="vr">services</span>:
  <span class="vr">orscan</span>:
    <span class="vr">image</span>: ghcr.io/orscan/orscan:<span class="kw">latest</span>
    <span class="vr">ports</span>: [<span class="st">"3000:3000"</span>]
    <span class="vr">environment</span>:
      - ORSCAN_API_KEY<span class="op">=</span><span class="st">${ORSCAN_API_KEY}</span>
      - SCAN_CRAWL_DEPTH<span class="op">=</span><span class="nm">3</span>
      - ORBOT_ENABLED<span class="op">=</span><span class="kw">true</span>
      - ORBOT_LLM_PROVIDER<span class="op">=</span>anthropic
      - ORBOT_LLM_API_KEY<span class="op">=</span><span class="st">${ORBOT_LLM_API_KEY}</span>
    <span class="vr">volumes</span>: [orscan_data:/data]
    <span class="vr">restart</span>: unless-stopped
  <span class="vr">redis</span>:
    <span class="vr">image</span>: redis:7-alpine
    <span class="vr">restart</span>: unless-stopped
<span class="vr">volumes</span>:
  orscan_data:<div class="code-lang">YAML</div></code></pre>

  <h3>System Requirements</h3>
  <ul>
    <li><strong>CPU:</strong> 2+ vCPU recommended for concurrent scans</li>
    <li><strong>RAM:</strong> 2GB minimum, 4GB recommended</li>
    <li><strong>Storage:</strong> 10GB minimum for scan data and screenshots</li>
    <li><strong>Node.js:</strong> v20+ or Docker (recommended)</li>
    <li><strong>Redis:</strong> Required for scan queue and caching</li>
  </ul>
</section>

<!-- 11 CONTRIBUTING -->
<section class="section" id="contributing">
  <div class="kicker">11 — Contributing</div>
  <h2>CONTRI<span class="out">BUTING</span></h2>
  <p>Contributions are welcome. Please read these guidelines before opening a PR.</p>

  <div class="steps">
    <div class="step-item"><div class="step-num">01</div><div class="step-body"><div class="step-title">Fork & Clone</div><div class="step-desc"><code>git clone https://github.com/orscan/orscan.git && cd orscan</code></div></div></div>
    <div class="step-item"><div class="step-num">02</div><div class="step-body"><div class="step-title">Install Dependencies</div><div class="step-desc"><code>npm install</code> — requires Node.js v20+. Copy <code>.env.example</code> to <code>.env</code> and add your API key.</div></div></div>
    <div class="step-item"><div class="step-num">03</div><div class="step-body"><div class="step-title">Create a Branch</div><div class="step-desc"><code>git checkout -b feature/your-feature-name</code> — keep branches focused on a single change.</div></div></div>
    <div class="step-item"><div class="step-num">04</div><div class="step-body"><div class="step-title">Run Tests</div><div class="step-desc"><code>npm test</code> — all tests must pass. Add tests for any new module logic (80%+ coverage required).</div></div></div>
    <div class="step-item"><div class="step-num">05</div><div class="step-body"><div class="step-title">Open a Pull Request</div><div class="step-desc">Submit against the <code>main</code> branch with a clear description. Reference any related issues with <code>#issue_number</code>.</div></div></div>
  </div>

  <h3>Code Style</h3>
  <ul>
    <li>ESLint + Prettier enforced — run <code>npm run lint</code> before committing</li>
    <li>Commit messages follow Conventional Commits: <code>feat:</code> / <code>fix:</code> / <code>docs:</code> / <code>chore:</code></li>
    <li>New scan modules must include unit tests with at least 80% coverage</li>
    <li>Document any new environment variables in <code>README.md</code> and <code>.env.example</code></li>
  </ul>

  <div class="callout tip">
    <span class="callout-ico">⭐</span>
    <div class="callout-body">Found ORSCAN useful? <strong>Star the repo</strong> at <code>github.com/orscan/orscan</code> — it genuinely helps visibility and motivates the team.</div>
  </div>
</section>

<!-- 12 CHANGELOG -->
<section class="section" id="changelog">
  <div class="kicker">12 — Changelog</div>
  <h2>CHANGE<br><span class="out">LOG</span></h2>

  <div class="cl">
    <div class="cl-row">
      <div class="cl-v">v2.4</div>
      <div class="cl-d">Apr 2025</div>
      <div class="cl-b">
        <div class="cl-ttl">Current Stable Release</div>
        <div class="cl-items">
          <div class="cl-ch">ORBOT AI Agent v2 with multi-turn conversation context <span class="tag-new">New</span></div>
          <div class="cl-ch">Competitor analysis module — top 3 rival comparison</div>
          <div class="cl-ch">White-label PDF reports for agencies</div>
          <div class="cl-ch">Custom LLM provider support (OpenAI, Anthropic, Gemini)</div>
          <div class="cl-ch">Webhook HMAC-SHA256 signature verification</div>
        </div>
      </div>
    </div>
    <div class="cl-row">
      <div class="cl-v">v2.3</div>
      <div class="cl-d">Feb 2025</div>
      <div class="cl-b">
        <div class="cl-ttl">Accessibility & Performance</div>
        <div class="cl-items">
          <div class="cl-ch">Full WCAG 2.2 accessibility audit module <span class="tag-new">New</span></div>
          <div class="cl-ch">Core Web Vitals now uses live CrUX data from Google</div>
          <div class="cl-ch">API rate limit headers added to all responses</div>
          <div class="cl-ch">Fixed false positives in CSP header detection <span class="tag-fix">Fix</span></div>
        </div>
      </div>
    </div>
    <div class="cl-row">
      <div class="cl-v">v2.2</div>
      <div class="cl-d">Dec 2024</div>
      <div class="cl-b">
        <div class="cl-ttl">REST API & Webhooks</div>
        <div class="cl-items">
          <div class="cl-ch">REST API v1 public release <span class="tag-new">New</span></div>
          <div class="cl-ch">Webhook support with automatic retry logic (3 attempts)</div>
          <div class="cl-ch">CSV and JSON export endpoints</div>
          <div class="cl-ch">40% faster average scan time through engine optimisation</div>
        </div>
      </div>
    </div>
    <div class="cl-row">
      <div class="cl-v">v2.0</div>
      <div class="cl-d">Oct 2024</div>
      <div class="cl-b">
        <div class="cl-ttl">ORBOT First Release</div>
        <div class="cl-items">
          <div class="cl-ch">ORBOT AI Agent v1 — initial release <span class="tag-new">New</span></div>
          <div class="cl-ch">Dashboard redesign — warm soft interface</div>
          <div class="cl-ch">Pro plan launch at $19/month</div>
          <div class="cl-ch">Mobile web app (PWA)</div>
        </div>
      </div>
    </div>
    <div class="cl-row">
      <div class="cl-v">v1.0</div>
      <div class="cl-d">Jun 2024</div>
      <div class="cl-b">
        <div class="cl-ttl">Initial Public Launch</div>
        <div class="cl-items">
          <div class="cl-ch">Public launch — free tier with 5 scan modules <span class="tag-new">New</span></div>
          <div class="cl-ch">SEO, Performance, Security, Mobile, Schema modules live</div>
          <div class="cl-ch">50,000 websites scanned in first 30 days</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer class="readme-footer">
  <div class="ft-logo">
    <svg viewBox="0 0 22 22" fill="none">
      <circle cx="11" cy="11" r="8.5" stroke="#2c2a26" stroke-width="1.5"/>
      <circle cx="11" cy="11" r="3.5" fill="#2c2a26"/>
      <line x1="11" y1="0" x2="11" y2="2.5" stroke="#2c2a26" stroke-width="1.5"/>
      <line x1="11" y1="19.5" x2="11" y2="22" stroke="#2c2a26" stroke-width="1.5"/>
      <line x1="0" y1="11" x2="2.5" y2="11" stroke="#2c2a26" stroke-width="1.5"/>
      <line x1="19.5" y1="11" x2="22" y2="11" stroke="#2c2a26" stroke-width="1.5"/>
    </svg>
    <span class="ft-brand">ORSCAN</span>
  </div>
  <div class="ft-links">
    <a href="https://orscan.io">Website</a>
    <a href="https://docs.orscan.io">Docs</a>
    <a href="https://github.com/orscan/orscan">GitHub</a>
    <a href="https://status.orscan.io">Status</a>
    <a href="mailto:hello@orscan.io">Contact</a>
  </div>
  <span class="ft-copy">MIT License · © 2025 ORSCAN</span>
</footer>

</div><!-- /wrap -->

<script>
// ── COPY BUTTON (install block) ───────────────────────
function doCopy(btn) {
  const cmd = `curl -X POST https://api.orscan.io/v1/scan \\\n  -H "Content-Type: application/json" \\\n  -d '{"url":"https://yourwebsite.com"}'`;
  navigator.clipboard.writeText(cmd).then(() => {
    btn.textContent = 'Copied!';
    setTimeout(() => btn.textContent = 'Copy', 2000);
  });
}

// ── CODE BLOCK COPY BUTTONS ───────────────────────────
document.querySelectorAll('pre').forEach(pre => {
  const btn = document.createElement('button');
  btn.textContent = 'Copy';
  const hasLang = pre.querySelector('.code-lang');
  btn.style.cssText = `
    position:absolute;top:10px;right:${hasLang ? '72px' : '12px'};
    background:none;border:1px solid #5a5750;color:#8a8680;
    padding:3px 10px;font-family:'JetBrains Mono',monospace;
    font-size:9px;letter-spacing:2px;text-transform:uppercase;
    cursor:pointer;transition:all .15s;border-radius:3px;
  `;
  btn.addEventListener('mouseenter',() => {btn.style.color='#e8e4da';btn.style.borderColor='#9a9690'});
  btn.addEventListener('mouseleave',() => {btn.style.color='#8a8680';btn.style.borderColor='#5a5750'});
  btn.addEventListener('click', () => {
    const raw = pre.innerText
      .replace(/^Copy\n?/,'').replace(/Copy\n?$/,'')
      .replace(/[A-Z]{2,10}\n?$/,'').trim();
    navigator.clipboard.writeText(raw);
    btn.textContent = 'Copied!';
    btn.style.color = '#c8c4b8';
    setTimeout(() => { btn.textContent = 'Copy'; btn.style.color = '#8a8680'; }, 1800);
  });
  pre.appendChild(btn);
});

// ── ACTIVE NAV HIGHLIGHT ──────────────────────────────
const secs = document.querySelectorAll('.section, .hero');
const navAs = document.querySelectorAll('.tb-nav a');
const io = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting && e.target.id) {
      navAs.forEach(a => {
        const active = a.getAttribute('href') === '#' + e.target.id;
        a.style.color = active ? '#2c2a26' : '';
        a.style.fontWeight = active ? '600' : '';
      });
    }
  });
}, { rootMargin: '-30% 0px -60% 0px' });
secs.forEach(s => s.id && io.observe(s));

// ── SMOOTH SCROLL ─────────────────────────────────────
document.querySelectorAll('a[href^="#"]').forEach(a => {
  a.addEventListener('click', e => {
    const el = document.querySelector(a.getAttribute('href'));
    if (el) { e.preventDefault(); el.scrollIntoView({ behavior:'smooth', block:'start' }); }
  });
});

// ── SCROLL REVEAL ─────────────────────────────────────
const sr = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.style.opacity = '1';
      e.target.style.transform = 'translateY(0)';
      sr.unobserve(e.target);
    }
  });
}, { threshold: 0.06 });
document.querySelectorAll('.fc, .step-item, .cl-row, .endpoint').forEach(el => {
  el.style.cssText += 'opacity:0;transform:translateY(14px);transition:opacity .45s ease,transform .45s ease';
  sr.observe(el);
});
</script>
</body>
</html>
