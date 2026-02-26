# nexusglobal
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NEXUS GLOBAL — International Logistics</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Rajdhani:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #050810;
    --bg2: #080d1a;
    --surface: #0d1428;
    --surface2: #111c35;
    --accent: #00d4ff;
    --accent2: #ff6b35;
    --accent3: #39ff14;
    --text: #e8edf5;
    --muted: #5a6a8a;
    --border: rgba(0, 212, 255, 0.15);
    --glow: 0 0 20px rgba(0, 212, 255, 0.3);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Rajdhani', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom Cursor */
  .cursor {
    position: fixed;
    width: 12px; height: 12px;
    background: var(--accent);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s, width 0.2s, height 0.2s;
    mix-blend-mode: screen;
  }
  .cursor-ring {
    position: fixed;
    width: 36px; height: 36px;
    border: 1px solid var(--accent);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: transform 0.15s ease, width 0.3s, height 0.3s;
    opacity: 0.5;
  }

  /* Grid Background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 50px 50px;
    pointer-events: none;
    z-index: 0;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 60px;
    background: rgba(5,8,16,0.9);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
  }

  .logo {
    font-family: 'Orbitron', monospace;
    font-size: 1.4rem;
    font-weight: 900;
    letter-spacing: 4px;
    color: var(--accent);
    text-shadow: var(--glow);
  }
  .logo span { color: var(--accent2); }

  .nav-links {
    display: flex;
    gap: 40px;
    list-style: none;
  }
  .nav-links a {
    font-family: 'Space Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.3s;
    position: relative;
  }
  .nav-links a::after {
    content: '';
    position: absolute;
    bottom: -4px; left: 0;
    width: 0; height: 1px;
    background: var(--accent);
    transition: width 0.3s;
  }
  .nav-links a:hover { color: var(--accent); }
  .nav-links a:hover::after { width: 100%; }

  .nav-cta {
    font-family: 'Space Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    padding: 10px 24px;
    border: 1px solid var(--accent);
    color: var(--accent);
    text-decoration: none;
    position: relative;
    overflow: hidden;
    transition: color 0.3s;
  }
  .nav-cta::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--accent);
    transform: translateX(-100%);
    transition: transform 0.3s;
  }
  .nav-cta:hover { color: var(--bg); }
  .nav-cta:hover::before { transform: translateX(0); }
  .nav-cta span { position: relative; z-index: 1; }

  /* PAGES */
  .page { display: none; min-height: 100vh; padding-top: 80px; position: relative; z-index: 1; }
  .page.active { display: block; }

  /* HERO */
  #home {
    display: none;
    min-height: 100vh;
    padding-top: 80px;
    position: relative;
    z-index: 1;
    overflow: hidden;
  }
  #home.active { display: flex; flex-direction: column; justify-content: center; }

  .hero-bg {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 100%, rgba(0,212,255,0.08) 0%, transparent 60%),
      radial-gradient(ellipse 40% 40% at 80% 20%, rgba(255,107,53,0.06) 0%, transparent 50%);
  }

  .hero-content {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 60px;
    position: relative;
  }

  .hero-tag {
    font-family: 'Space Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 4px;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 24px;
    display: flex;
    align-items: center;
    gap: 12px;
    animation: fadeUp 0.8s ease both;
  }
  .hero-tag::before {
    content: '';
    width: 40px; height: 1px;
    background: var(--accent);
  }

  h1 {
    font-family: 'Orbitron', monospace;
    font-size: clamp(2.5rem, 6vw, 5.5rem);
    font-weight: 900;
    line-height: 1.0;
    letter-spacing: -1px;
    margin-bottom: 30px;
    animation: fadeUp 0.8s 0.1s ease both;
  }
  h1 .line2 { color: var(--accent); display: block; }
  h1 .line3 { color: var(--muted); font-size: 0.6em; font-weight: 400; display: block; letter-spacing: 8px; font-family: 'Space Mono', monospace; }

  .hero-desc {
    font-size: 1.2rem;
    color: var(--muted);
    max-width: 520px;
    line-height: 1.7;
    margin-bottom: 50px;
    animation: fadeUp 0.8s 0.2s ease both;
  }

  .hero-actions {
    display: flex;
    gap: 20px;
    animation: fadeUp 0.8s 0.3s ease both;
  }

  .btn-primary {
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    padding: 16px 36px;
    background: var(--accent);
    color: var(--bg);
    border: none;
    cursor: none;
    font-weight: 700;
    position: relative;
    overflow: hidden;
    transition: box-shadow 0.3s;
  }
  .btn-primary:hover { box-shadow: 0 0 30px rgba(0,212,255,0.5); }

  .btn-outline {
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    padding: 16px 36px;
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
    cursor: none;
    transition: border-color 0.3s, color 0.3s;
  }
  .btn-outline:hover { border-color: var(--accent); color: var(--accent); }

  /* Stats Bar */
  .stats-bar {
    display: flex;
    gap: 0;
    margin-top: 80px;
    border-top: 1px solid var(--border);
    animation: fadeUp 0.8s 0.5s ease both;
  }
  .stat-item {
    flex: 1;
    padding: 30px 40px;
    border-right: 1px solid var(--border);
  }
  .stat-item:last-child { border-right: none; }
  .stat-num {
    font-family: 'Orbitron', monospace;
    font-size: 2.2rem;
    font-weight: 700;
    color: var(--accent);
  }
  .stat-label {
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    margin-top: 6px;
  }

  /* Floating globe visual */
  .hero-visual {
    position: absolute;
    right: 60px;
    top: 50%;
    transform: translateY(-40%);
    width: 380px;
    height: 380px;
    animation: fadeUp 0.8s 0.4s ease both;
  }
  .globe {
    width: 100%; height: 100%;
    border-radius: 50%;
    border: 1px solid rgba(0,212,255,0.2);
    position: relative;
    animation: spin 30s linear infinite;
    background: radial-gradient(circle at 30% 30%, rgba(0,212,255,0.1), transparent 60%),
                radial-gradient(circle at 70% 70%, rgba(255,107,53,0.05), transparent 50%);
  }
  .globe::before, .globe::after {
    content: '';
    position: absolute;
    inset: -1px;
    border-radius: 50%;
    border: 1px solid rgba(0,212,255,0.1);
    transform: rotateX(70deg);
  }
  .globe::after { transform: rotateY(70deg); }
  .globe-ring {
    position: absolute;
    inset: -30px;
    border-radius: 50%;
    border: 1px solid rgba(0,212,255,0.1);
  }
  .globe-ring2 {
    position: absolute;
    inset: -60px;
    border-radius: 50%;
    border: 1px dashed rgba(0,212,255,0.05);
    animation: spin 20s linear infinite reverse;
  }
  .globe-dot {
    position: absolute;
    width: 8px; height: 8px;
    background: var(--accent);
    border-radius: 50%;
    box-shadow: 0 0 10px var(--accent);
    animation: pulse 2s ease infinite;
  }
  .globe-dot:nth-child(1) { top: 20%; left: 30%; animation-delay: 0s; }
  .globe-dot:nth-child(2) { top: 60%; left: 70%; animation-delay: 0.5s; background: var(--accent2); box-shadow: 0 0 10px var(--accent2); }
  .globe-dot:nth-child(3) { top: 40%; left: 80%; animation-delay: 1s; }
  .globe-dot:nth-child(4) { top: 75%; left: 25%; animation-delay: 1.5s; background: var(--accent3); box-shadow: 0 0 10px var(--accent3); }

  /* SECTION COMMON */
  .section {
    max-width: 1200px;
    margin: 0 auto;
    padding: 100px 60px;
  }

  .section-tag {
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 4px;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-tag::before { content: '//'; color: var(--accent2); }

  .section-title {
    font-family: 'Orbitron', monospace;
    font-size: clamp(1.8rem, 3vw, 2.8rem);
    font-weight: 700;
    margin-bottom: 16px;
  }

  .section-sub {
    color: var(--muted);
    font-size: 1.1rem;
    max-width: 580px;
    line-height: 1.7;
    margin-bottom: 60px;
  }

  /* SERVICES */
  .services-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    background: var(--border);
  }

  .service-card {
    background: var(--surface);
    padding: 40px;
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
  }
  .service-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px; height: 0;
    background: var(--accent);
    transition: height 0.4s;
  }
  .service-card:hover { background: var(--surface2); }
  .service-card:hover::before { height: 100%; }

  .service-icon {
    font-size: 2.5rem;
    margin-bottom: 20px;
    display: block;
  }
  .service-num {
    position: absolute;
    top: 20px; right: 24px;
    font-family: 'Orbitron', monospace;
    font-size: 0.65rem;
    color: var(--muted);
    letter-spacing: 2px;
  }
  .service-card h3 {
    font-family: 'Orbitron', monospace;
    font-size: 0.9rem;
    font-weight: 700;
    letter-spacing: 2px;
    margin-bottom: 14px;
    color: var(--text);
  }
  .service-card p {
    font-size: 0.95rem;
    color: var(--muted);
    line-height: 1.7;
  }

  /* TRACKING */
  .tracking-container {
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 50px;
    position: relative;
  }
  .tracking-container::before {
    content: 'AI TRACKING SYSTEM';
    position: absolute;
    top: -10px; left: 30px;
    background: var(--surface);
    padding: 0 12px;
    font-family: 'Space Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 3px;
    color: var(--accent);
  }

  .tracking-input-row {
    display: flex;
    gap: 0;
    margin-bottom: 40px;
  }
  .tracking-input {
    flex: 1;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-right: none;
    padding: 16px 24px;
    font-family: 'Space Mono', monospace;
    font-size: 0.85rem;
    color: var(--text);
    letter-spacing: 2px;
    outline: none;
    transition: border-color 0.3s;
  }
  .tracking-input:focus { border-color: var(--accent); }
  .tracking-input::placeholder { color: var(--muted); }

  .track-btn {
    background: var(--accent);
    color: var(--bg);
    border: none;
    padding: 16px 32px;
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    cursor: none;
    font-weight: 700;
    transition: box-shadow 0.3s;
  }
  .track-btn:hover { box-shadow: 0 0 20px rgba(0,212,255,0.4); }

  .tracking-result { display: none; }
  .tracking-result.show { display: block; }

  .track-timeline {
    display: flex;
    flex-direction: column;
    gap: 0;
  }
  .track-step {
    display: flex;
    gap: 24px;
    position: relative;
    padding-bottom: 30px;
  }
  .track-step::before {
    content: '';
    position: absolute;
    left: 11px; top: 28px;
    width: 1px; height: calc(100% - 28px);
    background: var(--border);
  }
  .track-step:last-child::before { display: none; }
  .track-dot {
    width: 24px; height: 24px;
    border-radius: 50%;
    background: var(--surface2);
    border: 2px solid var(--border);
    flex-shrink: 0;
    margin-top: 2px;
    transition: all 0.3s;
  }
  .track-dot.done { background: var(--accent); border-color: var(--accent); box-shadow: 0 0 12px rgba(0,212,255,0.5); }
  .track-dot.active { background: var(--accent2); border-color: var(--accent2); box-shadow: 0 0 12px rgba(255,107,53,0.5); animation: pulse 1.5s infinite; }
  .track-info h4 {
    font-family: 'Orbitron', monospace;
    font-size: 0.75rem;
    letter-spacing: 2px;
    margin-bottom: 4px;
  }
  .track-info p { font-size: 0.9rem; color: var(--muted); }
  .track-info .track-time { font-family: 'Space Mono', monospace; font-size: 0.65rem; color: var(--accent); letter-spacing: 2px; margin-top: 4px; }

  /* AI STATUS */
  .ai-status {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 30px;
    padding: 12px 20px;
    background: rgba(57,255,20,0.05);
    border: 1px solid rgba(57,255,20,0.2);
    width: fit-content;
  }
  .ai-dot {
    width: 8px; height: 8px;
    background: var(--accent3);
    border-radius: 50%;
    box-shadow: 0 0 8px var(--accent3);
    animation: pulse 1.5s infinite;
  }
  .ai-text {
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent3);
  }

  /* QUOTE CALCULATOR */
  .quote-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    background: var(--border);
  }
  .quote-panel {
    background: var(--surface);
    padding: 50px;
  }

  .form-group { margin-bottom: 24px; }
  .form-label {
    display: block;
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 10px;
  }
  .form-input, .form-select {
    width: 100%;
    background: var(--bg2);
    border: 1px solid var(--border);
    padding: 14px 18px;
    font-family: 'Rajdhani', sans-serif;
    font-size: 1rem;
    color: var(--text);
    outline: none;
    transition: border-color 0.3s;
    appearance: none;
  }
  .form-input:focus, .form-select:focus { border-color: var(--accent); }
  .form-select option { background: var(--surface); }

  .quote-result {
    background: var(--surface);
    padding: 50px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .quote-amount {
    font-family: 'Orbitron', monospace;
    font-size: 3.5rem;
    font-weight: 900;
    color: var(--accent);
    text-shadow: var(--glow);
    margin-bottom: 8px;
    transition: all 0.4s;
  }
  .quote-label {
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 40px;
  }

  .quote-breakdown {
    width: 100%;
    margin-bottom: 30px;
  }
  .breakdown-row {
    display: flex;
    justify-content: space-between;
    padding: 12px 0;
    border-bottom: 1px solid var(--border);
    font-size: 0.95rem;
  }
  .breakdown-row .val { color: var(--accent); font-family: 'Space Mono', monospace; font-size: 0.8rem; }

  /* CONTACT */
  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1.5fr;
    gap: 2px;
    background: var(--border);
  }
  .contact-info {
    background: var(--surface);
    padding: 60px 50px;
  }
  .contact-form-panel {
    background: var(--surface);
    padding: 60px 50px;
  }

  .contact-item {
    display: flex;
    gap: 20px;
    margin-bottom: 40px;
    align-items: flex-start;
  }
  .contact-icon {
    font-size: 1.5rem;
    padding-top: 4px;
    flex-shrink: 0;
  }
  .contact-detail h4 {
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 8px;
  }
  .contact-detail p { color: var(--muted); font-size: 1rem; line-height: 1.6; }

  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  .form-textarea {
    width: 100%;
    background: var(--bg2);
    border: 1px solid var(--border);
    padding: 14px 18px;
    font-family: 'Rajdhani', sans-serif;
    font-size: 1rem;
    color: var(--text);
    outline: none;
    resize: vertical;
    min-height: 120px;
    transition: border-color 0.3s;
  }
  .form-textarea:focus { border-color: var(--accent); }

  .submit-btn {
    width: 100%;
    background: var(--accent);
    color: var(--bg);
    border: none;
    padding: 18px;
    font-family: 'Space Mono', monospace;
    font-size: 0.8rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    cursor: none;
    font-weight: 700;
    margin-top: 8px;
    transition: box-shadow 0.3s;
  }
  .submit-btn:hover { box-shadow: 0 0 30px rgba(0,212,255,0.4); }

  /* AI ASSISTANT */
  .ai-chat-widget {
    position: fixed;
    bottom: 30px; right: 30px;
    z-index: 200;
  }
  .ai-chat-toggle {
    width: 60px; height: 60px;
    background: var(--accent);
    border: none;
    border-radius: 50%;
    cursor: none;
    font-size: 1.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 0 30px rgba(0,212,255,0.4);
    transition: transform 0.3s;
  }
  .ai-chat-toggle:hover { transform: scale(1.1); }

  .ai-chat-panel {
    position: absolute;
    bottom: 80px; right: 0;
    width: 360px;
    background: var(--surface);
    border: 1px solid var(--border);
    display: none;
    flex-direction: column;
    overflow: hidden;
    box-shadow: 0 20px 60px rgba(0,0,0,0.5);
  }
  .ai-chat-panel.open { display: flex; }

  .ai-chat-header {
    background: var(--surface2);
    padding: 16px 20px;
    display: flex;
    align-items: center;
    gap: 12px;
    border-bottom: 1px solid var(--border);
  }
  .ai-chat-header .ai-dot { width: 10px; height: 10px; }
  .ai-chat-header h4 {
    font-family: 'Orbitron', monospace;
    font-size: 0.75rem;
    letter-spacing: 2px;
  }

  .ai-messages {
    padding: 20px;
    height: 260px;
    overflow-y: auto;
    display: flex;
    flex-direction: column;
    gap: 12px;
  }
  .ai-messages::-webkit-scrollbar { width: 4px; }
  .ai-messages::-webkit-scrollbar-track { background: var(--bg2); }
  .ai-messages::-webkit-scrollbar-thumb { background: var(--accent); }

  .msg {
    padding: 12px 16px;
    font-size: 0.9rem;
    line-height: 1.5;
    max-width: 85%;
  }
  .msg.bot {
    background: var(--surface2);
    border-left: 2px solid var(--accent);
    align-self: flex-start;
  }
  .msg.user {
    background: rgba(0,212,255,0.1);
    border-right: 2px solid var(--accent);
    align-self: flex-end;
    text-align: right;
  }

  .ai-input-row {
    display: flex;
    border-top: 1px solid var(--border);
  }
  .ai-input {
    flex: 1;
    background: var(--bg2);
    border: none;
    padding: 14px 16px;
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.95rem;
    color: var(--text);
    outline: none;
  }
  .ai-send {
    background: var(--accent);
    border: none;
    padding: 14px 20px;
    color: var(--bg);
    cursor: none;
    font-size: 1.1rem;
    font-weight: 700;
  }

  /* FOOTER */
  footer {
    border-top: 1px solid var(--border);
    position: relative;
    z-index: 1;
  }
  .footer-grid {
    max-width: 1200px;
    margin: 0 auto;
    padding: 60px 60px 40px;
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 60px;
  }
  .footer-brand p { color: var(--muted); font-size: 0.95rem; line-height: 1.7; margin-top: 16px; }

  .footer-col h4 {
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 20px;
  }
  .footer-col ul { list-style: none; }
  .footer-col ul li { margin-bottom: 10px; }
  .footer-col ul li a {
    color: var(--muted);
    text-decoration: none;
    font-size: 0.95rem;
    transition: color 0.3s;
    cursor: none;
  }
  .footer-col ul li a:hover { color: var(--text); }

  .footer-bottom {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px 60px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-top: 1px solid var(--border);
  }
  .footer-bottom p {
    font-family: 'Space Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 2px;
    color: var(--muted);
    text-transform: uppercase;
  }

  /* Animations */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes spin { to { transform: rotate(360deg); } }
  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.6; transform: scale(0.9); }
  }

  /* NOTIFICATION */
  .notification {
    position: fixed;
    top: 100px; right: 30px;
    background: var(--surface);
    border: 1px solid var(--accent);
    padding: 16px 24px;
    font-family: 'Space Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 2px;
    color: var(--accent);
    z-index: 300;
    transform: translateX(200%);
    transition: transform 0.4s;
    max-width: 300px;
  }
  .notification.show { transform: translateX(0); }

  @media (max-width: 768px) {
    nav { padding: 16px 24px; }
    .nav-links { display: none; }
    .hero-content { padding: 0 24px; }
    .hero-visual { display: none; }
    .section { padding: 60px 24px; }
    .services-grid { grid-template-columns: 1fr; }
    .quote-grid, .contact-grid { grid-template-columns: 1fr; }
    .footer-grid { grid-template-columns: 1fr 1fr; padding: 40px 24px; }
    .stats-bar { flex-direction: column; }
    h1 { font-size: 2.2rem; }
  }
