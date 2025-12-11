# ickcounter
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Ick Counter — Smirk Snow</title>
<style>
  :root{
    --bg:#fbf8ff;
    --card:#ffffff;
    --accent:#5a2d82;
    --noelle:#ff69b4;
    --charlie:#4da6ff;
    --reset:#d0d0d0;
  }

  html,body{
    height:100%;
    margin:0;
    font-family:system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial;
    background: linear-gradient(180deg,var(--bg) 0%, #f3f0fb 100%);
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
  }

  .wrap{
    min-height:100%;
    display:flex;
    align-items:center;
    justify-content:center;
    padding:28px;
    box-sizing:border-box;
    position:relative;
    overflow:hidden; /* keep emoji inside */
  }

  .app {
    width:100%;
    max-width:420px;
    background:var(--card);
    border-radius:18px;
    padding:20px;
    box-shadow:0 12px 30px rgba(60,30,90,0.08);
    text-align:center;
    z-index:2; /* above emoji layer so controls are tappable */
  }

  h1{
    margin:4px 0 12px;
    color:var(--accent);
    font-size:1.8rem;
    letter-spacing:-0.02em;
  }

  .counts{
    display:flex;
    gap:12px;
    justify-content:center;
    margin-bottom:14px;
    flex-wrap:wrap;
  }

  .count-card{
    background:linear-gradient(180deg,#fff,#fbfaff);
    border-radius:12px;
    padding:12px 18px;
    min-width:120px;
    box-shadow:0 6px 14px rgba(70,40,110,0.04);
  }

  .label{
    display:block;
    font-size:0.9rem;
    color:var(--accent);
    font-weight:700;
    margin-bottom:6px;
  }

  .value{
    font-size:1.8rem;
    font-weight:800;
    color:#222;
  }

  .buttons{
    margin-top:10px;
    display:flex;
    flex-direction:column;
    gap:10px;
  }

  .btn{
    padding:14px 16px;
    border-radius:12px;
    border:none;
    cursor:pointer;
    font-size:1.05rem;
    font-weight:700;
    color:#fff;
    box-shadow:0 6px 18px rgba(60,30,90,0.06);
  }

  .btn:active{ transform:scale(0.98); }

  .noelle { background:var(--noelle); }
  .charlie { background:var(--charlie); }

  .reset-row{
    margin-top:12px;
    display:flex;
    gap:8px;
    justify-content:center;
    align-items:center;
  }

  .reset-btn{
    background:var(--reset);
    color:#333;
    padding:8px 12px;
    border-radius:10px;
    border:none;
    font-weight:600;
    cursor:pointer;
  }

  .toggle-snow{
    background:#ffffffcc;
    border:1px solid #eee;
    padding:8px 12px;
    border-radius:10px;
    font-weight:600;
    cursor:pointer;
  }

  /* Floating smirk emojis container (positioned behind UI) */
  .emoji-layer{
    pointer-events:none; /* don't block taps */
    position:absolute;
    inset:0;
    z-index:1;
    overflow:hidden;
  }

  /* Each emoji element */
  .emoji {
    position:absolute;
    top:-10vh;
    will-change:transform,opacity;
    user-select:none;
    -webkit-user-select:none;
    font-size:28px; /* base, will be scaled via inline style */
    opacity:0.95;
    transform: translateY(-10vh);
    animation-
