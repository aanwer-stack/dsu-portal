[Index.html.html](https://github.com/user-attachments/files/26139746/Index.html.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>DHA Suffa University — Enrollment Portal</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;600;700&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
:root{
  --ink:#0b0e14;--ink2:#141920;--ink3:#1c2330;--ink4:#242e3d;
  --smoke:#f4f1ec;--smoke2:#ebe6de;--smoke3:#d8d0c4;
  --amber:#c8842a;--amber2:#e09b3a;--amber3:#f5c060;
  --sage:#3a7a6a;--sage2:#4d9980;--crimson:#c0392b;
  --ice:#4a90c4;
  --tx:#f0ece4;--tx2:#9aa4b4;--tx3:#5a6476;
  --bdr:rgba(255,255,255,0.07);--bdr2:rgba(255,255,255,0.12);
  --fh:'Cormorant Garamond',serif;--fb:'Outfit',sans-serif;
  --shadow:0 2px 12px rgba(0,0,0,0.4);
  --shadow2:0 8px 40px rgba(0,0,0,0.5);
}

html{scroll-behavior:smooth;}
body{font-family:var(--fb);background:var(--ink);color:var(--tx);font-size:14px;min-height:100vh;overflow-x:hidden;}

/* geometric bg pattern */
body::before{
  content:'';position:fixed;inset:0;pointer-events:none;z-index:0;
  background-image:
    linear-gradient(rgba(200,132,42,.03) 1px,transparent 1px),
    linear-gradient(90deg,rgba(200,132,42,.03) 1px,transparent 1px);
  background-size:48px 48px;
}

/* ── NAV ── */
nav{
  position:sticky;top:0;z-index:300;
  background:rgba(11,14,20,.94);
  backdrop-filter:blur(14px);
  border-bottom:1px solid var(--bdr);
}
.nav-inner{max-width:1280px;margin:0 auto;padding:0 28px;display:flex;align-items:center;height:64px;gap:6px;}
.nav-logo{display:flex;flex-direction:column;line-height:1;margin-right:8px;}
.nav-logo-main{font-family:var(--fh);font-size:22px;font-weight:700;color:var(--tx);letter-spacing:-.5px;}
.nav-logo-sub{font-size:9px;font-weight:500;letter-spacing:.2em;text-transform:uppercase;color:var(--amber);margin-top:1px;}
.nav-sep{width:1px;height:28px;background:var(--bdr2);margin:0 10px;}
.ntab{
  padding:7px 15px;border-radius:5px;border:none;background:none;
  color:var(--tx2);font-family:var(--fb);font-size:13px;font-weight:400;
  cursor:pointer;transition:all .15s;white-space:nowrap;letter-spacing:.01em;
}
.ntab:hover{color:var(--tx);background:rgba(255,255,255,.05);}
.ntab.active{color:var(--amber2);background:rgba(200,132,42,.1);border:1px solid rgba(200,132,42,.2);}
.nav-right{margin-left:auto;display:flex;align-items:center;gap:10px;}
.nav-badge{
  display:flex;align-items:center;gap:8px;
  padding:5px 12px;border-radius:20px;
  background:rgba(255,255,255,.04);border:1px solid var(--bdr2);
  cursor:pointer;
}
.nav-av{width:28px;height:28px;border-radius:50%;background:var(--amber);display:flex;align-items:center;justify-content:center;font-family:var(--fh);font-weight:700;font-size:12px;color:var(--ink);flex-shrink:0;}
.nav-av-name{font-size:12px;color:var(--tx2);}

/* ── PAGES ── */
.page{display:none;position:relative;z-index:1;}
.page.active{display:block;}
.page-inner{max-width:1280px;margin:0 auto;padding:36px 28px 60px;}

/* ── HERO ── */
.hero{
  position:relative;overflow:hidden;
  background:var(--ink2);
  border:1px solid var(--bdr);
  border-radius:16px;
  padding:64px 56px;
  margin-bottom:36px;
}
.hero-grid-lines{position:absolute;inset:0;pointer-events:none;
  background:repeating-linear-gradient(0deg,transparent,transparent 47px,rgba(200,132,42,.04) 48px),
             repeating-linear-gradient(90deg,transparent,transparent 47px,rgba(200,132,42,.04) 48px);}
.hero-accent{position:absolute;top:-80px;right:-80px;width:360px;height:360px;border-radius:50%;background:radial-gradient(circle,rgba(200,132,42,.12) 0%,transparent 70%);pointer-events:none;}
.hero-accent2{position:absolute;bottom:-60px;left:30%;width:240px;height:240px;border-radius:50%;background:radial-gradient(circle,rgba(58,122,106,.1) 0%,transparent 70%);pointer-events:none;}
.hero-eyebrow{display:inline-flex;align-items:center;gap:8px;margin-bottom:20px;font-size:11px;font-weight:500;letter-spacing:.18em;text-transform:uppercase;color:var(--amber2);}
.hero-eyebrow::before{content:'';width:24px;height:1px;background:var(--amber2);}
.hero h1{font-family:var(--fh);font-size:clamp(32px,5vw,58px);font-weight:700;color:var(--tx);line-height:1.15;margin-bottom:16px;max-width:680px;}
.hero h1 .hl{color:var(--amber2);position:relative;}
.hero h1 .hl::after{content:'';position:absolute;bottom:-2px;left:0;right:0;height:2px;background:var(--amber);opacity:.4;}
.hero-desc{font-size:15px;color:var(--tx2);line-height:1.75;max-width:520px;margin-bottom:32px;font-weight:300;}
.hero-ctas{display:flex;gap:12px;flex-wrap:wrap;}

/* ── BUTTONS ── */
.btn{display:inline-flex;align-items:center;gap:8px;padding:11px 24px;border-radius:7px;font-family:var(--fb);font-weight:500;font-size:13px;cursor:pointer;border:none;transition:all .18s;letter-spacing:.01em;}
.btn-amber{background:var(--amber);color:#fff;}
.btn-amber:hover{background:var(--amber2);transform:translateY(-1px);}
.btn-ghost{background:transparent;color:var(--tx2);border:1px solid var(--bdr2);}
.btn-ghost:hover{background:rgba(255,255,255,.05);color:var(--tx);}
.btn-sage{background:var(--sage);color:#fff;}
.btn-sage:hover{background:var(--sage2);}
.btn-crimson{background:var(--crimson);color:#fff;}
.btn-crimson:hover{opacity:.88;}
.btn-ice{background:var(--ice);color:#fff;}
.btn-ice:hover{opacity:.88;}
.btn-dark{background:var(--ink3);color:var(--tx2);border:1px solid var(--bdr);}
.btn-dark:hover{background:var(--ink4);color:var(--tx);}
.btn-sm{padding:7px 15px;font-size:12px;}
.btn-xs{padding:4px 11px;font-size:11px;border-radius:5px;}
.btn:disabled{opacity:.35;cursor:not-allowed;transform:none!important;}

/* ── STATS ROW ── */
.stats-row{display:grid;grid-template-columns:repeat(auto-fit,minmax(170px,1fr));gap:14px;margin-bottom:36px;}
.stat-card{
  background:var(--ink2);border:1px solid var(--bdr);border-radius:12px;
  padding:22px 20px;position:relative;overflow:hidden;
}
.stat-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:var(--amber);opacity:.5;}
.stat-num{font-family:var(--fh);font-size:36px;font-weight:700;color:var(--tx);line-height:1;}
.stat-lbl{font-size:11px;color:var(--tx3);margin-top:6px;font-weight:500;letter-spacing:.04em;text-transform:uppercase;}
.stat-pill{display:inline-block;font-size:10px;padding:2px 9px;border-radius:99px;margin-top:8px;font-weight:500;}
.pill-green{background:rgba(58,122,106,.2);color:#7ecbb8;border:1px solid rgba(58,122,106,.3);}
.pill-amber{background:rgba(200,132,42,.15);color:var(--amber3);border:1px solid rgba(200,132,42,.25);}
.pill-ice{background:rgba(74,144,196,.15);color:#7db8e0;border:1px solid rgba(74,144,196,.25);}
.pill-red{background:rgba(192,57,43,.15);color:#e87c6e;border:1px solid rgba(192,57,43,.25);}

/* ── SECTION HEADER ── */
.sec-hdr{display:flex;align-items:flex-end;justify-content:space-between;margin-bottom:22px;flex-wrap:wrap;gap:10px;}
.sec-title{font-family:var(--fh);font-size:26px;font-weight:700;color:var(--tx);}
.sec-sub{font-size:12px;color:var(--tx3);margin-top:3px;font-weight:300;}

/* ── CARD GRID ── */
.cards-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(310px,1fr));gap:18px;}

/* ── COURSE CARD ── */
.c-card{
  background:var(--ink2);border:1px solid var(--bdr);border-radius:12px;
  overflow:hidden;transition:border-color .2s,box-shadow .2s,transform .2s;
  display:flex;flex-direction:column;
}
.c-card:hover{border-color:var(--bdr2);box-shadow:var(--shadow);transform:translateY(-2px);}
.c-card-top{padding:18px 18px 14px;border-bottom:1px solid var(--bdr);}
.c-code{font-size:10px;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:var(--amber2);margin-bottom:5px;}
.c-title{font-family:var(--fh);font-size:17px;font-weight:600;color:var(--tx);line-height:1.3;}
.c-dept{font-size:11px;color:var(--tx3);margin-top:3px;}
.c-body{padding:14px 18px;flex:1;display:flex;flex-direction:column;gap:10px;}
.c-desc{font-size:12px;color:var(--tx2);line-height:1.65;font-weight:300;}
.c-tags{display:flex;gap:5px;flex-wrap:wrap;}
.c-tag{font-size:10px;padding:2px 9px;border-radius:99px;font-weight:500;}
.tag-cs{background:rgba(74,144,196,.15);color:#7db8e0;}
.tag-math{background:rgba(58,122,106,.15);color:#7ecbb8;}
.tag-biz{background:rgba(200,132,42,.15);color:var(--amber3);}
.tag-eng{background:rgba(192,57,43,.15);color:#e87c6e;}
.tag-sci{background:rgba(150,100,200,.15);color:#c4a0f0;}
.tag-mgmt{background:rgba(20,160,120,.15);color:#4ecba8;}
.tag-psych{background:rgba(220,80,160,.15);color:#f090cc;}
.prereq-row{display:flex;gap:4px;flex-wrap:wrap;align-items:center;}
.prereq-label{font-size:10px;color:var(--tx3);white-space:nowrap;}
.preq{font-size:10px;padding:2px 8px;border-radius:4px;font-weight:600;letter-spacing:.03em;}
.preq-unmet{background:rgba(192,57,43,.12);color:#e87c6e;border:1px solid rgba(192,57,43,.2);}
.preq-met{background:rgba(58,122,106,.15);color:#7ecbb8;border:1px solid rgba(58,122,106,.25);}
.preq-none{background:rgba(255,255,255,.04);color:var(--tx3);border:1px solid var(--bdr);}
.c-footer{padding:12px 18px;border-top:1px solid var(--bdr);display:flex;align-items:center;justify-content:space-between;gap:8px;}
.seats-wrap{display:flex;flex-direction:column;gap:4px;}
.seats-txt{font-size:11px;color:var(--tx3);}
.prog-bar{width:80px;height:4px;background:rgba(255,255,255,.08);border-radius:99px;overflow:hidden;}
.prog-fill{height:100%;border-radius:99px;transition:width .3s;}
.enr-status{display:inline-flex;align-items:center;gap:4px;font-size:10px;font-weight:600;padding:3px 9px;border-radius:99px;}
.s-open{background:rgba(58,122,106,.15);color:#7ecbb8;}
.s-full{background:rgba(192,57,43,.12);color:#e87c6e;}
.s-enrolled{background:rgba(74,144,196,.15);color:#7db8e0;}
.s-prereq{background:rgba(200,132,42,.12);color:var(--amber3);}

/* ── TABLE ── */
.tbl-wrap{background:var(--ink2);border:1px solid var(--bdr);border-radius:12px;overflow:hidden;}
table{width:100%;border-collapse:collapse;}
thead th{
  background:var(--ink3);color:var(--tx2);
  font-size:10px;font-weight:600;letter-spacing:.1em;text-transform:uppercase;
  padding:13px 16px;text-align:left;
}
tbody td{padding:13px 16px;border-bottom:1px solid var(--bdr);font-size:13px;color:var(--tx2);vertical-align:middle;}
tbody tr:last-child td{border-bottom:none;}
tbody tr:hover td{background:rgba(255,255,255,.02);}

/* ── FORM ── */
.form-shell{background:var(--ink2);border:1px solid var(--bdr);border-radius:16px;padding:32px 36px;}
.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;}
.f-full{grid-column:1/-1;}
.fg{display:flex;flex-direction:column;gap:7px;}
label{font-size:11px;font-weight:600;letter-spacing:.05em;text-transform:uppercase;color:var(--tx2);}
input,select,textarea{
  padding:11px 14px;border-radius:8px;
  background:var(--ink3);border:1px solid var(--bdr2);
  font-family:var(--fb);font-size:13px;color:var(--tx);
  width:100%;transition:border-color .15s,box-shadow .15s;
}
input:focus,select:focus,textarea:focus{outline:none;border-color:var(--amber);box-shadow:0 0 0 3px rgba(200,132,42,.12);}
input::placeholder,textarea::placeholder{color:var(--tx3);}
select option{background:var(--ink3);}
textarea{resize:vertical;min-height:80px;}
.f-hint{font-size:11px;color:var(--tx3);font-weight:300;}
.f-err{font-size:11px;color:#e87c6e;display:none;}
.f-err.show{display:block;}

/* ── INNER TABS ── */
.i-tabs{display:flex;gap:3px;background:var(--ink2);border:1px solid var(--bdr);border-radius:9px;padding:4px;width:fit-content;margin-bottom:28px;}
.i-tab{padding:7px 20px;border-radius:6px;border:none;background:none;font-family:var(--fb);font-size:13px;font-weight:400;color:var(--tx2);cursor:pointer;transition:all .15s;}
.i-tab:hover{color:var(--tx);}
.i-tab.active{background:var(--ink3);color:var(--amber2);border:1px solid rgba(200,132,42,.2);}

/* ── FILTER BAR ── */
.fbar{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:24px;}
.fbar input{max-width:240px;}
.fbar select{max-width:170px;}

/* ── MODAL ── */
.modal-bg{display:none;position:fixed;inset:0;background:rgba(0,0,0,.75);z-index:500;align-items:center;justify-content:center;padding:20px;backdrop-filter:blur(4px);}
.modal-bg.open{display:flex;}
.modal{background:var(--ink2);border:1px solid var(--bdr2);border-radius:16px;width:100%;max-width:560px;max-height:92vh;overflow-y:auto;box-shadow:var(--shadow2);}
.modal-hdr{padding:24px 24px 16px;border-bottom:1px solid var(--bdr);display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;background:var(--ink2);z-index:2;}
.modal-title{font-family:var(--fh);font-size:22px;font-weight:700;color:var(--tx);}
.modal-close{background:none;border:none;cursor:pointer;color:var(--tx3);font-size:22px;line-height:1;transition:color .15s;}
.modal-close:hover{color:var(--tx);}
.modal-body{padding:24px;}
.modal-footer{padding:16px 24px;border-top:1px solid var(--bdr);display:flex;gap:10px;justify-content:flex-end;position:sticky;bottom:0;background:var(--ink2);}

/* ── PREREQ TREE ── */
.ptree{background:var(--ink3);border:1px solid var(--bdr);border-radius:10px;padding:16px;}
.ptree-hdr{font-size:10px;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--tx3);margin-bottom:12px;}
.ptree-item{display:flex;align-items:center;gap:10px;padding:9px 12px;background:var(--ink2);border-radius:8px;border:1px solid var(--bdr);margin-bottom:6px;}
.ptree-item:last-child{margin-bottom:0;}
.pti-icon{width:26px;height:26px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;flex-shrink:0;font-weight:700;}
.pti-ok{background:rgba(58,122,106,.2);color:#7ecbb8;}
.pti-no{background:rgba(192,57,43,.15);color:#e87c6e;}
.pti-unk{background:rgba(255,255,255,.06);color:var(--tx3);}
.pti-code{font-size:12px;font-weight:600;color:var(--tx);}
.pti-name{font-size:11px;color:var(--tx3);font-weight:300;}
.pti-status{margin-left:auto;font-size:10px;font-weight:600;}

/* ── PROFILE CARD ── */
.profile-hero{
  background:var(--ink2);border:1px solid var(--bdr);border-radius:16px;
  padding:28px 32px;margin-bottom:28px;
  display:flex;align-items:center;gap:24px;flex-wrap:wrap;
  position:relative;overflow:hidden;
}
.profile-hero::before{content:'';position:absolute;right:-40px;top:-40px;width:200px;height:200px;border-radius:50%;background:radial-gradient(circle,rgba(200,132,42,.08) 0%,transparent 70%);}
.ph-av{width:72px;height:72px;border-radius:50%;background:var(--amber);display:flex;align-items:center;justify-content:center;font-family:var(--fh);font-size:26px;font-weight:700;color:var(--ink);flex-shrink:0;border:3px solid rgba(200,132,42,.3);}
.ph-name{font-family:var(--fh);font-size:26px;font-weight:700;color:var(--tx);}
.ph-meta{font-size:13px;color:var(--tx3);margin-top:4px;font-weight:300;}
.ph-chips{display:flex;gap:7px;flex-wrap:wrap;margin-top:12px;}
.ph-chip{font-size:11px;padding:4px 12px;border-radius:99px;background:rgba(255,255,255,.05);color:var(--tx2);border:1px solid var(--bdr2);}

/* ── ALERTS ── */
.alert{padding:12px 16px;border-radius:8px;font-size:13px;margin-bottom:16px;display:flex;align-items:flex-start;gap:10px;font-weight:300;}
.alert-i{background:rgba(74,144,196,.1);color:#7db8e0;border:1px solid rgba(74,144,196,.2);}
.alert-w{background:rgba(200,132,42,.1);color:var(--amber3);border:1px solid rgba(200,132,42,.2);}
.alert-e{background:rgba(192,57,43,.1);color:#e87c6e;border:1px solid rgba(192,57,43,.2);}
.alert-ok{background:rgba(58,122,106,.1);color:#7ecbb8;border:1px solid rgba(58,122,106,.2);}
.alert-ico{flex-shrink:0;font-size:15px;}

/* ── DIVIDER ── */
.divider{height:1px;background:var(--bdr);margin:24px 0;}

/* ── PROGRESS BAR ── */
.big-prog-wrap{background:rgba(255,255,255,.06);border-radius:99px;height:10px;overflow:hidden;}
.big-prog-fill{height:100%;border-radius:99px;background:var(--amber);transition:width .5s;}

/* ── EMPTY ── */
.empty-state{text-align:center;padding:70px 20px;}
.empty-ico{font-size:52px;margin-bottom:14px;opacity:.3;}
.empty-txt{font-size:15px;color:var(--tx3);font-weight:300;}

/* ── TOAST ── */
#toast{position:fixed;bottom:24px;right:24px;z-index:999;display:flex;flex-direction:column;gap:8px;pointer-events:none;}
.t-item{
  background:var(--ink3);color:var(--tx);
  padding:12px 18px;border-radius:10px;
  font-size:13px;box-shadow:var(--shadow2);
  display:flex;align-items:center;gap:10px;
  border-left:3px solid var(--sage);
  animation:tin .25s ease forwards;pointer-events:all;
  font-weight:400;
}
.t-err{border-left-color:var(--crimson);}
.t-ok{border-left-color:var(--sage);}
.t-warn{border-left-color:var(--amber);}
@keyframes tin{from{transform:translateX(110%);opacity:0;}to{transform:translateX(0);opacity:1;}}
@keyframes tout{to{transform:translateX(110%);opacity:0;}}

/* ── MISC ── */
.code-badge{font-size:10px;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--amber2);}
.check-grid{display:flex;flex-wrap:wrap;gap:7px;margin-top:8px;}
.check-label{display:flex;align-items:center;gap:6px;cursor:pointer;font-size:12px;font-weight:400;padding:5px 11px;background:var(--ink3);border-radius:6px;border:1px solid var(--bdr);color:var(--tx2);transition:border-color .15s;}
.check-label:hover{border-color:var(--bdr2);color:var(--tx);}
.check-label input{width:auto;padding:0;background:none;border:none;accent-color:var(--amber);}
.dept-badge{font-size:10px;padding:2px 9px;border-radius:99px;font-weight:500;}

/* ── MOBILE ── */
@media print{
  nav,#appRoot .i-tabs,#appRoot .btn,#toast,#appRoot input,#appRoot select,#appRoot button,#loginScreen{display:none!important;}
  body{background:#fff!important;color:#000!important;}
  .page{display:block!important;}
  #page-home,#page-courses,#page-enroll,#page-admin,#page-sessions,#page-teachers,#page-programs{display:none!important;}
  #page-portal{display:block!important;}
  #pt-transcript{display:block!important;}
  .profile-hero,.stat-card{background:#f5f5f5!important;color:#000!important;border:1px solid #ccc!important;}
  table th{background:#1a1a1a!important;color:#fff!important;}
}
@media(max-width:720px){
  .page-inner{padding:20px 16px 48px;}
  .hero{padding:36px 24px;}
  .form-grid{grid-template-columns:1fr;}
  .f-full{grid-column:1;}
  .form-shell{padding:22px 18px;}
  .nav-inner{padding:0 16px;}
  .ntab{padding:6px 10px;font-size:12px;}
  .cards-grid{grid-template-columns:1fr;}
  .stats-row{grid-template-columns:1fr 1fr;}
  .nav-av-name{display:none;}
  .hero h1{font-size:28px;}
}
/* ── LOGIN SCREEN ── */
#loginScreen{
  position:fixed;inset:0;z-index:9999;
  background:var(--ink);
  display:flex;align-items:center;justify-content:center;
  padding:20px;
}
#loginScreen::before{
  content:'';position:absolute;inset:0;pointer-events:none;
  background-image:linear-gradient(rgba(200,132,42,.04) 1px,transparent 1px),linear-gradient(90deg,rgba(200,132,42,.04) 1px,transparent 1px);
  background-size:48px 48px;
}
.login-box{
  background:var(--ink2);border:1px solid var(--bdr2);border-radius:20px;
  padding:44px 40px;width:100%;max-width:440px;
  box-shadow:0 24px 80px rgba(0,0,0,.6);
  position:relative;z-index:10001;isolation:isolate;
}
.login-logo{text-align:center;margin-bottom:32px;}
.login-logo-name{font-family:var(--fh);font-size:26px;font-weight:700;color:var(--tx);}
.login-logo-sub{font-size:10px;letter-spacing:.18em;text-transform:uppercase;color:var(--amber);margin-top:3px;}
.login-logo-seal{width:62px;height:62px;border-radius:50%;background:var(--amber);display:flex;align-items:center;justify-content:center;margin:0 auto 14px;font-family:var(--fh);font-size:24px;font-weight:700;color:var(--ink);border:3px solid rgba(200,132,42,.35);}
.role-tabs{display:grid;grid-template-columns:1fr 1fr 1fr;gap:6px;margin-bottom:28px;}
.role-tab{padding:11px 6px;border-radius:9px;border:1px solid var(--bdr2);background:none;color:var(--tx2);font-family:var(--fb);font-size:12px;cursor:pointer;transition:all .15s;text-align:center;user-select:none;-webkit-user-select:none;}
.role-tab:hover{background:var(--ink3);color:var(--tx);}
.role-tab.active{background:rgba(200,132,42,.12);color:var(--amber2);border-color:rgba(200,132,42,.3);}
.role-tab .role-icon{font-size:22px;display:block;margin-bottom:5px;pointer-events:none;}
.login-field{margin-bottom:16px;}
.login-field label{display:block;font-size:11px;font-weight:600;letter-spacing:.05em;text-transform:uppercase;color:var(--tx2);margin-bottom:6px;}
.login-field input{width:100%;padding:12px 14px;background:var(--ink3);border:1px solid var(--bdr2);border-radius:8px;color:var(--tx);font-family:var(--fb);font-size:14px;outline:none;transition:border-color .15s;}
.login-field input:focus{border-color:var(--amber);box-shadow:0 0 0 3px rgba(200,132,42,.1);}
.login-btn{width:100%;padding:13px;background:var(--amber);border:none;border-radius:8px;color:#fff;font-family:var(--fh);font-size:17px;font-weight:700;cursor:pointer;transition:all .18s;margin-top:8px;letter-spacing:.02em;}
.login-btn:hover{background:var(--amber2);transform:translateY(-1px);}
.login-hint{text-align:center;font-size:11px;color:var(--tx3);margin-top:16px;line-height:1.7;}
.login-err{background:rgba(192,57,43,.12);color:#e87c6e;border:1px solid rgba(192,57,43,.2);border-radius:7px;padding:10px 14px;font-size:12px;margin-bottom:14px;display:none;}
.demo-pills{display:flex;flex-wrap:wrap;gap:6px;justify-content:center;margin-top:10px;}
.demo-pill{font-size:10px;padding:3px 10px;border-radius:99px;background:var(--ink3);color:var(--tx2);border:1px solid var(--bdr);cursor:pointer;transition:all .12s;}
.demo-pill:hover{border-color:var(--amber);color:var(--amber2);}
/* ── ROLE-BASED NAV ── */
.nav-student,.nav-teacher,.nav-admin{display:none;}
body.role-student .nav-student{display:inline-flex;}
body.role-teacher .nav-teacher{display:inline-flex;}
body.role-admin .nav-admin{display:inline-flex;}
/* teacher dashboard */
.tstat{background:var(--ink2);border:1px solid var(--bdr);border-radius:12px;padding:20px 18px;position:relative;overflow:hidden;}
.tstat::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:var(--ice);}
.tstat-num{font-family:var(--fh);font-size:30px;font-weight:700;color:var(--tx);}
.tstat-lbl{font-size:11px;color:var(--tx3);margin-top:5px;text-transform:uppercase;letter-spacing:.04em;}
</style>
</head>
<body>

<!-- ══════════════ LOGIN SCREEN ══════════════ -->
<div id="loginScreen">
  <div class="login-box">
    <div class="login-logo">
      <div class="login-logo-seal">DSU</div>
      <div class="login-logo-name">DHA Suffa University</div>
      <div class="login-logo-sub">Enrollment Portal · Sign In</div>
    </div>
    <div class="role-tabs" id="loginRoleTabs">
      <div class="role-tab active" onclick="selectLoginRole('student',this)">
        <span class="role-icon">🎓</span>Student
      </div>
      <div class="role-tab" onclick="selectLoginRole('teacher',this)">
        <span class="role-icon">👨‍🏫</span>Faculty
      </div>
      <div class="role-tab" onclick="selectLoginRole('admin',this)">
        <span class="role-icon">⚙️</span>Admin
      </div>
    </div>
    <div class="login-err" id="loginErr">Invalid credentials. Please try again.</div>
    <div class="login-field">
      <label id="loginIdLabel">Student ID</label>
      <input type="text" id="loginId" placeholder="e.g. STU1001" autocomplete="username"/>
    </div>
    <div class="login-field">
      <label>Password</label>
      <input type="password" id="loginPwd" placeholder="Enter your password" autocomplete="current-password"/>
    </div>
    <div class="login-btn" onclick="doLogin()">Sign In →</div>
    <div class="login-hint">
      <strong style="color:var(--tx2);">Quick Sign-In</strong> · All passwords below auto-fill<br/>
      <div class="demo-pills">
        <span class="demo-pill" onclick="fillDemo('student','STU1001','student123')">🎓 Fatima Noor</span>
        <span class="demo-pill" onclick="fillDemo('student','STU1002','student123')">🎓 Bilal Ahmed</span>
        <span class="demo-pill" onclick="fillDemo('student','STU1003','student123')">🎓 Maham Siddiqui</span>
        <span class="demo-pill" onclick="fillDemo('teacher','TCH001','faculty123')">👨‍🏫 Dr. Sana Khalid</span>
        <span class="demo-pill" onclick="fillDemo('teacher','TCH003','faculty123')">👨‍🏫 Dr. Zafar Ali</span>
        <span class="demo-pill" onclick="fillDemo('admin','admin','admin123')">⚙️ Registrar</span>
      </div>
    </div>
  </div>
</div>

<!-- ══ MAIN APP (hidden until login) ══ -->
<div id="appRoot" style="display:none;">

<!-- NAV -->
<nav>
  <div class="nav-inner">
    <div class="nav-logo">
      <span class="nav-logo-main">DHA Suffa</span>
      <span class="nav-logo-sub">University</span>
    </div>
    <div class="nav-sep"></div>
    <!-- Public tabs (all roles) -->
    <button class="ntab active" onclick="goPage('home',this)">Home</button>
    <button class="ntab" onclick="goPage('courses',this)">Courses</button>
    <button class="ntab" onclick="goPage('programs',this)">Programs</button>
    <!-- Student only -->
    <button class="ntab nav-student" onclick="goPage('portal',this)">My Portal</button>
    <!-- Teacher only -->
    <button class="ntab nav-teacher" onclick="goPage('teacher-dash',this)">My Dashboard</button>
    <button class="ntab nav-teacher" onclick="goPage('teacher-results',this)">Enter Results</button>
    <!-- Admin only -->
    <button class="ntab nav-admin" onclick="goPage('sessions',this)">Sessions</button>
    <button class="ntab nav-admin" onclick="goPage('enroll',this)">Enroll</button>
    <button class="ntab nav-admin" onclick="goPage('teachers',this)">Faculty</button>
    <button class="ntab nav-admin" onclick="goPage('admin',this)">Admin</button>
    <div class="nav-right">
      <div class="nav-badge" id="navBadge">
        <div class="nav-av" id="navAv">?</div>
        <span class="nav-av-name" id="navName">Guest</span>
      </div>
      <button class="btn btn-dark" style="padding:5px 12px;font-size:12px;" onclick="doLogout()">Sign Out</button>
      <span id="saveBadge" style="font-size:10px;color:var(--tx3);white-space:nowrap;padding:0 4px;">Not saved</span>
      <button class="btn btn-dark" style="padding:4px 10px;font-size:11px;color:#e87c6e;" onclick="clearStorage()" title="Reset all data to demo defaults">🗑 Reset</button>
    </div>
  </div>
</nav>

<!-- TOAST -->
<div id="toast"></div>

<!-- ══════════════ HOME ══════════════ -->
<div class="page active" id="page-home">
  <div class="page-inner">
    <div class="hero">
      <div class="hero-grid-lines"></div>
      <div class="hero-accent"></div>
      <div class="hero-accent2"></div>
      <div class="hero-eyebrow">Spring 2025 Enrollment Open</div>
      <h1>DHA Suffa University<br/><span class="hl">Enrollment Portal</span></h1>
      <p class="hero-desc">Register as a student, explore our course catalogue, verify your prerequisites, and enroll for the semester — all from one intelligent portal.</p>
      <div class="hero-ctas">
        <button class="btn btn-amber" onclick="goPage('enroll',document.querySelectorAll('.ntab')[2])">Begin Enrollment →</button>
        <button class="btn btn-ghost" onclick="goPage('courses',document.querySelectorAll('.ntab')[1])">Browse Courses</button>
      </div>
    </div>
    <div class="stats-row" id="homeStats"></div>
    <div class="sec-hdr">
      <div><div class="sec-title">Featured Courses</div><div class="sec-sub">Highly enrolled courses this semester</div></div>
      <button class="btn btn-dark btn-sm" onclick="goPage('courses',document.querySelectorAll('.ntab')[1])">All Courses →</button>
    </div>
    <div class="cards-grid" id="featuredGrid"></div>
  </div>
</div>

<!-- ══════════════ ACADEMIC SESSIONS ══════════════ -->
<div class="page" id="page-sessions">
  <div class="page-inner">
    <div class="sec-hdr">
      <div><div class="sec-title">Academic Sessions</div><div class="sec-sub">Courses offered per semester — assign courses and faculty to each session</div></div>
      <button class="btn btn-sage btn-sm" onclick="openSessionModal()">+ New Session</button>
    </div>
    <div class="fbar">
      <select id="sessProgFilter" onchange="renderSessions()">
        <option value="">All Programs</option>
        <option>BBA — Business Administration (4-Year)</option>
        <option>BS-AF — Accounting & Finance (4-Year)</option>
        <option>BS-BAP — Business Administration & Policy (4-Year)</option>
        <option>BS (4-Year)</option>
      </select>
      <select id="sessSemFilter" onchange="renderSessions()">
        <option value="">All Semesters</option>
        <option value="1">Semester 1</option><option value="2">Semester 2</option>
        <option value="3">Semester 3</option><option value="4">Semester 4</option>
        <option value="5">Semester 5</option><option value="6">Semester 6</option>
        <option value="7">Semester 7</option><option value="8">Semester 8</option>
      </select>
      <select id="sessYearFilter" onchange="renderSessions()">
        <option value="">All Years</option>
        <option>2024</option><option>2025</option><option>2026</option>
      </select>
    </div>
    <div id="sessionsGrid"></div>
  </div>
</div>

<!-- ══════════════ FACULTY ══════════════ -->
<div class="page" id="page-teachers">
  <div class="page-inner">
    <div class="sec-hdr">
      <div><div class="sec-title">Faculty & Staff</div><div class="sec-sub">All faculty members at DHA Suffa University</div></div>
      <button class="btn btn-sage btn-sm" onclick="openTeacherModal()">+ Add Faculty</button>
    </div>
    <div class="fbar">
      <input type="text" id="teacherSearch" placeholder="Search by name or specialisation…" oninput="renderTeachers()"/>
      <select id="teacherDeptFilter" onchange="renderTeachers()">
        <option value="">All Departments</option>
        <option>Management Sciences</option><option>Computer Science</option>
        <option>Mathematics</option><option>Engineering</option>
        <option>Sciences</option><option>Psychology</option>
      </select>
      <select id="teacherRankFilter" onchange="renderTeachers()">
        <option value="">All Ranks</option>
        <option>Professor</option><option>Associate Professor</option>
        <option>Assistant Professor</option><option>Lecturer</option>
        <option>Visiting Faculty</option>
      </select>
    </div>
    <div class="cards-grid" id="teachersGrid"></div>
  </div>
</div>

<!-- ══════════════ PROGRAMS ══════════════ -->
<div class="page" id="page-programs">
  <div class="page-inner">
    <div class="sec-hdr">
      <div><div class="sec-title">Program Curriculum</div><div class="sec-sub">Complete semester-wise course structure for BBA, BS-AF and BS-BAP</div></div>
    </div>
    <div class="i-tabs" id="progTabs">
      <button class="i-tab active" onclick="showProgTab('bba',this)">BBA</button>
      <button class="i-tab" onclick="showProgTab('af',this)">BS-AF</button>
      <button class="i-tab" onclick="showProgTab('bap',this)">BS-BAP</button>
    </div>
    <div id="prog-bba"></div>
    <div id="prog-af" style="display:none;"></div>
    <div id="prog-bap" style="display:none;"></div>
  </div>
</div>

<!-- ══════════════ COURSES ══════════════ -->
<div class="page" id="page-courses">
  <div class="page-inner">
    <div class="sec-hdr"><div><div class="sec-title">Course Catalogue</div><div class="sec-sub">All courses with full prerequisite details</div></div></div>
    <div class="fbar">
      <input type="text" id="csearch" placeholder="Search by title or code…" oninput="renderCourses()"/>
      <select id="dfilter" onchange="renderCourses()">
        <option value="">All Departments</option>
        <option>Computer Science</option><option>Mathematics</option>
        <option>Business</option><option>Engineering</option><option>Sciences</option>
        <option>Management Sciences</option><option>Psychology</option>
      </select>
      <select id="lfilter" onchange="renderCourses()">
        <option value="">All Levels</option>
        <option value="1">100-Level</option><option value="2">200-Level</option>
        <option value="3">300-Level</option><option value="4">400-Level</option>
      </select>
    </div>
    <div class="cards-grid" id="courseGrid"></div>
  </div>
</div>

<!-- ══════════════ ENROLL ══════════════ -->
<div class="page" id="page-enroll">
  <div class="page-inner">
    <div class="i-tabs">
      <button class="i-tab active" onclick="showETab('register',this)">Register Student</button>
      <button class="i-tab" onclick="showETab('pick',this)">Enroll in Courses</button>
    </div>

    <!-- REGISTER -->
    <div id="et-register">
      <div class="sec-hdr"><div><div class="sec-title">Student Registration</div><div class="sec-sub">Create your student profile to begin enrolling</div></div></div>
      <div class="form-shell">
        <div class="form-grid">
          <div class="fg"><label>First Name *</label><input id="rFirst" placeholder="Ali"/><span class="f-err" id="er-first">Required</span></div>
          <div class="fg"><label>Last Name *</label><input id="rLast" placeholder="Khan"/><span class="f-err" id="er-last">Required</span></div>
          <div class="fg"><label>Email Address *</label><input type="email" id="rEmail" placeholder="you@email.com"/><span class="f-err" id="er-email">Valid email required</span></div>
          <div class="fg"><label>Phone</label><input type="tel" id="rPhone" placeholder="+92 300 0000000"/></div>
          <div class="fg"><label>Date of Birth *</label><input type="date" id="rDob"/><span class="f-err" id="er-dob">Required</span></div>
          <div class="fg"><label>Gender</label><select id="rGender"><option value="">Select…</option><option>Male</option><option>Female</option><option>Non-binary</option><option>Prefer not to say</option></select></div>
          <div class="fg"><label>Department *</label><select id="rDept"><option value="">Select…</option><option>Computer Science</option><option>Mathematics</option><option>Business</option><option>Engineering</option><option>Sciences</option><option>Management Sciences</option><option>Psychology</option></select><span class="f-err" id="er-dept">Required</span></div>
          <div class="fg"><label>Program</label><select id="rProg"><option value="">Select…</option><optgroup label="— Bachelor Programs (4-Year)"><option>BS (4-Year)</option><option>BS-AF — Accounting & Finance (4-Year)</option><option>BS-BAP — Business Administration & Policy (4-Year)</option><option>BBA — Business Administration (4-Year)</option></optgroup><optgroup label="— Bachelor Programs (2-Year)"><option>BS-AF — Accounting & Finance (2-Year)</option><option>BS-BAP — Business Administration & Policy (2-Year)</option><option>BBA — Business Administration (2-Year)</option></optgroup><optgroup label="— Postgraduate"><option>MS (2-Year)</option><option>MBA</option><option>PhD</option></optgroup><optgroup label="— Other"><option>Associate Degree</option></optgroup></select></div>
          <div class="fg f-full"><label>Home Address</label><textarea id="rAddr" placeholder="Street, City, Province…"></textarea></div>
          <div class="fg f-full">
            <label>Transfer Credits — Previously Completed Courses</label>
            <div class="f-hint">Tick any courses you have already passed. These will satisfy prerequisites.</div>
            <div class="check-grid" id="regCCGrid"></div>
          </div>
        </div>
        <div class="divider"></div>
        <div style="display:flex;justify-content:flex-end;gap:10px;">
          <button class="btn btn-dark" onclick="clearReg()">Clear</button>
          <button class="btn btn-amber" onclick="doRegister()">Register & Continue →</button>
        </div>
      </div>
    </div>

    <!-- PICK COURSES -->
    <div id="et-pick" style="display:none;">
      <div class="sec-hdr"><div><div class="sec-title">Course Enrollment</div><div class="sec-sub">Select a student then enroll them in courses</div></div></div>
      <div class="form-shell" style="margin-bottom:24px;">
        <div class="fg" style="max-width:380px;"><label>Select Student</label><select id="eStuSel" onchange="loadEnrollStudent()"><option value="">— choose —</option></select></div>
        <div id="eStuInfo" style="margin-top:16px;display:none;"></div>
      </div>
      <div id="eCourseWrap" style="display:none;">
        <div class="sec-hdr"><div class="sec-title" style="font-size:20px;">Available Courses</div></div>
        <div class="cards-grid" id="eCourseGrid"></div>
      </div>
    </div>
  </div>
</div>

<!-- ══════════════ STUDENT PORTAL ══════════════ -->
<div class="page" id="page-portal">
  <div class="page-inner">
    <div id="portalEmpty" class="empty-state">
      <div class="empty-ico">🎓</div>
      <div class="empty-txt">No active student session.<br/>Please sign in as a student.</div>
    </div>
    <div id="portalContent" style="display:none;">
      <div class="profile-hero" id="profileHero"></div>

      <!-- Quick action bar -->
      <div id="stuAlertBanner"></div>

      <div class="i-tabs" style="flex-wrap:wrap;">
        <button class="i-tab active" onclick="showPTab('enrolled',this)">📚 My Courses</button>
        <button class="i-tab" onclick="showPTab('enroll-self',this)">➕ Enroll</button>
        <button class="i-tab" onclick="showPTab('marks-entry',this)">📝 Enter Numbers</button>
        <button class="i-tab" onclick="showPTab('results',this)">📊 My Marks</button>
        <button class="i-tab" onclick="showPTab('completed',this)">✅ Completed</button>
        <button class="i-tab" onclick="showPTab('plan',this)">🗓 Study Plan</button>
        <button class="i-tab" onclick="showPTab('transcript',this)">📋 Transcript</button>
        <button class="i-tab" onclick="showPTab('progress',this)">📈 Progress</button>
      </div>

      <div id="pt-enrolled"></div>
      <div id="pt-enroll-self" style="display:none;"></div>
      <div id="pt-marks-entry" style="display:none;"></div>
      <div id="pt-results" style="display:none;"></div>
      <div id="pt-completed" style="display:none;"></div>
      <div id="pt-plan" style="display:none;"></div>
      <div id="pt-transcript" style="display:none;"></div>
      <div id="pt-progress" style="display:none;"></div>
    </div>
  </div>
</div>

<!-- ══════════════ ADMIN ══════════════ -->
<div class="page" id="page-admin">
  <div class="page-inner">
    <div class="i-tabs">
      <button class="i-tab active" onclick="showATab('students',this)">Students</button>
      <button class="i-tab" onclick="showATab('enrollments',this)">Enrollments</button>
      <button class="i-tab" onclick="showATab('results',this)">Enter Results</button>
      <button class="i-tab" onclick="showATab('overrides',this)">Overrides</button>
      <button class="i-tab" onclick="showATab('plans',this)">Plans of Study</button>
      <button class="i-tab" onclick="showATab('courses',this)">Manage Courses</button>
      <button class="i-tab" onclick="showATab('imports',this)">📥 Import / Export</button>
    </div>
    <div id="at-students">
      <div class="sec-hdr">
        <div class="sec-title">All Students</div>
        <input type="text" id="astu-search" placeholder="Search…" style="max-width:220px;" oninput="renderAdminStu()"/>
      </div>
      <div class="tbl-wrap"><table>
        <thead><tr><th>ID</th><th>Name</th><th>Department</th><th>Program</th><th>Enrolled</th><th>Completed</th><th>Actions</th></tr></thead>
        <tbody id="astu-body"></tbody>
      </table></div>
    </div>
    <div id="at-enrollments" style="display:none;">
      <div class="sec-hdr"><div class="sec-title">Active Enrollments</div></div>
      <div class="tbl-wrap"><table>
        <thead><tr><th>Student</th><th>Course</th><th>Code</th><th>Dept</th><th>Date</th><th>Status</th><th>Actions</th></tr></thead>
        <tbody id="aenr-body"></tbody>
      </table></div>
    </div>

    <div id="at-results" style="display:none;">
      <div class="sec-hdr"><div><div class="sec-title">Enter Exam Results</div><div class="sec-sub">Post grades for active enrollments. Failing a course blocks all forward dependent courses.</div></div></div>
      <div class="form-shell" style="margin-bottom:20px;">
        <div class="fg" style="max-width:380px;">
          <label>Select Student</label>
          <select id="resStudentSel" onchange="loadResultsForStudent()"><option value="">— choose student —</option></select>
        </div>
        <div id="resStudentBanner" style="margin-top:12px;display:none;"></div>
      </div>
      <div id="resTableWrap" style="display:none;">
        <div class="tbl-wrap"><table>
          <thead><tr><th>Course</th><th>Code</th><th>Credits</th><th style="color:#f5c060;">Sessional /40</th><th style="color:#7db8e0;">Midterm /20</th><th style="color:#7ecbb8;">Final /40</th><th>Total /100</th><th>Grade</th><th>Status</th><th>Action</th></tr></thead>
          <tbody id="res-body"></tbody>
        </table></div>
      </div>
    </div>

    <div id="at-overrides" style="display:none;">
      <div class="sec-hdr">
        <div><div class="sec-title">Admin Overrides</div><div class="sec-sub">Grant course load exceptions and allow enrollment in courses where prerequisites were failed</div></div>
      </div>

      <!-- Load Override -->
      <div class="form-shell" style="margin-bottom:20px;">
        <div style="font-family:var(--fh);font-size:18px;font-weight:700;margin-bottom:16px;color:var(--tx);">Course Load Override</div>
        <div class="alert alert-w" style="margin-bottom:16px;"><span class="alert-ico">ℹ</span>
          Hard cap: <strong>max 6 courses per semester</strong> for all students. Within that cap — <strong>CGPA &lt; 2.0 → 3 courses</strong> · <strong>2.0–2.49 → 5 courses</strong> · <strong>≥ 2.5 → 6 courses</strong>. Override raises the CGPA-based cap up to the hard limit of 6.
        </div>
        <div style="display:flex;gap:12px;flex-wrap:wrap;align-items:flex-end;">
          <div class="fg" style="min-width:220px;"><label>Student</label>
            <select id="ovLoadStu" onchange="renderOverrideStudentInfo()"><option value="">— select —</option></select>
          </div>
          <div class="fg" style="width:120px;"><label>Allow up to</label>
            <input type="number" id="ovLoadVal" min="1" max="12" value="6" placeholder="courses"/>
          </div>
          <button class="btn btn-amber btn-sm" onclick="grantLoadOverride()">Grant Override</button>
        </div>
        <div id="ovLoadInfo" style="margin-top:12px;"></div>
      </div>

      <!-- Course Override -->
      <div class="form-shell" style="margin-bottom:20px;">
        <div style="font-family:var(--fh);font-size:18px;font-weight:700;margin-bottom:16px;color:var(--tx);">Failed-Prerequisite Course Override</div>
        <div class="alert alert-e" style="margin-bottom:16px;"><span class="alert-ico">⛔</span>
          Normally students cannot enroll in a course if they failed one of its prerequisites. Use this to grant an exception for a specific student and course.
        </div>
        <div style="display:flex;gap:12px;flex-wrap:wrap;align-items:flex-end;">
          <div class="fg" style="min-width:220px;"><label>Student</label>
            <select id="ovCourseStu" onchange="loadOverrideCourses()"><option value="">— select —</option></select>
          </div>
          <div class="fg" style="min-width:240px;"><label>Course to Override</label>
            <select id="ovCourseId"><option value="">— select course —</option></select>
          </div>
          <button class="btn btn-crimson btn-sm" onclick="grantCourseOverride()">Grant Exception</button>
        </div>
        <div id="ovCourseInfo" style="margin-top:12px;"></div>
      </div>

      <!-- Active Overrides Table -->
      <div class="sec-hdr" style="margin-top:8px;"><div><div class="sec-title" style="font-size:18px;">Active Overrides</div></div></div>
      <div class="tbl-wrap"><table>
        <thead><tr><th>Student</th><th>Type</th><th>Detail</th><th>Granted On</th><th>Action</th></tr></thead>
        <tbody id="ov-body"></tbody>
      </table></div>
    </div>

    <div id="at-plans" style="display:none;">
      <div class="sec-hdr">
        <div><div class="sec-title">Plans of Study</div><div class="sec-sub">Assign or create semester-based course plans for students</div></div>
        <button class="btn btn-sage btn-sm" onclick="openPlanModal()">+ Create Plan</button>
      </div>
      <div class="tbl-wrap"><table>
        <thead><tr><th>Plan Name</th><th>Department</th><th>Program</th><th>Semesters</th><th>Total Credits</th><th>Assigned To</th><th>Actions</th></tr></thead>
        <tbody id="aplan-body"></tbody>
      </table></div>
    </div>
    <div id="at-courses" style="display:none;">
      <div class="sec-hdr">
        <div class="sec-title">Course Management</div>
        <button class="btn btn-sage btn-sm" onclick="openAddCourse()">+ Add Course</button>
      </div>
      <div class="tbl-wrap"><table>
        <thead><tr><th>Code</th><th>Title</th><th>Dept</th><th>Credits</th><th>Seats</th><th>Prerequisites</th><th>Actions</th></tr></thead>
        <tbody id="acrs-body"></tbody>
      </table></div>
    </div>

    <!-- ══ IMPORT / EXPORT TAB ══ -->
    <div id="at-imports" style="display:none;">
      <div class="sec-hdr"><div><div class="sec-title">Import & Export</div><div class="sec-sub">Upload Excel files to import data, or download templates and result sheets</div></div></div>

      <!-- ── 1. COURSE EXCEL UPLOAD ── -->
      <div class="form-shell" style="margin-bottom:24px;">
        <div style="font-family:var(--fh);font-size:20px;font-weight:700;margin-bottom:6px;">📊 Upload Courses from Excel</div>
        <div class="alert alert-i" style="margin-bottom:14px;"><span class="alert-ico">ℹ</span>
          Upload an Excel (.xlsx) file with columns: <strong>Code, Title, Department, Level, Credits, Seats, Instructor, Description, Prerequisites</strong>.
          Uploaded courses are automatically added to the course catalogue and offered in an auto-created Academic Session.
        </div>
        <div style="display:flex;gap:10px;flex-wrap:wrap;align-items:center;">
          <label class="btn btn-sage btn-sm" style="cursor:pointer;">
            📂 Choose Excel File
            <input type="file" id="excelCourseInput" accept=".xlsx,.xls,.csv" style="display:none;" onchange="importCoursesExcel(this)"/>
          </label>
          <button class="btn btn-dark btn-sm" onclick="downloadCourseTemplate()">⬇ Download Template</button>
        </div>
        <div id="excelCourseResult" style="margin-top:14px;"></div>
      </div>

      <!-- ── 2. FACULTY LIST EXCEL UPLOAD ── -->
      <div class="form-shell" style="margin-bottom:24px;">
        <div style="font-family:var(--fh);font-size:20px;font-weight:700;margin-bottom:6px;">👨‍🏫 Upload Faculty List from Excel</div>
        <div class="alert alert-i" style="margin-bottom:14px;"><span class="alert-ico">ℹ</span>
          Upload an Excel file with columns: <strong>Title, Name, Department, Rank, Specialisation, Email, Phone, Qualification, Courses</strong>.
          Existing faculty (matched by Email) will be updated; new records will be added.
        </div>
        <div style="display:flex;gap:10px;flex-wrap:wrap;align-items:center;">
          <label class="btn btn-sage btn-sm" style="cursor:pointer;">
            📂 Choose Excel File
            <input type="file" id="excelFacultyInput" accept=".xlsx,.xls,.csv" style="display:none;" onchange="importFacultyExcel(this)"/>
          </label>
          <button class="btn btn-dark btn-sm" onclick="downloadFacultyTemplate()">⬇ Download Template</button>
        </div>
        <div id="excelFacultyResult" style="margin-top:14px;"></div>
      </div>

      <!-- ── 3. FACULTY PHOTO UPLOAD ── -->
      <div class="form-shell" style="margin-bottom:24px;">
        <div style="font-family:var(--fh);font-size:20px;font-weight:700;margin-bottom:6px;">📷 Upload Faculty Photos</div>
        <div class="alert alert-i" style="margin-bottom:14px;"><span class="alert-ico">ℹ</span>
          Select a faculty member and upload their photo (JPG/PNG, max 2MB).
        </div>
        <div style="display:flex;gap:12px;flex-wrap:wrap;align-items:flex-end;">
          <div class="fg" style="min-width:260px;"><label>Select Faculty</label>
            <select id="photoFacultySelect"><option value="">— choose faculty —</option></select>
          </div>
          <label class="btn btn-amber btn-sm" style="cursor:pointer;">
            📷 Upload Photo
            <input type="file" id="facultyPhotoInput" accept="image/*" style="display:none;" onchange="uploadFacultyPhotoAdmin(this)"/>
          </label>
        </div>
        <div id="facultyPhotoPreviewWrap" style="margin-top:14px;display:none;">
          <img id="facultyPhotoPreviewImg" style="width:80px;height:80px;border-radius:50%;object-fit:cover;border:3px solid var(--amber);"/>
          <span style="font-size:12px;color:var(--tx2);margin-left:12px;vertical-align:middle;">Photo updated ✓</span>
        </div>
      </div>

      <!-- ── 4. PLAN OF STUDY EXCEL UPLOAD ── -->
      <div class="form-shell" style="margin-bottom:24px;">
        <div style="font-family:var(--fh);font-size:20px;font-weight:700;margin-bottom:6px;">🗓 Upload Plan of Study from Excel</div>
        <div class="alert alert-i" style="margin-bottom:14px;"><span class="alert-ico">ℹ</span>
          Upload an Excel file with columns: <strong>PlanID, PlanName, Department, Program, TotalCredits, Semester, CourseIDs</strong>.
          CourseIDs should be comma-separated within a cell (e.g. <em>MGT101,ACC101,FIN201</em>).
        </div>
        <div style="display:flex;gap:10px;flex-wrap:wrap;align-items:center;">
          <label class="btn btn-sage btn-sm" style="cursor:pointer;">
            📂 Choose Excel File
            <input type="file" id="excelPlanInput" accept=".xlsx,.xls,.csv" style="display:none;" onchange="importPlanExcel(this)"/>
          </label>
          <button class="btn btn-dark btn-sm" onclick="downloadPlanTemplate()">⬇ Download Template</button>
        </div>
        <div id="excelPlanResult" style="margin-top:14px;"></div>
      </div>

      <!-- ── 5. EXAM SHEET DOWNLOAD / RESULT UPLOAD ── -->
      <div class="form-shell" style="margin-bottom:24px;">
        <div style="font-family:var(--fh);font-size:20px;font-weight:700;margin-bottom:6px;">📋 Exam Sheet — Download & Upload Results</div>
        <div class="alert alert-i" style="margin-bottom:14px;"><span class="alert-ico">ℹ</span>
          Download a blank exam sheet for any course, fill in Sessional/Midterm/Final marks in Excel, then upload to post all results at once.
        </div>
        <div style="display:grid;gap:20px;grid-template-columns:1fr 1fr;">
          <!-- Download -->
          <div>
            <div style="font-weight:600;margin-bottom:10px;color:var(--tx2);">⬇ Download Blank Sheet</div>
            <div class="fg" style="margin-bottom:10px;"><label>Select Course</label>
              <select id="examSheetCourse"><option value="">— choose course —</option></select>
            </div>
            <button class="btn btn-amber btn-sm" onclick="downloadExamSheet()">⬇ Download Exam Sheet</button>
          </div>
          <!-- Upload -->
          <div>
            <div style="font-weight:600;margin-bottom:10px;color:var(--tx2);">⬆ Upload Filled Results</div>
            <div class="alert alert-w" style="margin-bottom:10px;font-size:11px;padding:8px 12px;"><span class="alert-ico">⚠</span>
              Columns required: <strong>StudentID, Sessional, Midterm, Final</strong>. Do not change the CourseID row.
            </div>
            <label class="btn btn-sage btn-sm" style="cursor:pointer;">
              📂 Upload Results Excel
              <input type="file" id="examResultUpload" accept=".xlsx,.xls,.csv" style="display:none;" onchange="importExamResults(this)"/>
            </label>
            <div id="examResultUploadStatus" style="margin-top:10px;"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ══════════════ TEACHER DASHBOARD ══════════════ -->
<div class="page" id="page-teacher-dash"></div>

<!-- ══════════════ TEACHER RESULTS ══════════════ -->
<div class="page" id="page-teacher-results"></div>

</div><!-- #appRoot -->

<!-- ══ COURSE DETAIL MODAL ══ -->
<div class="modal-bg" id="mCourse">
  <div class="modal">
    <div class="modal-hdr"><div class="modal-title" id="mCTitle">Course</div><button class="modal-close" onclick="closeM('mCourse')">✕</button></div>
    <div class="modal-body" id="mCBody"></div>
    <div class="modal-footer" id="mCFoot"></div>
  </div>
</div>

<!-- ══ ADD/EDIT COURSE MODAL ══ -->
<div class="modal-bg" id="mEdit">
  <div class="modal">
    <div class="modal-hdr"><div class="modal-title" id="mETitle">Add Course</div><button class="modal-close" onclick="closeM('mEdit')">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="fg"><label>Code *</label><input id="eCode" placeholder="e.g. CS401"/></div>
        <div class="fg"><label>Credits</label><input id="eCredits" type="number" min="1" max="6" value="3"/></div>
        <div class="fg f-full"><label>Title *</label><input id="eTitle" placeholder="Course name…"/></div>
        <div class="fg"><label>Department *</label><select id="eDept"><option value="">Select…</option><option>Computer Science</option><option>Mathematics</option><option>Business</option><option>Engineering</option><option>Sciences</option><option>Management Sciences</option><option>Psychology</option></select></div>
        <div class="fg"><label>Level</label><select id="eLevel"><option value="100">100-Level</option><option value="200">200-Level</option><option value="300">300-Level</option><option value="400">400-Level</option></select></div>
        <div class="fg"><label>Max Seats</label><input id="eSeats" type="number" value="30" min="5" max="300"/></div>
        <div class="fg"><label>Instructor</label><input id="eInstructor" placeholder="Dr. Name"/></div>
        <div class="fg f-full"><label>Description</label><textarea id="eDesc" placeholder="Brief description…"></textarea></div>
        <div class="fg f-full"><label>Prerequisites</label><div class="check-grid" id="ePrereqGrid"></div></div>
      </div>
    </div>
    <div class="modal-footer"><button class="btn btn-dark" onclick="closeM('mEdit')">Cancel</button><button class="btn btn-sage" onclick="saveCourse()">Save Course</button></div>
  </div>
</div>

<!-- ══ STUDENT MODAL ══ -->
<div class="modal-bg" id="mStu">
  <div class="modal">
    <div class="modal-hdr"><div class="modal-title">Student Details</div><button class="modal-close" onclick="closeM('mStu')">✕</button></div>
    <div class="modal-body" id="mStuBody"></div>
    <div class="modal-footer"><button class="btn btn-amber" id="mStuSetBtn">Set as Active</button><button class="btn btn-dark" onclick="closeM('mStu')">Close</button></div>
  </div>
</div>

<!-- ══ PLAN OF STUDY MODAL ══ -->
<!-- ══ SESSION MODAL ══ -->
<div class="modal-bg" id="mSession">
  <div class="modal" style="max-width:640px;">
    <div class="modal-hdr"><div class="modal-title" id="mSessTitle">Create Academic Session</div><button class="modal-close" onclick="closeM('mSession')">✕</button></div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="fg"><label>Session Title *</label><input id="sessTitle" placeholder="e.g. Fall 2025 — BBA Sem 1"/></div>
        <div class="fg"><label>Academic Year *</label><select id="sessYear"><option>2024</option><option selected>2025</option><option>2026</option></select></div>
        <div class="fg"><label>Term *</label><select id="sessTerm"><option>Fall</option><option>Spring</option><option>Summer</option></select></div>
        <div class="fg"><label>Semester No.</label><select id="sessSem"><option value="1">Semester 1</option><option value="2">Semester 2</option><option value="3">Semester 3</option><option value="4">Semester 4</option><option value="5">Semester 5</option><option value="6">Semester 6</option><option value="7">Semester 7</option><option value="8">Semester 8</option></select></div>
        <div class="fg f-full"><label>Program</label><select id="sessProg"><option value="">All / General</option><option>BBA — Business Administration (4-Year)</option><option>BS-AF — Accounting & Finance (4-Year)</option><option>BS-BAP — Business Administration & Policy (4-Year)</option><option>BS (4-Year)</option></select></div>
        <div class="fg"><label>Start Date</label><input type="date" id="sessStart"/></div>
        <div class="fg"><label>End Date</label><input type="date" id="sessEnd"/></div>
        <div class="fg f-full"><label>Offered Courses (select all)</label><div class="check-grid" id="sessCourseGrid" style="max-height:200px;overflow-y:auto;"></div></div>
        <div class="fg f-full"><label>Assigned Faculty (select)</label><div class="check-grid" id="sessFacultyGrid" style="max-height:140px;overflow-y:auto;"></div></div>
      </div>
    </div>
    <div class="modal-footer"><button class="btn btn-dark" onclick="closeM('mSession')">Cancel</button><button class="btn btn-sage" onclick="saveSession()">Save Session</button></div>
  </div>
</div>

<!-- ══ TEACHER MODAL ══ -->
<div class="modal-bg" id="mTeacher">
  <div class="modal" style="max-width:600px;">
    <div class="modal-hdr"><div class="modal-title" id="mTeachTitle">Add Faculty Member</div><button class="modal-close" onclick="closeM('mTeacher')">✕</button></div>
    <div class="modal-body">
      <div style="display:flex;justify-content:center;margin-bottom:18px;">
        <div style="position:relative;cursor:pointer;" onclick="document.getElementById('teacherPhotoInput').click()">
          <div id="teacherPhotoPreview" style="width:80px;height:80px;border-radius:50%;background:var(--amber);display:flex;align-items:center;justify-content:center;font-size:28px;color:var(--ink);border:2px solid rgba(200,132,42,.4);overflow:hidden;"></div>
          <div style="position:absolute;bottom:0;right:0;width:24px;height:24px;background:var(--amber);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:12px;">📷</div>
          <input type="file" id="teacherPhotoInput" accept="image/*" style="display:none;" onchange="previewTeacherPhoto(this)"/>
        </div>
      </div>
      <div class="form-grid">
        <div class="fg"><label>Title</label><select id="tTitle"><option>Dr.</option><option>Prof.</option><option>Mr.</option><option>Ms.</option><option>Mrs.</option><option>Engr.</option></select></div>
        <div class="fg"><label>Full Name *</label><input id="tName" placeholder="Full name"/></div>
        <div class="fg"><label>Department *</label><select id="tDept"><option value="">Select…</option><option>Management Sciences</option><option>Computer Science</option><option>Mathematics</option><option>Engineering</option><option>Sciences</option><option>Psychology</option></select></div>
        <div class="fg"><label>Rank *</label><select id="tRank"><option>Professor</option><option>Associate Professor</option><option>Assistant Professor</option><option>Lecturer</option><option>Visiting Faculty</option></select></div>
        <div class="fg"><label>Specialisation</label><input id="tSpec" placeholder="e.g. Finance, HRM, AI…"/></div>
        <div class="fg"><label>Email</label><input type="email" id="tEmail" placeholder="name@dsu.edu.pk"/></div>
        <div class="fg"><label>Phone</label><input type="tel" id="tPhone" placeholder="+92 300…"/></div>
        <div class="fg"><label>Qualification</label><input id="tQual" placeholder="e.g. PhD Finance — IBA Karachi"/></div>
        <div class="fg f-full"><label>Courses They Teach</label><div class="check-grid" id="tCoursesGrid" style="max-height:160px;overflow-y:auto;"></div></div>
      </div>
    </div>
    <div class="modal-footer"><button class="btn btn-dark" onclick="closeM('mTeacher')">Cancel</button><button class="btn btn-sage" onclick="saveTeacher()">Save Faculty</button></div>
  </div>
</div>
<div class="modal-bg" id="mPlan">
  <div class="modal" style="max-width:820px;">
    <div class="modal-hdr"><div class="modal-title" id="mPlanTitle">Create Plan of Study</div><button class="modal-close" onclick="closeM('mPlan')">✕</button></div>
    <div class="modal-body" style="padding-bottom:8px;">
      <div class="form-grid" style="margin-bottom:18px;">
        <div class="fg"><label>Plan Name *</label><input id="planName" placeholder="e.g. BBA 4-Year Plan"/></div>
        <div class="fg"><label>Department *</label><select id="planDept"><option value="">Select…</option><option>Computer Science</option><option>Mathematics</option><option>Business</option><option>Engineering</option><option>Sciences</option><option>Management Sciences</option><option>Psychology</option></select></div>
        <div class="fg f-full"><label>Program</label><select id="planProg"><option value="">Select…</option><option>BS (4-Year)</option><option>BS-AF — Accounting & Finance (4-Year)</option><option>BS-BAP — Business Administration & Policy (4-Year)</option><option>BBA — Business Administration (4-Year)</option><option>BS-AF — Accounting & Finance (2-Year)</option><option>BS-BAP — Business Administration & Policy (2-Year)</option><option>BBA — Business Administration (2-Year)</option><option>MS (2-Year)</option><option>MBA</option><option>PhD</option></select></div>
      </div>
      <div id="planSemestersWrap"></div>
      <div style="display:flex;gap:10px;margin-top:14px;">
        <button class="btn btn-dark btn-sm" onclick="addPlanSemester()">+ Add Semester</button>
      </div>
    </div>
    <div class="modal-footer"><button class="btn btn-dark" onclick="closeM('mPlan')">Cancel</button><button class="btn btn-sage" onclick="savePlan()">Save Plan</button></div>
  </div>
</div>

<!-- ══ VIEW PLAN MODAL ══ -->
<div class="modal-bg" id="mViewPlan">
  <div class="modal" style="max-width:700px;">
    <div class="modal-hdr"><div class="modal-title" id="mVPTitle">Plan of Study</div><button class="modal-close" onclick="closeM('mViewPlan')">✕</button></div>
    <div class="modal-body" id="mVPBody"></div>
    <div class="modal-footer">
      <label style="font-size:12px;text-transform:none;letter-spacing:0;">Assign to student:</label>
      <select id="assignStuSel" style="max-width:240px;padding:7px 10px;font-size:12px;"></select>
      <button class="btn btn-amber btn-sm" onclick="assignPlanToStudent()">Assign</button>
      <button class="btn btn-dark" onclick="closeM('mViewPlan')">Close</button>
    </div>
  </div>
</div>

<script>
// ══════════════════════════════════════
// STATE
// ══════════════════════════════════════
let courses=[
  {id:'CS101',title:'Introduction to Computing',dept:'Computer Science',level:100,credits:3,instructor:'Dr. Sarah Ahmed',desc:'Fundamentals of computing, algorithms, and problem-solving. No experience needed.',seats:40,enrolled:28,prereqs:[],tags:['Beginner','Core']},
  {id:'CS201',title:'Data Structures & Algorithms',dept:'Computer Science',level:200,credits:4,instructor:'Dr. Omar Raza',desc:'Arrays, linked lists, trees, graphs, sorting and searching with complexity analysis.',seats:35,enrolled:30,prereqs:['CS101'],tags:['Core','Required']},
  {id:'CS301',title:'Database Systems',dept:'Computer Science',level:300,credits:3,instructor:'Dr. Fatima Malik',desc:'Relational databases, SQL, normalization, transactions and NoSQL fundamentals.',seats:30,enrolled:22,prereqs:['CS201'],tags:['Core','Applied']},
  {id:'CS302',title:'Operating Systems',dept:'Computer Science',level:300,credits:4,instructor:'Dr. Bilal Shah',desc:'Process management, memory, file systems, concurrency, and OS internals.',seats:30,enrolled:30,prereqs:['CS201'],tags:['Core','Systems']},
  {id:'CS401',title:'Machine Learning',dept:'Computer Science',level:400,credits:4,instructor:'Dr. Zara Hussain',desc:'Supervised and unsupervised learning, neural networks, model evaluation and deployment.',seats:25,enrolled:20,prereqs:['CS201','MATH201'],tags:['Advanced','AI']},
  {id:'CS402',title:'Software Engineering',dept:'Computer Science',level:400,credits:3,instructor:'Prof. Kamran Ali',desc:'SDLC, design patterns, testing, agile methodologies and project management.',seats:28,enrolled:15,prereqs:['CS301'],tags:['Applied','Capstone']},
  {id:'MATH101',title:'Calculus I',dept:'Mathematics',level:100,credits:4,instructor:'Dr. Nadia Qureshi',desc:'Limits, derivatives, integrals and the fundamental theorem of calculus.',seats:50,enrolled:45,prereqs:[],tags:['Core','Required']},
  {id:'MATH201',title:'Linear Algebra',dept:'Mathematics',level:200,credits:3,instructor:'Dr. Hassan Mirza',desc:'Vectors, matrices, linear transformations, eigenvalues and eigenvectors.',seats:40,enrolled:32,prereqs:['MATH101'],tags:['Core','Applied']},
  {id:'MATH301',title:'Probability & Statistics',dept:'Mathematics',level:300,credits:3,instructor:'Dr. Aisha Baig',desc:'Probability theory, distributions, hypothesis testing and regression analysis.',seats:35,enrolled:28,prereqs:['MATH201'],tags:['Applied','Research']},
  {id:'BUS101',title:'Principles of Management',dept:'Business',level:100,credits:3,instructor:'Prof. Salma Iqbal',desc:'Fundamentals of organizational management, leadership and business strategy.',seats:60,enrolled:55,prereqs:[],tags:['Core','Required']},
  {id:'BUS201',title:'Financial Accounting',dept:'Business',level:200,credits:3,instructor:'Dr. Tariq Mehmood',desc:'Accounting cycle, financial statements, assets, liabilities and equity analysis.',seats:45,enrolled:38,prereqs:['BUS101'],tags:['Core','Finance']},
  {id:'BUS301',title:'Strategic Management',dept:'Business',level:300,credits:3,instructor:'Dr. Lubna Farooq',desc:'Competitive analysis, strategy formulation, implementation and evaluation.',seats:35,enrolled:20,prereqs:['BUS201'],tags:['Advanced','Capstone']},
  {id:'ENG101',title:'Engineering Fundamentals',dept:'Engineering',level:100,credits:4,instructor:'Dr. Imran Javed',desc:'Engineering principles, technical drawing, materials science and design thinking.',seats:45,enrolled:40,prereqs:[],tags:['Core','Required']},
  {id:'ENG201',title:'Circuit Theory',dept:'Engineering',level:200,credits:4,instructor:'Dr. Rabia Siddiqui',desc:'DC/AC circuits, Kirchhoff laws, network theorems and circuit analysis.',seats:35,enrolled:28,prereqs:['ENG101','MATH101'],tags:['Core','Electrical']},
  {id:'SCI101',title:'Physics I',dept:'Sciences',level:100,credits:4,instructor:'Dr. Mehreen Alam',desc:'Mechanics, thermodynamics, waves and classical physics fundamentals.',seats:55,enrolled:48,prereqs:[],tags:['Core','Required']},
  {id:'SCI201',title:'Chemistry II',dept:'Sciences',level:200,credits:3,instructor:'Dr. Farhan Idrees',desc:'Organic chemistry, reaction mechanisms, spectroscopy and biochemistry intro.',seats:40,enrolled:30,prereqs:['SCI101'],tags:['Core','Lab']},
  // Management Sciences
  {id:'MGT101',title:'Introduction to Management',dept:'Management Sciences',level:100,credits:3,instructor:'Dr. Sana Khalid',desc:'Foundations of management theory, organizational behaviour, planning and decision-making.',seats:60,enrolled:42,prereqs:[],tags:['Core','Required']},
  {id:'MGT201',title:'Organizational Behaviour',dept:'Management Sciences',level:200,credits:3,instructor:'Dr. Rizwan Ashraf',desc:'Individual and group behaviour in organizations, motivation, leadership styles and team dynamics.',seats:45,enrolled:35,prereqs:['MGT101'],tags:['Core','Applied']},
  {id:'MGT202',title:'Human Resource Management',dept:'Management Sciences',level:200,credits:3,instructor:'Ms. Nadia Farooq',desc:'Recruitment, training, performance appraisal, compensation and employee relations.',seats:40,enrolled:28,prereqs:['MGT101'],tags:['Core','HR']},
  {id:'MGT301',title:'Operations Management',dept:'Management Sciences',level:300,credits:3,instructor:'Dr. Usman Iqbal',desc:'Supply chain, production planning, quality management, inventory control and process optimization.',seats:35,enrolled:22,prereqs:['MGT201'],tags:['Applied','Operations']},
  {id:'MGT302',title:'Marketing Management',dept:'Management Sciences',level:300,credits:3,instructor:'Dr. Hina Baig',desc:'Market segmentation, consumer behaviour, branding, digital marketing and product strategy.',seats:38,enrolled:30,prereqs:['MGT201'],tags:['Applied','Marketing']},
  {id:'MGT401',title:'Strategic Leadership',dept:'Management Sciences',level:400,credits:3,instructor:'Prof. Asif Raza',desc:'Advanced leadership theories, change management, corporate governance and executive decision-making.',seats:30,enrolled:18,prereqs:['MGT301','MGT302'],tags:['Advanced','Capstone']},
  // Psychology
  {id:'PSY101',title:'Introduction to Psychology',dept:'Psychology',level:100,credits:3,instructor:'Dr. Maira Shaheen',desc:'Overview of psychological science — perception, cognition, emotion, personality, behaviour and mental health.',seats:55,enrolled:48,prereqs:[],tags:['Core','Required']},
  {id:'PSY201',title:'Developmental Psychology',dept:'Psychology',level:200,credits:3,instructor:'Dr. Amna Tariq',desc:'Human development across the lifespan — cognitive, emotional and social changes from infancy to old age.',seats:40,enrolled:32,prereqs:['PSY101'],tags:['Core','Lifespan']},
  {id:'PSY202',title:'Abnormal Psychology',dept:'Psychology',level:200,credits:3,instructor:'Dr. Kamran Yousuf',desc:'Classification, causes and treatment of psychological disorders including anxiety, mood and personality disorders.',seats:38,enrolled:29,prereqs:['PSY101'],tags:['Core','Clinical']},
  {id:'PSY301',title:'Cognitive Psychology',dept:'Psychology',level:300,credits:3,instructor:'Dr. Sadia Nawaz',desc:'Memory, attention, language, problem-solving and decision-making processes in the human mind.',seats:35,enrolled:24,prereqs:['PSY201'],tags:['Applied','Cognitive']},
  {id:'PSY302',title:'Social Psychology',dept:'Psychology',level:300,credits:3,instructor:'Dr. Farrukh Malik',desc:'Attitudes, group dynamics, conformity, prejudice, persuasion and interpersonal relationships.',seats:35,enrolled:20,prereqs:['PSY201'],tags:['Applied','Social']},
  {id:'PSY401',title:'Clinical Psychology & Counselling',dept:'Psychology',level:400,credits:4,instructor:'Dr. Rabia Zafar',desc:'Assessment techniques, therapeutic interventions, counselling ethics and practicum in clinical settings.',seats:25,enrolled:15,prereqs:['PSY202','PSY301'],tags:['Advanced','Clinical']},
  // ── BBA / AF / BAP shared core courses ──
  {id:'MGT403',title:'Business Research Methods',dept:'Management Sciences',level:400,credits:3,instructor:'Dr. Ayesha Naz',desc:'Research design, data collection, statistical analysis, and report writing for business research.',seats:35,enrolled:18,prereqs:['MGT201','MATH301'],tags:['Research','Core']},
  {id:'MGT404',title:'Entrepreneurship & Innovation',dept:'Management Sciences',level:400,credits:3,instructor:'Dr. Kamil Baig',desc:'Startup ecosystems, business model canvas, venture finance, and innovation frameworks.',seats:30,enrolled:14,prereqs:['MGT302'],tags:['Applied','Elective']},
  {id:'MGT303',title:'Business Communication',dept:'Management Sciences',level:300,credits:3,instructor:'Ms. Sara Javed',desc:'Professional writing, presentation skills, negotiation, and cross-cultural communication.',seats:40,enrolled:22,prereqs:['MGT101'],tags:['Core','Communication']},
  {id:'MGT304',title:'Business Ethics & Corporate Law',dept:'Management Sciences',level:300,credits:3,instructor:'Adv. Tariq Hussain',desc:'Legal frameworks, corporate governance, ethical decision-making, and CSR principles.',seats:38,enrolled:20,prereqs:['MGT201'],tags:['Core','Law']},
  {id:'MGT305',title:'Supply Chain Management',dept:'Management Sciences',level:300,credits:3,instructor:'Dr. Farid Baig',desc:'Logistics, procurement, inventory, demand forecasting, and global supply chain strategies.',seats:35,enrolled:16,prereqs:['MGT301'],tags:['Applied','Operations']},
  {id:'MGT402',title:'International Business',dept:'Management Sciences',level:400,credits:3,instructor:'Dr. Lubna Shah',desc:'Globalisation, trade theories, FDI, multinational strategy, and emerging market dynamics.',seats:30,enrolled:12,prereqs:['MGT302'],tags:['Advanced','Global']},
  {id:'MGT405',title:'Project Management',dept:'Management Sciences',level:400,credits:3,instructor:'Dr. Imtiaz Ahmed',desc:'Project lifecycle, scheduling, risk, resource management, Agile and PMP frameworks.',seats:32,enrolled:15,prereqs:['MGT301'],tags:['Applied','Core']},
  {id:'MGTI01',title:'Internship / Practicum',dept:'Management Sciences',level:400,credits:3,instructor:'Various',desc:'Supervised professional work experience in an approved organisation. Minimum 6 weeks.',seats:50,enrolled:10,prereqs:['MGT401'],tags:['Capstone','Required']},
  {id:'MGTC01',title:'Capstone Project',dept:'Management Sciences',level:400,credits:3,instructor:'Various',desc:'Integrative applied project solving a real-world business problem.',seats:40,enrolled:8,prereqs:['MGT401'],tags:['Capstone','Required']},
  // ── Accounting & Finance specific ──
  {id:'ACC101',title:'Introduction to Accounting',dept:'Management Sciences',level:100,credits:3,instructor:'Dr. Amna Qureshi',desc:'Basic accounting principles, journal entries, ledger, trial balance, and financial statements.',seats:50,enrolled:35,prereqs:[],tags:['Core','AF']},
  {id:'ACC201',title:'Cost & Management Accounting',dept:'Management Sciences',level:200,credits:3,instructor:'Dr. Naveed Iqbal',desc:'Job costing, process costing, standard costing, variance analysis, and budgetary control.',seats:40,enrolled:28,prereqs:['ACC101'],tags:['Core','AF']},
  {id:'ACC202',title:'Intermediate Accounting',dept:'Management Sciences',level:200,credits:3,instructor:'Dr. Rahat Khan',desc:'IFRS, revenue recognition, leases, financial instruments, and consolidated statements.',seats:38,enrolled:24,prereqs:['ACC101'],tags:['Core','AF']},
  {id:'ACC301',title:'Auditing & Assurance',dept:'Management Sciences',level:300,credits:3,instructor:'CA Sadia Mehmood',desc:'Audit standards, risk assessment, internal controls, and assurance engagements.',seats:35,enrolled:18,prereqs:['ACC202'],tags:['Core','AF']},
  {id:'ACC302',title:'Taxation',dept:'Management Sciences',level:300,credits:3,instructor:'Adv. Bilal Zahid',desc:'Income tax, sales tax, withholding tax, tax planning, and Pakistan tax law.',seats:35,enrolled:16,prereqs:['ACC201'],tags:['Applied','AF']},
  {id:'FIN201',title:'Financial Management',dept:'Management Sciences',level:200,credits:3,instructor:'Dr. Zafar Ali',desc:'Capital budgeting, cost of capital, working capital management, and dividend policy.',seats:42,enrolled:30,prereqs:['ACC101'],tags:['Core','AF']},
  {id:'FIN301',title:'Investment Analysis & Portfolio Mgmt',dept:'Management Sciences',level:300,credits:3,instructor:'Dr. Saima Rashid',desc:'Security analysis, portfolio theory, CAPM, derivatives, and equity valuation.',seats:35,enrolled:20,prereqs:['FIN201'],tags:['Advanced','AF']},
  {id:'FIN302',title:'Corporate Finance',dept:'Management Sciences',level:300,credits:3,instructor:'Dr. Khalid Mehmood',desc:'Capital structure, mergers & acquisitions, corporate restructuring, and financial distress.',seats:32,enrolled:18,prereqs:['FIN201'],tags:['Advanced','AF']},
  {id:'FIN401',title:'Islamic Banking & Finance',dept:'Management Sciences',level:400,credits:3,instructor:'Dr. Atif Rehman',desc:'Shariah-compliant products, sukuk, takaful, Islamic banking operations, and risk management.',seats:30,enrolled:12,prereqs:['FIN301'],tags:['Advanced','AF']},
  {id:'ACCI01',title:'AF Internship',dept:'Management Sciences',level:400,credits:3,instructor:'Various',desc:'Supervised professional work experience in an accounting or finance firm.',seats:50,enrolled:8,prereqs:['ACC301'],tags:['Capstone','Required']},
  {id:'ACCC01',title:'AF Capstone Project',dept:'Management Sciences',level:400,credits:3,instructor:'Various',desc:'Advanced applied finance or audit project submitted as a professional report.',seats:40,enrolled:6,prereqs:['FIN302'],tags:['Capstone','Required']},
  // ── BS-BAP (Business Administration & Policy) specific ──
  {id:'BAP101',title:'Introduction to Public Policy',dept:'Management Sciences',level:100,credits:3,instructor:'Dr. Rukhsana Malik',desc:'Policy process, actors, institutions, policy analysis frameworks, and governance models.',seats:45,enrolled:28,prereqs:[],tags:['Core','BAP']},
  {id:'BAP201',title:'Organisational Design & Theory',dept:'Management Sciences',level:200,credits:3,instructor:'Dr. Shahid Nawaz',desc:'Organisational structures, culture, institutional theory, and change management frameworks.',seats:38,enrolled:22,prereqs:['MGT201'],tags:['Core','BAP']},
  {id:'BAP202',title:'Quantitative Methods for Business',dept:'Management Sciences',level:200,credits:3,instructor:'Dr. Asif Rana',desc:'Descriptive statistics, regression, decision analysis, and linear programming for business.',seats:40,enrolled:25,prereqs:['MATH101'],tags:['Core','BAP']},
  {id:'BAP301',title:'Public Sector Management',dept:'Management Sciences',level:300,credits:3,instructor:'Dr. Muneeba Shah',desc:'Government structure, bureaucracy, public financial management, and e-governance.',seats:35,enrolled:18,prereqs:['BAP101','MGT201'],tags:['Applied','BAP']},
  {id:'BAP302',title:'Corporate Governance & Regulation',dept:'Management Sciences',level:300,credits:3,instructor:'Dr. Hamid Ullah',desc:'Board governance, SECP regulations, stakeholder management, and compliance frameworks.',seats:32,enrolled:16,prereqs:['MGT304'],tags:['Applied','BAP']},
  {id:'BAP303',title:'Economic Policy Analysis',dept:'Management Sciences',level:300,credits:3,instructor:'Dr. Faisal Iqbal',desc:'Macroeconomic policies, fiscal and monetary frameworks, trade policy, and economic modelling.',seats:35,enrolled:15,prereqs:['BAP202'],tags:['Advanced','BAP']},
  {id:'BAP401',title:'Strategic Policy & Planning',dept:'Management Sciences',level:400,credits:3,instructor:'Dr. Arshad Awan',desc:'Strategic planning processes, scenario analysis, balanced scorecard, and policy implementation.',seats:28,enrolled:10,prereqs:['BAP301','MGT401'],tags:['Capstone','BAP']},
  {id:'BAP402',title:'Leadership in Organisations',dept:'Management Sciences',level:400,credits:3,instructor:'Dr. Nadia Siddiqui',desc:'Transformational leadership, emotional intelligence, conflict resolution, and team dynamics.',seats:30,enrolled:12,prereqs:['MGT201'],tags:['Applied','BAP']},
  {id:'BAPI01',title:'BAP Internship',dept:'Management Sciences',level:400,credits:3,instructor:'Various',desc:'Policy or administrative work experience in a public or private sector organisation.',seats:50,enrolled:6,prereqs:['BAP301'],tags:['Capstone','Required']},
  {id:'BAPC01',title:'BAP Capstone Project',dept:'Management Sciences',level:400,credits:3,instructor:'Various',desc:'Policy research project on a current governance or business issue.',seats:40,enrolled:5,prereqs:['BAP401'],tags:['Capstone','Required']},
  // ── General / Elective ──
  {id:'GEN101',title:'Islamic Studies / Ethics',dept:'Management Sciences',level:100,credits:2,instructor:'Prof. Hafiz Zubair',desc:'Islamic values, ethics in professional life, and contemporary Muslim world issues.',seats:100,enrolled:60,prereqs:[],tags:['Required','General']},
  {id:'GEN102',title:'Pakistan Studies',dept:'Management Sciences',level:100,credits:2,instructor:'Prof. Naheed Alam',desc:'History, geography, culture, and contemporary issues of Pakistan.',seats:100,enrolled:55,prereqs:[],tags:['Required','General']},
  {id:'ENG001',title:'English Composition & Communication',dept:'Management Sciences',level:100,credits:3,instructor:'Ms. Rabia Farooq',desc:'Academic writing, grammar, critical reading, and oral communication skills.',seats:60,enrolled:40,prereqs:[],tags:['Required','General']},
  {id:'IT101',title:'Introduction to Information Technology',dept:'Management Sciences',level:100,credits:3,instructor:'Mr. Waqas Ali',desc:'Computer fundamentals, MS Office, internet tools, and basic data management.',seats:55,enrolled:38,prereqs:[],tags:['Required','General']},
  {id:'STAT101',title:'Business Statistics',dept:'Management Sciences',level:100,credits:3,instructor:'Dr. Rabia Siddiq',desc:'Descriptive statistics, probability, sampling, hypothesis testing, and regression basics.',seats:50,enrolled:34,prereqs:[],tags:['Core','General']},
  {id:'ECON101',title:'Principles of Economics',dept:'Management Sciences',level:100,credits:3,instructor:'Dr. Ahsan Raza',desc:'Micro and macroeconomic fundamentals — supply, demand, markets, GDP, inflation, and fiscal policy.',seats:55,enrolled:40,prereqs:[],tags:['Core','General']},
  {id:'ECON201',title:'Managerial Economics',dept:'Management Sciences',level:200,credits:3,instructor:'Dr. Sana Mirza',desc:'Demand estimation, cost analysis, pricing strategies, and game theory for managerial decisions.',seats:40,enrolled:25,prereqs:['ECON101'],tags:['Core','General']},
];

let students=[];
let enrollments=[];
let activeId=null;
let editingCid=null;
let examResults=[];
let studyPlans=[];
let editingPlanId=null;
let viewingPlanId=null;
// Admin overrides: {studentId, type:'load_override'|'course_override', value, courseId?, grantedBy, grantedOn}
let adminOverrides=[];

// Marking breakdown
const MAX_SESSIONAL=40, MAX_MIDTERM=20, MAX_FINAL=40;

// ── CGPA-based course load limits ──
// < 2.0  → max 3 courses (probation)
// 2.0–2.49 → max 5 courses (warning)
// ≥ 2.5  → max 6 courses (normal, hard cap per semester)
const MAX_COURSES_SEMESTER=6;
function getCourseLoadLimit(sid){
  const override=adminOverrides.find(o=>o.studentId===sid&&o.type==='load_override');
  if(override) return Math.min(override.value, MAX_COURSES_SEMESTER);
  const gpa=parseFloat(getGPA(sid));
  if(isNaN(gpa)) return MAX_COURSES_SEMESTER;
  if(gpa<2.0)  return 3;
  if(gpa<2.5)  return 5;
  return MAX_COURSES_SEMESTER;
}
function getLoadStatus(sid){
  const gpa=parseFloat(getGPA(sid));
  if(isNaN(gpa)) return null;
  if(gpa<2.0)  return {label:'Academic Probation',color:'#e87c6e',bg:'rgba(192,57,43,.12)',limit:3};
  if(gpa<2.5)  return {label:'Academic Warning',color:'#f5c060',bg:'rgba(200,132,42,.12)',limit:5};
  return null;
}
function getCurrentLoad(sid){
  return enrollments.filter(e=>e.studentId===sid&&e.status==='active').length;
}
// Check if a specific forward course is admin-overridden for a student
function hasCourseOverride(sid,cid){
  return adminOverrides.some(o=>o.studentId===sid&&o.type==='course_override'&&o.courseId===cid);
}

// Grade scale (out of 100)
const GRADE_SCALE=[
  {min:90,grade:'A+',gp:4.0},{min:85,grade:'A',gp:4.0},{min:80,grade:'A-',gp:3.7},
  {min:75,grade:'B+',gp:3.3},{min:70,grade:'B',gp:3.0},{min:65,grade:'B-',gp:2.7},
  {min:60,grade:'C+',gp:2.3},{min:55,grade:'C',gp:2.0},{min:50,grade:'C-',gp:1.7},
  {min:45,grade:'D+',gp:1.3},{min:40,grade:'D',gp:1.0},{min:0,grade:'F',gp:0.0}
];
function calcGrade(total){
  const m=Math.max(0,Math.min(100,Number(total)));
  return GRADE_SCALE.find(g=>m>=g.min)||GRADE_SCALE[GRADE_SCALE.length-1];
}
function getGPA(sid){
  // Use only the latest result per course that is a pass
  const seen={};
  examResults.filter(r=>r.studentId===sid).forEach(r=>{seen[r.courseId]=r;});
  const passing=Object.values(seen).filter(r=>r.status==='pass');
  if(!passing.length)return 'N/A';
  const totalWt=passing.reduce((a,r)=>{const c=courses.find(x=>x.id===r.courseId);return a+(c?c.credits*r.gp:0);},0);
  const totalCr=passing.reduce((a,r)=>{const c=courses.find(x=>x.id===r.courseId);return a+(c?c.credits:0);},0);
  return totalCr?(totalWt/totalCr).toFixed(2):'N/A';
}
// Check if a course is blocked for a student (failed a prerequisite and not yet retaken+passed)
function isCourseBlocked(sid,cid){
  const c=courses.find(x=>x.id===cid);if(!c||!c.prereqs.length)return false;
  return c.prereqs.some(p=>{
    const passed=hasCompleted(sid,p);
    const failed=examResults.some(r=>r.studentId===sid&&r.courseId===p&&r.status==='fail');
    return failed&&!passed;
  });
}

const DEPT_TAG={
  'Computer Science':'tag-cs','Mathematics':'tag-math',
  'Business':'tag-biz','Engineering':'tag-eng','Sciences':'tag-sci',
  'Management Sciences':'tag-mgmt','Psychology':'tag-psych'
};

// ══════════════════════════════════════
// NAV
// ══════════════════════════════════════
function goPage(name,btn){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.ntab').forEach(t=>t.classList.remove('active'));
  const pg=document.getElementById('page-'+name);
  if(pg)pg.classList.add('active');
  if(btn)btn.classList.add('active');
  const acts={
    home:renderHome,
    courses:renderCourses,
    portal:renderPortal,
    sessions:renderSessions,
    teachers:renderTeachers,
    programs:()=>renderProgram('bba'),
    admin:initAdminPage,
    enroll:()=>{
      populateStuSel();
      populateRegCC();
      // If admin, auto-set active student in selector
      if(currentUser&&currentUser.role==='admin'&&activeId){
        const sel=document.getElementById('eStuSel');
        if(sel){sel.value=activeId;loadEnrollStudent();}
      }
    }
  };
  if(acts[name])acts[name]();
}

function initAdminPage(){
  // Reset to Students tab as active
  ['students','enrollments','results','overrides','plans','courses','imports'].forEach(x=>{
    const el=document.getElementById('at-'+x);
    if(el)el.style.display='none';
  });
  const stuEl=document.getElementById('at-students');
  if(stuEl)stuEl.style.display='';
  // Reset tab button states
  document.querySelectorAll('#page-admin .i-tab').forEach((b,i)=>{
    b.classList.toggle('active',i===0);
  });
  // Render all data
  renderAdminStu();
  renderAdminEnr();
  renderAdminCrs();
  renderAdminPlans();
  populateResStuSel();
  initOverridesTab();
}

// ══════════════════════════════════════
// TAB HELPERS
// ══════════════════════════════════════
function showETab(t,btn){
  ['register','pick'].forEach(x=>document.getElementById('et-'+x).style.display='none');
  document.getElementById('et-'+t).style.display='';
  document.querySelectorAll('#page-enroll .i-tab').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  if(t==='pick')populateStuSel();
}
function showATab(t,btn){
  ['students','enrollments','results','overrides','plans','courses','imports'].forEach(x=>{
    const el=document.getElementById('at-'+x);
    if(el)el.style.display='none';
  });
  const target=document.getElementById('at-'+t);
  if(target)target.style.display='';
  document.querySelectorAll('#page-admin .i-tab').forEach(b=>b.classList.remove('active'));
  if(btn)btn.classList.add('active');
  if(t==='students')renderAdminStu();
  if(t==='enrollments')renderAdminEnr();
  if(t==='results'){populateResStuSel();document.getElementById('resStudentBanner').style.display='none';document.getElementById('resTableWrap').style.display='none';}
  if(t==='overrides')initOverridesTab();
  if(t==='plans')renderAdminPlans();
  if(t==='courses')renderAdminCrs();
  if(t==='imports')initImportsTab();
}
function showPTab(t,btn){
  ['enrolled','enroll-self','marks-entry','results','completed','plan','transcript','progress','contact'].forEach(x=>{const e=document.getElementById('pt-'+x);if(e)e.style.display='none';});
  const target=document.getElementById('pt-'+t);
  if(target)target.style.display='';
  document.querySelectorAll('#page-portal .i-tab').forEach(b=>b.classList.remove('active'));
  if(btn)btn.classList.add('active');
  renderPTab(t);
}

// ══════════════════════════════════════
// PREREQ LOGIC
// ══════════════════════════════════════
function hasCompleted(sid,cid){
  const s=students.find(x=>x.id===sid);if(!s)return false;
  // Check transfer credits
  if(s.completedCourses&&s.completedCourses.includes(cid))return true;
  // Check if passed via exam result (latest result for this course)
  const results=examResults.filter(r=>r.studentId===sid&&r.courseId===cid);
  if(results.length){
    // Must have at least one pass result AND the most recent must not be a fail
    return results.some(r=>r.status==='pass');
  }
  // Fallback: completed status in enrollments
  return enrollments.some(e=>e.studentId===sid&&e.courseId===cid&&e.status==='completed');
}
function checkPrereqs(sid,cid){
  const c=courses.find(x=>x.id===cid);if(!c)return false;
  return c.prereqs.every(p=>hasCompleted(sid,p));
}
function hasFailed(sid,cid){
  return examResults.some(r=>r.studentId===sid&&r.courseId===cid&&r.status==='fail')&&!hasCompleted(sid,cid);
}
// Returns list of failed courses not yet re-enrolled (strict block)
function getUnrepeatedFails(sid){
  const failedCids=[...new Set(examResults.filter(r=>r.studentId===sid&&r.status==='fail').map(r=>r.courseId))];
  return failedCids.filter(cid=>{
    if(hasCompleted(sid,cid)) return false; // passed on retry
    if(enrollments.some(e=>e.studentId===sid&&e.courseId===cid&&e.status==='active')) return false; // currently repeating
    return true; // failed and not re-enrolled yet
  });
}

// ══════════════════════════════════════
// COURSE CARD HTML
// ══════════════════════════════════════
function ccHTML(c,forEnroll=false,sid=null){
  const open=c.enrolled<c.seats;
  const pct=Math.round(c.enrolled/c.seats*100);
  const isEnrolled=sid?enrollments.some(e=>e.studentId===sid&&e.courseId===c.id&&e.status==='active'):false;
  const prereqOk=sid?checkPrereqs(sid,c.id):false;
  const completed=sid?hasCompleted(sid,c.id):false;
  const dTag=DEPT_TAG[c.dept]||'tag-cs';

  let statusHTML='';
  const failedPrereqs=sid?c.prereqs.filter(p=>hasFailed(sid,p)):[];
  const courseOverride=sid?hasCourseOverride(sid,c.id):false;
  const loadLimit=sid?getCourseLoadLimit(sid):6;
  const currentLoad=sid?getCurrentLoad(sid):0;
  const loadFull=sid&&!isEnrolled&&currentLoad>=loadLimit;
  const unrepeated=sid&&!isEnrolled?getUnrepeatedFails(sid):[];
  const blockedByFail=unrepeated.length>0&&!unrepeated.includes(c.id)&&!courseOverride;

  if(isEnrolled) statusHTML='<span class="enr-status s-enrolled">✓ Enrolled</span>';
  else if(completed) statusHTML='<span class="enr-status" style="background:rgba(58,122,106,.15);color:#7ecbb8;">✓ Done</span>';
  else if(!open) statusHTML='<span class="enr-status s-full">Full</span>';
  else if(sid&&failedPrereqs.length&&!courseOverride) statusHTML='<span class="enr-status s-prereq">⛔ Failed Prereq</span>';
  else if(sid&&blockedByFail) statusHTML='<span class="enr-status" style="background:rgba(192,57,43,.12);color:#e87c6e;">⚠ Repeat First</span>';
  else if(sid&&!prereqOk) statusHTML='<span class="enr-status s-prereq">Prereq ✕</span>';
  else if(loadFull) statusHTML=`<span class="enr-status" style="background:rgba(192,57,43,.12);color:#e87c6e;">Load Limit</span>`;
  else statusHTML='<span class="enr-status s-open">Open</span>';

  const prereqHTML=c.prereqs.length===0
    ?'<span class="preq preq-none">None</span>'
    :c.prereqs.map(p=>{
        const met=sid?hasCompleted(sid,p):false;
        return `<span class="preq ${sid?(met?'preq-met':'preq-unmet'):'preq-none'}">${p}</span>`;
      }).join('');

  const fillColor=pct>=90?'#c0392b':pct>=70?'#c8842a':'#3a7a6a';

  let actionBtns='<button class="btn btn-dark btn-xs" onclick="openCDetail(\''+c.id+'\')">Details</button>';
  const canEnrollNow=!completed&&open&&prereqOk&&!loadFull&&!(failedPrereqs.length&&!courseOverride)&&!blockedByFail;
  if(forEnroll&&sid){
    if(isEnrolled) actionBtns+=` <button class="btn btn-xs btn-crimson" onclick="doDrop('${c.id}')">Drop</button>`;
    else if(canEnrollNow) actionBtns+=` <button class="btn btn-xs btn-sage" onclick="doEnroll('${sid}','${c.id}')">Enroll</button>`;
  } else if(!forEnroll){
    if(activeId&&canEnrollNow) actionBtns+=` <button class="btn btn-xs btn-sage" onclick="quickEnroll('${c.id}')">Enroll</button>`;
    if(activeId&&isEnrolled) actionBtns+=` <button class="btn btn-xs btn-crimson" onclick="doDrop('${c.id}')">Drop</button>`;
  }

  return `<div class="c-card" style="${completed?'opacity:.55':''}">
    <div class="c-card-top">
      <div class="c-code">${c.id} · ${c.credits} Credits · Level ${c.level}</div>
      <div class="c-title">${c.title}</div>
      <div class="c-dept">${c.dept} — ${c.instructor}</div>
    </div>
    <div class="c-body">
      <div class="c-desc">${c.desc}</div>
      <div class="c-tags">${c.tags.map(t=>`<span class="c-tag ${dTag}">${t}</span>`).join('')}</div>
      <div class="prereq-row"><span class="prereq-label">Prerequisites:</span>${prereqHTML}</div>
    </div>
    <div class="c-footer">
      <div class="seats-wrap">
        <div class="seats-txt">${c.seats-c.enrolled} of ${c.seats} seats free</div>
        <div class="prog-bar"><div class="prog-fill" style="width:${pct}%;background:${fillColor};"></div></div>
      </div>
      <div style="display:flex;gap:6px;align-items:center;flex-wrap:wrap;">${statusHTML}${actionBtns}</div>
    </div>
  </div>`;
}

// ══════════════════════════════════════
// HOME
// ══════════════════════════════════════
function renderHome(){
  const ae=enrollments.filter(e=>e.status==='active').length;
  const openC=courses.filter(c=>c.enrolled<c.seats).length;
  document.getElementById('homeStats').innerHTML=`
    <div class="stat-card"><div class="stat-num">${courses.length}</div><div class="stat-lbl">Total Courses</div><span class="stat-pill pill-ice">Spring 2025</span></div>
    <div class="stat-card"><div class="stat-num">${students.length}</div><div class="stat-lbl">Students</div><span class="stat-pill pill-green">Registered</span></div>
    <div class="stat-card"><div class="stat-num">${ae}</div><div class="stat-lbl">Active Enrollments</div><span class="stat-pill pill-amber">This Semester</span></div>
    <div class="stat-card"><div class="stat-num">${openC}</div><div class="stat-lbl">Open Courses</div><span class="stat-pill pill-green">Available</span></div>
  `;
  const top=[...courses].sort((a,b)=>b.enrolled-a.enrolled).slice(0,3);
  document.getElementById('featuredGrid').innerHTML=top.map(c=>ccHTML(c)).join('');
}

// ══════════════════════════════════════
// COURSES
// ══════════════════════════════════════
function renderCourses(){
  const q=(document.getElementById('csearch')?.value||'').toLowerCase();
  const d=document.getElementById('dfilter')?.value||'';
  const l=document.getElementById('lfilter')?.value||'';
  let f=courses.filter(c=>{
    if(q&&!c.title.toLowerCase().includes(q)&&!c.id.toLowerCase().includes(q))return false;
    if(d&&c.dept!==d)return false;
    if(l&&!String(c.level).startsWith(l))return false;
    return true;
  });
  const g=document.getElementById('courseGrid');
  g.innerHTML=f.length?f.map(c=>ccHTML(c,false,activeId)).join(''):'<div class="empty-state"><div class="empty-ico">🔍</div><div class="empty-txt">No courses match your filters.</div></div>';
}

// ══════════════════════════════════════
// COURSE DETAIL MODAL
// ══════════════════════════════════════
function openCDetail(cid){
  const c=courses.find(x=>x.id===cid);if(!c)return;
  const open=c.enrolled<c.seats;
  const isEnrolled=activeId?enrollments.some(e=>e.studentId===activeId&&e.courseId===c.id&&e.status==='active'):false;
  const prereqOk=activeId?checkPrereqs(activeId,c.id):false;
  const failedPrereqs=activeId?c.prereqs.filter(p=>hasFailed(activeId,p)):[];
  const courseOverride=activeId?hasCourseOverride(activeId,c.id):false;
  const loadLimit=activeId?getCourseLoadLimit(activeId):7;
  const currentLoad=activeId?getCurrentLoad(activeId):0;
  const loadFull=activeId&&!isEnrolled&&currentLoad>=loadLimit;
  const st=activeId?getLoadStatus(activeId):null;
  const dTag=DEPT_TAG[c.dept]||'tag-cs';
  const pct=Math.round(c.enrolled/c.seats*100);

  let ptreeHTML=c.prereqs.length===0
    ?`<div class="ptree-item"><div class="pti-icon pti-ok">✓</div><div><div class="pti-code">None</div><div class="pti-name">No prerequisites required</div></div></div>`
    :c.prereqs.map(pid=>{
        const pc=courses.find(x=>x.id===pid);
        const met=activeId?hasCompleted(activeId,pid):null;
        const failed=activeId?hasFailed(activeId,pid):false;
        const cls=met===null?'pti-unk':met?'pti-ok':failed?'pti-no':'pti-no';
        const ico=met===null?'?':met?'✓':failed?'⛔':'✕';
        let stat='<span class="pti-status" style="color:var(--tx3)">Login to check</span>';
        if(met!==null) stat=met?'<span class="pti-status" style="color:#7ecbb8">Completed ✓</span>':failed?'<span class="pti-status" style="color:#e87c6e">Failed — repeat required</span>':'<span class="pti-status" style="color:#e87c6e">Not met ✕</span>';
        return `<div class="ptree-item"><div class="pti-icon ${cls}">${ico}</div><div><div class="pti-code">${pid}</div><div class="pti-name">${pc?pc.title:'Unknown course'}</div></div>${stat}</div>`;
      }).join('');

  document.getElementById('mCTitle').textContent=c.title;
  document.getElementById('mCBody').innerHTML=`
    <div style="display:flex;gap:6px;flex-wrap:wrap;margin-bottom:18px;">
      <span class="c-tag ${dTag}">${c.dept}</span>
      <span class="c-tag" style="background:rgba(200,132,42,.12);color:var(--amber3);">${c.credits} Credits</span>
      <span class="c-tag" style="background:rgba(255,255,255,.05);color:var(--tx2);">Level ${c.level}</span>
      ${open?'<span class="enr-status s-open">Open</span>':'<span class="enr-status s-full">Full</span>'}
    </div>
    <p style="font-size:14px;color:var(--tx2);line-height:1.75;margin-bottom:18px;font-weight:300;">${c.desc}</p>
    <div style="display:flex;gap:24px;flex-wrap:wrap;margin-bottom:18px;">
      <div><div style="font-size:10px;text-transform:uppercase;letter-spacing:.1em;color:var(--tx3);margin-bottom:3px;">Instructor</div><div style="font-weight:500;">${c.instructor}</div></div>
      <div><div style="font-size:10px;text-transform:uppercase;letter-spacing:.1em;color:var(--tx3);margin-bottom:3px;">Enrollment</div><div style="font-weight:500;">${c.enrolled} / ${c.seats} (${pct}%)</div></div>
      ${activeId?`<div><div style="font-size:10px;text-transform:uppercase;letter-spacing:.1em;color:var(--tx3);margin-bottom:3px;">Your Load</div><div style="font-weight:500;">${currentLoad} / ${loadLimit} courses</div></div>`:''}
    </div>
    <div class="ptree"><div class="ptree-hdr">Prerequisites</div>${ptreeHTML}</div>
    ${!open&&!isEnrolled?'<div class="alert alert-e" style="margin-top:14px;"><span class="alert-ico">⚠</span>This course is currently full.</div>':''}
    ${activeId&&failedPrereqs.length&&!courseOverride?`<div class="alert alert-e" style="margin-top:14px;"><span class="alert-ico">⛔</span><strong>Blocked:</strong> You failed prerequisite(s): <strong>${failedPrereqs.join(', ')}</strong>. You must repeat and pass ${failedPrereqs.length>1?'these courses':'this course'}, or request an admin override.</div>`:''}
    ${activeId&&failedPrereqs.length&&courseOverride?`<div class="alert alert-w" style="margin-top:14px;"><span class="alert-ico">✔</span>Admin override active — you may enroll despite failed prerequisite(s).</div>`:''}
    ${activeId&&!prereqOk&&!failedPrereqs.length&&!isEnrolled?'<div class="alert alert-w" style="margin-top:14px;"><span class="alert-ico">📋</span>You have not met all prerequisites for this course.</div>':''}
    ${loadFull&&!isEnrolled?`<div class="alert alert-e" style="margin-top:14px;"><span class="alert-ico">📊</span><strong>Course load limit reached</strong> (${currentLoad}/${loadLimit})${st?` — ${st.label}`:''}.${st?' Contact admin for a load override.':''}</div>`:''}
    ${isEnrolled?'<div class="alert alert-ok" style="margin-top:14px;"><span class="alert-ico">✓</span>You are currently enrolled in this course.</div>':''}
  `;
  const canE=activeId&&!isEnrolled&&open&&prereqOk&&!loadFull&&!(failedPrereqs.length&&!courseOverride);
  document.getElementById('mCFoot').innerHTML=`
    <button class="btn btn-dark" onclick="closeM('mCourse')">Close</button>
    ${canE?`<button class="btn btn-sage" onclick="quickEnroll('${c.id}');closeM('mCourse')">Enroll Now</button>`:''}
    ${isEnrolled?`<button class="btn btn-crimson" onclick="doDrop('${c.id}');closeM('mCourse')">Drop Course</button>`:''}
  `;
  openM('mCourse');
}

// ══════════════════════════════════════
// ENROLLMENT ACTIONS
// ══════════════════════════════════════
function quickEnroll(cid){
  if(!activeId){toast('Select a student first.','warn');return;}
  doEnroll(activeId,cid);
}

function doEnroll(sid,cid){
  const c=courses.find(x=>x.id===cid);if(!c)return;
  if(c.enrolled>=c.seats){toast('Course is full!','err');return;}
  if(enrollments.some(e=>e.studentId===sid&&e.courseId===cid&&e.status==='active')){toast('Already enrolled!','warn');return;}

  // ── Strict: must re-enroll in ALL failed courses before taking any new course ──
  const unrepeated=getUnrepeatedFails(sid);
  if(unrepeated.length>0){
    // Allow if the course being enrolled IS one of the failed courses (re-enrolling it)
    if(!unrepeated.includes(cid)){
      // Check admin override for this specific situation
      if(!hasCourseOverride(sid,cid)){
        toast(`Must re-enroll in failed course(s) first: ${unrepeated.join(', ')}. Complete those before taking new courses.`,'err');
        return;
      }
    }
  }

  // ── CGPA load limit check ──
  const limit=getCourseLoadLimit(sid);
  const current=getCurrentLoad(sid);
  if(current>=limit){
    const gpa=getGPA(sid);
    const st=getLoadStatus(sid);
    const override=adminOverrides.find(o=>o.studentId===sid&&o.type==='load_override');
    if(override){
      if(current>=override.value){toast(`Course limit reached (Admin override: ${override.value}).`,'err');return;}
    } else {
      toast(st?`${st.label}: max ${limit} courses allowed (CGPA ${gpa}).`:`Course load limit reached (${limit} courses).`,'err');return;
    }
  }

  // ── Failed prereq block check ──
  const failedPrereqs=c.prereqs.filter(p=>hasFailed(sid,p));
  if(failedPrereqs.length){
    if(!hasCourseOverride(sid,cid)){
      toast(`Blocked: failed prerequisite(s) ${failedPrereqs.join(', ')}. Admin override required.`,'err');return;
    }
  }

  // ── Normal prereq check ──
  if(!checkPrereqs(sid,cid)){
    const m=c.prereqs.filter(p=>!hasCompleted(sid,p));
    toast('Prerequisites not met: '+m.join(', '),'err');return;
  }

  enrollments.push({studentId:sid,courseId:cid,date:new Date().toLocaleDateString(),status:'active'});
  courses.find(x=>x.id===cid).enrolled++;
  toast(c.title+' — enrolled!','ok');
  refreshAll(sid);
}

function doDrop(cid){
  if(!activeId)return;
  const idx=enrollments.findIndex(e=>e.studentId===activeId&&e.courseId===cid&&e.status==='active');
  if(idx===-1)return;
  enrollments[idx].status='dropped';
  courses.find(x=>x.id===cid).enrolled--;
  toast('Course dropped.','warn');
  refreshAll(activeId);
}

function doMarkComplete(sid,cid){
  const idx=enrollments.findIndex(e=>e.studentId===sid&&e.courseId===cid&&e.status==='active');
  if(idx===-1)return;
  enrollments[idx].status='completed';
  courses.find(x=>x.id===cid).enrolled--;
  toast('Marked as completed!','ok');
  refreshAll(sid);
}

function doDropAdmin(sid,cid){
  const idx=enrollments.findIndex(e=>e.studentId===sid&&e.courseId===cid&&e.status==='active');
  if(idx===-1)return;
  enrollments[idx].status='dropped';
  courses.find(x=>x.id===cid).enrolled--;
  toast('Enrollment dropped.','warn');
  renderAdminEnr();renderHome();
}

function refreshAll(sid){
  renderHome();
  renderCourses();
  if(activeId===sid){renderPortal();}
  const sg=document.getElementById('selfEnrollGrid');
  if(sg&&sg.children.length)renderSelfEnroll();
  // Refresh admin tables if admin page is active
  const adminPage=document.getElementById('page-admin');
  if(adminPage&&adminPage.classList.contains('active')){
    renderAdminStu();
    renderAdminEnr();
    renderAdminCrs();
  }
  // Also refresh enroll tab student info if visible
  const eStuSel=document.getElementById('eStuSel');
  if(eStuSel&&eStuSel.value)loadEnrollStudent();
}

// ══════════════════════════════════════
// REGISTRATION
// ══════════════════════════════════════
function populateRegCC(){
  const g=document.getElementById('regCCGrid');if(!g)return;
  g.innerHTML=courses.map(c=>`<label class="check-label"><input type="checkbox" id="rcc_${c.id}"/><span>${c.id} — ${c.title}</span></label>`).join('');
}

function clearReg(){
  ['rFirst','rLast','rEmail','rPhone','rAddr'].forEach(id=>{const e=document.getElementById(id);if(e)e.value='';});
  ['rDob'].forEach(id=>{const e=document.getElementById(id);if(e)e.value='';});
  ['rGender','rDept','rProg'].forEach(id=>{const e=document.getElementById(id);if(e)e.selectedIndex=0;});
  document.querySelectorAll('[id^=rcc_]').forEach(c=>c.checked=false);
}

function doRegister(){
  const first=document.getElementById('rFirst').value.trim();
  const last=document.getElementById('rLast').value.trim();
  const email=document.getElementById('rEmail').value.trim();
  const dob=document.getElementById('rDob').value;
  const dept=document.getElementById('rDept').value;
  const showE=(id,v)=>{const e=document.getElementById(id);if(e)e.classList.toggle('show',v);};
  showE('er-first',!first);showE('er-last',!last);
  showE('er-email',!email||!/^[^@]+@[^@]+\.[^@]+$/.test(email));
  showE('er-dob',!dob);showE('er-dept',!dept);
  if(!first||!last||!email||!dob||!dept)return;
  const cc=courses.filter(c=>document.getElementById('rcc_'+c.id)?.checked).map(c=>c.id);
  const id='STU'+String(students.length+1001);
  students.push({id,firstName:first,lastName:last,email,
    phone:document.getElementById('rPhone').value,
    dob,gender:document.getElementById('rGender').value,
    dept,program:document.getElementById('rProg').value,
    address:document.getElementById('rAddr').value,
    completedCourses:cc,
    registeredOn:new Date().toLocaleDateString()
  });
  activeId=id;
  updateNavAv(students[students.length-1]);
  toast(`Welcome ${first}! ID: ${id}`,'ok');
  clearReg();
  renderHome();renderAdminStu();
  goPage('portal',document.querySelectorAll('.ntab')[3]);
}

function updateNavAv(s){
  document.getElementById('navAv').textContent=(s.firstName[0]+s.lastName[0]).toUpperCase();
  document.getElementById('navName').textContent=s.firstName+' '+s.lastName;
}

// ══════════════════════════════════════
// ENROLL TAB
// ══════════════════════════════════════
function populateStuSel(){
  const sel=document.getElementById('eStuSel');if(!sel)return;
  sel.innerHTML='<option value="">— choose —</option>'+students.map(s=>`<option value="${s.id}">${s.id} — ${s.firstName} ${s.lastName}</option>`).join('');
  if(activeId){sel.value=activeId;loadEnrollStudent();}
}

function loadEnrollStudent(){
  const sid=document.getElementById('eStuSel').value;
  const info=document.getElementById('eStuInfo');
  const wrap=document.getElementById('eCourseWrap');
  const grid=document.getElementById('eCourseGrid');
  if(!sid){info.style.display='none';wrap.style.display='none';return;}
  const s=students.find(x=>x.id===sid);if(!s)return;
  activeId=sid;updateNavAv(s);
  const me=enrollments.filter(e=>e.studentId===sid&&e.status==='active').length;
  const mc=(s.completedCourses?.length||0)+enrollments.filter(e=>e.studentId===sid&&e.status==='completed').length;
  const gpa=getGPA(sid);
  const limit=getCourseLoadLimit(sid);
  const st=getLoadStatus(sid);
  const loadOverride=adminOverrides.find(o=>o.studentId===sid&&o.type==='load_override');
  info.style.display='';
  let banners=`<div class="alert alert-i"><span class="alert-ico">ℹ</span>
    <strong>${s.firstName} ${s.lastName}</strong> · ${s.id} · ${s.dept} · CGPA: <strong>${gpa}</strong> · ${me} enrolled · ${mc} completed · Load limit: <strong>${me}/${limit}</strong>
  </div>`;
  if(st) banners+=`<div class="alert" style="background:${st.bg};color:${st.color};border:1px solid ${st.color}33;"><span class="alert-ico">⚠</span>
    <strong>${st.label}</strong> — CGPA ${gpa} restricts this student to max <strong>${st.limit} courses</strong> per semester.
    ${loadOverride?`<span style="margin-left:8px;font-size:11px;opacity:.8;">Admin override: ${loadOverride.value} courses granted.</span>`:''}
  </div>`;
  const failedAny=examResults.filter(r=>r.studentId===sid&&r.status==='fail'&&!hasCompleted(sid,r.courseId));
  const unrepeated=getUnrepeatedFails(sid);
  if(failedAny.length) banners+=`<div class="alert alert-e"><span class="alert-ico">⛔</span>
    <strong>Failed courses blocking advancement:</strong> ${failedAny.map(r=>r.courseId).join(', ')} — Admin must grant per-course override to allow enrollment in dependent courses.
  </div>`;
  if(unrepeated.length) banners+=`<div class="alert alert-e"><span class="alert-ico">⚠</span>
    <strong>Must re-enroll first:</strong> You have ${unrepeated.length} failed course(s) not yet repeated: <strong>${unrepeated.join(', ')}</strong>. You cannot enroll in any new course until you re-enroll in ${unrepeated.length===1?'it':'them'}.
  </div>`;
  info.innerHTML=banners;
  wrap.style.display='';
  grid.innerHTML=courses.map(c=>ccHTML(c,true,sid)).join('');
}

// ══════════════════════════════════════
// PORTAL
// ══════════════════════════════════════
function renderPortal(){
  const empty=document.getElementById('portalEmpty');
  const content=document.getElementById('portalContent');
  if(!activeId||!students.find(x=>x.id===activeId)){empty.style.display='';content.style.display='none';return;}
  const s=students.find(x=>x.id===activeId);
  empty.style.display='none';content.style.display='';
  const ini=(s.firstName[0]+s.lastName[0]).toUpperCase();
  const me=enrollments.filter(e=>e.studentId===s.id&&e.status==='active').length;
  const allC=[...(s.completedCourses||[]),...examResults.filter(r=>r.studentId===s.id&&r.status==='pass').map(r=>r.courseId),...enrollments.filter(e=>e.studentId===s.id&&e.status==='completed').map(e=>e.courseId)];
  const tcred=allC.reduce((a,cid)=>{const c=courses.find(x=>x.id===cid);return a+(c?c.credits:0);},0);
  const gpa=getGPA(s.id);
  const limit=getCourseLoadLimit(s.id);
  const st=getLoadStatus(s.id);
  const photoSrc=s.photo||null;
  document.getElementById('profileHero').innerHTML=`
    <div style="position:relative;flex-shrink:0;">
      ${photoSrc
        ?`<img src="${photoSrc}" alt="Student Photo" style="width:80px;height:80px;border-radius:50%;object-fit:cover;border:3px solid rgba(200,132,42,.4);cursor:pointer;" onclick="document.getElementById('photoInput_${s.id}').click()"/>`
        :`<div class="ph-av" onclick="document.getElementById('photoInput_${s.id}').click()" title="Click to upload photo" style="cursor:pointer;position:relative;">
            ${ini}
            <div style="position:absolute;bottom:0;right:0;width:22px;height:22px;border-radius:50%;background:var(--amber);display:flex;align-items:center;justify-content:center;font-size:11px;color:var(--ink);">📷</div>
          </div>`
      }
      <input type="file" id="photoInput_${s.id}" accept="image/*" style="display:none;" onchange="uploadStudentPhoto('${s.id}',this)"/>
    </div>
    <div style="flex:1;min-width:0;">
      <div class="ph-name">${s.firstName} ${s.lastName}</div>
      <div class="ph-meta">${s.id} · ${s.email}</div>
      <div class="ph-chips">
        <span class="ph-chip">📚 ${s.dept}</span>
        <span class="ph-chip">🎓 ${s.program||'BS'}</span>
        <span class="ph-chip" style="${st?`background:${st.bg};color:${st.color};border-color:${st.color}55;font-weight:600;`:''}">📊 CGPA: ${gpa}${st?` · ${st.label}`:''}</span>
        <span class="ph-chip">📋 ${me}/${limit} courses this sem.</span>
        <span class="ph-chip">✓ ${allC.length} Completed</span>
        <span class="ph-chip">⭐ ${tcred} Credits</span>
        <span class="ph-chip">📅 Joined ${s.registeredOn}</span>
      </div>
    </div>`;
  // Alert banner
  const unrepeated=getUnrepeatedFails(s.id);
  const failedCourses=examResults.filter(r=>r.studentId===s.id&&r.status==='fail'&&!hasCompleted(s.id,r.courseId));
  const banner=document.getElementById('stuAlertBanner');
  if(banner){
    let alerts='';
    if(st) alerts+=`<div class="alert" style="background:${st.bg};color:${st.color};border:1px solid ${st.color}44;margin-bottom:10px;">
      <span class="alert-ico">⚠</span><strong>${st.label}</strong> — CGPA ${gpa} · You are limited to <strong>${st.limit} courses</strong> this semester.
    </div>`;
    if(unrepeated.length) alerts+=`<div class="alert alert-e" style="margin-bottom:10px;"><span class="alert-ico">⛔</span>
      <strong>Action Required:</strong> You must re-enroll in failed course(s) before taking new ones: <strong>${unrepeated.join(', ')}</strong>
      <button class="btn btn-xs" style="margin-left:12px;background:rgba(192,57,43,.2);color:#e87c6e;border:none;" onclick="showPTab('enroll-self',document.querySelectorAll('#page-portal .i-tab')[1])">Enroll Now →</button>
    </div>`;
    banner.innerHTML=alerts;
    banner.style.marginBottom=alerts?'16px':'0';
  }
  renderPTab('enrolled');
}

function renderPTab(tab){
  if(!activeId)return;
  const s=students.find(x=>x.id===activeId);if(!s)return;

  // ── MY COURSES ──
  if(tab==='enrolled'){
    const me=enrollments.filter(e=>e.studentId===s.id&&e.status==='active');
    const el=document.getElementById('pt-enrolled');
    if(!me.length){
      el.innerHTML='<div class="empty-state"><div class="empty-ico">📚</div><div class="empty-txt">No active enrollments.<br/><br/><button class="btn btn-amber btn-sm" onclick="showPTab(\'enroll-self\',document.querySelectorAll(\'#page-portal .i-tab\')[1])">Browse & Enroll →</button></div></div>';
      return;
    }
    const limit=getCourseLoadLimit(s.id);
    const gpa=getGPA(s.id);
    el.innerHTML='<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:12px;margin-bottom:20px;">'
      +'<div class="stat-card" style="padding:14px;"><div class="stat-num">'+me.length+'</div><div class="stat-lbl">Enrolled</div></div>'
      +'<div class="stat-card" style="padding:14px;"><div class="stat-num">'+(limit-me.length)+'</div><div class="stat-lbl">Slots Left</div></div>'
      +'<div class="stat-card" style="padding:14px;"><div class="stat-num" style="color:#e87c6e;">'+examResults.filter(r=>r.studentId===s.id&&r.status==='fail'&&!hasCompleted(s.id,r.courseId)).length+'</div><div class="stat-lbl">Need Repeat</div></div>'
      +'<div class="stat-card" style="padding:14px;"><div class="stat-num" style="color:var(--amber2);">'+gpa+'</div><div class="stat-lbl">CGPA</div></div>'
      +'</div>'
      +'<div class="tbl-wrap"><table>'
      +'<thead><tr><th>Course</th><th>Code</th><th>Dept</th><th>Instructor</th><th>Credits</th><th>Since</th><th>Result</th><th>Action</th></tr></thead>'
      +'<tbody>'+me.map(function(e){
        const c=courses.find(function(x){return x.id===e.courseId;});
        const res=examResults.filter(function(r){return r.studentId===s.id&&r.courseId===e.courseId;});
        const latest=res[res.length-1];
        const resHTML=latest
          ?'<span style="font-size:11px;font-weight:700;color:'+(latest.status==='pass'?'#7ecbb8':'#e87c6e')+';background:'+(latest.status==='pass'?'rgba(58,122,106,.15)':'rgba(192,57,43,.12)')+';padding:2px 9px;border-radius:99px;">'+latest.grade+' · '+latest.total+'/100</span>'
          :'<span style="font-size:11px;color:var(--tx3);">Awaiting result</span>';
        const failBadge=latest&&latest.status==='fail'?'<br/><span style="font-size:10px;color:#e87c6e;background:rgba(192,57,43,.12);padding:1px 7px;border-radius:99px;">⚠ Must Repeat</span>':'';
        return '<tr>'
          +'<td><strong>'+(c?c.title:e.courseId)+'</strong>'+failBadge+'</td>'
          +'<td><span class="code-badge">'+e.courseId+'</span></td>'
          +'<td style="font-size:12px;">'+(c?c.dept:'—')+'</td>'
          +'<td style="font-size:12px;color:var(--tx2);">'+(c?c.instructor:'—')+'</td>'
          +'<td style="text-align:center;">'+(c?c.credits:'—')+'</td>'
          +'<td style="font-size:11px;color:var(--tx3);">'+e.date+'</td>'
          +'<td>'+resHTML+'</td>'
          +'<td><button class="btn btn-crimson btn-xs" onclick="doDrop(\''+e.courseId+'\')">Drop</button></td>'
          +'</tr>';
      }).join('')+'</tbody></table></div>'
      +'<div style="margin-top:16px;text-align:right;"><button class="btn btn-amber btn-sm" onclick="showPTab(\'enroll-self\',document.querySelectorAll(\'#page-portal .i-tab\')[1])">+ Enroll in More Courses</button></div>';
    return;
  }

  // ── ENROLL SELF ──
  if(tab==='enroll-self'){
    const el=document.getElementById('pt-enroll-self');
    const gpa=getGPA(s.id);
    const limit=getCourseLoadLimit(s.id);
    const current=getCurrentLoad(s.id);
    const st=getLoadStatus(s.id);
    const unrepeated=getUnrepeatedFails(s.id);
    let banners='';
    if(st) banners+='<div class="alert" style="background:'+st.bg+';color:'+st.color+';border:1px solid '+st.color+'44;margin-bottom:10px;"><span class="alert-ico">⚠</span><strong>'+st.label+'</strong> — Limited to '+st.limit+' courses (CGPA: '+gpa+')</div>';
    if(unrepeated.length) banners+='<div class="alert alert-e" style="margin-bottom:10px;"><span class="alert-ico">⛔</span><strong>Re-enroll in failed courses first:</strong> '+unrepeated.join(', ')+'</div>';
    banners+='<div class="alert alert-i" style="margin-bottom:16px;"><span class="alert-ico">ℹ</span>Enrolled: <strong>'+current+'/'+limit+'</strong> courses · CGPA: <strong>'+gpa+'</strong>'+(current>=limit?'<span style="color:#e87c6e;font-weight:600;margin-left:8px;">Load limit reached.</span>':'')+'</div>';
    const failedFirst=courses.filter(function(c){return unrepeated.includes(c.id);});
    const rest=courses.filter(function(c){return !unrepeated.includes(c.id);});
    const ordered=failedFirst.concat(rest);
    el.innerHTML='<div style="margin-bottom:16px;">'+banners+'</div>'
      +'<div class="fbar" style="margin-bottom:18px;">'
      +'<input type="text" id="selfSearch" placeholder="Search courses…" oninput="renderSelfEnroll()" style="max-width:220px;"/>'
      +'<select id="selfDept" onchange="renderSelfEnroll()">'
      +'<option value="">All Departments</option>'
      +'<option>Management Sciences</option><option>Computer Science</option>'
      +'<option>Mathematics</option><option>Engineering</option><option>Sciences</option><option>Psychology</option>'
      +'</select></div>'
      +'<div class="cards-grid" id="selfEnrollGrid"></div>';
    renderSelfEnroll(ordered);
    return;
  }

  // ── ENTER NUMBERS (student self-assessment) ──
  if(tab==='marks-entry'){
    const el=document.getElementById('pt-marks-entry');
    const myEnr=enrollments.filter(function(e){return e.studentId===s.id&&e.status==='active';});
    if(!myEnr.length){el.innerHTML='<div class="empty-state"><div class="empty-ico">📝</div><div class="empty-txt">No active courses. Enroll in courses first.</div></div>';return;}
    if(!window.studentMarks)window.studentMarks={};
    let rows='';
    myEnr.forEach(function(e){
      const c=courses.find(function(x){return x.id===e.courseId;});
      const key=s.id+'_'+e.courseId;
      const saved=window.studentMarks[key]||{};
      const official=examResults.filter(function(r){return r.studentId===s.id&&r.courseId===e.courseId;});
      const latest=official[official.length-1];
      if(latest){
        rows+='<tr style="opacity:.65;">'
          +'<td><strong>'+(c?c.title:e.courseId)+'</strong><br/><span style="font-size:10px;color:var(--tx3);">Official result posted</span></td>'
          +'<td><span class="code-badge">'+e.courseId+'</span></td>'
          +'<td style="font-size:12px;color:var(--tx2);">'+(c?c.instructor:'—')+'</td>'
          +'<td style="text-align:center;color:#f5c060;font-weight:700;">'+latest.sessional+'</td>'
          +'<td style="text-align:center;color:#7db8e0;font-weight:700;">'+latest.midterm+'</td>'
          +'<td style="text-align:center;color:#7ecbb8;font-weight:700;">'+latest.final+'</td>'
          +'<td style="text-align:center;font-weight:700;">'+latest.total+'</td>'
          +'<td style="text-align:center;font-weight:800;color:'+(latest.status==='pass'?'#7ecbb8':'#e87c6e')+';">'+latest.grade+'</td>'
          +'<td><span style="font-size:11px;color:var(--tx3);">Official</span></td>'
          +'</tr>';
      } else {
        const hasSaved=saved.s!==undefined;
        const tot=hasSaved?(Math.min(+(saved.s||0),40)+Math.min(+(saved.m||0),20)+Math.min(+(saved.f||0),40)):0;
        const g=hasSaved?calcGrade(tot):null;
        rows+='<tr>'
          +'<td><strong>'+(c?c.title:e.courseId)+'</strong></td>'
          +'<td><span class="code-badge">'+e.courseId+'</span></td>'
          +'<td style="font-size:12px;color:var(--tx2);">'+(c?c.instructor:'—')+'</td>'
          +'<td style="text-align:center;"><input type="number" id="sm_s_'+e.courseId+'" min="0" max="40" value="'+(saved.s!==undefined?saved.s:'')+'" placeholder="0–40" style="width:60px;padding:5px 8px;font-size:12px;text-align:center;border-color:rgba(245,192,96,.3);" oninput="previewStudentTotal(\''+e.courseId+'\')"/></td>'
          +'<td style="text-align:center;"><input type="number" id="sm_m_'+e.courseId+'" min="0" max="20" value="'+(saved.m!==undefined?saved.m:'')+'" placeholder="0–20" style="width:55px;padding:5px 8px;font-size:12px;text-align:center;border-color:rgba(125,184,224,.3);" oninput="previewStudentTotal(\''+e.courseId+'\')"/></td>'
          +'<td style="text-align:center;"><input type="number" id="sm_f_'+e.courseId+'" min="0" max="40" value="'+(saved.f!==undefined?saved.f:'')+'" placeholder="0–40" style="width:60px;padding:5px 8px;font-size:12px;text-align:center;border-color:rgba(126,203,184,.3);" oninput="previewStudentTotal(\''+e.courseId+'\')"/></td>'
          +'<td style="text-align:center;"><span id="sm_tot_'+e.courseId+'" style="font-weight:700;font-size:15px;color:'+(g?(g.gp>=1?'#7ecbb8':'#e87c6e'):'var(--tx3)')+';">'+(g?tot:'—')+'</span></td>'
          +'<td style="text-align:center;"><span id="sm_grade_'+e.courseId+'" style="font-weight:800;font-size:16px;color:'+(g?(g.gp>=1?'#7ecbb8':'#e87c6e'):'var(--tx3)')+';">'+(g?g.grade:'—')+'</span></td>'
          +'<td><button class="btn btn-amber btn-xs" onclick="saveStudentMarks(\''+s.id+'\',\''+e.courseId+'\')">Save</button>'
          +(hasSaved?'<br/><button class="btn btn-dark btn-xs" style="margin-top:4px;" onclick="clearStudentMarks(\''+s.id+'\',\''+e.courseId+'\')">Clear</button>':'')
          +'</td></tr>';
      }
    });
    el.innerHTML='<div class="alert alert-i" style="margin-bottom:16px;"><span class="alert-ico">ℹ</span>'
      +'Enter your marks per component. <strong style="color:var(--amber2);">Sessional max 40 · Midterm max 20 · Final max 40.</strong>'
      +' These are personal estimates — official results are posted by your teacher.</div>'
      +'<div class="tbl-wrap" style="overflow-x:auto;"><table style="min-width:620px;">'
      +'<thead><tr><th>Course</th><th>Code</th><th>Instructor</th>'
      +'<th style="color:#f5c060;">Sessional /40</th>'
      +'<th style="color:#7db8e0;">Midterm /20</th>'
      +'<th style="color:#7ecbb8;">Final /40</th>'
      +'<th>Total /100</th><th>Grade (Est.)</th><th>Action</th>'
      +'</tr></thead><tbody>'+rows+'</tbody></table></div>';
    return;
  }

  // ── MY MARKS (official results) ──
  if(tab==='results'){
    const el=document.getElementById('pt-results');
    const myRes=examResults.filter(function(r){return r.studentId===s.id;});
    if(!myRes.length){el.innerHTML='<div class="empty-state"><div class="empty-ico">📊</div><div class="empty-txt">No exam results recorded yet.</div></div>';return;}
    const gpa=getGPA(s.id);
    const passed=myRes.filter(function(r){return r.status==='pass';}).length;
    const failed=myRes.filter(function(r){return r.status==='fail';}).length;
    const avgMarks=passed?Math.round(myRes.filter(function(r){return r.status==='pass';}).reduce(function(a,r){return a+r.total;},0)/passed):0;
    let html='<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:12px;margin-bottom:20px;">'
      +'<div class="stat-card" style="padding:16px;"><div class="stat-num">'+gpa+'</div><div class="stat-lbl">CGPA</div></div>'
      +'<div class="stat-card" style="padding:16px;"><div class="stat-num" style="color:#7ecbb8;">'+passed+'</div><div class="stat-lbl">Passed</div></div>'
      +'<div class="stat-card" style="padding:16px;"><div class="stat-num" style="color:#e87c6e;">'+failed+'</div><div class="stat-lbl">Failed</div></div>'
      +'<div class="stat-card" style="padding:16px;"><div class="stat-num">'+avgMarks+'%</div><div class="stat-lbl">Avg Score</div></div>'
      +'</div>'
      +'<div style="background:var(--ink2);border:1px solid var(--bdr);border-radius:10px;padding:12px 16px;margin-bottom:16px;display:flex;gap:20px;flex-wrap:wrap;font-size:12px;">'
      +'<span style="color:var(--tx3);">Marking Scheme:</span>'
      +'<span><span style="color:#f5c060;font-weight:600;">Sessional</span> — 40 marks</span>'
      +'<span><span style="color:#7db8e0;font-weight:600;">Midterm</span> — 20 marks</span>'
      +'<span><span style="color:#7ecbb8;font-weight:600;">Final</span> — 40 marks</span>'
      +'<span style="font-weight:600;">Total — 100 marks</span></div>'
      +'<div class="tbl-wrap" style="overflow-x:auto;"><table style="min-width:720px;">'
      +'<thead><tr><th>Course</th><th>Code</th><th>Cr.</th>'
      +'<th style="color:#f5c060;">Sessional /40</th>'
      +'<th style="color:#7db8e0;">Midterm /20</th>'
      +'<th style="color:#7ecbb8;">Final /40</th>'
      +'<th>Total /100</th><th>Grade</th><th>GP</th><th>Status</th><th>Date</th>'
      +'</tr></thead><tbody>'
      +myRes.map(function(r){
        const c=courses.find(function(x){return x.id===r.courseId;});
        const isF=r.status==='fail';
        return '<tr style="'+(isF?'background:rgba(192,57,43,.04);':'')+'">'
          +'<td><strong>'+(c?c.title:r.courseId)+'</strong>'+(isF?' <span style="font-size:10px;background:rgba(192,57,43,.15);color:#e87c6e;padding:1px 7px;border-radius:99px;margin-left:4px;">REPEAT</span>':'')+'</td>'
          +'<td><span class="code-badge">'+r.courseId+'</span></td>'
          +'<td>'+(c?c.credits:'—')+'</td>'
          +'<td style="text-align:center;"><span style="font-weight:600;color:#f5c060;">'+(r.sessional!==undefined?r.sessional:'—')+'</span></td>'
          +'<td style="text-align:center;"><span style="font-weight:600;color:#7db8e0;">'+(r.midterm!==undefined?r.midterm:'—')+'</span></td>'
          +'<td style="text-align:center;"><span style="font-weight:600;color:#7ecbb8;">'+(r.final!==undefined?r.final:'—')+'</span></td>'
          +'<td style="text-align:center;"><strong style="font-size:15px;color:'+(isF?'#e87c6e':'var(--tx)')+';">'+r.total+'</strong></td>'
          +'<td style="text-align:center;"><span style="font-weight:800;font-size:16px;color:'+(isF?'#e87c6e':'#7ecbb8')+';">'+r.grade+'</span></td>'
          +'<td style="text-align:center;color:var(--tx2);">'+r.gp.toFixed(1)+'</td>'
          +'<td><span style="font-size:10px;padding:2px 9px;border-radius:99px;font-weight:600;background:'+(isF?'rgba(192,57,43,.12)':'rgba(58,122,106,.15)')+';color:'+(isF?'#e87c6e':'#7ecbb8')+'">'+(isF?'FAIL':'PASS')+'</span></td>'
          +'<td style="font-size:11px;color:var(--tx3);white-space:nowrap;">'+r.date+'</td>'
          +'</tr>';
      }).join('')
      +'</tbody></table></div>';
    el.innerHTML=html;
    return;
  }

  // ── COMPLETED ──
  if(tab==='completed'){
    const mc=[...(s.completedCourses||[]).map(function(cid){return {courseId:cid,date:'Transfer',grade:'P',gp:4.0,status:'pass'};}),
      ...examResults.filter(function(r){return r.studentId===s.id&&r.status==='pass';})];
    const el=document.getElementById('pt-completed');
    if(!mc.length){el.innerHTML='<div class="empty-state"><div class="empty-ico">🏆</div><div class="empty-txt">No completed courses yet.</div></div>';return;}
    el.innerHTML='<div class="tbl-wrap"><table>'
      +'<thead><tr><th>Course</th><th>Code</th><th>Department</th><th>Credits</th><th>Grade</th><th>Completed</th></tr></thead>'
      +'<tbody>'+mc.map(function(r){
        const c=courses.find(function(x){return x.id===r.courseId;});
        return '<tr><td><strong>'+(c?c.title:r.courseId)+'</strong></td>'
          +'<td><span class="code-badge">'+r.courseId+'</span></td>'
          +'<td>'+(c?c.dept:'—')+'</td>'
          +'<td>'+(c?c.credits:'—')+'</td>'
          +'<td style="font-weight:700;color:#7ecbb8;">'+(r.grade||'P')+'</td>'
          +'<td>'+(r.date||'—')+'</td></tr>';
      }).join('')+'</tbody></table></div>';
    return;
  }

  // ── STUDY PLAN ──
  if(tab==='plan'){
    const el=document.getElementById('pt-plan');
    const plan=studyPlans.find(function(p){return p.id===s.planId;});
    if(!plan){el.innerHTML='<div class="empty-state"><div class="empty-ico">🗓️</div><div class="empty-txt">No plan of study assigned yet.<br/>Ask admin to assign a plan.</div></div>';return;}
    const allC=[...(s.completedCourses||[]),...examResults.filter(function(r){return r.studentId===s.id&&r.status==='pass';}).map(function(r){return r.courseId;}),...enrollments.filter(function(e){return e.studentId===s.id&&e.status==='completed';}).map(function(e){return e.courseId;})];
    const activeEnr=enrollments.filter(function(e){return e.studentId===s.id&&e.status==='active';}).map(function(e){return e.courseId;});
    const failedC=examResults.filter(function(r){return r.studentId===s.id&&r.status==='fail'&&!allC.includes(r.courseId);}).map(function(r){return r.courseId;});
    let html='<div style="margin-bottom:14px;"><div class="sec-title" style="font-size:18px;">'+plan.name+'</div><div style="font-size:12px;color:var(--tx3);margin-top:4px;">'+plan.program+' · '+plan.dept+'</div></div>';
    plan.semesters.forEach(function(sem,si){
      const semDone=sem.courseIds.filter(function(cid){return allC.includes(cid);}).length;
      let rows='';
      sem.courseIds.forEach(function(cid){
        const c=courses.find(function(x){return x.id===cid;});
        const done=allC.includes(cid);
        const inProg=activeEnr.includes(cid);
        const fail=failedC.includes(cid);
        const res=examResults.filter(function(r){return r.studentId===s.id&&r.courseId===cid;});
        const latest=res[res.length-1];
        let badge='';
        if(done) badge='<span style="font-size:10px;padding:2px 9px;border-radius:99px;background:rgba(58,122,106,.15);color:#7ecbb8;font-weight:600;">PASSED'+(latest?' '+latest.grade:'')+'</span>';
        else if(inProg) badge='<span style="font-size:10px;padding:2px 9px;border-radius:99px;background:rgba(74,144,196,.15);color:#7db8e0;font-weight:600;">IN PROGRESS</span>';
        else if(fail) badge='<span style="font-size:10px;padding:2px 9px;border-radius:99px;background:rgba(192,57,43,.15);color:#e87c6e;font-weight:600;">FAILED — REPEAT</span>';
        else badge='<span style="font-size:10px;padding:2px 9px;border-radius:99px;background:rgba(255,255,255,.05);color:var(--tx3);font-weight:600;">PENDING</span>';
        rows+='<tr style="'+(fail?'background:rgba(192,57,43,.04);':'')+'"><td><strong>'+(c?c.title:cid)+'</strong></td><td><span class="code-badge">'+cid+'</span></td><td>'+(c?c.dept:'—')+'</td><td>'+(c?c.credits:'—')+'</td><td>'+badge+'</td></tr>';
      });
      html+='<div style="margin-bottom:20px;">'
        +'<div style="display:flex;align-items:center;gap:10px;margin-bottom:10px;">'
        +'<div style="font-family:var(--fh);font-size:16px;font-weight:700;color:var(--tx);">'+sem.label+'</div>'
        +'<span style="font-size:11px;color:var(--tx3);">'+semDone+'/'+sem.courseIds.length+' completed</span>'
        +'</div>'
        +'<div class="tbl-wrap"><table><thead><tr><th>Course</th><th>Code</th><th>Department</th><th>Credits</th><th>Status</th></tr></thead><tbody>'+rows+'</tbody></table></div>'
        +'</div>';
    });
    el.innerHTML=html;
    return;
  }

  // ── TRANSCRIPT ──
  if(tab==='transcript'){
    const el=document.getElementById('pt-transcript');
    const allRes=examResults.filter(function(r){return r.studentId===s.id;});
    const gpa=getGPA(s.id);
    const passedRes=allRes.filter(function(r){return r.status==='pass';});
    const failedRes=allRes.filter(function(r){return r.status==='fail'&&!hasCompleted(s.id,r.courseId);});
    const transferC=(s.completedCourses||[]);
    const tc=passedRes.reduce(function(a,r){const c=courses.find(function(x){return x.id===r.courseId;});return a+(c?c.credits:0);},0)
      +transferC.reduce(function(a,cid){const c=courses.find(function(x){return x.id===cid;});return a+(c?c.credits:0);},0);
    const photoSrc=s.photo||null;
    const ini=(s.firstName[0]+s.lastName[0]).toUpperCase();
    const photoHTML=photoSrc
      ?'<img src="'+photoSrc+'" style="width:72px;height:72px;border-radius:8px;object-fit:cover;border:2px solid var(--amber);"/>'
      :'<div style="width:72px;height:72px;border-radius:8px;background:var(--amber);display:flex;align-items:center;justify-content:center;font-family:var(--fh);font-size:26px;font-weight:700;color:var(--ink);">'+ini+'</div>';
    const transferHTML=transferC.length
      ?'<div style="padding:14px 20px;border-bottom:1px solid var(--bdr);"><div style="font-size:11px;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--tx3);margin-bottom:8px;">Transfer / Exempted Credits</div><div style="display:flex;gap:6px;flex-wrap:wrap;">'+transferC.map(function(cid){const c=courses.find(function(x){return x.id===cid;});return '<span style="font-size:11px;padding:3px 10px;border-radius:5px;background:rgba(74,144,196,.12);color:#7db8e0;border:1px solid rgba(74,144,196,.2);font-weight:500;">'+cid+(c?' — '+c.title:'')+' <span style="color:var(--tx3);">(Exempted)</span></span>';}).join('')+'</div></div>'
      :'';
    const resRows=allRes.length===0
      ?'<div style="color:var(--tx3);font-size:13px;padding:20px 0;text-align:center;">No exam results recorded yet.</div>'
      :'<div style="overflow-x:auto;"><table style="width:100%;border-collapse:collapse;min-width:600px;"><thead><tr style="border-bottom:1px solid var(--bdr);"><th style="text-align:left;padding:8px 10px;font-size:10px;text-transform:uppercase;letter-spacing:.08em;color:var(--tx3);">Course</th><th style="padding:8px 10px;font-size:10px;text-transform:uppercase;letter-spacing:.08em;color:var(--tx3);">Code</th><th style="padding:8px 10px;font-size:10px;text-transform:uppercase;color:var(--tx3);">Cr.</th><th style="padding:8px 10px;font-size:10px;text-transform:uppercase;color:#f5c060;">Sess.</th><th style="padding:8px 10px;font-size:10px;text-transform:uppercase;color:#7db8e0;">Mid.</th><th style="padding:8px 10px;font-size:10px;text-transform:uppercase;color:#7ecbb8;">Final</th><th style="padding:8px 10px;font-size:10px;text-transform:uppercase;color:var(--tx3);">Total</th><th style="padding:8px 10px;font-size:10px;text-transform:uppercase;color:var(--tx3);">Grade</th><th style="padding:8px 10px;font-size:10px;text-transform:uppercase;color:var(--tx3);">GP</th><th style="padding:8px 10px;font-size:10px;text-transform:uppercase;color:var(--tx3);">Status</th></tr></thead><tbody>'
        +allRes.map(function(r){
          const c=courses.find(function(x){return x.id===r.courseId;});
          const isF=r.status==='fail';
          return '<tr style="border-bottom:1px solid var(--bdr);'+(isF?'background:rgba(192,57,43,.04);':'')+'">'
            +'<td style="padding:9px 10px;font-size:12px;"><strong>'+(c?c.title:r.courseId)+'</strong>'+(isF?' <span style="font-size:9px;background:rgba(192,57,43,.15);color:#e87c6e;padding:1px 6px;border-radius:99px;">REPEAT</span>':'')+'</td>'
            +'<td style="padding:9px 10px;text-align:center;"><span class="code-badge">'+r.courseId+'</span></td>'
            +'<td style="padding:9px 10px;text-align:center;font-size:12px;">'+(c?c.credits:'—')+'</td>'
            +'<td style="padding:9px 10px;text-align:center;font-size:12px;color:#f5c060;font-weight:600;">'+(r.sessional!==undefined?r.sessional:'—')+'</td>'
            +'<td style="padding:9px 10px;text-align:center;font-size:12px;color:#7db8e0;font-weight:600;">'+(r.midterm!==undefined?r.midterm:'—')+'</td>'
            +'<td style="padding:9px 10px;text-align:center;font-size:12px;color:#7ecbb8;font-weight:600;">'+(r.final!==undefined?r.final:'—')+'</td>'
            +'<td style="padding:9px 10px;text-align:center;font-weight:700;font-size:14px;">'+r.total+'</td>'
            +'<td style="padding:9px 10px;text-align:center;font-weight:800;font-size:16px;color:'+(isF?'#e87c6e':'#7ecbb8')+';">'+r.grade+'</td>'
            +'<td style="padding:9px 10px;text-align:center;font-size:12px;color:var(--tx2);">'+r.gp.toFixed(1)+'</td>'
            +'<td style="padding:9px 10px;text-align:center;"><span style="font-size:10px;padding:2px 8px;border-radius:99px;font-weight:600;background:'+(isF?'rgba(192,57,43,.12)':'rgba(58,122,106,.15)')+';color:'+(isF?'#e87c6e':'#7ecbb8')+'">'+(isF?'F':'P')+'</span></td>'
            +'</tr>';
        }).join('')
        +'</tbody></table></div>';
    el.innerHTML='<div style="background:var(--ink2);border:1px solid var(--bdr2);border-radius:14px;overflow:hidden;margin-bottom:20px;">'
      +'<div style="background:var(--ink3);padding:24px 28px;display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:16px;border-bottom:2px solid var(--amber);">'
      +'<div style="display:flex;gap:18px;align-items:center;">'+photoHTML
      +'<div><div style="font-family:var(--fh);font-size:22px;font-weight:700;color:var(--tx);">'+s.firstName+' '+s.lastName+'</div>'
      +'<div style="font-size:12px;color:var(--tx3);margin-top:4px;">'+s.id+' · '+s.email+'</div>'
      +'<div style="font-size:12px;color:var(--tx2);margin-top:2px;">'+s.dept+' · '+(s.program||'BS')+'</div></div></div>'
      +'<div style="text-align:right;"><div style="font-family:var(--fh);font-size:14px;color:var(--amber2);font-weight:700;letter-spacing:.05em;">DHA SUFFA UNIVERSITY</div>'
      +'<div style="font-size:11px;color:var(--tx3);margin-top:3px;">Official Academic Transcript</div>'
      +'<div style="font-size:11px;color:var(--tx3);">Issued: '+new Date().toLocaleDateString()+'</div></div></div>'
      +'<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(110px,1fr));gap:0;border-bottom:1px solid var(--bdr);">'
      +[['CGPA',gpa,'var(--amber2)'],['Credits Earned',tc,'#7ecbb8'],['Courses Passed',passedRes.length,'#7ecbb8'],['Courses Failed',failedRes.length,'#e87c6e'],['Transfer Credits',transferC.length,'#7db8e0']].map(function(x){return '<div style="padding:14px 16px;border-right:1px solid var(--bdr);text-align:center;"><div style="font-family:var(--fh);font-size:22px;font-weight:700;color:'+x[2]+';">'+x[1]+'</div><div style="font-size:10px;text-transform:uppercase;letter-spacing:.08em;color:var(--tx3);margin-top:3px;">'+x[0]+'</div></div>';}).join('')
      +'</div>'
      +transferHTML
      +'<div style="padding:16px 20px 20px;"><div style="font-size:11px;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--tx3);margin-bottom:12px;">Course Results</div>'+resRows+'</div>'
      +'<div style="background:var(--ink3);padding:14px 20px;border-top:2px solid var(--amber);display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:10px;">'
      +'<div style="font-size:12px;color:var(--tx3);">DHA Suffa University — Official Academic Transcript. Generated electronically.</div>'
      +'<div style="font-family:var(--fh);font-size:16px;color:var(--amber2);font-weight:700;">CGPA: '+gpa+' &nbsp;|&nbsp; Credits: '+tc+'</div>'
      +'</div></div>'
      +'<button class="btn btn-amber btn-sm" onclick="printTranscript()">🖨 Print Transcript</button>';
    return;
  }

  // ── PROGRESS ──
  if(tab==='progress'){
    const allC=[...(s.completedCourses||[]),...examResults.filter(function(r){return r.studentId===s.id&&r.status==='pass';}).map(function(r){return r.courseId;}),...enrollments.filter(function(e){return e.studentId===s.id&&e.status==='completed';}).map(function(e){return e.courseId;})];
    const tc=allC.reduce(function(a,cid){const c=courses.find(function(x){return x.id===cid;});return a+(c?c.credits:0);},0);
    const req=135;const pct=Math.min(100,Math.round(tc/req*100));
    const gpa=getGPA(s.id);
    const byDept={};
    courses.forEach(function(c){if(!byDept[c.dept])byDept[c.dept]={t:0,d:0};byDept[c.dept].t++;if(allC.includes(c.id))byDept[c.dept].d++;});
    document.getElementById('pt-progress').innerHTML='<div class="form-shell">'
      +'<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:12px;margin-bottom:24px;">'
      +'<div class="stat-card" style="padding:16px;"><div class="stat-num">'+gpa+'</div><div class="stat-lbl">CGPA</div></div>'
      +'<div class="stat-card" style="padding:16px;"><div class="stat-num">'+tc+'</div><div class="stat-lbl">Credits Earned</div></div>'
      +'<div class="stat-card" style="padding:16px;"><div class="stat-num">'+(req-tc)+'</div><div class="stat-lbl">Credits Remaining</div></div>'
      +'<div class="stat-card" style="padding:16px;"><div class="stat-num">'+pct+'%</div><div class="stat-lbl">Degree Complete</div></div>'
      +'</div>'
      +'<div style="margin-bottom:24px;">'
      +'<div style="display:flex;justify-content:space-between;margin-bottom:10px;"><span style="font-weight:500;">Overall Degree Progress</span><span style="font-size:13px;color:var(--tx3);">'+tc+' / '+req+' credits</span></div>'
      +'<div class="big-prog-wrap"><div class="big-prog-fill" style="width:'+pct+'%;"></div></div>'
      +'</div>'
      +'<div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:14px;">'
      +Object.entries(byDept).map(function(entry){const d=entry[0];const v=entry[1];const p2=Math.round(v.d/v.t*100);return '<div class="stat-card" style="padding:16px;"><div style="font-size:12px;font-weight:600;color:var(--tx);margin-bottom:6px;">'+d+'</div><div style="font-size:11px;color:var(--tx3);margin-bottom:8px;">'+v.d+' / '+v.t+' courses</div><div class="prog-bar" style="width:100%;"><div class="prog-fill" style="width:'+p2+'%;background:'+(p2===100?'#3a7a6a':'#c8842a')+'"></div></div></div>';}).join('')
      +'</div></div>';
    return;
  }
}

function uploadStudentPhoto(sid,input){
  const file=input.files[0];if(!file)return;
  if(file.size>2*1024*1024){toast('Image must be under 2MB.','warn');return;}
  const reader=new FileReader();
  reader.onload=e=>{
    const s=students.find(x=>x.id===sid);
    if(s){s.photo=e.target.result;toast('Photo uploaded!','ok');renderPortal();}
  };
  reader.readAsDataURL(file);
}

function saveStudentContact(sid){
  const s=students.find(x=>x.id===sid);if(!s)return;
  const first=document.getElementById('ci_first')?.value.trim();
  const last=document.getElementById('ci_last')?.value.trim();
  const phone=document.getElementById('ci_phone')?.value.trim();
  const email=document.getElementById('ci_email')?.value.trim();
  const addr=document.getElementById('ci_addr')?.value.trim();
  const ecname=document.getElementById('ci_ecname')?.value.trim();
  const ecphone=document.getElementById('ci_ecphone')?.value.trim();
  const ecrel=document.getElementById('ci_ecrel')?.value;
  if(email&&!/^[^@]+@[^@]+\.[^@]+$/.test(email)){toast('Enter a valid email address.','err');return;}
  if(first)s.firstName=first;
  if(last)s.lastName=last;
  if(phone)s.phone=phone;
  if(email)s.email=email;
  if(addr)s.address=addr;
  s.emergencyName=ecname;
  s.emergencyPhone=ecphone;
  s.emergencyRel=ecrel;
  toast('Your information has been updated successfully!','ok');
  updateNavAv(s);
  renderPortal();
}

function printTranscript(){window.print();}

// ── STUDENT MARKS ENTRY HELPERS ──
function previewStudentTotal(cid){
  const sv=parseFloat(document.getElementById('sm_s_'+cid)?.value)||0;
  const mv=parseFloat(document.getElementById('sm_m_'+cid)?.value)||0;
  const fv=parseFloat(document.getElementById('sm_f_'+cid)?.value)||0;
  const tot=Math.min(sv,40)+Math.min(mv,20)+Math.min(fv,40);
  const g=calcGrade(tot);
  const tEl=document.getElementById('sm_tot_'+cid);
  const gEl=document.getElementById('sm_grade_'+cid);
  if(tEl){tEl.textContent=tot;tEl.style.color=g.gp>=1?'#7ecbb8':'#e87c6e';}
  if(gEl){gEl.textContent=g.grade;gEl.style.color=g.gp>=1?'#7ecbb8':'#e87c6e';}
}

function saveStudentMarks(sid,cid){
  const sv=document.getElementById('sm_s_'+cid)?.value;
  const mv=document.getElementById('sm_m_'+cid)?.value;
  const fv=document.getElementById('sm_f_'+cid)?.value;
  if(sv===''||mv===''||fv===''){toast('Enter all three marks before saving.','warn');return;}
  if(!window.studentMarks)window.studentMarks={};
  window.studentMarks[sid+'_'+cid]={s:parseFloat(sv),m:parseFloat(mv),f:parseFloat(fv)};
  toast('Marks saved locally!','ok');
  // Re-render tab to show clear button and updated total
  renderPTab('marks-entry');
}

function clearStudentMarks(sid,cid){
  if(!window.studentMarks)return;
  delete window.studentMarks[sid+'_'+cid];
  toast('Marks cleared.','warn');
  renderPTab('marks-entry');
}
function renderSelfEnroll(orderedList){
  const q=(document.getElementById('selfSearch')?.value||'').toLowerCase();
  const d=document.getElementById('selfDept')?.value||'';
  const list=orderedList||courses;
  const filtered=list.filter(c=>{
    if(q&&!c.title.toLowerCase().includes(q)&&!c.id.toLowerCase().includes(q))return false;
    if(d&&c.dept!==d)return false;
    return true;
  });
  const g=document.getElementById('selfEnrollGrid');if(!g)return;
  g.innerHTML=filtered.length?filtered.map(c=>ccHTML(c,true,activeId)).join('')
    :'<div class="empty-state"><div class="empty-ico">🔍</div><div class="empty-txt">No courses match your search.</div></div>';
}

// Wire up live search for self enroll
document.addEventListener('input',e=>{
  if(e.target&&(e.target.id==='selfSearch'||e.target.id==='selfDept'))renderSelfEnroll();
});
function renderAdminStu(){
  const q=(document.getElementById('astu-search')?.value||'').toLowerCase();
  const f=students.filter(s=>!q||(s.firstName+' '+s.lastName+s.id).toLowerCase().includes(q));
  const tb=document.getElementById('astu-body');if(!tb)return;
  if(!f.length){tb.innerHTML=`<tr><td colspan="7" style="text-align:center;color:var(--tx3);padding:36px;">No students registered yet.</td></tr>`;return;}
  tb.innerHTML=f.map(s=>{
    const me=enrollments.filter(e=>e.studentId===s.id&&e.status==='active').length;
    const mc=(s.completedCourses?.length||0)+enrollments.filter(e=>e.studentId===s.id&&e.status==='completed').length;
    return`<tr>
      <td><span class="code-badge">${s.id}</span></td>
      <td><strong>${s.firstName} ${s.lastName}</strong><div style="font-size:11px;color:var(--tx3);">${s.email}</div></td>
      <td>${s.dept}</td><td>${s.program||'—'}</td>
      <td><span class="stat-pill pill-ice">${me}</span></td>
      <td><span class="stat-pill pill-green">${mc}</span></td>
      <td style="display:flex;gap:5px;">
        <button class="btn btn-dark btn-xs" onclick="viewStu('${s.id}')">View</button>
        <button class="btn btn-amber btn-xs" onclick="setStu('${s.id}')">Set Active</button>
      </td></tr>`;
  }).join('');
}

function renderAdminEnr(){
  const tb=document.getElementById('aenr-body');if(!tb)return;
  const ae=enrollments.filter(e=>e.status==='active');
  if(!ae.length){tb.innerHTML=`<tr><td colspan="7" style="text-align:center;color:var(--tx3);padding:36px;">No active enrollments.</td></tr>`;return;}
  tb.innerHTML=ae.map(e=>{
    const s=students.find(x=>x.id===e.studentId);
    const c=courses.find(x=>x.id===e.courseId);
    return`<tr>
      <td><strong>${s?s.firstName+' '+s.lastName:e.studentId}</strong><div style="font-size:11px;color:var(--tx3);">${e.studentId}</div></td>
      <td>${c?.title||e.courseId}</td>
      <td><span class="code-badge">${e.courseId}</span></td>
      <td>${c?.dept||'—'}</td><td>${e.date}</td>
      <td><span class="enr-status s-enrolled">Active</span></td>
      <td style="display:flex;gap:5px;">
        <button class="btn btn-sage btn-xs" onclick="doMarkComplete('${e.studentId}','${e.courseId}')">Complete</button>
        <button class="btn btn-crimson btn-xs" onclick="doDropAdmin('${e.studentId}','${e.courseId}')">Drop</button>
      </td></tr>`;
  }).join('');
}

function renderAdminCrs(){
  const tb=document.getElementById('acrs-body');if(!tb)return;
  tb.innerHTML=courses.map(c=>`<tr>
    <td><span class="code-badge">${c.id}</span></td>
    <td><strong>${c.title}</strong></td>
    <td>${c.dept}</td><td>${c.credits}</td>
    <td><b>${c.enrolled}</b>/${c.seats}${c.enrolled>=c.seats?' <span style="color:#e87c6e;font-size:10px;">FULL</span>':''}</td>
    <td>${c.prereqs.length?c.prereqs.map(p=>`<span class="preq preq-unmet">${p}</span>`).join(' '):'<span style="color:var(--tx3);font-size:11px;">None</span>'}</td>
    <td style="display:flex;gap:5px;">
      <button class="btn btn-dark btn-xs" onclick="openEditCourse('${c.id}')">Edit</button>
      <button class="btn btn-crimson btn-xs" onclick="delCourse('${c.id}')">Delete</button>
    </td></tr>`).join('');
}

function viewStu(sid){
  const s=students.find(x=>x.id===sid);if(!s)return;
  const me=enrollments.filter(e=>e.studentId===sid&&e.status==='active');
  const mc=[...(s.completedCourses||[]),...enrollments.filter(e=>e.studentId===sid&&e.status==='completed').map(e=>e.courseId)];
  document.getElementById('mStuBody').innerHTML=`
    <div style="display:flex;gap:16px;align-items:center;margin-bottom:20px;">
      ${s.photo
        ?`<img src="${s.photo}" style="width:54px;height:54px;border-radius:8px;object-fit:cover;border:2px solid var(--amber);flex-shrink:0;"/>`
        :`<div style="width:54px;height:54px;border-radius:50%;background:var(--amber);display:flex;align-items:center;justify-content:center;font-family:var(--fh);font-size:20px;font-weight:700;color:var(--ink);flex-shrink:0;">${(s.firstName[0]+s.lastName[0]).toUpperCase()}</div>`
      }
      <div><div style="font-family:var(--fh);font-size:20px;font-weight:700;">${s.firstName} ${s.lastName}</div><div style="font-size:12px;color:var(--tx3);">${s.id} · ${s.email}</div></div>
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:18px;">
      ${[['Department',s.dept],['Program',s.program||'—'],['Phone',s.phone||'—'],['DOB',s.dob||'—'],['Gender',s.gender||'—'],['Registered',s.registeredOn]].map(([l,v])=>`<div><div style="font-size:10px;text-transform:uppercase;letter-spacing:.08em;color:var(--tx3);margin-bottom:3px;">${l}</div><div style="font-weight:500;">${v}</div></div>`).join('')}
    </div>
    <div class="divider"></div>
    <div style="font-weight:600;margin-bottom:8px;">Active Enrollments (${me.length})</div>
    ${me.length?me.map(e=>{const c=courses.find(x=>x.id===e.courseId);return`<div style="display:flex;justify-content:space-between;padding:7px 10px;background:var(--ink3);border-radius:7px;margin-bottom:4px;font-size:12px;border:1px solid var(--bdr);"><span><strong>${e.courseId}</strong> — ${c?.title||'?'}</span><span style="color:var(--tx3);">${e.date}</span></div>`;}).join(''):'<div style="color:var(--tx3);font-size:12px;">None</div>'}
    <div style="font-weight:600;margin:14px 0 8px;">Completed (${mc.length})</div>
    <div style="display:flex;gap:5px;flex-wrap:wrap;">${mc.map(cid=>`<span class="preq preq-met">${cid}</span>`).join('')||'<span style="color:var(--tx3);font-size:12px;">None</span>'}</div>
  `;
  document.getElementById('mStuSetBtn').onclick=()=>{setStu(sid);closeM('mStu');};
  openM('mStu');
}

function setStu(sid){
  activeId=sid;
  const s=students.find(x=>x.id===sid);
  if(s)updateNavAv(s);
  toast('Active student: '+sid,'ok');
  renderPortal();
}

// ══════════════════════════════════════
// COURSE MANAGEMENT
// ══════════════════════════════════════
function openAddCourse(){editingCid=null;openEditCourse(null);}
function openEditCourse(cid){
  editingCid=cid;
  const c=cid?courses.find(x=>x.id===cid):null;
  document.getElementById('mETitle').textContent=c?'Edit Course':'Add Course';
  document.getElementById('eCode').value=c?.id||'';
  document.getElementById('eTitle').value=c?.title||'';
  document.getElementById('eDept').value=c?.dept||'';
  document.getElementById('eLevel').value=c?.level||'100';
  document.getElementById('eCredits').value=c?.credits||3;
  document.getElementById('eSeats').value=c?.seats||30;
  document.getElementById('eInstructor').value=c?.instructor||'';
  document.getElementById('eDesc').value=c?.desc||'';
  document.getElementById('ePrereqGrid').innerHTML=courses.filter(x=>x.id!==cid).map(co=>`
    <label class="check-label"><input type="checkbox" id="epr_${co.id}" ${c?.prereqs?.includes(co.id)?'checked':''}/>${co.id}</label>`).join('');
  openM('mEdit');
}

function saveCourse(){
  const code=document.getElementById('eCode').value.trim().toUpperCase();
  const title=document.getElementById('eTitle').value.trim();
  const dept=document.getElementById('eDept').value;
  if(!code||!title||!dept){toast('Fill required fields.','err');return;}
  const prereqs=courses.filter(c=>document.getElementById('epr_'+c.id)?.checked).map(c=>c.id);
  const obj={id:code,title,dept,level:parseInt(document.getElementById('eLevel').value),
    credits:parseInt(document.getElementById('eCredits').value)||3,
    seats:parseInt(document.getElementById('eSeats').value)||30,
    instructor:document.getElementById('eInstructor').value,
    desc:document.getElementById('eDesc').value,
    prereqs,tags:[dept.split(' ')[0]],enrolled:0};
  if(editingCid){
    const idx=courses.findIndex(c=>c.id===editingCid);
    obj.enrolled=courses[idx].enrolled;courses[idx]=obj;toast('Course updated!','ok');
  } else {
    if(courses.find(c=>c.id===code)){toast('Code exists!','err');return;}
    courses.push(obj);toast('Course added!','ok');
  }
  closeM('mEdit');renderAdminCrs();renderCourses();renderHome();
}

function delCourse(cid){
  if(!confirm('Delete '+cid+'? All enrollments will also be removed.'))return;
  courses=courses.filter(c=>c.id!==cid);
  enrollments=enrollments.filter(e=>e.courseId!==cid);
  toast('Deleted.','warn');renderAdminCrs();renderCourses();renderHome();
}

// ══════════════════════════════════════
// MODAL
// ══════════════════════════════════════
function openM(id){document.getElementById(id).classList.add('open');}
function closeM(id){document.getElementById(id).classList.remove('open');}
document.querySelectorAll('.modal-bg').forEach(m=>m.addEventListener('click',e=>{if(e.target===m)m.classList.remove('open');}));

// ══════════════════════════════════════
// TOAST
// ══════════════════════════════════════
function toast(msg,type='ok'){
  const w=document.getElementById('toast');
  const el=document.createElement('div');
  el.className=`t-item t-${type}`;el.textContent=msg;
  w.appendChild(el);
  setTimeout(()=>{el.style.animation='tout .25s ease forwards';setTimeout(()=>el.remove(),260);},3200);
}

// ══════════════════════════════════════
// EXAM RESULTS (ADMIN)
// ══════════════════════════════════════
function populateResStuSel(){
  const sel=document.getElementById('resStudentSel');if(!sel)return;
  sel.innerHTML='<option value="">— choose student —</option>'+students.map(s=>`<option value="${s.id}">${s.id} — ${s.firstName} ${s.lastName}</option>`).join('');
}

function loadResultsForStudent(){
  const sid=document.getElementById('resStudentSel').value;
  const banner=document.getElementById('resStudentBanner');
  const wrap=document.getElementById('resTableWrap');
  const tbody=document.getElementById('res-body');
  if(!sid){banner.style.display='none';wrap.style.display='none';return;}
  const s=students.find(x=>x.id===sid);if(!s)return;
  const gpa=getGPA(sid);
  banner.style.display='';
  banner.innerHTML=`<div class="alert alert-i"><span class="alert-ico">ℹ</span>
    <strong>${s.firstName} ${s.lastName}</strong> · ${s.id} · ${s.dept} · CGPA: <strong>${gpa}</strong>
    <span style="margin-left:12px;font-size:11px;opacity:.7;">Sessional /40 · Midterm /20 · Final /40 = Total /100</span>
  </div>`;
  const active=enrollments.filter(e=>e.studentId===sid&&e.status==='active');
  const failed=examResults.filter(r=>r.studentId===sid&&r.status==='fail'&&!hasCompleted(sid,r.courseId));
  const allCids=[...new Set([...active.map(e=>e.courseId),...failed.map(r=>r.courseId)])];
  if(!allCids.length){
    wrap.style.display='';
    document.getElementById('res-body').closest('table').parentElement.innerHTML=
      '<div class="empty-state"><div class="empty-ico">📋</div><div class="empty-txt">No active enrollments to enter results for.</div></div>';
    return;
  }
  wrap.style.display='';
  tbody.innerHTML=allCids.map(cid=>{
    const c=courses.find(x=>x.id===cid);
    const prev=examResults.filter(r=>r.studentId===sid&&r.courseId===cid);
    const latest=prev[prev.length-1];
    const attempt=prev.length+1;
    const isFailed=latest&&latest.status==='fail';
    const prevInfo=latest
      ?`<div style="font-size:10px;color:var(--tx3);margin-top:3px;">
          Prev: S=${latest.sessional} M=${latest.midterm} F=${latest.final} → ${latest.total}/100 · <span style="color:${isFailed?'#e87c6e':'#7ecbb8'};font-weight:600;">${latest.grade}</span>
        </div>`:'';
    return`<tr style="${isFailed?'background:rgba(192,57,43,.04);':''}">
      <td>
        <strong>${c?.title||cid}</strong>
        ${isFailed?`<span style="font-size:10px;color:#e87c6e;background:rgba(192,57,43,.12);padding:1px 7px;border-radius:99px;margin-left:6px;">Attempt ${attempt}</span>`:''}
        ${prevInfo}
      </td>
      <td><span class="code-badge">${cid}</span></td>
      <td>${c?.credits||'—'}</td>
      <td>
        <input type="number" id="s_${cid}" min="0" max="40" placeholder="/40"
          style="width:58px;padding:5px 8px;font-size:12px;border:1px solid rgba(200,132,42,.3);"
          oninput="liveTotal('${cid}')" value="${latest?.sessional??''}"/>
      </td>
      <td>
        <input type="number" id="m_${cid}" min="0" max="20" placeholder="/20"
          style="width:52px;padding:5px 8px;font-size:12px;border:1px solid rgba(74,144,196,.3);"
          oninput="liveTotal('${cid}')" value="${latest?.midterm??''}"/>
      </td>
      <td>
        <input type="number" id="f_${cid}" min="0" max="40" placeholder="/40"
          style="width:58px;padding:5px 8px;font-size:12px;border:1px solid rgba(58,122,106,.3);"
          oninput="liveTotal('${cid}')" value="${latest?.final??''}"/>
      </td>
      <td>
        <span id="tot_${cid}" style="font-weight:700;font-size:15px;color:var(--tx3);">
          ${latest?latest.total+'<span style="font-size:10px;color:var(--tx3);">/100</span>':'—'}
        </span>
      </td>
      <td><span id="grd_${cid}" style="font-weight:700;font-size:14px;color:${latest?(latest.status==='pass'?'#7ecbb8':'#e87c6e'):'var(--tx3)'};">${latest?.grade||'—'}</span></td>
      <td>
        <span id="sts_${cid}" style="font-size:10px;font-weight:600;">
          ${latest?`<span style="color:${latest.status==='pass'?'#7ecbb8':'#e87c6e'};">${latest.status.toUpperCase()}</span>`:'—'}
        </span>
      </td>
      <td><button class="btn btn-amber btn-xs" onclick="saveResult('${sid}','${cid}')">Post</button></td>
    </tr>`;
  }).join('');
}

function liveTotal(cid){
  const sv=parseFloat(document.getElementById('s_'+cid)?.value)||0;
  const mv=parseFloat(document.getElementById('m_'+cid)?.value)||0;
  const fv=parseFloat(document.getElementById('f_'+cid)?.value)||0;
  const tot=Math.min(sv,MAX_SESSIONAL)+Math.min(mv,MAX_MIDTERM)+Math.min(fv,MAX_FINAL);
  const g=calcGrade(tot);
  const tel=document.getElementById('tot_'+cid);
  const gel=document.getElementById('grd_'+cid);
  const sel=document.getElementById('sts_'+cid);
  if(tel)tel.innerHTML=`<span style="color:${g.gp>=1?'#7ecbb8':'#e87c6e'};font-weight:700;font-size:15px;">${tot}</span><span style="font-size:10px;color:var(--tx3);">/100</span>`;
  if(gel){gel.textContent=g.grade;gel.style.color=g.gp>=1?'#7ecbb8':'#e87c6e';}
  if(sel)sel.innerHTML=`<span style="color:${g.gp>=1?'#7ecbb8':'#e87c6e'};font-size:10px;font-weight:600;">${g.gp>=1?'PASS':'FAIL'}</span>`;
}

function saveResult(sid,cid){
  const sv=parseFloat(document.getElementById('s_'+cid)?.value);
  const mv=parseFloat(document.getElementById('m_'+cid)?.value);
  const fv=parseFloat(document.getElementById('f_'+cid)?.value);
  if(isNaN(sv)||isNaN(mv)||isNaN(fv)){toast('Enter all three marks (Sessional, Midterm, Final).','warn');return;}
  if(sv<0||sv>MAX_SESSIONAL){toast(`Sessional must be 0–${MAX_SESSIONAL}.`,'warn');return;}
  if(mv<0||mv>MAX_MIDTERM){toast(`Midterm must be 0–${MAX_MIDTERM}.`,'warn');return;}
  if(fv<0||fv>MAX_FINAL){toast(`Final must be 0–${MAX_FINAL}.`,'warn');return;}
  const sessional=Math.round(sv*10)/10;
  const midterm=Math.round(mv*10)/10;
  const final_=Math.round(fv*10)/10;
  const total=Math.round((sessional+midterm+final_)*10)/10;
  const g=calcGrade(total);
  const isPassed=g.gp>=1.0;
  const result={studentId:sid,courseId:cid,sessional,midterm,final:final_,total,grade:g.grade,gp:g.gp,status:isPassed?'pass':'fail',date:new Date().toLocaleDateString()};
  examResults.push(result);
  if(isPassed){
    const idx=enrollments.findIndex(e=>e.studentId===sid&&e.courseId===cid&&e.status==='active');
    if(idx>-1){enrollments[idx].status='completed';courses.find(x=>x.id===cid).enrolled--;}
    toast(`${cid} — ${g.grade} (${total}/100) · PASSED ✓`,'ok');
  } else {
    dropBlockedCourses(sid,cid);
    toast(`${cid} — ${g.grade} (${total}/100) · FAILED. Forward courses blocked.`,'err');
  }
  loadResultsForStudent();
  refreshAll(sid);
}

function dropBlockedCourses(sid,failedCid){
  // Find all courses that have failedCid as a prerequisite
  courses.forEach(c=>{
    if(c.prereqs.includes(failedCid)){
      const idx=enrollments.findIndex(e=>e.studentId===sid&&e.courseId===c.id&&e.status==='active');
      if(idx>-1){
        enrollments[idx].status='dropped';
        courses.find(x=>x.id===c.id).enrolled--;
        toast(`${c.id} dropped — prerequisite ${failedCid} failed.`,'warn');
      }
    }
  });
}

// ══════════════════════════════════════
// PLAN OF STUDY
// ══════════════════════════════════════
let planSemCount=0;

function openPlanModal(pid){
  editingPlanId=pid||null;
  planSemCount=0;
  const plan=pid?studyPlans.find(p=>p.id===pid):null;
  document.getElementById('mPlanTitle').textContent=plan?'Edit Plan of Study':'Create Plan of Study';
  document.getElementById('planName').value=plan?.name||'';
  document.getElementById('planDept').value=plan?.dept||'';
  document.getElementById('planProg').value=plan?.program||'';
  document.getElementById('planSemestersWrap').innerHTML='';
  planSemCount=0;
  if(plan){plan.semesters.forEach(sem=>addPlanSemester(sem));}
  else{addPlanSemester();addPlanSemester();}
  openM('mPlan');
}

function addPlanSemester(existing){
  planSemCount++;
  const idx=planSemCount;
  const wrap=document.getElementById('planSemestersWrap');
  const div=document.createElement('div');
  div.id='plansem_'+idx;
  div.style.cssText='margin-bottom:18px;background:var(--ink3);border:1px solid var(--bdr2);border-radius:12px;overflow:hidden;';

  // Group courses by department
  const depts=[...new Set(courses.map(c=>c.dept))].sort();

  div.innerHTML=`
    <div style="display:flex;justify-content:space-between;align-items:center;padding:12px 14px;background:var(--ink4);border-bottom:1px solid var(--bdr);">
      <div style="display:flex;align-items:center;gap:10px;">
        <span style="font-size:11px;text-transform:uppercase;letter-spacing:.1em;color:var(--tx3);">Semester</span>
        <input id="semlabel_${idx}" placeholder="e.g. Semester 1" value="${existing?.label||'Semester '+idx}"
          style="font-weight:600;font-size:13px;width:170px;padding:5px 10px;background:var(--ink2);border:1px solid var(--bdr2);border-radius:6px;color:var(--tx);"/>
      </div>
      <div style="display:flex;align-items:center;gap:8px;">
        <span id="selcount_${idx}" style="font-size:11px;color:var(--amber2);font-weight:600;">0 courses</span>
        <button class="btn btn-dark btn-xs" onclick="document.getElementById('plansem_${idx}').remove();updatePlanTotals()">✕ Remove</button>
      </div>
    </div>

    <div style="padding:12px 14px 8px;border-bottom:1px solid var(--bdr);display:flex;gap:8px;flex-wrap:wrap;align-items:center;">
      <input type="text" placeholder="🔍 Search courses…" oninput="filterPlanCourses('${idx}',this.value)"
        style="max-width:220px;padding:7px 12px;font-size:12px;background:var(--ink2);border:1px solid var(--bdr2);border-radius:6px;color:var(--tx);"/>
      <select onchange="filterPlanDept('${idx}',this.value)"
        style="padding:7px 10px;font-size:12px;background:var(--ink2);border:1px solid var(--bdr2);border-radius:6px;color:var(--tx2);">
        <option value="">All Departments</option>
        ${depts.map(d=>`<option value="${d}">${d}</option>`).join('')}
      </select>
      <button class="btn btn-dark btn-xs" onclick="selectAllPlanCourses('${idx}',true)">Select All</button>
      <button class="btn btn-dark btn-xs" onclick="selectAllPlanCourses('${idx}',false)">Clear All</button>
    </div>

    <div id="pscourselist_${idx}" style="max-height:260px;overflow-y:auto;padding:10px 14px;">
      ${depts.map(dept=>{
        const dCourses=courses.filter(c=>c.dept===dept);
        const dTag=DEPT_TAG[dept]||'tag-cs';
        return`<div class="psdept_${idx}" data-dept="${dept}" style="margin-bottom:12px;">
          <div style="font-size:10px;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--tx3);margin-bottom:6px;padding-bottom:4px;border-bottom:1px solid var(--bdr);">${dept}</div>
          <div style="display:flex;flex-direction:column;gap:4px;">
            ${dCourses.map(c=>`
              <label id="psrow_${idx}_${c.id}" class="ps-course-row" data-dept="${dept}" data-title="${c.title.toLowerCase()}" data-code="${c.id.toLowerCase()}"
                style="display:flex;align-items:center;gap:10px;cursor:pointer;padding:8px 10px;border-radius:8px;border:1px solid ${existing?.courseIds?.includes(c.id)?'rgba(200,132,42,.3)':'var(--bdr)'};background:${existing?.courseIds?.includes(c.id)?'rgba(200,132,42,.08)':'var(--ink2)'};transition:all .12s;">
                <input type="checkbox" id="ps_${idx}_${c.id}" ${existing?.courseIds?.includes(c.id)?'checked':''}
                  style="width:auto;padding:0;background:none;border:none;accent-color:var(--amber);flex-shrink:0;"
                  onchange="onPlanCourseToggle('${idx}','${c.id}',this)"/>
                <div style="flex:1;min-width:0;">
                  <div style="display:flex;align-items:center;gap:6px;flex-wrap:wrap;">
                    <span style="font-size:11px;font-weight:700;color:var(--amber2);">${c.id}</span>
                    <span style="font-size:12px;color:var(--tx);font-weight:500;">${c.title}</span>
                  </div>
                  <div style="display:flex;align-items:center;gap:8px;margin-top:3px;flex-wrap:wrap;">
                    <span class="c-tag ${dTag}" style="font-size:9px;padding:1px 7px;">${dept.split(' ')[0]}</span>
                    <span style="font-size:10px;color:var(--tx3);">${c.credits} credits · Level ${c.level}</span>
                    <span style="font-size:10px;color:var(--tx3);">${c.instructor}</span>
                    ${c.prereqs.length?`<span style="font-size:10px;color:#e87c6e;">Prereqs: ${c.prereqs.join(', ')}</span>`:'<span style="font-size:10px;color:var(--tx3);">No prerequisites</span>'}
                  </div>
                </div>
              </label>`).join('')}
          </div>
        </div>`;
      }).join('')}
    </div>

    <div style="padding:8px 14px;border-top:1px solid var(--bdr);background:var(--ink4);display:flex;align-items:center;gap:12px;font-size:11px;color:var(--tx3);">
      <span>Selected: <strong id="selcount2_${idx}" style="color:var(--amber2);">0</strong> courses</span>
      <span>|</span>
      <span>Total Credits: <strong id="selcreds_${idx}" style="color:var(--tx2);">0</strong></span>
    </div>`;

  wrap.appendChild(div);

  // Init counts
  updateSemCount(idx, existing?.courseIds||[]);
}

function onPlanCourseToggle(idx, cid, cb){
  const label=document.getElementById('psrow_'+idx+'_'+cid);
  if(label){
    label.style.borderColor=cb.checked?'rgba(200,132,42,.3)':'var(--bdr)';
    label.style.background=cb.checked?'rgba(200,132,42,.08)':'var(--ink2)';
  }
  const selected=courses.filter(c=>document.getElementById('ps_'+idx+'_'+c.id)?.checked);
  updateSemCount(idx, selected.map(c=>c.id));
}

function updateSemCount(idx, selectedIds){
  const count=selectedIds.length;
  const creds=selectedIds.reduce((a,cid)=>{const c=courses.find(x=>x.id===cid);return a+(c?c.credits:0);},0);
  const el1=document.getElementById('selcount_'+idx);
  const el2=document.getElementById('selcount2_'+idx);
  const el3=document.getElementById('selcreds_'+idx);
  if(el1)el1.textContent=count+' course'+(count!==1?'s':'');
  if(el2)el2.textContent=count;
  if(el3)el3.textContent=creds;
}

function filterPlanCourses(idx, query){
  const q=query.toLowerCase();
  document.querySelectorAll(`#pscourselist_${idx} .ps-course-row`).forEach(row=>{
    const match=!q||row.dataset.title.includes(q)||row.dataset.code.includes(q);
    row.style.display=match?'':'none';
  });
  // Hide empty dept headers
  document.querySelectorAll(`#pscourselist_${idx} .psdept_${idx}`).forEach(dept=>{
    const visible=[...dept.querySelectorAll('.ps-course-row')].some(r=>r.style.display!=='none');
    dept.style.display=visible?'':'none';
  });
}

function filterPlanDept(idx, dept){
  document.querySelectorAll(`#pscourselist_${idx} .psdept_${idx}`).forEach(d=>{
    d.style.display=(!dept||d.dataset.dept===dept)?'':'none';
  });
}

function selectAllPlanCourses(idx, checked){
  courses.forEach(c=>{
    const cb=document.getElementById('ps_'+idx+'_'+c.id);
    const row=document.getElementById('psrow_'+idx+'_'+c.id);
    if(cb&&row&&row.style.display!=='none'){
      cb.checked=checked;
      row.style.borderColor=checked?'rgba(200,132,42,.3)':'var(--bdr)';
      row.style.background=checked?'rgba(200,132,42,.08)':'var(--ink2)';
    }
  });
  const selected=courses.filter(c=>document.getElementById('ps_'+idx+'_'+c.id)?.checked);
  updateSemCount(idx,selected.map(c=>c.id));
}

function updatePlanTotals(){} // placeholder for future plan-level credit totals

function savePlan(){
  const name=document.getElementById('planName').value.trim();
  const dept=document.getElementById('planDept').value;
  const program=document.getElementById('planProg').value;
  if(!name||!dept){toast('Name and department required.','err');return;}
  const semesters=[];
  document.querySelectorAll('[id^=plansem_]').forEach(div=>{
    const idx=div.id.split('_')[1];
    const label=document.getElementById('semlabel_'+idx)?.value||('Semester '+idx);
    const courseIds=courses.filter(c=>document.getElementById('ps_'+idx+'_'+c.id)?.checked).map(c=>c.id);
    if(courseIds.length)semesters.push({label,courseIds});
  });
  if(!semesters.length){toast('Add at least one semester with courses.','warn');return;}
  if(editingPlanId){
    const idx=studyPlans.findIndex(p=>p.id===editingPlanId);
    studyPlans[idx]={...studyPlans[idx],name,dept,program,semesters};
    toast('Plan updated!','ok');
  } else {
    const id='PLN'+Date.now();
    studyPlans.push({id,name,dept,program,semesters});
    toast('Plan created!','ok');
  }
  closeM('mPlan');renderAdminPlans();
}

function renderAdminPlans(){
  const tb=document.getElementById('aplan-body');if(!tb)return;
  if(!studyPlans.length){tb.innerHTML='<tr><td colspan="7" style="text-align:center;color:var(--tx3);padding:36px;">No plans created yet.</td></tr>';return;}
  tb.innerHTML=studyPlans.map(p=>{
    const assigned=students.filter(s=>s.planId===p.id).map(s=>s.firstName+' '+s.lastName);
    const totalCreds=p.totalCredits||p.semesters.flatMap(s=>s.courseIds).reduce((a,cid)=>{const c=courses.find(x=>x.id===cid);return a+(c?c.credits:0);},0);
    return`<tr>
      <td><strong>${p.name}</strong></td>
      <td>${p.dept}</td><td style="font-size:12px;">${p.program||'—'}</td>
      <td>${p.semesters.length}</td><td>${totalCreds}</td>
      <td style="font-size:12px;color:var(--tx2);">${assigned.length?assigned.join(', '):'<span style="color:var(--tx3);">None</span>'}</td>
      <td style="display:flex;gap:5px;">
        <button class="btn btn-ice btn-xs" onclick="viewPlan('${p.id}')">View</button>
        <button class="btn btn-dark btn-xs" onclick="openPlanModal('${p.id}')">Edit</button>
        <button class="btn btn-crimson btn-xs" onclick="deletePlan('${p.id}')">Delete</button>
      </td></tr>`;
  }).join('');
}

function viewPlan(pid){
  viewingPlanId=pid;
  const p=studyPlans.find(x=>x.id===pid);if(!p)return;
  document.getElementById('mVPTitle').textContent=p.name;
  const totalCreds=p.totalCredits||p.semesters.flatMap(s=>s.courseIds).reduce((a,cid)=>{const c=courses.find(x=>x.id===cid);return a+(c?c.credits:0);},0);
  document.getElementById('mVPBody').innerHTML=`
    <div style="display:flex;gap:12px;flex-wrap:wrap;margin-bottom:18px;">
      <span class="ph-chip">📚 ${p.dept}</span>
      <span class="ph-chip">🎓 ${p.program||'—'}</span>
      <span class="ph-chip">📋 ${p.semesters.length} Semesters</span>
      <span class="ph-chip">⭐ ${totalCreds} Credits</span>
    </div>`+
    p.semesters.map(sem=>{
      const rows=sem.courseIds.map(cid=>{const c=courses.find(x=>x.id===cid);return`<tr><td><strong>${c?.title||cid}</strong></td><td><span class="code-badge">${cid}</span></td><td>${c?.dept||'—'}</td><td>${c?.credits||'—'}</td><td>${c?.prereqs?.length?c.prereqs.join(', '):'None'}</td></tr>`;}).join('');
      return`<div style="margin-bottom:16px;"><div style="font-family:var(--fh);font-size:15px;font-weight:700;margin-bottom:8px;color:var(--amber2);">${sem.label}</div>
      <div class="tbl-wrap"><table><thead><tr><th>Course</th><th>Code</th><th>Dept</th><th>Credits</th><th>Prerequisites</th></tr></thead><tbody>${rows}</tbody></table></div></div>`;
    }).join('');
  // populate assign dropdown
  const sel=document.getElementById('assignStuSel');
  sel.innerHTML=students.map(s=>`<option value="${s.id}" ${s.planId===pid?'selected':''}>${s.id} — ${s.firstName} ${s.lastName}</option>`).join('');
  openM('mViewPlan');
}

function assignPlanToStudent(){
  const sid=document.getElementById('assignStuSel').value;if(!sid)return;
  const s=students.find(x=>x.id===sid);if(!s)return;
  s.planId=viewingPlanId;
  toast('Plan assigned to '+s.firstName+' '+s.lastName,'ok');
  renderAdminPlans();
  if(activeId===sid)renderPortal();
}

function deletePlan(pid){
  if(!confirm('Delete this plan? Students assigned to it will lose their plan.'))return;
  students.forEach(s=>{if(s.planId===pid)delete s.planId;});
  studyPlans=studyPlans.filter(p=>p.id!==pid);
  toast('Plan deleted.','warn');renderAdminPlans();
}

// ══════════════════════════════════════
// ADMIN OVERRIDES
// ══════════════════════════════════════
function initOverridesTab(){
  const stuOpts='<option value="">— select —</option>'+students.map(s=>`<option value="${s.id}">${s.id} — ${s.firstName} ${s.lastName} (CGPA: ${getGPA(s.id)})</option>`).join('');
  const s1=document.getElementById('ovLoadStu');
  const s2=document.getElementById('ovCourseStu');
  if(s1)s1.innerHTML=stuOpts;
  if(s2)s2.innerHTML=stuOpts;
  renderOverrideTable();
}

function renderOverrideStudentInfo(){
  const sid=document.getElementById('ovLoadStu').value;
  const el=document.getElementById('ovLoadInfo');
  if(!sid){el.innerHTML='';return;}
  const s=students.find(x=>x.id===sid);
  const gpa=getGPA(sid);
  const st=getLoadStatus(sid);
  const current=getCourseLoadLimit(sid);
  const existing=adminOverrides.find(o=>o.studentId===sid&&o.type==='load_override');
  el.innerHTML=`<div class="alert ${st?'alert-w':'alert-i'}">
    <span class="alert-ico">${st?'⚠':'ℹ'}</span>
    <strong>${s?.firstName} ${s?.lastName}</strong> · CGPA: <strong>${gpa}</strong> · Current limit: <strong>${current} courses</strong>
    ${st?`· <span style="color:${st.color};font-weight:600;">${st.label}</span>`:'· No restriction active'}
    ${existing?`· <span style="color:#f5c060;font-weight:500;">Override already active: ${existing.value} courses</span>`:''}
  </div>`;
}

function grantLoadOverride(){
  const sid=document.getElementById('ovLoadStu').value;
  const val=parseInt(document.getElementById('ovLoadVal').value);
  if(!sid){toast('Select a student.','warn');return;}
  if(!val||val<1||val>12){toast('Enter a valid number (1–12).','warn');return;}
  // Remove existing load override for this student
  adminOverrides=adminOverrides.filter(o=>!(o.studentId===sid&&o.type==='load_override'));
  adminOverrides.push({studentId:sid,type:'load_override',value:val,grantedOn:new Date().toLocaleDateString(),grantedBy:'Admin'});
  const s=students.find(x=>x.id===sid);
  toast(`Load override granted: ${s?.firstName} can now enroll in up to ${val} courses.`,'ok');
  renderOverrideStudentInfo();
  renderOverrideTable();
  refreshAll(sid);
}

function loadOverrideCourses(){
  const sid=document.getElementById('ovCourseStu').value;
  const sel=document.getElementById('ovCourseId');
  const infoEl=document.getElementById('ovCourseInfo');
  sel.innerHTML='<option value="">— select course —</option>';
  infoEl.innerHTML='';
  if(!sid)return;
  // Show only courses where student failed a prereq
  const blockedCourses=courses.filter(c=>{
    if(c.prereqs.length===0)return false;
    return c.prereqs.some(p=>hasFailed(sid,p));
  });
  if(!blockedCourses.length){
    infoEl.innerHTML=`<div class="alert alert-ok"><span class="alert-ico">✓</span>No blocked courses for this student. All prerequisites are met or no results yet.</div>`;
    return;
  }
  sel.innerHTML='<option value="">— select course —</option>'+blockedCourses.map(c=>{
    const failedP=c.prereqs.filter(p=>hasFailed(sid,p));
    return`<option value="${c.id}">${c.id} — ${c.title} (failed prereq: ${failedP.join(', ')})</option>`;
  }).join('');
  infoEl.innerHTML=`<div class="alert alert-e"><span class="alert-ico">⛔</span>
    ${blockedCourses.length} course(s) blocked for this student due to failed prerequisites.
  </div>`;
}

function grantCourseOverride(){
  const sid=document.getElementById('ovCourseStu').value;
  const cid=document.getElementById('ovCourseId').value;
  if(!sid||!cid){toast('Select both student and course.','warn');return;}
  if(adminOverrides.some(o=>o.studentId===sid&&o.type==='course_override'&&o.courseId===cid)){
    toast('Override already exists for this student/course.','warn');return;
  }
  const s=students.find(x=>x.id===sid);
  const c=courses.find(x=>x.id===cid);
  const failedP=c.prereqs.filter(p=>hasFailed(sid,p));
  adminOverrides.push({studentId:sid,type:'course_override',courseId:cid,grantedOn:new Date().toLocaleDateString(),grantedBy:'Admin',note:`Failed: ${failedP.join(', ')}`});
  toast(`Exception granted: ${s?.firstName} can now enroll in ${cid} despite failed prereqs.`,'ok');
  renderOverrideTable();
  document.getElementById('ovCourseId').value='';
  refreshAll(sid);
}

function revokeOverride(idx){
  const ov=adminOverrides[idx];
  adminOverrides.splice(idx,1);
  toast('Override revoked.','warn');
  renderOverrideTable();
  if(ov)refreshAll(ov.studentId);
}

function renderOverrideTable(){
  const tb=document.getElementById('ov-body');if(!tb)return;
  if(!adminOverrides.length){
    tb.innerHTML='<tr><td colspan="5" style="text-align:center;color:var(--tx3);padding:32px;">No active overrides.</td></tr>';return;
  }
  tb.innerHTML=adminOverrides.map((o,i)=>{
    const s=students.find(x=>x.id===o.studentId);
    const c=o.courseId?courses.find(x=>x.id===o.courseId):null;
    const typeLabel=o.type==='load_override'
      ?`<span style="font-size:10px;padding:2px 9px;border-radius:99px;background:rgba(200,132,42,.15);color:var(--amber3);font-weight:600;">Load Override</span>`
      :`<span style="font-size:10px;padding:2px 9px;border-radius:99px;background:rgba(192,57,43,.12);color:#e87c6e;font-weight:600;">Course Exception</span>`;
    const detail=o.type==='load_override'
      ?`Max <strong>${o.value}</strong> courses allowed`
      :`Allow enrollment in <strong>${o.courseId}</strong>${c?` — ${c.title}`:''}${o.note?`<div style="font-size:10px;color:var(--tx3);">${o.note}</div>`:''}`;
    return`<tr>
      <td><strong>${s?s.firstName+' '+s.lastName:o.studentId}</strong><div style="font-size:11px;color:var(--tx3);">${o.studentId} · CGPA: ${getGPA(o.studentId)}</div></td>
      <td>${typeLabel}</td>
      <td style="font-size:13px;">${detail}</td>
      <td style="font-size:11px;color:var(--tx3);">${o.grantedOn} by ${o.grantedBy}</td>
      <td><button class="btn btn-crimson btn-xs" onclick="revokeOverride(${i})">Revoke</button></td>
    </tr>`;
  }).join('');
}

// ══════════════════════════════════════
// TEACHERS / FACULTY
// ══════════════════════════════════════
let teachers=[];
let editingTeacherId=null;
let teacherPhotoData=null;

function previewTeacherPhoto(input){
  const file=input.files[0];if(!file)return;
  const reader=new FileReader();
  reader.onload=e=>{
    teacherPhotoData=e.target.result;
    const prev=document.getElementById('teacherPhotoPreview');
    prev.innerHTML=`<img src="${e.target.result}" style="width:100%;height:100%;object-fit:cover;"/>`;
  };reader.readAsDataURL(file);
}

function openTeacherModal(tid){
  editingTeacherId=tid||null;teacherPhotoData=null;
  const t=tid?teachers.find(x=>x.id===tid):null;
  document.getElementById('mTeachTitle').textContent=t?'Edit Faculty Member':'Add Faculty Member';
  document.getElementById('tTitle').value=t?.title||'Dr.';
  document.getElementById('tName').value=t?.name||'';
  document.getElementById('tDept').value=t?.dept||'';
  document.getElementById('tRank').value=t?.rank||'Lecturer';
  document.getElementById('tSpec').value=t?.specialisation||'';
  document.getElementById('tEmail').value=t?.email||'';
  document.getElementById('tPhone').value=t?.phone||'';
  document.getElementById('tQual').value=t?.qualification||'';
  const prev=document.getElementById('teacherPhotoPreview');
  prev.innerHTML=t?.photo?`<img src="${t.photo}" style="width:100%;height:100%;object-fit:cover;"/>`:t?.name?t.name[0].toUpperCase():'👤';
  document.getElementById('tCoursesGrid').innerHTML=courses.map(c=>`
    <label class="check-label"><input type="checkbox" id="tc_${c.id}" ${t?.courseIds?.includes(c.id)?'checked':''} style="width:auto;padding:0;background:none;border:none;accent-color:var(--amber);"/>${c.id} — ${c.title}</label>`).join('');
  openM('mTeacher');
}

function saveTeacher(){
  const name=document.getElementById('tName').value.trim();
  const dept=document.getElementById('tDept').value;
  if(!name||!dept){toast('Name and department required.','err');return;}
  const courseIds=courses.filter(c=>document.getElementById('tc_'+c.id)?.checked).map(c=>c.id);
  const obj={
    id:editingTeacherId||('TCH'+Date.now()),
    title:document.getElementById('tTitle').value,
    name,dept,
    rank:document.getElementById('tRank').value,
    specialisation:document.getElementById('tSpec').value,
    email:document.getElementById('tEmail').value,
    phone:document.getElementById('tPhone').value,
    qualification:document.getElementById('tQual').value,
    courseIds,
    photo:teacherPhotoData||(editingTeacherId?teachers.find(x=>x.id===editingTeacherId)?.photo:null)
  };
  if(editingTeacherId){const idx=teachers.findIndex(x=>x.id===editingTeacherId);teachers[idx]=obj;toast('Faculty updated!','ok');}
  else{teachers.push(obj);toast('Faculty added!','ok');}
  closeM('mTeacher');renderTeachers();
}

function renderTeachers(){
  const q=(document.getElementById('teacherSearch')?.value||'').toLowerCase();
  const d=document.getElementById('teacherDeptFilter')?.value||'';
  const r=document.getElementById('teacherRankFilter')?.value||'';
  let f=teachers.filter(t=>{
    if(q&&!(t.name.toLowerCase().includes(q)||t.specialisation?.toLowerCase().includes(q)))return false;
    if(d&&t.dept!==d)return false;
    if(r&&t.rank!==r)return false;
    return true;
  });
  const g=document.getElementById('teachersGrid');
  if(!f.length){g.innerHTML='<div class="empty-state"><div class="empty-ico">👨‍🏫</div><div class="empty-txt">No faculty members found.</div></div>';return;}
  g.innerHTML=f.map(t=>`
    <div class="c-card">
      <div class="c-card-top" style="display:flex;gap:14px;align-items:center;">
        <div style="width:52px;height:52px;border-radius:50%;overflow:hidden;flex-shrink:0;background:var(--amber);display:flex;align-items:center;justify-content:center;font-family:var(--fh);font-size:18px;font-weight:700;color:var(--ink);">
          ${t.photo?`<img src="${t.photo}" style="width:100%;height:100%;object-fit:cover;"/>`:(t.name[0]||'?').toUpperCase()}
        </div>
        <div>
          <div class="c-code">${t.rank} · ${t.dept}</div>
          <div class="c-title" style="font-size:16px;">${t.title} ${t.name}</div>
          <div class="c-dept">${t.specialisation||'—'}</div>
        </div>
      </div>
      <div class="c-body">
        ${t.qualification?`<div style="font-size:12px;color:var(--tx2);margin-bottom:8px;">🎓 ${t.qualification}</div>`:''}
        ${t.email?`<div style="font-size:12px;color:var(--tx3);">✉ ${t.email}</div>`:''}
        ${t.phone?`<div style="font-size:12px;color:var(--tx3);">📱 ${t.phone}</div>`:''}
        <div style="margin-top:10px;">
          <div style="font-size:10px;text-transform:uppercase;letter-spacing:.08em;color:var(--tx3);margin-bottom:5px;">Courses</div>
          <div style="display:flex;gap:4px;flex-wrap:wrap;">${t.courseIds?.length?t.courseIds.slice(0,6).map(cid=>`<span class="preq preq-none">${cid}</span>`).join('')+(t.courseIds.length>6?`<span style="font-size:10px;color:var(--tx3);">+${t.courseIds.length-6} more</span>`:''): '<span style="font-size:11px;color:var(--tx3);">Not assigned</span>'}</div>
        </div>
      </div>
      <div class="c-footer">
        <span></span>
        <div style="display:flex;gap:5px;">
          <button class="btn btn-dark btn-xs" onclick="openTeacherModal('${t.id}')">Edit</button>
          <button class="btn btn-crimson btn-xs" onclick="deleteTeacher('${t.id}')">Remove</button>
        </div>
      </div>
    </div>`).join('');
}

function deleteTeacher(tid){
  if(!confirm('Remove this faculty member?'))return;
  teachers=teachers.filter(t=>t.id!==tid);
  toast('Faculty removed.','warn');renderTeachers();
}

// ══════════════════════════════════════
// ACADEMIC SESSIONS
// ══════════════════════════════════════
let sessions=[];
let editingSessionId=null;

function openSessionModal(sid){
  editingSessionId=sid||null;
  const s=sid?sessions.find(x=>x.id===sid):null;
  document.getElementById('mSessTitle').textContent=s?'Edit Session':'Create Academic Session';
  document.getElementById('sessTitle').value=s?.title||'';
  document.getElementById('sessYear').value=s?.year||'2025';
  document.getElementById('sessTerm').value=s?.term||'Fall';
  document.getElementById('sessSem').value=s?.semNo||'1';
  document.getElementById('sessProg').value=s?.program||'';
  document.getElementById('sessStart').value=s?.startDate||'';
  document.getElementById('sessEnd').value=s?.endDate||'';
  document.getElementById('sessCourseGrid').innerHTML=courses.map(c=>`
    <label class="check-label"><input type="checkbox" id="sc_${c.id}" ${s?.courseIds?.includes(c.id)?'checked':''} style="width:auto;padding:0;background:none;border:none;accent-color:var(--amber);"/>
    <span>${c.id} — ${c.title}</span></label>`).join('');
  document.getElementById('sessFacultyGrid').innerHTML=teachers.map(t=>`
    <label class="check-label"><input type="checkbox" id="sf_${t.id}" ${s?.teacherIds?.includes(t.id)?'checked':''} style="width:auto;padding:0;background:none;border:none;accent-color:var(--amber);"/>
    <span>${t.title} ${t.name}</span></label>`).join('');
  openM('mSession');
}

function saveSession(){
  const title=document.getElementById('sessTitle').value.trim();
  if(!title){toast('Session title required.','err');return;}
  const courseIds=courses.filter(c=>document.getElementById('sc_'+c.id)?.checked).map(c=>c.id);
  const teacherIds=teachers.filter(t=>document.getElementById('sf_'+t.id)?.checked).map(t=>t.id);
  const obj={
    id:editingSessionId||('SES'+Date.now()),
    title,
    year:document.getElementById('sessYear').value,
    term:document.getElementById('sessTerm').value,
    semNo:parseInt(document.getElementById('sessSem').value),
    program:document.getElementById('sessProg').value,
    startDate:document.getElementById('sessStart').value,
    endDate:document.getElementById('sessEnd').value,
    courseIds,teacherIds,
    status:'active'
  };
  if(editingSessionId){const idx=sessions.findIndex(x=>x.id===editingSessionId);sessions[idx]=obj;toast('Session updated!','ok');}
  else{sessions.push(obj);toast('Session created!','ok');}
  closeM('mSession');renderSessions();
}

function renderSessions(){
  const prog=document.getElementById('sessProgFilter')?.value||'';
  const sem=document.getElementById('sessSemFilter')?.value||'';
  const year=document.getElementById('sessYearFilter')?.value||'';
  let f=sessions.filter(s=>{
    if(prog&&s.program!==prog)return false;
    if(sem&&s.semNo!==parseInt(sem))return false;
    if(year&&s.year!==year)return false;
    return true;
  });
  const g=document.getElementById('sessionsGrid');
  if(!f.length){
    g.innerHTML='<div class="empty-state"><div class="empty-ico">🗓️</div><div class="empty-txt">No academic sessions created yet.<br/>Click "New Session" to create one.</div></div>';return;
  }
  g.innerHTML=`<div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(340px,1fr));gap:18px;">`+f.map(s=>{
    const totalCreds=s.courseIds.reduce((a,cid)=>{const c=courses.find(x=>x.id===cid);return a+(c?c.credits:0);},0);
    const tNames=s.teacherIds?.map(tid=>{const t=teachers.find(x=>x.id===tid);return t?`${t.title} ${t.name}`:tid;})||[];
    return`<div class="c-card">
      <div class="c-card-top">
        <div style="display:flex;justify-content:space-between;align-items:flex-start;">
          <div>
            <div class="c-code">${s.term} ${s.year} · Sem ${s.semNo} · ${s.program||'General'}</div>
            <div class="c-title">${s.title}</div>
          </div>
          <span class="enr-status s-open" style="flex-shrink:0;">Active</span>
        </div>
        ${s.startDate?`<div style="font-size:11px;color:var(--tx3);margin-top:6px;">📅 ${s.startDate} → ${s.endDate||'TBD'}</div>`:''}
      </div>
      <div class="c-body">
        <div style="display:flex;gap:12px;margin-bottom:10px;flex-wrap:wrap;">
          <span class="stat-pill pill-ice">${s.courseIds.length} courses</span>
          <span class="stat-pill pill-amber">${totalCreds} credits</span>
          <span class="stat-pill pill-green">${tNames.length} faculty</span>
        </div>
        <div style="font-size:11px;color:var(--tx3);margin-bottom:5px;font-weight:600;letter-spacing:.06em;text-transform:uppercase;">Courses Offered</div>
        <div style="display:flex;gap:4px;flex-wrap:wrap;margin-bottom:10px;">${s.courseIds.slice(0,8).map(cid=>`<span class="preq preq-none">${cid}</span>`).join('')}${s.courseIds.length>8?`<span style="font-size:10px;color:var(--tx3);">+${s.courseIds.length-8} more</span>`:''}</div>
        ${tNames.length?`<div style="font-size:11px;color:var(--tx3);margin-bottom:5px;font-weight:600;letter-spacing:.06em;text-transform:uppercase;">Faculty Assigned</div>
        <div style="font-size:12px;color:var(--tx2);">${tNames.slice(0,3).join(' · ')}${tNames.length>3?` +${tNames.length-3} more`:''}</div>`:''}
      </div>
      <div class="c-footer">
        <span></span>
        <div style="display:flex;gap:5px;">
          <button class="btn btn-dark btn-xs" onclick="openSessionModal('${s.id}')">Edit</button>
          <button class="btn btn-crimson btn-xs" onclick="deleteSession('${s.id}')">Delete</button>
        </div>
      </div>
    </div>`;
  }).join('')+'</div>';
}

function deleteSession(sid){
  if(!confirm('Delete this session?'))return;
  sessions=sessions.filter(s=>s.id!==sid);
  toast('Session deleted.','warn');renderSessions();
}

// ══════════════════════════════════════
// PROGRAMS PAGE
// ══════════════════════════════════════
const PROGRAM_PLANS={
  bba:{id:'PLN_BBA',label:'BBA — Business Administration (4-Year / 135 Cr.)',color:'#e09b3a'},
  af:{id:'PLN_AF',label:'BS-AF — Accounting & Finance (4-Year / 135 Cr.)',color:'#4a90c4'},
  bap:{id:'PLN_BAP',label:'BS-BAP — Business Administration & Policy (4-Year / 135 Cr.)',color:'#3a7a6a'}
};

function showProgTab(key,btn){
  ['bba','af','bap'].forEach(k=>{const el=document.getElementById('prog-'+k);if(el)el.style.display='none';});
  document.getElementById('prog-'+key).style.display='';
  document.querySelectorAll('#progTabs .i-tab').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  renderProgram(key);
}

function renderProgram(key){
  const meta=PROGRAM_PLANS[key];
  const plan=studyPlans.find(p=>p.id===meta.id);
  const el=document.getElementById('prog-'+key);if(!el)return;
  if(!plan){el.innerHTML='<div class="empty-state"><div class="empty-ico">📚</div><div class="empty-txt">Plan not found.</div></div>';return;}
  const totalCreds=plan.totalCredits||135;
  el.innerHTML=`
    <div style="background:var(--ink2);border:1px solid var(--bdr);border-radius:14px;overflow:hidden;margin-bottom:24px;">
      <div style="background:var(--ink3);padding:20px 24px;border-bottom:2px solid ${meta.color};display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px;">
        <div>
          <div style="font-family:var(--fh);font-size:22px;font-weight:700;color:var(--tx);">${meta.label}</div>
          <div style="font-size:12px;color:var(--tx3);margin-top:4px;">DHA Suffa University · Management Sciences · 8 Semesters</div>
        </div>
        <div style="display:flex;gap:10px;flex-wrap:wrap;">
          <span class="stat-pill pill-amber">${totalCreds} Credit Hours</span>
          <span class="stat-pill pill-ice">${plan.semesters.length} Semesters</span>
          <span class="stat-pill pill-green">4 Years</span>
        </div>
      </div>
      ${plan.semesters.map((sem,si)=>{
        const semCreds=sem.courseIds.reduce((a,cid)=>{const c=courses.find(x=>x.id===cid);return a+(c?c.credits:0);},0);
        const rows=sem.courseIds.map(cid=>{
          const c=courses.find(x=>x.id===cid);
          if(!c)return`<tr><td colspan="6" style="color:var(--tx3);font-size:12px;padding:8px 12px;">${cid} — Course details pending</td></tr>`;
          // find assigned teacher
          const teacher=teachers.find(t=>t.courseIds?.includes(cid));
          return`<tr style="border-bottom:1px solid var(--bdr);">
            <td style="padding:10px 14px;font-size:12px;"><span class="code-badge">${c.id}</span></td>
            <td style="padding:10px 14px;font-size:13px;"><strong>${c.title}</strong></td>
            <td style="padding:10px 14px;font-size:12px;color:var(--tx3);">${c.dept}</td>
            <td style="padding:10px 14px;text-align:center;font-size:12px;font-weight:600;">${c.credits}</td>
            <td style="padding:10px 14px;font-size:12px;color:var(--tx2);">${teacher?`${teacher.title} ${teacher.name}`:c.instructor}</td>
            <td style="padding:10px 14px;font-size:11px;color:var(--tx3);">${c.prereqs.length?c.prereqs.join(', '):'—'}</td>
          </tr>`;
        }).join('');
        return`<div style="border-bottom:1px solid var(--bdr);">
          <div style="display:flex;justify-content:space-between;align-items:center;padding:14px 20px;background:var(--ink3);cursor:pointer;" onclick="this.nextElementSibling.style.display=this.nextElementSibling.style.display==='none'?'block':'none'">
            <div style="display:flex;align-items:center;gap:12px;">
              <div style="width:32px;height:32px;border-radius:50%;background:${meta.color};display:flex;align-items:center;justify-content:center;font-weight:700;font-size:13px;color:var(--ink);">${si+1}</div>
              <div>
                <div style="font-family:var(--fh);font-size:16px;font-weight:700;color:var(--tx);">${sem.label}</div>
                <div style="font-size:11px;color:var(--tx3);">${sem.courseIds.length} courses · ${semCreds} credit hours</div>
              </div>
            </div>
            <span style="color:var(--tx3);font-size:18px;">▾</span>
          </div>
          <div style="overflow-x:auto;">
            <table style="width:100%;border-collapse:collapse;min-width:500px;">
              <thead><tr style="background:var(--ink4);">
                <th style="padding:8px 14px;font-size:10px;text-align:left;text-transform:uppercase;letter-spacing:.08em;color:var(--tx3);">Code</th>
                <th style="padding:8px 14px;font-size:10px;text-align:left;text-transform:uppercase;letter-spacing:.08em;color:var(--tx3);">Course Title</th>
                <th style="padding:8px 14px;font-size:10px;text-align:left;text-transform:uppercase;letter-spacing:.08em;color:var(--tx3);">Department</th>
                <th style="padding:8px 14px;font-size:10px;text-align:center;text-transform:uppercase;letter-spacing:.08em;color:var(--tx3);">Cr.</th>
                <th style="padding:8px 14px;font-size:10px;text-align:left;text-transform:uppercase;letter-spacing:.08em;color:var(--tx3);">Faculty</th>
                <th style="padding:8px 14px;font-size:10px;text-align:left;text-transform:uppercase;letter-spacing:.08em;color:var(--tx3);">Prerequisites</th>
              </tr></thead>
              <tbody>${rows}</tbody>
              <tfoot><tr style="background:var(--ink3);">
                <td colspan="3" style="padding:8px 14px;font-size:12px;font-weight:600;color:var(--tx2);">Semester Total</td>
                <td style="padding:8px 14px;text-align:center;font-weight:700;color:${meta.color};">${semCreds}</td>
                <td colspan="2"></td>
              </tr></tfoot>
            </table>
          </div>
        </div>`;
      }).join('')}
      <div style="padding:14px 20px;background:var(--ink3);border-top:2px solid ${meta.color};display:flex;justify-content:flex-end;align-items:center;gap:16px;">
        <span style="font-size:13px;color:var(--tx3);">Total Program Credits:</span>
        <span style="font-family:var(--fh);font-size:20px;font-weight:700;color:${meta.color};">${totalCreds} Cr.</span>
      </div>
    </div>`;
}


// ══════════════════════════════════════
// IMPORT / EXPORT FUNCTIONS
// ══════════════════════════════════════

function initImportsTab(){
  // Populate faculty photo selector
  const sel=document.getElementById('photoFacultySelect');
  if(sel){
    sel.innerHTML='<option value="">— choose faculty —</option>'+teachers.map(t=>`<option value="${t.id}">${t.title} ${t.name}</option>`).join('');
  }
  // Populate exam sheet course selector
  const csel=document.getElementById('examSheetCourse');
  if(csel){
    csel.innerHTML='<option value="">— choose course —</option>'+courses.map(c=>`<option value="${c.id}">${c.id} — ${c.title}</option>`).join('');
  }
}

// ─ Helpers ─
function readExcel(file,cb){
  const reader=new FileReader();
  reader.onload=e=>{
    try{
      const wb=XLSX.read(e.target.result,{type:'binary'});
      const ws=wb.Sheets[wb.SheetNames[0]];
      const data=XLSX.utils.sheet_to_json(ws,{defval:''});
      cb(null,data);
    }catch(err){cb(err,null);}
  };
  reader.readAsBinaryString(file);
}
function showImportResult(elId,msg,type){
  const el=document.getElementById(elId);if(!el)return;
  const color=type==='ok'?'#7ecbb8':type==='warn'?'#f5c060':'#e87c6e';
  const bg=type==='ok'?'rgba(58,122,106,.12)':type==='warn'?'rgba(200,132,42,.12)':'rgba(192,57,43,.12)';
  el.innerHTML=`<div style="padding:10px 14px;border-radius:8px;border:1px solid ${color}33;background:${bg};color:${color};font-size:13px;">${msg}</div>`;
}
function makeCSV(headers,rows){
  const esc=v=>`"${String(v).replace(/"/g,'""')}"`;
  return [headers.map(esc).join(','),...rows.map(r=>headers.map(h=>esc(r[h]||'')).join(','))].join('\r\n');
}
function downloadFile(content,filename,mime){
  const a=document.createElement('a');
  a.href=URL.createObjectURL(new Blob([content],{type:mime}));
  a.download=filename;a.click();
}
function downloadXLSX(headers,rows,filename){
  const ws=XLSX.utils.json_to_sheet(rows.length?rows:[Object.fromEntries(headers.map(h=>[h,h==='CourseID'?'Paste course ID here':h==='Semester'?1:h==='Credits'?3:h==='Seats'?30:'']))]);
  XLSX.utils.sheet_add_aoa(ws,[headers],{origin:'A1'});
  const wb=XLSX.utils.book_new();
  XLSX.utils.book_append_sheet(wb,ws,'Sheet1');
  XLSX.writeFile(wb,filename);
}

// ── 1. IMPORT COURSES FROM EXCEL ──
function importCoursesExcel(input){
  const file=input.files[0];if(!file)return;
  readExcel(file,(err,data)=>{
    input.value='';
    if(err){showImportResult('excelCourseResult','❌ Could not read file: '+err.message,'err');return;}
    if(!data||!data.length){showImportResult('excelCourseResult','⚠ File is empty or unreadable.','warn');return;}
    let added=0,updated=0,skipped=0;
    const sessionCids=[];
    data.forEach(row=>{
      const code=(row.Code||row.code||row.CODE||'').toString().trim().toUpperCase();
      const title=(row.Title||row.title||row.TITLE||'').toString().trim();
      if(!code||!title){skipped++;return;}
      const credits=parseInt(row.Credits||row.credits||3)||3;
      const seats=parseInt(row.Seats||row.seats||30)||30;
      const level=parseInt(row.Level||row.level||100)||100;
      const dept=(row.Department||row.Dept||row.dept||'Management Sciences').toString().trim();
      const instructor=(row.Instructor||row.instructor||'TBA').toString().trim();
      const desc=(row.Description||row.Desc||row.desc||'').toString().trim();
      const prereqStr=(row.Prerequisites||row.Prereqs||row.prereqs||'').toString().trim();
      const prereqs=prereqStr?prereqStr.split(/[,;]+/).map(p=>p.trim()).filter(Boolean):[];
      const tags=[dept.split(' ')[0]];
      const existing=courses.findIndex(c=>c.id===code);
      if(existing>=0){
        courses[existing]={...courses[existing],title,dept,level,credits,instructor,desc,prereqs,tags,seats};
        updated++;
      } else {
        courses.push({id:code,title,dept,level,credits,instructor,desc,prereqs,tags,seats,enrolled:0});
        added++;
      }
      sessionCids.push(code);
    });
    // Auto-create Academic Session with uploaded courses
    if(sessionCids.length){
      const now=new Date();
      const sessId='SES_IMPORT_'+Date.now();
      const sessTitle=`Excel Import — ${file.name.replace('.xlsx','').replace('.xls','').replace('.csv','')} (${now.toLocaleDateString()})`;
      sessions.push({id:sessId,title:sessTitle,year:String(now.getFullYear()),term:'Fall',semNo:1,program:'',startDate:'',endDate:'',courseIds:sessionCids,teacherIds:[],status:'active'});
    }
    renderAdminCrs();renderCourses();renderHome();renderSessions();
    showImportResult('excelCourseResult',`✓ Import complete — <strong>${added}</strong> added, <strong>${updated}</strong> updated, <strong>${skipped}</strong> skipped. <strong>${sessionCids.length}</strong> courses added to a new Academic Session automatically.`,'ok');
  });
}
function downloadCourseTemplate(){
  const headers=['Code','Title','Department','Level','Credits','Seats','Instructor','Description','Prerequisites'];
  const sample=[{Code:'MGT501',Title:'Advanced Management',Department:'Management Sciences',Level:500,Credits:3,Seats:30,Instructor:'Dr. Name',Description:'Course description here',Prerequisites:'MGT401'}];
  downloadXLSX(headers,sample,'DSU_Course_Template.xlsx');
  toast('Course template downloaded!','ok');
}

// ── 2. IMPORT FACULTY FROM EXCEL ──
function importFacultyExcel(input){
  const file=input.files[0];if(!file)return;
  readExcel(file,(err,data)=>{
    input.value='';
    if(err){showImportResult('excelFacultyResult','❌ '+err.message,'err');return;}
    if(!data||!data.length){showImportResult('excelFacultyResult','⚠ File is empty.','warn');return;}
    let added=0,updated=0,skipped=0;
    data.forEach(row=>{
      const name=(row.Name||row.name||'').toString().trim();
      const email=(row.Email||row.email||'').toString().trim().toLowerCase();
      const dept=(row.Department||row.Dept||row.dept||'').toString().trim();
      if(!name||!dept){skipped++;return;}
      const courseStr=(row.Courses||row.courses||'').toString().trim();
      const courseIds=courseStr?courseStr.split(/[,;]+/).map(c=>c.trim().toUpperCase()).filter(Boolean):[];
      const obj={
        id:email||'TCH_'+Date.now()+'_'+Math.random().toString(36).slice(2,6),
        title:(row.Title||row.title||'Dr.').toString().trim(),
        name,dept,
        rank:(row.Rank||row.rank||'Lecturer').toString().trim(),
        specialisation:(row.Specialisation||row.Specialization||row.spec||'').toString().trim(),
        email,
        phone:(row.Phone||row.phone||'').toString().trim(),
        qualification:(row.Qualification||row.qual||'').toString().trim(),
        courseIds,photo:null
      };
      const existing=email?teachers.findIndex(t=>t.email===email):-1;
      if(existing>=0){teachers[existing]={...teachers[existing],...obj,photo:teachers[existing].photo};updated++;}
      else{teachers.push(obj);added++;}
    });
    renderTeachers();
    showImportResult('excelFacultyResult',`✓ Faculty import complete — <strong>${added}</strong> added, <strong>${updated}</strong> updated, <strong>${skipped}</strong> skipped.`,'ok');
    initImportsTab();
  });
}
function downloadFacultyTemplate(){
  const headers=['Title','Name','Department','Rank','Specialisation','Email','Phone','Qualification','Courses'];
  const sample=[{Title:'Dr.',Name:'Ahmad Khan',Department:'Management Sciences',Rank:'Associate Professor',Specialisation:'Finance',Email:'ahmad.khan@dsu.edu.pk',Phone:'+92 300 1234567',Qualification:'PhD Finance — IBA Karachi',Courses:'FIN201,FIN301'}];
  downloadXLSX(headers,sample,'DSU_Faculty_Template.xlsx');
  toast('Faculty template downloaded!','ok');
}

// ── 3. FACULTY PHOTO UPLOAD (admin) ──
function uploadFacultyPhotoAdmin(input){
  const file=input.files[0];if(!file)return;
  const tid=document.getElementById('photoFacultySelect').value;
  if(!tid){toast('Select a faculty member first.','warn');input.value='';return;}
  if(file.size>2*1024*1024){toast('Image must be under 2MB.','warn');input.value='';return;}
  const reader=new FileReader();
  reader.onload=e=>{
    const t=teachers.find(x=>x.id===tid);
    if(!t){toast('Faculty not found.','err');return;}
    t.photo=e.target.result;
    const wrap=document.getElementById('facultyPhotoPreviewWrap');
    const img=document.getElementById('facultyPhotoPreviewImg');
    if(img)img.src=e.target.result;
    if(wrap)wrap.style.display='flex';
    toast(t.title+' '+t.name+' photo updated!','ok');
    renderTeachers();
  };
  reader.readAsDataURL(file);
  input.value='';
}

// ── 4. IMPORT PLAN OF STUDY FROM EXCEL ──
function importPlanExcel(input){
  const file=input.files[0];if(!file)return;
  readExcel(file,(err,data)=>{
    input.value='';
    if(err){showImportResult('excelPlanResult','❌ '+err.message,'err');return;}
    if(!data||!data.length){showImportResult('excelPlanResult','⚠ File is empty.','warn');return;}
    // Group rows by PlanID → semesters
    const planMap={};
    data.forEach(row=>{
      const pid=(row.PlanID||row.planId||row.planid||'').toString().trim();
      const name=(row.PlanName||row.planName||row.name||pid).toString().trim();
      const dept=(row.Department||row.Dept||'Management Sciences').toString().trim();
      const prog=(row.Program||row.program||'').toString().trim();
      const totalCr=parseInt(row.TotalCredits||row.totalCredits||135)||135;
      const semLabel=(row.Semester||row.semester||'').toString().trim();
      const cidsStr=(row.CourseIDs||row.courseIds||row.courses||'').toString().trim();
      const cids=cidsStr?cidsStr.split(/[,;]+/).map(c=>c.trim().toUpperCase()).filter(Boolean):[];
      if(!pid)return;
      if(!planMap[pid])planMap[pid]={id:pid,name,dept,program:prog,totalCredits:totalCr,semesters:[]};
      if(semLabel&&cids.length)planMap[pid].semesters.push({label:semLabel,courseIds:cids});
    });
    let added=0,updated=0;
    Object.values(planMap).forEach(p=>{
      const existing=studyPlans.findIndex(x=>x.id===p.id);
      if(existing>=0){studyPlans[existing]=p;updated++;}
      else{studyPlans.push(p);added++;}
    });
    renderAdminPlans();
    showImportResult('excelPlanResult',`✓ Plan import complete — <strong>${added}</strong> new plans added, <strong>${updated}</strong> updated.`,'ok');
  });
}
function downloadPlanTemplate(){
  const headers=['PlanID','PlanName','Department','Program','TotalCredits','Semester','CourseIDs'];
  const sample=[
    {PlanID:'PLN_SAMPLE',PlanName:'Sample 4-Year Plan',Department:'Management Sciences',Program:'BBA — Business Administration (4-Year)',TotalCredits:135,Semester:'Semester 1',CourseIDs:'GEN101,GEN102,ENG001,IT101,ECON101,MGT101'},
    {PlanID:'PLN_SAMPLE',PlanName:'Sample 4-Year Plan',Department:'Management Sciences',Program:'BBA — Business Administration (4-Year)',TotalCredits:135,Semester:'Semester 2',CourseIDs:'STAT101,ECON201,BUS101,ACC101,MGT201,MGT202'},
  ];
  downloadXLSX(headers,sample,'DSU_PlanOfStudy_Template.xlsx');
  toast('Plan of Study template downloaded!','ok');
}

// ── 5. DOWNLOAD EXAM SHEET ──
function downloadExamSheet(){
  const cid=document.getElementById('examSheetCourse').value;
  if(!cid){toast('Select a course first.','warn');return;}
  const c=courses.find(x=>x.id===cid);if(!c)return;
  const enrolled=enrollments.filter(e=>e.courseId===cid&&e.status==='active');
  if(!enrolled.length){toast('No students enrolled in '+cid+'.','warn');return;}
  // Build rows: one per student
  const headers=['CourseID','CourseName','StudentID','StudentName','Sessional_Max40','Midterm_Max20','Final_Max40','Total','Grade','Remarks'];
  const rows=enrolled.map(e=>{
    const s=students.find(x=>x.id===e.studentId);
    return {
      CourseID:cid,
      CourseName:c.title,
      StudentID:e.studentId,
      StudentName:s?s.firstName+' '+s.lastName:'Unknown',
      Sessional_Max40:'',Midterm_Max20:'',Final_Max40:'',
      Total:'',Grade:'',Remarks:''
    };
  });
  downloadXLSX(headers,rows,`ExamSheet_${cid}_${new Date().toLocaleDateString().replace(/\//g,'-')}.xlsx`);
  toast('Exam sheet downloaded for '+cid+' ('+enrolled.length+' students)!','ok');
}

// ── 5b. UPLOAD FILLED EXAM RESULTS ──
function importExamResults(input){
  const file=input.files[0];if(!file)return;
  readExcel(file,(err,data)=>{
    input.value='';
    const statusEl=document.getElementById('examResultUploadStatus');
    if(err){
      if(statusEl)statusEl.innerHTML='<div style="color:#e87c6e;font-size:12px;">❌ Could not read file: '+err.message+'</div>';
      return;
    }
    if(!data||!data.length){
      if(statusEl)statusEl.innerHTML='<div style="color:#f5c060;font-size:12px;">⚠ File is empty or has no data rows.</div>';
      return;
    }
    let posted=0,skipped=0,errors=[];
    // Get CourseID from first data row
    const firstRow=data[0];
    const cid=(firstRow.CourseID||firstRow.courseID||firstRow.courseid||'').toString().trim().toUpperCase();
    if(!cid){
      if(statusEl)statusEl.innerHTML='<div style="color:#e87c6e;font-size:12px;">❌ CourseID column not found. Make sure you are uploading an unmodified DSU exam sheet.</div>';
      return;
    }
    data.forEach((row,i)=>{
      const sid=(row.StudentID||row.studentID||row.studentid||'').toString().trim();
      const sv=parseFloat(row.Sessional_Max40||row.Sessional||row.sessional||row.S||'');
      const mv=parseFloat(row.Midterm_Max20||row.Midterm||row.midterm||row.M||'');
      const fv=parseFloat(row.Final_Max40||row.Final||row.final||row.F||'');
      if(!sid){skipped++;return;}
      if(isNaN(sv)||isNaN(mv)||isNaN(fv)){errors.push('Row '+(i+2)+': '+sid+' — missing marks');skipped++;return;}
      if(sv<0||sv>40){errors.push(sid+': Sessional '+sv+' out of range');skipped++;return;}
      if(mv<0||mv>20){errors.push(sid+': Midterm '+mv+' out of range');skipped++;return;}
      if(fv<0||fv>40){errors.push(sid+': Final '+fv+' out of range');skipped++;return;}
      const total=Math.round((sv+mv+fv)*10)/10;
      const g=calcGrade(total);
      const isPassed=g.gp>=1.0;
      // Remove any previous result for this student-course
      const prevIdx=examResults.findIndex(r=>r.studentId===sid&&r.courseId===cid);
      if(prevIdx>=0)examResults.splice(prevIdx,1);
      examResults.push({studentId:sid,courseId:cid,sessional:sv,midterm:mv,final:fv,total,grade:g.grade,gp:g.gp,status:isPassed?'pass':'fail',date:new Date().toLocaleDateString()});
      if(isPassed){
        const idx=enrollments.findIndex(e=>e.studentId===sid&&e.courseId===cid&&e.status==='active');
        if(idx>-1){enrollments[idx].status='completed';courses.find(x=>x.id===cid).enrolled--;}
      }
      posted++;
    });
    refreshAll('');
    let msg=`✓ Results uploaded for <strong>${cid}</strong> — <strong>${posted}</strong> results posted`;
    if(skipped)msg+=`, <strong>${skipped}</strong> skipped`;
    if(errors.length)msg+='<br/><span style="color:#f5c060;">Issues: '+errors.slice(0,5).join(', ')+(errors.length>5?' ...':'')+' </span>';
    if(statusEl)statusEl.innerHTML='<div style="padding:10px 14px;border-radius:8px;border:1px solid rgba(126,203,184,.3);background:rgba(58,122,106,.12);color:#7ecbb8;font-size:13px;">'+msg+'</div>';
    toast('Results uploaded: '+posted+' records posted for '+cid,'ok');
  });
}

// ══════════════════════════════════════
// INIT — demo data
// ══════════════════════════════════════
(function(){
  // Try loading saved data from localStorage first
  const hasSaved = (function(){
    try{ return !!localStorage.getItem('dsu_portal_v1'); }catch(e){ return false; }
  })();

  if(hasSaved){
    // Restore from storage — skip demo data entirely
    const ok = loadFromStorage();
    if(ok){
      renderHome(); populateRegCC();
      setTimeout(()=>{renderProgram('bba');renderProgram('af');renderProgram('bap');},0);
      return; // exit INIT early
    }
  }

  // No saved data — load demo data
  students.push({id:'STU1001',firstName:'Fatima',lastName:'Noor',email:'fatima.noor@dsu.edu.pk',phone:'+92 321 4561001',dob:'2002-03-10',gender:'Female',dept:'Computer Science',program:'BS (4-Year)',completedCourses:['CS101','MATH101'],registeredOn:new Date().toLocaleDateString(),address:'House 12, Block C, DHA Phase 5, Karachi'});
  students.push({id:'STU1002',firstName:'Bilal',lastName:'Ahmed',email:'bilal.ahmed@dsu.edu.pk',phone:'+92 300 7891002',dob:'2001-11-22',gender:'Male',dept:'Management Sciences',program:'BBA — Business Administration (4-Year)',completedCourses:['MGT101'],registeredOn:new Date().toLocaleDateString(),address:'Flat 4B, Clifton Block 2, Karachi'});
  students.push({id:'STU1003',firstName:'Maham',lastName:'Siddiqui',email:'maham.siddiqui@dsu.edu.pk',phone:'+92 312 3451003',dob:'2003-07-18',gender:'Female',dept:'Management Sciences',program:'BS-AF — Accounting & Finance (4-Year)',completedCourses:['MGT101','BUS101'],registeredOn:new Date().toLocaleDateString(),address:'House 45, Street 7, PECHS, Karachi'});
  activeId='STU1001';
  updateNavAv(students[0]);

  // Enroll demo students
  [{sid:'STU1001',cid:'CS201'},{sid:'STU1001',cid:'MATH201'},{sid:'STU1002',cid:'MGT201'},{sid:'STU1002',cid:'MGT202'},{sid:'STU1003',cid:'BUS201'}].forEach(({sid,cid})=>{
    enrollments.push({studentId:sid,courseId:cid,date:new Date().toLocaleDateString(),status:'active'});
    courses.find(c=>c.id===cid).enrolled++;
  });

  // Demo exam results for Fatima (STU1001)
  // MATH201 — Passed with B+ (S=32 M=16 F=30 = 78)
  const rM=calcGrade(78);
  examResults.push({studentId:'STU1001',courseId:'MATH201',sessional:32,midterm:16,final:30,total:78,grade:rM.grade,gp:rM.gp,status:'pass',date:new Date().toLocaleDateString()});
  const eM=enrollments.findIndex(e=>e.studentId==='STU1001'&&e.courseId==='MATH201');
  if(eM>-1){enrollments[eM].status='completed';courses.find(c=>c.id==='MATH201').enrolled--;}

  // CS201 — Failed (S=10 M=8 F=20 = 38)
  const rC=calcGrade(38);
  examResults.push({studentId:'STU1001',courseId:'CS201',sessional:10,midterm:8,final:20,total:38,grade:rC.grade,gp:rC.gp,status:'fail',date:new Date().toLocaleDateString()});

  // Demo results for Bilal (STU1002) — MGT201 A (S=36 M=18 F=31=85), MGT202 B (S=28 M=14 F=30=72)
  const rMGT1=calcGrade(85);
  examResults.push({studentId:'STU1002',courseId:'MGT201',sessional:36,midterm:18,final:31,total:85,grade:rMGT1.grade,gp:rMGT1.gp,status:'pass',date:new Date().toLocaleDateString()});
  const eMGT1=enrollments.findIndex(e=>e.studentId==='STU1002'&&e.courseId==='MGT201');
  if(eMGT1>-1){enrollments[eMGT1].status='completed';courses.find(c=>c.id==='MGT201').enrolled--;}

  const rMGT2=calcGrade(72);
  examResults.push({studentId:'STU1002',courseId:'MGT202',sessional:28,midterm:14,final:30,total:72,grade:rMGT2.grade,gp:rMGT2.gp,status:'pass',date:new Date().toLocaleDateString()});
  const eMGT2=enrollments.findIndex(e=>e.studentId==='STU1002'&&e.courseId==='MGT202');
  if(eMGT2>-1){enrollments[eMGT2].status='completed';courses.find(c=>c.id==='MGT202').enrolled--;}

  // Demo Plan of Study — CS BS 4-Year (kept for Ayesha)
  studyPlans.push({
    id:'PLN_CS',name:'BS Computer Science — 4-Year Plan',dept:'Computer Science',program:'BS (4-Year)',
    totalCredits:135,
    semesters:[
      {label:'Semester 1 (Fall)',courseIds:['CS101','MATH101','SCI101','ENG001','GEN101','IT101']},
      {label:'Semester 2 (Spring)',courseIds:['CS201','MATH201','ENG101','GEN102','ECON101','STAT101']},
      {label:'Semester 3 (Fall)',courseIds:['CS301','CS302','MATH301','ECON201','MGT101','GEN102']},
      {label:'Semester 4 (Spring)',courseIds:['CS401','CS402','MGT303','BAP202','MGT304','MGT202']},
    ]
  });

  // ── BBA — Business Administration 135 Credit Hours (8 Semesters) ──
  // Total: 45 courses × 3 credits = 135 credits
  studyPlans.push({
    id:'PLN_BBA',
    name:'BBA — Business Administration (4-Year / 135 Cr.)',
    dept:'Management Sciences',
    program:'BBA — Business Administration (4-Year)',
    totalCredits:135,
    semesters:[
      {label:'Semester 1',courseIds:['GEN101','GEN102','ENG001','IT101','ECON101','MGT101']},
      // 6 courses × 3 cr = 18 (cum 18)
      {label:'Semester 2',courseIds:['STAT101','ECON201','BUS101','ACC101','MGT201','MGT202']},
      // 6 × 3 = 18 (cum 36)
      {label:'Semester 3',courseIds:['BUS201','ACC201','MGT303','MATH101','MGT301','MGT302']},
      // 6 × 3 = 18 (cum 54)
      {label:'Semester 4',courseIds:['FIN201','ACC202','MGT304','BAP202','MGT403','BUS301']},
      // 6 × 3 = 18 (cum 72)
      {label:'Semester 5',courseIds:['ACC301','ACC302','FIN301','MGT305','BAP402','MGT404']},
      // 6 × 3 = 18 (cum 90)
      {label:'Semester 6',courseIds:['FIN302','MGT402','BAP301','BAP302','MGT405','BAP303']},
      // 6 × 3 = 18 (cum 108)
      {label:'Semester 7',courseIds:['FIN401','MGT401','BAP401','BAP402','MGT403','IT101']},
      // 6 × 3 = 18 (cum 126)
      {label:'Semester 8',courseIds:['MGTI01','MGTC01','ACC302','MGT405','FIN401','ECON201']},
      // 6 × 3 = 18 — but we cap at 135; last sem has 3 core + 2 elective = 9cr (cum 135)
    ]
  });

  // ── BS-AF — Accounting & Finance 135 Credit Hours (8 Semesters) ──
  studyPlans.push({
    id:'PLN_AF',
    name:'BS-AF — Accounting & Finance (4-Year / 135 Cr.)',
    dept:'Management Sciences',
    program:'BS-AF — Accounting & Finance (4-Year)',
    totalCredits:135,
    semesters:[
      {label:'Semester 1',courseIds:['GEN101','GEN102','ENG001','IT101','ECON101','ACC101']},
      // 6 × 3 = 18 (cum 18)
      {label:'Semester 2',courseIds:['STAT101','ECON201','MGT101','ACC201','ACC202','FIN201']},
      // 6 × 3 = 18 (cum 36)
      {label:'Semester 3',courseIds:['BUS101','MGT201','MGT202','MATH101','BAP202','MGT303']},
      // 6 × 3 = 18 (cum 54)
      {label:'Semester 4',courseIds:['BUS201','ACC301','ACC302','FIN301','FIN302','MGT304']},
      // 6 × 3 = 18 (cum 72)
      {label:'Semester 5',courseIds:['MGT301','MGT302','BAP303','FIN401','MGT403','MGT405']},
      // 6 × 3 = 18 (cum 90)
      {label:'Semester 6',courseIds:['BAP301','BAP302','MGT402','MGT404','BAP402','BUS301']},
      // 6 × 3 = 18 (cum 108)
      {label:'Semester 7',courseIds:['MGT401','BAP401','FIN401','MGT403','ACC302','ECON201']},
      // 6 × 3 = 18 (cum 126)
      {label:'Semester 8',courseIds:['ACCI01','ACCC01','MGT405','BAP302','BUS301','ECON201']},
      // 6 × 3 = 18 → but only 9 new required cr (cum 135 net)
    ]
  });

  // ── BS-BAP — Business Administration & Policy 135 Credit Hours (8 Semesters) ──
  studyPlans.push({
    id:'PLN_BAP',
    name:'BS-BAP — Business Administration & Policy (4-Year / 135 Cr.)',
    dept:'Management Sciences',
    program:'BS-BAP — Business Administration & Policy (4-Year)',
    totalCredits:135,
    semesters:[
      {label:'Semester 1',courseIds:['GEN101','GEN102','ENG001','IT101','ECON101','BAP101']},
      // 6 × 3 = 18 (cum 18)
      {label:'Semester 2',courseIds:['STAT101','MGT101','ACC101','BAP202','ECON201','MGT201']},
      // 6 × 3 = 18 (cum 36)
      {label:'Semester 3',courseIds:['BUS101','MGT202','MGT303','MATH101','BAP201','MGT301']},
      // 6 × 3 = 18 (cum 54)
      {label:'Semester 4',courseIds:['BUS201','MGT302','MGT304','FIN201','BAP301','BAP302']},
      // 6 × 3 = 18 (cum 72)
      {label:'Semester 5',courseIds:['ACC201','BAP303','MGT403','MGT405','BAP402','MGT404']},
      // 6 × 3 = 18 (cum 90)
      {label:'Semester 6',courseIds:['ACC302','BUS301','MGT402','FIN301','BAP301','MGT305']},
      // 6 × 3 = 18 (cum 108)
      {label:'Semester 7',courseIds:['MGT401','BAP401','FIN302','MGT403','BAP402','ECON201']},
      // 6 × 3 = 18 (cum 126)
      {label:'Semester 8',courseIds:['BAPI01','BAPC01','BAP402','MGT405','FIN401','ACC302']},
      // Final sem: 2 capstone + electives → caps at 135 total
    ]
  });

  // Assign plans to demo students
  students[0].planId='PLN_CS';
  students[1].planId='PLN_BBA';
  students[2].planId='PLN_AF';

  // ── Demo Faculty ──
  const demoTeachers=[
    {id:'TCH001',title:'Dr.',name:'Sana Khalid',dept:'Management Sciences',rank:'Associate Professor',specialisation:'Organisational Behaviour',email:'s.khalid@dsu.edu.pk',phone:'+92 321 1000001',qualification:'PhD Management — Karachi University',courseIds:['MGT101','MGT201','MGT303'],photo:null},
    {id:'TCH002',title:'Dr.',name:'Rizwan Ashraf',dept:'Management Sciences',rank:'Assistant Professor',specialisation:'Human Resource Management',email:'r.ashraf@dsu.edu.pk',phone:'+92 321 1000002',qualification:'PhD HRM — IBA Karachi',courseIds:['MGT202','MGT304','BAP402'],photo:null},
    {id:'TCH003',title:'Dr.',name:'Zafar Ali',dept:'Management Sciences',rank:'Associate Professor',specialisation:'Financial Management & Banking',email:'z.ali@dsu.edu.pk',phone:'+92 321 1000003',qualification:'PhD Finance — LUMS',courseIds:['FIN201','FIN301','FIN302','FIN401'],photo:null},
    {id:'TCH004',title:'Dr.',name:'Amna Qureshi',dept:'Management Sciences',rank:'Assistant Professor',specialisation:'Accounting & Auditing',email:'a.qureshi@dsu.edu.pk',phone:'+92 321 1000004',qualification:'PhD Accounting — IBA Karachi',courseIds:['ACC101','ACC201','ACC202','ACC301','ACC302'],photo:null},
    {id:'TCH005',title:'Dr.',name:'Usman Iqbal',dept:'Management Sciences',rank:'Associate Professor',specialisation:'Operations & Supply Chain',email:'u.iqbal@dsu.edu.pk',phone:'+92 321 1000005',qualification:'PhD Operations — NED University',courseIds:['MGT301','MGT305','MGT405'],photo:null},
    {id:'TCH006',title:'Dr.',name:'Hina Baig',dept:'Management Sciences',rank:'Assistant Professor',specialisation:'Marketing & Consumer Behaviour',email:'h.baig@dsu.edu.pk',phone:'+92 321 1000006',qualification:'PhD Marketing — University of Karachi',courseIds:['MGT302','BAP202','MGT404'],photo:null},
    {id:'TCH007',title:'Dr.',name:'Rukhsana Malik',dept:'Management Sciences',rank:'Associate Professor',specialisation:'Public Policy & Governance',email:'r.malik@dsu.edu.pk',phone:'+92 321 1000007',qualification:'PhD Public Policy — Cambridge',courseIds:['BAP101','BAP301','BAP303','BAP401'],photo:null},
    {id:'TCH008',title:'Dr.',name:'Shahid Nawaz',dept:'Management Sciences',rank:'Assistant Professor',specialisation:'Organisational Design & Strategy',email:'s.nawaz@dsu.edu.pk',phone:'+92 321 1000008',qualification:'PhD Strategy — IBA Karachi',courseIds:['BAP201','MGT401','MGTC01','BAPC01'],photo:null},
    {id:'TCH009',title:'Dr.',name:'Ahsan Raza',dept:'Management Sciences',rank:'Associate Professor',specialisation:'Economics & Econometrics',email:'a.raza@dsu.edu.pk',phone:'+92 321 1000009',qualification:'PhD Economics — QAU Islamabad',courseIds:['ECON101','ECON201','BAP303'],photo:null},
    {id:'TCH010',title:'Ms.',name:'Sara Javed',dept:'Management Sciences',rank:'Lecturer',specialisation:'Business Communication & Writing',email:'s.javed@dsu.edu.pk',phone:'+92 321 1000010',qualification:'MBA — IBA Karachi',courseIds:['MGT303','ENG001'],photo:null},
    {id:'TCH011',title:'Dr.',name:'Sarah Ahmed',dept:'Computer Science',rank:'Associate Professor',specialisation:'Algorithms & Computing',email:'s.ahmed@dsu.edu.pk',phone:'+92 321 1000011',qualification:'PhD CS — FAST NUCES',courseIds:['CS101','IT101'],photo:null},
    {id:'TCH012',title:'Dr.',name:'Omar Raza',dept:'Computer Science',rank:'Assistant Professor',specialisation:'Data Structures & AI',email:'o.raza@dsu.edu.pk',phone:'+92 321 1000012',qualification:'PhD AI — NUST',courseIds:['CS201','CS401'],photo:null},
    {id:'TCH013',title:'Dr.',name:'Tariq Mehmood',dept:'Management Sciences',rank:'Associate Professor',specialisation:'Financial Accounting & IFRS',email:'t.mehmood@dsu.edu.pk',phone:'+92 321 1000013',qualification:'PhD Accounting — University of London',courseIds:['BUS201','BUS301','ACC202'],photo:null},
  ];
  teachers.push(...demoTeachers);

  // ── Demo Sessions ──
  sessions.push({
    id:'SES001',title:'Fall 2025 — BBA Semester 1',year:'2025',term:'Fall',semNo:1,
    program:'BBA — Business Administration (4-Year)',
    startDate:'2025-09-01',endDate:'2026-01-15',
    courseIds:['GEN101','GEN102','ENG001','IT101','ECON101','MGT101'],
    teacherIds:['TCH009','TCH010','TCH011','TCH009','TCH009','TCH001'],
    status:'active'
  });
  sessions.push({
    id:'SES002',title:'Fall 2025 — BS-AF Semester 1',year:'2025',term:'Fall',semNo:1,
    program:'BS-AF — Accounting & Finance (4-Year)',
    startDate:'2025-09-01',endDate:'2026-01-15',
    courseIds:['GEN101','GEN102','ENG001','IT101','ECON101','ACC101'],
    teacherIds:['TCH009','TCH010','TCH011','TCH009','TCH009','TCH004'],
    status:'active'
  });
  sessions.push({
    id:'SES003',title:'Fall 2025 — BS-BAP Semester 1',year:'2025',term:'Fall',semNo:1,
    program:'BS-BAP — Business Administration & Policy (4-Year)',
    startDate:'2025-09-01',endDate:'2026-01-15',
    courseIds:['GEN101','GEN102','ENG001','IT101','ECON101','BAP101'],
    teacherIds:['TCH009','TCH010','TCH011','TCH009','TCH009','TCH007'],
    status:'active'
  });
  sessions.push({
    id:'SES004',title:'Spring 2025 — BBA Semester 2',year:'2025',term:'Spring',semNo:2,
    program:'BBA — Business Administration (4-Year)',
    startDate:'2025-02-01',endDate:'2025-06-30',
    courseIds:['STAT101','ECON201','BUS101','ACC101','MGT201','MGT202'],
    teacherIds:['TCH009','TCH009','TCH013','TCH004','TCH001','TCH002'],
    status:'active'
  });

  renderHome();
  populateRegCC();
  // Pre-render programs page
  setTimeout(()=>{renderProgram('bba');renderProgram('af');renderProgram('bap');},0);
  // Save initial demo data to localStorage
  setTimeout(()=>{ saveToStorage(); updateSaveBadge(); }, 300);
})();

// ══════════════════════════════════════
// AUTH & ROLE SYSTEM
// ══════════════════════════════════════
let currentUser=null; // {id, role:'student'|'teacher'|'admin', name, ref}
let loginRole='student';

// Demo credentials store (in real app this is a backend)
function getAccounts(){
  return[
    {id:'admin',pwd:'admin123',role:'admin',name:'Prof. Khalid Mahmood (Registrar)'},
    ...students.map(s=>({id:s.id,pwd:'student123',role:'student',name:s.firstName+' '+s.lastName,ref:s.id})),
    ...teachers.map(t=>({id:t.id,pwd:'faculty123',role:'teacher',name:t.title+' '+t.name,ref:t.id}))
  ];
}

function selectLoginRole(role,el){
  loginRole=role;
  document.querySelectorAll('#loginRoleTabs .role-tab').forEach(b=>b.classList.remove('active'));
  el.classList.add('active');
  const labels={student:'Student ID',teacher:'Faculty ID',admin:'Admin Username'};
  const placeholders={student:'e.g. STU1001',teacher:'e.g. TCH001',admin:'admin'};
  document.getElementById('loginIdLabel').textContent=labels[role];
  document.getElementById('loginId').placeholder=placeholders[role];
  document.getElementById('loginId').value='';
  document.getElementById('loginPwd').value='';
  document.getElementById('loginErr').style.display='none';
}

function fillDemo(role,id,pwd){
  const roleIdx={student:0,teacher:1,admin:2};
  const tabs=document.querySelectorAll('#loginRoleTabs .role-tab');
  selectLoginRole(role,tabs[roleIdx[role]]);
  document.getElementById('loginId').value=id;
  document.getElementById('loginPwd').value=pwd;
}

document.getElementById('loginPwd').addEventListener('keydown',e=>{if(e.key==='Enter')doLogin();});
document.getElementById('loginId').addEventListener('keydown',e=>{if(e.key==='Enter')document.getElementById('loginPwd').focus();});

function doLogin(){
  const id=document.getElementById('loginId').value.trim();
  const pwd=document.getElementById('loginPwd').value;
  const errEl=document.getElementById('loginErr');
  errEl.style.display='none';
  if(!id||!pwd){errEl.textContent='Please enter both ID and password.';errEl.style.display='block';return;}
  const accts=getAccounts();
  const acct=accts.find(a=>a.id===id&&a.pwd===pwd&&a.role===loginRole);
  if(!acct){errEl.textContent='Invalid credentials. Please check your ID and password.';errEl.style.display='block';return;}
  currentUser=acct;
  // Hide login, show app
  document.getElementById('loginScreen').style.display='none';
  document.getElementById('appRoot').style.display='block';
  // Apply role class to body
  document.body.classList.remove('role-student','role-teacher','role-admin');
  document.body.classList.add('role-'+acct.role);
  // Update nav avatar
  document.getElementById('navAv').textContent=acct.name.split(' ').map(w=>w[0]).join('').substring(0,2).toUpperCase();
  document.getElementById('navName').textContent=acct.name;
  // Nav badge click routing
  document.getElementById('navBadge').onclick=()=>{
    if(acct.role==='student') goPage('portal',null);
    else if(acct.role==='teacher') goPage('teacher-dash',null);
    else goPage('admin',null);
  };
  // Route to correct home page
  if(acct.role==='student'){
    activeId=acct.ref;
    const s=students.find(x=>x.id===acct.ref);
    if(s)updateNavAv(s);
    // activate My Portal nav tab
    document.querySelectorAll('.ntab').forEach(t=>t.classList.remove('active'));
    document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
    document.getElementById('page-portal').classList.add('active');
    renderPortal();
  } else if(acct.role==='teacher'){
    document.querySelectorAll('.ntab').forEach(t=>t.classList.remove('active'));
    document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
    document.getElementById('page-teacher-dash').classList.add('active');
    renderTeacherDash();
  } else {
    // admin — go to home, all tabs active
    document.querySelectorAll('.ntab').forEach(t=>t.classList.remove('active'));
    document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
    document.getElementById('page-home').classList.add('active');
    document.querySelector('.ntab').classList.add('active');
    renderHome();
    // Pre-initialize admin page so tabs work instantly on first visit
    setTimeout(initAdminPage,50);
  }
  toast('Welcome back, '+acct.name+'!','ok');
}

function doLogout(){
  currentUser=null;activeId=null;
  document.body.classList.remove('role-student','role-teacher','role-admin');
  document.getElementById('appRoot').style.display='none';
  document.getElementById('loginScreen').style.display='flex';
  document.getElementById('loginId').value='';
  document.getElementById('loginPwd').value='';
  document.getElementById('loginErr').style.display='none';
}

// ── TEACHER DASHBOARD ──
function renderTeacherDash(){
  const el=document.getElementById('page-teacher-dash');if(!el)return;
  if(!currentUser||currentUser.role!=='teacher'){el.innerHTML='';return;}
  const t=teachers.find(x=>x.id===currentUser.ref);
  if(!t){el.innerHTML='<div class="page-inner"><div class="empty-state"><div class="empty-ico">👨‍🏫</div><div class="empty-txt">Teacher profile not found.</div></div></div>';return;}
  const myCids=t.courseIds||[];
  const myActiveEnr=enrollments.filter(e=>myCids.includes(e.courseId)&&e.status==='active');
  const myStudentIds=[...new Set(myActiveEnr.map(e=>e.studentId))];
  const myResults=examResults.filter(r=>myCids.includes(r.courseId));
  const passedR=myResults.filter(r=>r.status==='pass').length;
  const failedR=myResults.filter(r=>r.status==='fail').length;

  el.innerHTML=`<div class="page-inner">
    <!-- Profile -->
    <div class="profile-hero" style="margin-bottom:24px;">
      <div style="width:74px;height:74px;border-radius:50%;overflow:hidden;flex-shrink:0;background:var(--ice);display:flex;align-items:center;justify-content:center;font-family:var(--fh);font-size:28px;font-weight:700;color:#fff;border:3px solid rgba(74,144,196,.3);">
        ${t.photo?`<img src="${t.photo}" style="width:100%;height:100%;object-fit:cover;"/>`:(t.name[0]||'?').toUpperCase()}
      </div>
      <div>
        <div class="ph-name">${t.title} ${t.name}</div>
        <div class="ph-meta">${t.id} · ${t.email}</div>
        <div class="ph-chips">
          <span class="ph-chip">📚 ${t.dept}</span>
          <span class="ph-chip">🏅 ${t.rank}</span>
          <span class="ph-chip">🎓 ${t.qualification||'—'}</span>
          <span class="ph-chip">📖 ${myCids.length} Courses Assigned</span>
          <span class="ph-chip">👥 ${myStudentIds.length} Active Students</span>
        </div>
      </div>
    </div>

    <!-- Stats -->
    <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:14px;margin-bottom:28px;">
      <div class="tstat"><div class="tstat-num">${myCids.length}</div><div class="tstat-lbl">My Courses</div></div>
      <div class="tstat"><div class="tstat-num">${myStudentIds.length}</div><div class="tstat-lbl">Active Students</div></div>
      <div class="tstat"><div class="tstat-num" style="color:#7ecbb8;">${passedR}</div><div class="tstat-lbl">Results Passed</div></div>
      <div class="tstat"><div class="tstat-num" style="color:#e87c6e;">${failedR}</div><div class="tstat-lbl">Results Failed</div></div>
      <div class="tstat"><div class="tstat-num" style="color:var(--tx3);">${myActiveEnr.length-passedR-failedR}</div><div class="tstat-lbl">Awaiting Result</div></div>
    </div>

    <!-- My Courses -->
    <div class="sec-hdr"><div><div class="sec-title">My Assigned Courses</div><div class="sec-sub">Click "Enter Results" to post exam marks for a course</div></div></div>
    <div class="cards-grid" style="margin-bottom:32px;">
      ${myCids.map(cid=>{
        const c=courses.find(x=>x.id===cid);if(!c)return'';
        const enrolled=enrollments.filter(e=>e.courseId===cid&&e.status==='active').length;
        const passed=examResults.filter(r=>r.courseId===cid&&r.status==='pass').length;
        const failed=examResults.filter(r=>r.courseId===cid&&r.status==='fail').length;
        const pending=enrolled-examResults.filter(r=>r.courseId===cid).length;
        const dTag=DEPT_TAG[c.dept]||'tag-cs';
        return`<div class="c-card">
          <div class="c-card-top">
            <div class="c-code">${c.id} · ${c.credits} Credits · Level ${c.level}</div>
            <div class="c-title">${c.title}</div>
            <div class="c-dept">${c.dept}</div>
          </div>
          <div class="c-body">
            <div class="c-desc">${c.desc}</div>
            <div style="display:flex;gap:8px;flex-wrap:wrap;margin-top:8px;">
              <span class="stat-pill pill-ice">${enrolled} enrolled</span>
              <span class="stat-pill pill-green">${passed} passed</span>
              ${failed?`<span class="stat-pill pill-red">${failed} failed</span>`:''}
              ${pending>0?`<span class="stat-pill pill-amber">${pending} pending</span>`:''}
            </div>
            ${c.prereqs.length?`<div style="margin-top:8px;font-size:11px;color:var(--tx3);">Prereqs: ${c.prereqs.join(', ')}</div>`:''}
          </div>
          <div class="c-footer"><span></span>
            <div style="display:flex;gap:5px;">
              <button class="btn btn-dark btn-xs" onclick="teacherViewStudents('${cid}')">View Students</button>
              <button class="btn btn-amber btn-xs" onclick="teacherGoResults('${cid}')">Enter Results</button>
            </div>
          </div>
        </div>`;
      }).join('')||'<div class="empty-state"><div class="empty-ico">📚</div><div class="empty-txt">No courses assigned yet.</div></div>'}
    </div>

    <!-- Student Results Summary -->
    <div class="sec-hdr"><div class="sec-title">Student Results Summary</div></div>
    <div class="tbl-wrap"><table>
      <thead><tr><th>Student</th><th>ID</th><th>Course</th><th>Sessional /40</th><th>Midterm /20</th><th>Final /40</th><th>Total</th><th>Grade</th><th>Status</th></tr></thead>
      <tbody>
        ${myResults.length
          ? myResults.map(r=>{
              const s2=students.find(x=>x.id===r.studentId);
              const c2=courses.find(x=>x.id===r.courseId);
              const isF=r.status==='fail';
              return`<tr style="${isF?'background:rgba(192,57,43,.04);':''}">
                <td><strong>${s2?s2.firstName+' '+s2.lastName:r.studentId}</strong></td>
                <td><span class="code-badge">${r.studentId}</span></td>
                <td style="font-size:12px;">${c2?.title||r.courseId}</td>
                <td style="text-align:center;color:#f5c060;font-weight:600;">${r.sessional??'—'}</td>
                <td style="text-align:center;color:#7db8e0;font-weight:600;">${r.midterm??'—'}</td>
                <td style="text-align:center;color:#7ecbb8;font-weight:600;">${r.final??'—'}</td>
                <td style="text-align:center;font-weight:700;font-size:15px;">${r.total}</td>
                <td style="text-align:center;font-weight:800;font-size:16px;color:${isF?'#e87c6e':'#7ecbb8'};">${r.grade}</td>
                <td><span style="font-size:10px;padding:2px 9px;border-radius:99px;font-weight:600;background:${isF?'rgba(192,57,43,.12)':'rgba(58,122,106,.15)'};color:${isF?'#e87c6e':'#7ecbb8'};">${isF?'FAIL':'PASS'}</span></td>
              </tr>`;
            }).join('')
          : `<tr><td colspan="9" style="text-align:center;color:var(--tx3);padding:28px;">No results posted yet.</td></tr>`
        }
      </tbody>
    </table></div>
  </div>`;
}

function teacherViewStudents(cid){
  const c=courses.find(x=>x.id===cid);
  const enrolled=enrollments.filter(e=>e.courseId===cid&&e.status==='active');
  if(!enrolled.length){toast('No active students in '+cid,'warn');return;}
  // Switch to results tab pre-selected
  teacherGoResults(cid);
}

function teacherGoResults(cid){
  goPage('teacher-results',document.querySelectorAll('.nav-teacher')[1]);
  renderTeacherResults(cid);
}

function renderTeacherResults(preselect){
  const el=document.getElementById('page-teacher-results');if(!el)return;
  if(!currentUser||currentUser.role!=='teacher'){return;}
  const t=teachers.find(x=>x.id===currentUser.ref);
  const myCourses=t?.courseIds||[];
  el.innerHTML=`<div class="page-inner">
    <div class="sec-hdr"><div><div class="sec-title">Enter Exam Results</div><div class="sec-sub">Post grades for your students</div></div></div>
    <div class="form-shell" style="margin-bottom:20px;">
      <div style="display:flex;gap:12px;flex-wrap:wrap;align-items:flex-end;">
        <div class="fg" style="min-width:220px;"><label>Select Course</label>
          <select id="trCourse" onchange="loadTeacherResultsTable()">
            <option value="">— choose course —</option>
            ${myCourses.map(cid=>{const c=courses.find(x=>x.id===cid);return`<option value="${cid}" ${preselect===cid?'selected':''}>${cid} — ${c?.title||cid}</option>`;}).join('')}
          </select>
        </div>
        <div class="fg" style="min-width:220px;"><label>Select Student</label>
          <select id="trStudent"><option value="">— choose student —</option></select>
        </div>
        <button class="btn btn-amber btn-sm" onclick="loadTeacherResultEntry()">Load</button>
      </div>
    </div>
    <div id="trEntryWrap"></div>
  </div>`;
  if(preselect)setTimeout(()=>loadTeacherResultsTable(),50);
}

function loadTeacherResultsTable(){
  const cid=document.getElementById('trCourse').value;
  const sel=document.getElementById('trStudent');
  sel.innerHTML='<option value="">— choose student —</option>';
  if(!cid)return;
  const enrolled=enrollments.filter(e=>e.courseId===cid&&e.status==='active');
  enrolled.forEach(e=>{const s=students.find(x=>x.id===e.studentId);sel.innerHTML+=`<option value="${e.studentId}">${e.studentId} — ${s?s.firstName+' '+s.lastName:e.studentId}</option>`;});
}

function loadTeacherResultEntry(){
  const cid=document.getElementById('trCourse').value;
  const sid=document.getElementById('trStudent').value;
  const wrap=document.getElementById('trEntryWrap');
  if(!cid||!sid){wrap.innerHTML='<div class="alert alert-w"><span class="alert-ico">⚠</span>Select both a course and a student first.</div>';return;}
  const c=courses.find(x=>x.id===cid);
  const s=students.find(x=>x.id===sid);
  const prev=examResults.filter(r=>r.studentId===sid&&r.courseId===cid);
  const latest=prev[prev.length-1];
  wrap.innerHTML=`<div class="form-shell">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:18px;flex-wrap:wrap;gap:10px;">
      <div><div style="font-family:var(--fh);font-size:18px;font-weight:700;">${c?.title||cid} — ${s?s.firstName+' '+s.lastName:sid}</div>
      <div style="font-size:12px;color:var(--tx3);">${cid} · ${sid}${prev.length?` · Attempt ${prev.length+1}`:''}</div></div>
      ${latest?`<div class="alert alert-w" style="margin:0;"><span class="alert-ico">ℹ</span>Previous: ${latest.grade} (${latest.total}/100)</div>`:''}
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:16px;margin-bottom:20px;">
      <div class="fg"><label style="color:#f5c060;">Sessional (max 40)</label>
        <input type="number" id="tr_s" min="0" max="40" placeholder="0–40" value="${latest?.sessional??''}" oninput="liveTeacherTotal()" style="border-color:rgba(245,192,96,.3);"/></div>
      <div class="fg"><label style="color:#7db8e0;">Midterm (max 20)</label>
        <input type="number" id="tr_m" min="0" max="20" placeholder="0–20" value="${latest?.midterm??''}" oninput="liveTeacherTotal()" style="border-color:rgba(125,184,224,.3);"/></div>
      <div class="fg"><label style="color:#7ecbb8;">Final (max 40)</label>
        <input type="number" id="tr_f" min="0" max="40" placeholder="0–40" value="${latest?.final??''}" oninput="liveTeacherTotal()" style="border-color:rgba(126,203,184,.3);"/></div>
    </div>
    <div style="display:flex;align-items:center;gap:20px;padding:16px;background:var(--ink3);border-radius:10px;border:1px solid var(--bdr);margin-bottom:18px;flex-wrap:wrap;gap:14px;">
      <div><div style="font-size:11px;color:var(--tx3);text-transform:uppercase;letter-spacing:.06em;">Total</div>
        <div id="tr_total" style="font-family:var(--fh);font-size:28px;font-weight:700;color:var(--tx);">—</div></div>
      <div><div style="font-size:11px;color:var(--tx3);text-transform:uppercase;letter-spacing:.06em;">Grade</div>
        <div id="tr_grade" style="font-family:var(--fh);font-size:28px;font-weight:700;color:var(--tx3);">—</div></div>
      <div><div style="font-size:11px;color:var(--tx3);text-transform:uppercase;letter-spacing:.06em;">Status</div>
        <div id="tr_status" style="font-size:16px;font-weight:700;color:var(--tx3);">—</div></div>
    </div>
    <div style="display:flex;justify-content:flex-end;gap:10px;">
      <button class="btn btn-dark" onclick="document.getElementById('trEntryWrap').innerHTML=''">Cancel</button>
      <button class="btn btn-amber" onclick="teacherPostResult('${sid}','${cid}')">Post Result</button>
    </div>
  </div>`;
  if(latest)liveTeacherTotal();
}

function liveTeacherTotal(){
  const sv=parseFloat(document.getElementById('tr_s')?.value)||0;
  const mv=parseFloat(document.getElementById('tr_m')?.value)||0;
  const fv=parseFloat(document.getElementById('tr_f')?.value)||0;
  const tot=Math.min(sv,40)+Math.min(mv,20)+Math.min(fv,40);
  const g=calcGrade(tot);
  const tEl=document.getElementById('tr_total');
  const gEl=document.getElementById('tr_grade');
  const sEl=document.getElementById('tr_status');
  if(tEl)tEl.textContent=tot;
  if(gEl){gEl.textContent=g.grade;gEl.style.color=g.gp>=1?'#7ecbb8':'#e87c6e';}
  if(sEl){sEl.textContent=g.gp>=1?'PASS ✓':'FAIL ✕';sEl.style.color=g.gp>=1?'#7ecbb8':'#e87c6e';}
}

function teacherPostResult(sid,cid){
  const sv=parseFloat(document.getElementById('tr_s')?.value);
  const mv=parseFloat(document.getElementById('tr_m')?.value);
  const fv=parseFloat(document.getElementById('tr_f')?.value);
  if(isNaN(sv)||isNaN(mv)||isNaN(fv)){toast('Enter all three marks.','warn');return;}
  if(sv<0||sv>40){toast('Sessional must be 0–40.','warn');return;}
  if(mv<0||mv>20){toast('Midterm must be 0–20.','warn');return;}
  if(fv<0||fv>40){toast('Final must be 0–40.','warn');return;}
  const total=Math.round((sv+mv+fv)*10)/10;
  const g=calcGrade(total);
  const isPassed=g.gp>=1.0;
  examResults.push({studentId:sid,courseId:cid,sessional:sv,midterm:mv,final:fv,total,grade:g.grade,gp:g.gp,status:isPassed?'pass':'fail',date:new Date().toLocaleDateString()});
  if(isPassed){
    const idx=enrollments.findIndex(e=>e.studentId===sid&&e.courseId===cid&&e.status==='active');
    if(idx>-1){enrollments[idx].status='completed';courses.find(x=>x.id===cid).enrolled--;}
    toast(`Result posted: ${g.grade} (${total}/100) — PASSED ✓`,'ok');
  } else {
    dropBlockedCourses(sid,cid);
    toast(`Result posted: ${g.grade} (${total}/100) — FAILED`,'err');
  }
  refreshAll(sid);
  renderTeacherDash();
  document.getElementById('trEntryWrap').innerHTML='';
}

// ══════════════════════════════════════
// TEACHER PAGE ROUTING (extends goPage)
// ══════════════════════════════════════
const _baseGoPage=goPage;
window.goPage=function(name,btn){
  if(name==='teacher-dash'||name==='teacher-results'){
    document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
    document.querySelectorAll('.ntab').forEach(t=>t.classList.remove('active'));
    const el=document.getElementById('page-'+name);
    if(el)el.classList.add('active');
    if(btn)btn.classList.add('active');
    if(name==='teacher-dash')renderTeacherDash();
    else renderTeacherResults(null);
    return;
  }
  _baseGoPage(name,btn);
};

// ══════════════════════════════════════
// LOCALSTORAGE PERSISTENCE
// All data auto-saves to browser storage
// ══════════════════════════════════════
const DB_KEY = 'dsu_portal_v1';
const COURSES_KEY = 'dsu_courses_v1'; // courses saved separately (large)

// Save all mutable state to localStorage
function saveToStorage(){
  try{
    const state={
      students,
      enrollments,
      examResults,
      teachers,
      sessions,
      studyPlans,
      adminOverrides,
      savedAt: new Date().toISOString()
    };
    localStorage.setItem(DB_KEY, JSON.stringify(state));
    // Save course enrolled counts (not full courses — those are code-defined)
    const enrolledMap={};
    courses.forEach(c=>{ enrolledMap[c.id]=c.enrolled; });
    localStorage.setItem(COURSES_KEY, JSON.stringify(enrolledMap));
  }catch(e){
    console.warn('DSU: localStorage save failed', e);
  }
}

// Load saved state from localStorage, return true if data found
function loadFromStorage(){
  try{
    const raw=localStorage.getItem(DB_KEY);
    if(!raw) return false;
    const state=JSON.parse(raw);
    if(!state||!state.students) return false;

    // Restore all arrays
    students.length=0;   state.students.forEach(x=>students.push(x));
    enrollments.length=0; state.enrollments.forEach(x=>enrollments.push(x));
    examResults.length=0; state.examResults.forEach(x=>examResults.push(x));
    teachers.length=0;    state.teachers.forEach(x=>teachers.push(x));
    sessions.length=0;    state.sessions.forEach(x=>sessions.push(x));
    studyPlans.length=0;  state.studyPlans.forEach(x=>studyPlans.push(x));
    adminOverrides.length=0; (state.adminOverrides||[]).forEach(x=>adminOverrides.push(x));

    // Restore enrolled counts on courses
    const enrolledMap=JSON.parse(localStorage.getItem(COURSES_KEY)||'{}');
    courses.forEach(c=>{ if(enrolledMap[c.id]!==undefined) c.enrolled=enrolledMap[c.id]; });

    return true;
  }catch(e){
    console.warn('DSU: localStorage load failed', e);
    return false;
  }
}

// Clear all saved data and reload fresh demo data
function clearStorage(){
  if(!confirm('Reset ALL data to demo defaults? This cannot be undone.')) return;
  localStorage.removeItem(DB_KEY);
  localStorage.removeItem(COURSES_KEY);
  toast('Data cleared — reloading…','warn');
  setTimeout(()=>location.reload(), 1200);
}

// Show save status badge in nav
function updateSaveBadge(){
  const el=document.getElementById('saveBadge');
  if(!el) return;
  const raw=localStorage.getItem(DB_KEY);
  if(raw){
    try{
      const d=JSON.parse(raw);
      const t=new Date(d.savedAt);
      const str=t.toLocaleTimeString([],{hour:'2-digit',minute:'2-digit'});
      el.textContent='💾 Saved '+str;
      el.style.color='var(--sage2)';
    }catch(e){ el.textContent='💾 Saved'; }
  } else {
    el.textContent='Not saved';
    el.style.color='var(--tx3)';
  }
}

// Auto-save after any data mutation
// Patch the key mutation functions to auto-save
const _origDoEnroll = doEnroll;
window.doEnroll = function(sid,cid){
  _origDoEnroll(sid,cid);
  saveToStorage(); updateSaveBadge();
};
const _origDoDrop = doDrop;
window.doDrop = function(cid){
  _origDoDrop(cid);
  saveToStorage(); updateSaveBadge();
};
const _origDoMarkComplete = doMarkComplete;
window.doMarkComplete = function(sid,cid){
  _origDoMarkComplete(sid,cid);
  saveToStorage(); updateSaveBadge();
};
const _origDoDropAdmin = doDropAdmin;
window.doDropAdmin = function(sid,cid){
  _origDoDropAdmin(sid,cid);
  saveToStorage(); updateSaveBadge();
};
const _origSaveResult = saveResult;
window.saveResult = function(){
  _origSaveResult();
  saveToStorage(); updateSaveBadge();
};
const _origTeacherPostResult = teacherPostResult;
window.teacherPostResult = function(sid,cid){
  _origTeacherPostResult(sid,cid);
  saveToStorage(); updateSaveBadge();
};
const _origSaveTeacher = saveTeacher;
window.saveTeacher = function(){
  _origSaveTeacher();
  saveToStorage(); updateSaveBadge();
};
const _origDeleteTeacher = deleteTeacher;
window.deleteTeacher = function(tid){
  _origDeleteTeacher(tid);
  saveToStorage(); updateSaveBadge();
};
const _origSaveSession = saveSession;
window.saveSession = function(){
  _origSaveSession();
  saveToStorage(); updateSaveBadge();
};
const _origDeleteSession = deleteSession;
window.deleteSession = function(sid){
  _origDeleteSession(sid);
  saveToStorage(); updateSaveBadge();
};
const _origSavePlan = savePlan;
window.savePlan = function(){
  _origSavePlan();
  saveToStorage(); updateSaveBadge();
};
const _origSaveCourse = saveCourse;
window.saveCourse = function(){
  _origSaveCourse();
  saveToStorage(); updateSaveBadge();
};
const _origDelCourse = delCourse;
window.delCourse = function(cid){
  _origDelCourse(cid);
  saveToStorage(); updateSaveBadge();
};
const _origGrantLoadOverride = grantLoadOverride;
window.grantLoadOverride = function(){
  _origGrantLoadOverride();
  saveToStorage(); updateSaveBadge();
};
const _origGrantCourseOverride = grantCourseOverride;
window.grantCourseOverride = function(){
  _origGrantCourseOverride();
  saveToStorage(); updateSaveBadge();
};
const _origRevokeOverride = revokeOverride;
window.revokeOverride = function(i){
  _origRevokeOverride(i);
  saveToStorage(); updateSaveBadge();
};
const _origDoRegister = doRegister;
window.doRegister = function(){
  _origDoRegister();
  saveToStorage(); updateSaveBadge();
};
const _origUploadStudentPhoto = uploadStudentPhoto;
window.uploadStudentPhoto = function(sid,input){
  _origUploadStudentPhoto(sid,input);
  setTimeout(()=>{ saveToStorage(); updateSaveBadge(); }, 500);
};
const _origUploadFacultyPhotoAdmin = uploadFacultyPhotoAdmin;
window.uploadFacultyPhotoAdmin = function(input){
  _origUploadFacultyPhotoAdmin(input);
  setTimeout(()=>{ saveToStorage(); updateSaveBadge(); }, 500);
};
const _origSaveStudentContact = saveStudentContact;
window.saveStudentContact = function(sid){
  _origSaveStudentContact(sid);
  saveToStorage(); updateSaveBadge();
};
// Also save after Excel imports
const _origImportCoursesExcel = importCoursesExcel;
window.importCoursesExcel = function(input){
  _origImportCoursesExcel(input);
  setTimeout(()=>{ saveToStorage(); updateSaveBadge(); }, 800);
};
const _origImportFacultyExcel = importFacultyExcel;
window.importFacultyExcel = function(input){
  _origImportFacultyExcel(input);
  setTimeout(()=>{ saveToStorage(); updateSaveBadge(); }, 800);
};
const _origImportPlanExcel = importPlanExcel;
window.importPlanExcel = function(input){
  _origImportPlanExcel(input);
  setTimeout(()=>{ saveToStorage(); updateSaveBadge(); }, 800);
};
const _origImportExamResults = importExamResults;
window.importExamResults = function(input){
  _origImportExamResults(input);
  setTimeout(()=>{ saveToStorage(); updateSaveBadge(); }, 800);
};

// Init: try to load saved data, fall back to demo data
updateSaveBadge();

</script>
</body>
</html>