</style>
</head>
<body>

<!-- Custom Cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- Notification -->
<div class="notification" id="notification"></div>

<!-- NAV -->
<nav>
  <div class="logo">NEXUS<span>.</span>GLOBAL</div>
  <ul class="nav-links">
    <li><a href="#" onclick="showPage('home')">Home</a></li>
    <li><a href="#" onclick="showPage('services')">Services</a></li>
    <li><a href="#" onclick="showPage('tracking')">Tracking</a></li>
    <li><a href="#" onclick="showPage('quote')">Get Quote</a></li>
    <li><a href="#" onclick="showPage('contact')">Contact</a></li>
  </ul>
  <a href="#" class="nav-cta" onclick="showPage('quote')"><span>Get Quote</span></a>
</nav>

<!-- HOME PAGE -->
<section id="home" class="page active">
  <div class="hero-bg"></div>
  <div class="hero-content">
    <div class="hero-tag">AI-Powered International Logistics</div>
    <h1>
      MOVE CARGO<br>
      <span class="line2">ACROSS BORDERS</span>
      <span class="line3">WITH INTELLIGENCE</span>
    </h1>
    <p class="hero-desc">Real-time AI-driven shipment tracking, intelligent route optimization, and seamless global logistics for the modern enterprise.</p>
    <div class="hero-actions">
      <button class="btn-primary" onclick="showPage('tracking')">Track Shipment</button>
      <button class="btn-outline" onclick="showPage('quote')">Get Instant Quote</button>
    </div>

    <div class="stats-bar">
      <div class="stat-item">
        <div class="stat-num">180+</div>
        <div class="stat-label">Countries Served</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">2.4M</div>
        <div class="stat-label">Shipments / Year</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">99.7%</div>
        <div class="stat-label">On-Time Delivery</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">AI</div>
        <div class="stat-label">Real-Time Tracking</div>
      </div>
    </div>
  </div>

  <div class="hero-visual">
    <div class="globe-ring2"></div>
    <div class="globe-ring"></div>
    <div class="globe">
      <div class="globe-dot"></div>
      <div class="globe-dot"></div>
      <div class="globe-dot"></div>
      <div class="globe-dot"></div>
    </div>
  </div>
</section>

<!-- SERVICES PAGE -->
<section id="services" class="page">
  <div class="section">
    <div class="section-tag">What We Offer</div>
    <h2 class="section-title">GLOBAL LOGISTICS SOLUTIONS</h2>
    <p class="section-sub">From air freight to last-mile delivery, our AI systems optimize every step of your supply chain.</p>

    <div class="services-grid">
      <div class="service-card">
        <span class="service-num">01</span>
        <span class="service-icon">✈️</span>
        <h3>AIR FREIGHT</h3>
        <p>Express air cargo solutions to over 180 countries. AI-optimized routing ensures fastest transit times with real-time flight tracking and automated customs clearance.</p>
      </div>
      <div class="service-card">
        <span class="service-num">02</span>
        <span class="service-icon">🚢</span>
        <h3>OCEAN FREIGHT</h3>
        <p>Full container load (FCL) and less-than-container load (LCL) services. Machine learning models predict port congestion and optimize sailing schedules automatically.</p>
      </div>
      <div class="service-card">
        <span class="service-num">03</span>
        <span class="service-icon">🚛</span>
        <h3>ROAD FREIGHT</h3>
        <p>Cross-border trucking with intelligent route planning. Our AI analyzes traffic, weather, and border wait times to deliver on schedule, every time.</p>
      </div>
      <div class="service-card">
        <span class="service-num">04</span>
        <span class="service-icon">🏭</span>
        <h3>WAREHOUSING</h3>
        <p>Smart warehouses with automated inventory management. IoT sensors and AI provide real-time stock visibility across our global network of 240+ facilities.</p>
      </div>
      <div class="service-card">
        <span class="service-num">05</span>
        <span class="service-icon">📦</span>
        <h3>LAST-MILE DELIVERY</h3>
        <p>Dynamic routing algorithms for urban and rural last-mile delivery. Predictive analytics reduce failed deliveries by 87% and cut costs significantly.</p>
      </div>
      <div class="service-card">
        <span class="service-num">06</span>
        <span class="service-icon">🛃</span>
        <h3>CUSTOMS BROKERAGE</h3>
        <p>AI-powered customs documentation and compliance. Automated HS code classification, duty calculation, and electronic filing across 180+ jurisdictions.</p>
      </div>
    </div>
  </div>
</section>

<!-- TRACKING PAGE -->
<section id="tracking" class="page">
  <div class="section">
    <div class="section-tag">Live Tracking</div>
    <h2 class="section-title">TRACK YOUR SHIPMENT</h2>
    <p class="section-sub">AI-powered real-time visibility into every stage of your cargo's journey. Enter your tracking number below.</p>

    <div class="ai-status">
      <div class="ai-dot"></div>
      <span class="ai-text">AI tracking engine online — 2,847 shipments monitored</span>
    </div>

    <div class="tracking-container">
      <div class="tracking-input-row">
        <input type="text" class="tracking-input" id="trackInput" placeholder="ENTER TRACKING NUMBER (e.g. NXG-2024-001847)" />
        <button class="track-btn" onclick="trackShipment()">TRACK</button>
      </div>

      <div class="tracking-result" id="trackResult">
        <div class="track-timeline">
          <div class="track-step">
            <div class="track-dot done"></div>
            <div class="track-info">
              <h4>ORDER RECEIVED</h4>
              <p>Shipment booked and confirmed — Shanghai, China</p>
              <p class="track-time">2024-03-01 09:14 CST</p>
            </div>
          </div>
          <div class="track-step">
            <div class="track-dot done"></div>
            <div class="track-info">
              <h4>CUSTOMS CLEARANCE</h4>
              <p>AI-automated export declaration filed and approved</p>
              <p class="track-time">2024-03-02 14:33 CST</p>
            </div>
          </div>
          <div class="track-step">
            <div class="track-dot done"></div>
            <div class="track-info">
              <h4>DEPARTED ORIGIN</h4>
              <p>Flight NX-447 departed Shanghai Pudong International</p>
              <p class="track-time">2024-03-03 23:10 CST</p>
            </div>
          </div>
          <div class="track-step">
            <div class="track-dot active"></div>
            <div class="track-info">
              <h4>IN TRANSIT — DUBAI HUB ✦ CURRENT</h4>
              <p>Cargo in transit at Dubai Logistics Hub — ETA Frankfurt 14h</p>
              <p class="track-time">2024-03-04 07:22 GST — AI ETA: March 5, 16:00 CET</p>
            </div>
          </div>
          <div class="track-step">
            <div class="track-dot"></div>
            <div class="track-info">
              <h4>ARRIVAL — FRANKFURT</h4>
              <p>Expected arrival Frankfurt Airport, Germany</p>
              <p class="track-time">AI Predicted: 2024-03-05 16:00 CET</p>
            </div>
          </div>
          <div class="track-step">
            <div class="track-dot"></div>
            <div class="track-info">
              <h4>FINAL DELIVERY</h4>
              <p>Last-mile delivery to recipient address</p>
              <p class="track-time">AI Predicted: 2024-03-06 10:00–14:00 CET</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- QUOTE PAGE -->
<section id="quote" class="page">
  <div class="section">
    <div class="section-tag">Instant AI Quote</div>
    <h2 class="section-title">GET YOUR INSTANT QUOTE</h2>
    <p class="section-sub">Our AI pricing engine analyzes real-time market rates, fuel costs, and route data to give you the most competitive price instantly.</p>

    <div class="quote-grid">
      <div class="quote-panel">
        <div class="form-group">
          <label class="form-label">Service Type</label>
          <select class="form-select" id="qService" onchange="calcQuote()">
            <option value="air">Air Freight</option>
            <option value="ocean">Ocean Freight</option>
            <option value="road">Road Freight</option>
            <option value="express">Express Courier</option>
          </select>
        </div>
        <div class="form-row">
          <div class="form-group">
            <label class="form-label">Origin Country</label>
            <select class="form-select" id="qOrigin" onchange="calcQuote()">
              <option value="cn">China</option>
              <option value="us">USA</option>
              <option value="de">Germany</option>
              <option value="in">India</option>
              <option value="uk">UK</option>
            </select>
          </div>
          <div class="form-group">
            <label class="form-label">Destination</label>
            <select class="form-select" id="qDest" onchange="calcQuote()">
              <option value="us">USA</option>
              <option value="de">Germany</option>
              <option value="au">Australia</option>
              <option value="ae">UAE</option>
              <option value="br">Brazil</option>
            </select>
          </div>
        </div>
        <div class="form-row">
          <div class="form-group">
            <label class="form-label">Weight (kg)</label>
            <input type="number" class="form-input" id="qWeight" value="500" min="1" onchange="calcQuote()" oninput="calcQuote()">
          </div>
          <div class="form-group">
            <label class="form-label">Volume (CBM)</label>
            <input type="number" class="form-input" id="qVolume" value="2" min="0.1" step="0.1" onchange="calcQuote()" oninput="calcQuote()">
          </div>
        </div>
        <div class="form-group">
          <label class="form-label">Cargo Type</label>
          <select class="form-select" id="qCargo" onchange="calcQuote()">
            <option value="general">General Cargo</option>
            <option value="hazmat">Hazardous Materials</option>
            <option value="perishable">Perishable Goods</option>
            <option value="valuable">High-Value Goods</option>
          </select>
        </div>
      </div>

      <div class="quote-result">
        <div style="font-family:'Space Mono',monospace;font-size:0.6rem;letter-spacing:3px;color:var(--accent);margin-bottom:20px;text-transform:uppercase;">AI Quote Engine</div>
        <div class="quote-amount" id="quoteTotal">$2,840</div>
        <div class="quote-label">Estimated Total Cost</div>

        <div class="quote-breakdown" id="quoteBreakdown">
          <div class="breakdown-row">
            <span>Freight Cost</span>
            <span class="val" id="bFreight">$2,100</span>
          </div>
          <div class="breakdown-row">
            <span>Fuel Surcharge</span>
            <span class="val" id="bFuel">$340</span>
          </div>
          <div class="breakdown-row">
            <span>Customs & Handling</span>
            <span class="val" id="bCustoms">$280</span>
          </div>
          <div class="breakdown-row">
            <span>Insurance</span>
            <span class="val" id="bInsurance">$120</span>
          </div>
          <div class="breakdown-row" style="border-bottom:none;font-weight:700;">
            <span>Transit Time</span>
            <span class="val" id="bTransit" style="color:var(--accent3);">5–7 Days</span>
          </div>
        </div>
        <button class="btn-primary" style="width:100%;" onclick="showNotif('Quote sent to your email! Our team will confirm within 2 hours.')">BOOK THIS SHIPMENT</button>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT PAGE -->
<section id="contact" class="page">
  <div class="section">
    <div class="section-tag">Get In Touch</div>
    <h2 class="section-title">CONTACT OUR TEAM</h2>
    <p class="section-sub">Our global logistics experts are available 24/7. Reach out for quotes, support, or partnership inquiries.</p>

    <div class="contact-grid">
      <div class="contact-info">
        <div class="contact-item">
          <div class="contact-icon">📍</div>
          <div class="contact-detail">
            <h4>Headquarters</h4>
            <p>One Nexus Tower, Level 42<br>Dubai International Financial Centre<br>Dubai, UAE 00000</p>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">📞</div>
          <div class="contact-detail">
            <h4>24/7 Operations Center</h4>
            <p>+971 4 000 0000<br>+1 (800) NEXUS-GL</p>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">✉️</div>
          <div class="contact-detail">
            <h4>Email</h4>
            <p>ops@nexusglobal.com<br>sales@nexusglobal.com</p>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">🌐</div>
          <div class="contact-detail">
            <h4>Global Offices</h4>
            <p>Dubai · Shanghai · Frankfurt<br>New York · Singapore · Mumbai</p>
          </div>
        </div>
      </div>

      <div class="contact-form-panel">
        <div class="form-row" style="margin-bottom:24px;">
          <div class="form-group" style="margin-bottom:0;">
            <label class="form-label">First Name</label>
            <input type="text" class="form-input" placeholder="John">
          </div>
          <div class="form-group" style="margin-bottom:0;">
            <label class="form-label">Last Name</label>
            <input type="text" class="form-input" placeholder="Smith">
          </div>
        </div>
        <div class="form-group">
          <label class="form-label">Company</label>
          <input type="text" class="form-input" placeholder="Acme Corporation">
        </div>
        <div class="form-group">
          <label class="form-label">Email</label>
          <input type="email" class="form-input" placeholder="john@company.com">
        </div>
        <div class="form-group">
          <label class="form-label">Inquiry Type</label>
          <select class="form-select">
            <option>Freight Quote Request</option>
            <option>Shipment Support</option>
            <option>Partnership Inquiry</option>
            <option>General Inquiry</option>
          </select>
        </div>
        <div class="form-group">
          <label class="form-label">Message</label>
          <textarea class="form-textarea" placeholder="Tell us about your logistics needs..."></textarea>
        </div>
        <button class="submit-btn" onclick="showNotif('Message received! We\'ll respond within 2 hours.')">SEND MESSAGE →</button>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-grid">
    <div class="footer-brand">
      <div class="logo">NEXUS<span>.</span>GLOBAL</div>
      <p>AI-powered international logistics connecting businesses across 180+ countries with intelligent, reliable, and transparent supply chain solutions.</p>
    </div>
    <div class="footer-col">
      <h4>Services</h4>
      <ul>
        <li><a href="#" onclick="showPage('services')">Air Freight</a></li>
        <li><a href="#" onclick="showPage('services')">Ocean Freight</a></li>
        <li><a href="#" onclick="showPage('services')">Road Freight</a></li>
        <li><a href="#" onclick="showPage('services')">Warehousing</a></li>
        <li><a href="#" onclick="showPage('services')">Customs</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Company</h4>
      <ul>
        <li><a href="#">About Us</a></li>
        <li><a href="#">Careers</a></li>
        <li><a href="#">Press</a></li>
        <li><a href="#">Partners</a></li>
        <li><a href="#">Sustainability</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Support</h4>
      <ul>
        <li><a href="#" onclick="showPage('tracking')">Track Shipment</a></li>
        <li><a href="#" onclick="showPage('quote')">Get Quote</a></li>
        <li><a href="#" onclick="showPage('contact')">Contact Us</a></li>
        <li><a href="#">API Docs</a></li>
        <li><a href="#">Status Page</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <p>© 2024 Nexus Global Logistics. All rights reserved.</p>
    <p>Privacy Policy · Terms of Service · Cookie Settings</p>
  </div>
</footer>

<!-- AI Chat Widget -->
<div class="ai-chat-widget">
  <div class="ai-chat-panel" id="chatPanel">
    <div class="ai-chat-header">
      <div class="ai-dot"></div>
      <h4>NEXUS AI ASSISTANT</h4>
    </div>
    <div class="ai-messages" id="chatMessages">
      <div class="msg bot">Hello! I'm your Nexus AI logistics assistant. I can help you with tracking, quotes, customs info, and more. How can I help?</div>
    </div>
    <div class="ai-input-row">
      <input type="text" class="ai-input" id="aiInput" placeholder="Ask me anything..." onkeydown="if(event.key==='Enter') sendChat()">
      <button class="ai-send" onclick="sendChat()">↑</button>
    </div>
  </div>
  <button class="ai-chat-toggle" onclick="toggleChat()">🤖</button>
</div>

<script>
  // Custom Cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  document.addEventListener('mousemove', e => {
    cursor.style.left = e.clientX + 'px';
    cursor.style.top = e.clientY + 'px';
    setTimeout(() => {
      ring.style.left = e.clientX + 'px';
      ring.style.top = e.clientY + 'px';
    }, 80);
  });
  document.querySelectorAll('button, a, input, select, textarea').forEach(el => {
    el.addEventListener('mouseenter', () => { cursor.style.width = '20px'; cursor.style.height = '20px'; ring.style.width = '50px'; ring.style.height = '50px'; });
    el.addEventListener('mouseleave', () => { cursor.style.width = '12px'; cursor.style.height = '12px'; ring.style.width = '36px'; ring.style.height = '36px'; });
  });

  // Page navigation
  function showPage(id) {
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    window.scrollTo(0, 0);
  }

  // Tracking
  function trackShipment() {
    const val = document.getElementById('trackInput').value.trim();
    if (!val) { showNotif('Please enter a tracking number'); return; }
    const res = document.getElementById('trackResult');
    res.style.display = 'none';
    setTimeout(() => { res.classList.add('show'); res.style.display = 'block'; }, 300);
    showNotif('AI tracking engine located your shipment!');
  }

  // Quote Calculator
  const rates = {
    air: { base: 8, time: '3–5 Days' },
    ocean: { base: 1.2, time: '18–25 Days' },
    road: { base: 3, time: '5–10 Days' },
    express: { base: 20, time: '1–2 Days' }
  };
  const routeMult = { 'cn-us': 1.4, 'cn-de': 1.2, 'cn-au': 1.3, 'us-de': 1.1, 'de-ae': 0.9 };
  const cargoMult = { general: 1, hazmat: 1.8, perishable: 1.5, valuable: 1.6 };

  function calcQuote() {
    const svc = document.getElementById('qService').value;
    const weight = parseFloat(document.getElementById('qWeight').value) || 500;
    const vol = parseFloat(document.getElementById('qVolume').value) || 2;
    const cargo = document.getElementById('qCargo').value;
    const origin = document.getElementById('qOrigin').value;
    const dest = document.getElementById('qDest').value;

    const rate = rates[svc];
    const rm = routeMult[origin + '-' + dest] || 1.1;
    const cm = cargoMult[cargo];
    const chargeable = Math.max(weight, vol * 167);
    const freight = Math.round(chargeable * rate.base * rm * cm);
    const fuel = Math.round(freight * 0.14);
    const customs = Math.round(freight * 0.11);
    const insurance = Math.round(freight * 0.05);
    const total = freight + fuel + customs + insurance;

    document.getElementById('quoteTotal').textContent = '$' + total.toLocaleString();
    document.getElementById('bFreight').textContent = '$' + freight.toLocaleString();
    document.getElementById('bFuel').textContent = '$' + fuel.toLocaleString();
    document.getElementById('bCustoms').textContent = '$' + customs.toLocaleString();
    document.getElementById('bInsurance').textContent = '$' + insurance.toLocaleString();
    document.getElementById('bTransit').textContent = rate.time;
  }

  // Notification
  function showNotif(msg) {
    const n = document.getElementById('notification');
    n.textContent = msg;
    n.classList.add('show');
    setTimeout(() => n.classList.remove('show'), 3500);
  }

  // AI Chat
  function toggleChat() {
    document.getElementById('chatPanel').classList.toggle('open');
  }

  const chatResponses = [
    "I can track any shipment in real-time using our AI engine. Just provide me with your tracking number and I'll pull the full journey details!",
    "Our AI pricing engine analyzes 50+ variables in milliseconds to give you the most competitive quote. Head to the Get Quote section to get an instant estimate.",
    "We serve 180+ countries with air, ocean, road, and express services. Our AI optimizes routes to ensure fastest delivery at lowest cost.",
    "Customs clearance is fully automated through our AI system — HS code classification, duty calculation, and electronic filing are all handled automatically.",
    "Our on-time delivery rate is 99.7%, maintained through predictive AI that anticipates delays and reroutes shipments proactively.",
    "For urgent shipments, our express service offers 1–2 day delivery globally. Would you like me to calculate a quote for you?",
    "I'm monitoring 2,847 active shipments right now. Your cargo is in safe hands with our 24/7 AI operations center!"
  ];
  let chatIdx = 0;

  function sendChat() {
    const input = document.getElementById('aiInput');
    const msgs = document.getElementById('chatMessages');
    if (!input.value.trim()) return;

    const userMsg = document.createElement('div');
    userMsg.className = 'msg user';
    userMsg.textContent = input.value;
    msgs.appendChild(userMsg);

    const val = input.value.toLowerCase();
    input.value = '';

    setTimeout(() => {
      const botMsg = document.createElement('div');
      botMsg.className = 'msg bot';
      let response = chatResponses[chatIdx % chatResponses.length];
      if (val.includes('track')) response = chatResponses[0];
      else if (val.includes('quote') || val.includes('price') || val.includes('cost')) response = chatResponses[1];
      else if (val.includes('service') || val.includes('offer')) response = chatResponses[2];
      else if (val.includes('custom')) response = chatResponses[3];
      chatIdx++;
      botMsg.textContent = response;
      msgs.appendChild(botMsg);
      msgs.scrollTop = msgs.scrollHeight;
    }, 600);
    msgs.scrollTop = msgs.scrollHeight;
  }

  // Init quote
  calcQuote();
</script>
</body>
</html>
