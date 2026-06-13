[index.html](https://github.com/user-attachments/files/28909485/index.html)
# Thiranex-Internship-Portfolio<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="Full-stack web developer portfolio showcasing semantic HTML5, advanced CSS3, and JavaScript projects." />
  <meta name="keywords" content="web developer, HTML5, CSS3, JavaScript, portfolio, frontend" />
  <meta name="author" content="Your Name" />
  <meta property="og:title" content="Dev Portfolio | Web Developer" />
  <meta property="og:description" content="Showcasing modern web development skills with HTML5, CSS3, and JavaScript." />
  <meta property="og:type" content="website" />
  <title>Dev Portfolio | Web Developer</title>

  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet" />

  <style>
    /* ===== CSS CUSTOM PROPERTIES (TASK 2: CSS Variables) ===== */
    :root {
      --clr-bg: #0d0d0f;
      --clr-surface: #141418;
      --clr-card: #1c1c22;
      --clr-border: #2a2a35;
      --clr-accent: #7c6dfa;
      --clr-accent-2: #fa6d8d;
      --clr-accent-3: #6dfabd;
      --clr-text: #e8e8f0;
      --clr-text-muted: #7a7a90;
      --clr-text-dim: #4a4a60;

      --font-display: 'Space Grotesk', sans-serif;
      --font-mono: 'Space Mono', monospace;

      --radius-sm: 6px;
      --radius-md: 12px;
      --radius-lg: 20px;
      --radius-xl: 32px;

      --shadow-card: 0 4px 24px rgba(0,0,0,0.4);
      --shadow-accent: 0 0 40px rgba(124,109,250,0.15);

      --transition: 0.25s cubic-bezier(0.4,0,0.2,1);
    }

    /* Light / Dark mode via class on <html> */
    html.light {
      --clr-bg: #f5f4ff;
      --clr-surface: #ffffff;
      --clr-card: #ffffff;
      --clr-border: #e0dff7;
      --clr-text: #1a1a2e;
      --clr-text-muted: #5a5a7a;
      --clr-text-dim: #a0a0b8;
      --shadow-card: 0 4px 24px rgba(124,109,250,0.08);
      --shadow-accent: 0 0 40px rgba(124,109,250,0.1);
    }

    /* ===== RESET ===== */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }

    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; }
      html { scroll-behavior: auto; }
    }

    body {
      font-family: var(--font-display);
      background: var(--clr-bg);
      color: var(--clr-text);
      line-height: 1.6;
      min-height: 100vh;
      transition: background var(--transition), color var(--transition);
    }

    /* ===== SKIP LINK (WCAG Accessibility) ===== */
    .skip-link {
      position: absolute;
      top: -9999px;
      left: 1rem;
      background: var(--clr-accent);
      color: #fff;
      padding: 0.5rem 1rem;
      border-radius: var(--radius-sm);
      font-weight: 600;
      z-index: 9999;
      text-decoration: none;
    }
    .skip-link:focus { top: 1rem; }

    /* ===== LAYOUT ===== */
    .container {
      width: min(1100px, 100% - 2rem);
      margin-inline: auto;
    }

    /* ===== HEADER / NAV (TASK 1: Semantic HTML5) ===== */
    header {
      position: sticky;
      top: 0;
      z-index: 100;
      background: rgba(13,13,15,0.85);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--clr-border);
      transition: background var(--transition);
    }
    html.light header { background: rgba(245,244,255,0.9); }

    nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 1rem 1.5rem;
      max-width: 1100px;
      margin: 0 auto;
    }

    .logo {
      font-family: var(--font-mono);
      font-size: 1.2rem;
      font-weight: 700;
      color: var(--clr-accent);
      text-decoration: none;
      letter-spacing: -0.5px;
    }
    .logo span { color: var(--clr-accent-2); }

    .nav-links {
      display: flex;
      gap: 0.25rem;
      list-style: none;
      align-items: center;
    }

    .nav-links a {
      color: var(--clr-text-muted);
      text-decoration: none;
      font-size: 0.9rem;
      font-weight: 500;
      padding: 0.4rem 0.8rem;
      border-radius: var(--radius-sm);
      transition: color var(--transition), background var(--transition);
    }
    .nav-links a:hover,
    .nav-links a:focus-visible { color: var(--clr-text); background: var(--clr-border); outline: none; }

    .theme-toggle {
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      color: var(--clr-text);
      width: 38px; height: 38px;
      border-radius: 50%;
      cursor: pointer;
      display: grid; place-items: center;
      font-size: 1rem;
      transition: all var(--transition);
    }
    .theme-toggle:hover { border-color: var(--clr-accent); }
    .theme-toggle:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 2px; }

    /* Hamburger */
    .hamburger {
      display: none;
      background: none;
      border: 1px solid var(--clr-border);
      color: var(--clr-text);
      width: 38px; height: 38px;
      border-radius: var(--radius-sm);
      cursor: pointer;
      font-size: 1.2rem;
      align-items: center;
      justify-content: center;
    }
    .hamburger:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 2px; }

    /* ===== HERO SECTION ===== */
    .hero {
      min-height: 92vh;
      display: grid;
      place-items: center;
      text-align: center;
      padding: 4rem 1.5rem;
      position: relative;
      overflow: hidden;
    }

    .hero-bg {
      position: absolute;
      inset: 0;
      background: radial-gradient(ellipse 60% 50% at 50% 30%, rgba(124,109,250,0.12) 0%, transparent 70%),
                  radial-gradient(ellipse 40% 40% at 80% 70%, rgba(250,109,141,0.08) 0%, transparent 60%);
      pointer-events: none;
    }

    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      background: rgba(124,109,250,0.12);
      border: 1px solid rgba(124,109,250,0.3);
      color: var(--clr-accent);
      font-size: 0.78rem;
      font-family: var(--font-mono);
      font-weight: 700;
      letter-spacing: 1px;
      text-transform: uppercase;
      padding: 0.35rem 0.9rem;
      border-radius: 100px;
      margin-bottom: 1.5rem;
    }
    .hero-badge::before {
      content: '';
      width: 6px; height: 6px;
      background: var(--clr-accent-3);
      border-radius: 50%;
      animation: pulse 2s ease-in-out infinite;
    }
    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.5; transform: scale(0.8); }
    }

    .hero h1 {
      font-size: clamp(2.4rem, 7vw, 5.5rem);
      font-weight: 700;
      line-height: 1.08;
      letter-spacing: -2px;
      margin-bottom: 1.2rem;
    }

    .hero h1 .accent-text {
      background: linear-gradient(135deg, var(--clr-accent), var(--clr-accent-2));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .hero-desc {
      font-size: clamp(1rem, 2.5vw, 1.2rem);
      color: var(--clr-text-muted);
      max-width: 540px;
      margin: 0 auto 2.5rem;
      line-height: 1.7;
    }

    .hero-cta {
      display: flex;
      gap: 1rem;
      justify-content: center;
      flex-wrap: wrap;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      padding: 0.75rem 1.75rem;
      border-radius: var(--radius-md);
      font-family: var(--font-display);
      font-size: 0.95rem;
      font-weight: 600;
      text-decoration: none;
      border: none;
      cursor: pointer;
      transition: all var(--transition);
    }
    .btn:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 3px; }

    .btn-primary {
      background: var(--clr-accent);
      color: #fff;
    }
    .btn-primary:hover { background: #6a5ce8; transform: translateY(-1px); box-shadow: 0 8px 24px rgba(124,109,250,0.35); }

    .btn-secondary {
      background: transparent;
      color: var(--clr-text);
      border: 1px solid var(--clr-border);
    }
    .btn-secondary:hover { border-color: var(--clr-accent); color: var(--clr-accent); transform: translateY(-1px); }

    /* ===== SECTION STYLES ===== */
    section { padding: 5rem 1.5rem; }

    .section-label {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      font-family: var(--font-mono);
      font-size: 0.72rem;
      font-weight: 700;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: var(--clr-accent);
      margin-bottom: 0.75rem;
    }
    .section-label::before {
      content: '';
      display: block;
      width: 20px;
      height: 1px;
      background: var(--clr-accent);
    }

    .section-title {
      font-size: clamp(1.8rem, 4vw, 2.8rem);
      font-weight: 700;
      letter-spacing: -1px;
      line-height: 1.15;
      margin-bottom: 0.75rem;
    }

    .section-desc {
      color: var(--clr-text-muted);
      font-size: 1.05rem;
      max-width: 520px;
      line-height: 1.7;
      margin-bottom: 3rem;
    }

    /* ===== SKILLS SECTION ===== */
    #skills { background: var(--clr-surface); }

    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.25rem;
    }

    .skill-card {
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      border-radius: var(--radius-lg);
      padding: 1.75rem;
      transition: all var(--transition);
      position: relative;
      overflow: hidden;
    }
    .skill-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(90deg, var(--clr-accent), var(--clr-accent-2));
      transform: scaleX(0);
      transform-origin: left;
      transition: transform var(--transition);
    }
    .skill-card:hover { border-color: rgba(124,109,250,0.4); transform: translateY(-3px); box-shadow: var(--shadow-card); }
    .skill-card:hover::before { transform: scaleX(1); }

    .skill-icon {
      font-size: 2rem;
      margin-bottom: 0.75rem;
    }
    .skill-card h3 { font-size: 1.05rem; font-weight: 600; margin-bottom: 0.4rem; }
    .skill-card p { font-size: 0.88rem; color: var(--clr-text-muted); line-height: 1.6; }

    .skill-bar-wrap { margin-top: 1rem; }
    .skill-bar-label {
      display: flex;
      justify-content: space-between;
      font-size: 0.75rem;
      color: var(--clr-text-muted);
      margin-bottom: 0.3rem;
      font-family: var(--font-mono);
    }
    .skill-bar {
      height: 4px;
      background: var(--clr-border);
      border-radius: 2px;
      overflow: hidden;
    }
    .skill-bar-fill {
      height: 100%;
      border-radius: 2px;
      background: linear-gradient(90deg, var(--clr-accent), var(--clr-accent-2));
      transition: width 1.2s ease;
    }

    /* ===== PROJECTS SECTION ===== */
    #projects {
      background: var(--clr-bg);
    }

    .projects-grid {
      display: grid;
      gap: 1.5rem;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    }

    .project-card {
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      border-radius: var(--radius-lg);
      padding: 2rem;
      display: flex;
      flex-direction: column;
      gap: 1rem;
      transition: all var(--transition);
    }
    .project-card:hover { border-color: rgba(124,109,250,0.4); transform: translateY(-3px); box-shadow: var(--shadow-card); }

    .project-num {
      font-family: var(--font-mono);
      font-size: 0.7rem;
      color: var(--clr-accent);
      font-weight: 700;
      letter-spacing: 1px;
    }
    .project-card h3 { font-size: 1.15rem; font-weight: 700; }
    .project-card p { font-size: 0.9rem; color: var(--clr-text-muted); line-height: 1.65; flex: 1; }

    .project-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
    }
    .tag {
      background: rgba(124,109,250,0.1);
      color: var(--clr-accent);
      font-size: 0.72rem;
      font-family: var(--font-mono);
      font-weight: 700;
      padding: 0.25rem 0.6rem;
      border-radius: 4px;
      border: 1px solid rgba(124,109,250,0.2);
    }

    /* ===== TODO APP SECTION (TASK 3: JavaScript) ===== */
    #todo {
      background: var(--clr-surface);
    }

    .todo-wrapper {
      max-width: 640px;
      margin: 0 auto;
    }

    .todo-input-group {
      display: flex;
      gap: 0.75rem;
      margin-bottom: 1.5rem;
    }

    .todo-input {
      flex: 1;
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      border-radius: var(--radius-md);
      padding: 0.85rem 1.1rem;
      font-family: var(--font-display);
      font-size: 0.95rem;
      color: var(--clr-text);
      outline: none;
      transition: border-color var(--transition), box-shadow var(--transition);
    }
    .todo-input::placeholder { color: var(--clr-text-dim); }
    .todo-input:focus { border-color: var(--clr-accent); box-shadow: 0 0 0 3px rgba(124,109,250,0.15); }

    .todo-add-btn {
      background: var(--clr-accent);
      color: #fff;
      border: none;
      border-radius: var(--radius-md);
      padding: 0.85rem 1.4rem;
      font-family: var(--font-display);
      font-size: 0.95rem;
      font-weight: 600;
      cursor: pointer;
      transition: all var(--transition);
      white-space: nowrap;
    }
    .todo-add-btn:hover { background: #6a5ce8; transform: translateY(-1px); }
    .todo-add-btn:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 2px; }
    .todo-add-btn:active { transform: translateY(0); }

    .todo-filters {
      display: flex;
      gap: 0.5rem;
      margin-bottom: 1.25rem;
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      border-radius: var(--radius-md);
      padding: 0.3rem;
    }

    .filter-btn {
      flex: 1;
      background: none;
      border: none;
      border-radius: var(--radius-sm);
      padding: 0.5rem;
      font-family: var(--font-display);
      font-size: 0.85rem;
      font-weight: 500;
      color: var(--clr-text-muted);
      cursor: pointer;
      transition: all var(--transition);
    }
    .filter-btn.active {
      background: var(--clr-accent);
      color: #fff;
    }
    .filter-btn:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 2px; }

    .todo-stats {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 0.75rem;
      font-size: 0.82rem;
      color: var(--clr-text-muted);
      font-family: var(--font-mono);
    }

    .clear-btn {
      background: none;
      border: none;
      color: var(--clr-accent-2);
      font-family: var(--font-mono);
      font-size: 0.78rem;
      cursor: pointer;
      text-decoration: underline;
      text-underline-offset: 2px;
      opacity: 0.7;
      transition: opacity var(--transition);
    }
    .clear-btn:hover { opacity: 1; }
    .clear-btn:focus-visible { outline: 2px solid var(--clr-accent-2); outline-offset: 2px; border-radius: 2px; }

    .todo-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 0.6rem;
      min-height: 100px;
    }

    .todo-item {
      display: flex;
      align-items: center;
      gap: 0.9rem;
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      border-radius: var(--radius-md);
      padding: 0.9rem 1.1rem;
      transition: all var(--transition);
      animation: slideIn 0.25s ease;
    }
    @keyframes slideIn {
      from { opacity: 0; transform: translateY(-6px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .todo-item:hover { border-color: rgba(124,109,250,0.3); }
    .todo-item.completed { opacity: 0.55; }

    .todo-checkbox {
      width: 20px; height: 20px;
      border-radius: 6px;
      border: 2px solid var(--clr-border);
      background: none;
      cursor: pointer;
      display: grid;
      place-items: center;
      flex-shrink: 0;
      transition: all var(--transition);
      position: relative;
      appearance: none;
      -webkit-appearance: none;
    }
    .todo-checkbox:checked {
      background: var(--clr-accent-3);
      border-color: var(--clr-accent-3);
    }
    .todo-checkbox:checked::after {
      content: '✓';
      color: #0d0d0f;
      font-size: 0.7rem;
      font-weight: 700;
    }
    .todo-checkbox:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 2px; }

    .todo-text {
      flex: 1;
      font-size: 0.95rem;
      transition: all var(--transition);
    }
    .todo-item.completed .todo-text {
      text-decoration: line-through;
      color: var(--clr-text-muted);
    }

    .todo-delete {
      background: none;
      border: none;
      color: var(--clr-text-dim);
      cursor: pointer;
      font-size: 1rem;
      width: 28px; height: 28px;
      border-radius: var(--radius-sm);
      display: grid; place-items: center;
      transition: all var(--transition);
      flex-shrink: 0;
    }
    .todo-delete:hover { background: rgba(250,109,141,0.12); color: var(--clr-accent-2); }
    .todo-delete:focus-visible { outline: 2px solid var(--clr-accent-2); outline-offset: 2px; }

    .todo-empty {
      text-align: center;
      padding: 2.5rem 1rem;
      color: var(--clr-text-dim);
      font-size: 0.9rem;
    }
    .todo-empty span { display: block; font-size: 2rem; margin-bottom: 0.5rem; }

    /* ===== CONTACT SECTION (accessible form) ===== */
    #contact { background: var(--clr-bg); }

    .contact-layout {
      display: grid;
      grid-template-columns: 1fr 1.3fr;
      gap: 3rem;
      align-items: start;
    }

    .contact-info h3 { font-size: 1.2rem; font-weight: 600; margin-bottom: 0.75rem; }
    .contact-info p { color: var(--clr-text-muted); font-size: 0.95rem; line-height: 1.7; margin-bottom: 1.5rem; }

    .contact-links { display: flex; flex-direction: column; gap: 0.6rem; }
    .contact-link {
      display: flex;
      align-items: center;
      gap: 0.6rem;
      color: var(--clr-text-muted);
      text-decoration: none;
      font-size: 0.9rem;
      padding: 0.6rem 0.8rem;
      border-radius: var(--radius-sm);
      transition: all var(--transition);
      border: 1px solid transparent;
    }
    .contact-link:hover { color: var(--clr-accent); border-color: rgba(124,109,250,0.2); background: rgba(124,109,250,0.05); }
    .contact-link:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 2px; }

    /* Accessible Contact Form */
    .contact-form {
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      border-radius: var(--radius-lg);
      padding: 2rem;
    }

    .form-group { margin-bottom: 1.25rem; }

    .form-group label {
      display: block;
      font-size: 0.85rem;
      font-weight: 600;
      color: var(--clr-text);
      margin-bottom: 0.4rem;
    }
    .form-group label .required {
      color: var(--clr-accent-2);
      margin-left: 2px;
    }

    .form-input,
    .form-textarea {
      width: 100%;
      background: var(--clr-surface);
      border: 1px solid var(--clr-border);
      border-radius: var(--radius-sm);
      padding: 0.75rem 0.9rem;
      font-family: var(--font-display);
      font-size: 0.92rem;
      color: var(--clr-text);
      outline: none;
      transition: border-color var(--transition), box-shadow var(--transition);
      -webkit-appearance: none;
    }
    .form-input::placeholder,
    .form-textarea::placeholder { color: var(--clr-text-dim); }
    .form-input:focus,
    .form-textarea:focus { border-color: var(--clr-accent); box-shadow: 0 0 0 3px rgba(124,109,250,0.12); }
    .form-textarea { resize: vertical; min-height: 120px; }

    .form-submit {
      width: 100%;
      background: var(--clr-accent);
      color: #fff;
      border: none;
      border-radius: var(--radius-md);
      padding: 0.9rem;
      font-family: var(--font-display);
      font-size: 0.95rem;
      font-weight: 600;
      cursor: pointer;
      transition: all var(--transition);
    }
    .form-submit:hover { background: #6a5ce8; transform: translateY(-1px); }
    .form-submit:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 3px; }

    .form-success {
      display: none;
      text-align: center;
      padding: 1.5rem;
      background: rgba(109,250,189,0.08);
      border: 1px solid rgba(109,250,189,0.25);
      border-radius: var(--radius-md);
      color: var(--clr-accent-3);
      font-size: 0.95rem;
    }

    /* ===== FOOTER ===== */
    footer {
      background: var(--clr-surface);
      border-top: 1px solid var(--clr-border);
      padding: 2rem 1.5rem;
      text-align: center;
    }
    .footer-inner {
      max-width: 1100px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 1rem;
      flex-wrap: wrap;
    }
    .footer-inner p { font-size: 0.85rem; color: var(--clr-text-muted); }
    .footer-inner a { color: var(--clr-accent); text-decoration: none; }
    .footer-inner a:hover { text-decoration: underline; }
    .footer-inner a:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 2px; border-radius: 2px; }

    /* ===== RESPONSIVE (TASK 2: Mobile-first) ===== */
    @media (max-width: 768px) {
      .hamburger { display: flex; }

      .nav-links {
        display: none;
        position: fixed;
        top: 65px; left: 0; right: 0;
        background: var(--clr-surface);
        border-bottom: 1px solid var(--clr-border);
        flex-direction: column;
        padding: 1rem;
        gap: 0.25rem;
        z-index: 99;
      }
      .nav-links.open { display: flex; }
      .nav-links a { padding: 0.75rem 1rem; width: 100%; }

      .contact-layout { grid-template-columns: 1fr; gap: 2rem; }

      section { padding: 3.5rem 1.25rem; }
    }

    @media (max-width: 480px) {
      .hero h1 { letter-spacing: -1px; }
      .hero-cta { flex-direction: column; align-items: center; }
      .btn { width: 100%; justify-content: center; }
      .todo-input-group { flex-direction: column; }
      .footer-inner { flex-direction: column; text-align: center; }
    }

    /* ===== WEATHER SECTION (TASK 4) ===== */
    #weather { background: var(--clr-bg); }

    .weather-wrapper { max-width: 680px; margin: 0 auto; }

    .weather-search-row {
      display: flex;
      gap: 0.75rem;
      margin-bottom: 1.5rem;
    }
    .weather-input { flex: 1; }

    .weather-error {
      background: rgba(250,109,141,0.1);
      border: 1px solid rgba(250,109,141,0.3);
      color: var(--clr-accent-2);
      border-radius: var(--radius-md);
      padding: 0.85rem 1.1rem;
      font-size: 0.9rem;
      margin-bottom: 1rem;
    }

    .weather-loading {
      display: flex;
      align-items: center;
      gap: 0.75rem;
      color: var(--clr-text-muted);
      font-size: 0.9rem;
      padding: 1.5rem 0;
      justify-content: center;
    }
    .weather-spinner {
      width: 20px; height: 20px;
      border: 2px solid var(--clr-border);
      border-top-color: var(--clr-accent);
      border-radius: 50%;
      animation: spin 0.8s linear infinite;
    }
    @keyframes spin { to { transform: rotate(360deg); } }

    .weather-card {
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      border-radius: var(--radius-lg);
      padding: 2rem;
      animation: slideIn 0.3s ease;
    }
    .weather-top {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      margin-bottom: 1.75rem;
    }
    .weather-city { font-size: 1.5rem; font-weight: 700; margin-bottom: 0.25rem; }
    .weather-desc { color: var(--clr-text-muted); font-size: 0.9rem; }
    .weather-icon-big { font-size: 3.5rem; line-height: 1; }

    .weather-metrics {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 1rem;
      margin-bottom: 1rem;
    }
    .weather-metric {
      background: var(--clr-surface);
      border: 1px solid var(--clr-border);
      border-radius: var(--radius-md);
      padding: 1rem 0.75rem;
      text-align: center;
      display: flex;
      flex-direction: column;
      gap: 0.3rem;
    }
    .metric-icon { font-size: 1.3rem; }
    .metric-val { font-size: 1.15rem; font-weight: 700; font-family: var(--font-mono); color: var(--clr-accent); }
    .metric-label { font-size: 0.72rem; color: var(--clr-text-muted); }
    .weather-source { font-size: 0.75rem; color: var(--clr-text-dim); }
    .weather-source a { color: var(--clr-accent); text-decoration: none; }
    .weather-source a:hover { text-decoration: underline; }

    @media (max-width: 540px) {
      .weather-metrics { grid-template-columns: repeat(2, 1fr); }
      .weather-search-row { flex-direction: column; }
    }

    /* ===== SHOP SECTION (TASK 5) ===== */
    #shop { background: var(--clr-surface); }

    .shop-toolbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 0.75rem;
      margin-bottom: 1.75rem;
    }

    .shop-filters {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
    }
    .shop-filter {
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      color: var(--clr-text-muted);
      border-radius: 100px;
      padding: 0.4rem 1rem;
      font-size: 0.82rem;
      font-weight: 600;
      font-family: var(--font-display);
      cursor: pointer;
      transition: all var(--transition);
    }
    .shop-filter.active,
    .shop-filter:hover { background: var(--clr-accent); color: #fff; border-color: var(--clr-accent); }
    .shop-filter:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 2px; }

    .cart-btn {
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      color: var(--clr-text);
      border-radius: var(--radius-md);
      padding: 0.5rem 1.1rem;
      font-size: 0.9rem;
      font-weight: 600;
      font-family: var(--font-display);
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 0.5rem;
      transition: all var(--transition);
      position: relative;
    }
    .cart-btn:hover { border-color: var(--clr-accent); }
    .cart-btn:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 2px; }
    .cart-count {
      background: var(--clr-accent-2);
      color: #fff;
      font-size: 0.7rem;
      font-weight: 700;
      width: 18px; height: 18px;
      border-radius: 50%;
      display: grid; place-items: center;
    }

    .cart-panel {
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      border-radius: var(--radius-lg);
      padding: 1.5rem;
      margin-bottom: 1.5rem;
      animation: slideIn 0.25s ease;
    }
    .cart-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 1rem; }
    .cart-header h3 { font-size: 1rem; font-weight: 700; }
    .cart-close { background: none; border: none; font-size: 1rem; cursor: pointer; color: var(--clr-text-muted); padding: 0.25rem; border-radius: 4px; transition: color var(--transition); }
    .cart-close:hover { color: var(--clr-accent-2); }
    .cart-close:focus-visible { outline: 2px solid var(--clr-accent); }

    .cart-list { list-style: none; display: flex; flex-direction: column; gap: 0.6rem; max-height: 260px; overflow-y: auto; margin-bottom: 1rem; }
    .cart-item { display: flex; align-items: center; gap: 0.75rem; padding: 0.6rem 0; border-bottom: 1px solid var(--clr-border); }
    .cart-item-img { width: 40px; height: 40px; object-fit: contain; border-radius: var(--radius-sm); background: #fff; padding: 4px; flex-shrink: 0; }
    .cart-item-info { flex: 1; min-width: 0; }
    .cart-item-name { font-size: 0.82rem; font-weight: 600; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
    .cart-item-price { font-size: 0.78rem; color: var(--clr-accent); font-family: var(--font-mono); }
    .cart-item-qty { display: flex; align-items: center; gap: 0.4rem; }
    .qty-btn { background: var(--clr-border); border: none; color: var(--clr-text); width: 22px; height: 22px; border-radius: 4px; cursor: pointer; font-size: 0.85rem; display: grid; place-items: center; transition: background var(--transition); }
    .qty-btn:hover { background: var(--clr-accent); color: #fff; }
    .qty-num { font-size: 0.82rem; font-weight: 600; min-width: 16px; text-align: center; }

    .cart-footer { display: flex; flex-direction: column; }
    .cart-total-label { font-size: 0.8rem; color: var(--clr-text-muted); }
    .cart-total { font-size: 1.4rem; font-weight: 700; font-family: var(--font-mono); color: var(--clr-accent-3); }
    .cart-empty-msg { text-align: center; padding: 1.5rem; color: var(--clr-text-dim); font-size: 0.9rem; }

    .shop-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap: 1.25rem;
    }

    .product-card {
      background: var(--clr-card);
      border: 1px solid var(--clr-border);
      border-radius: var(--radius-lg);
      padding: 1.5rem;
      display: flex;
      flex-direction: column;
      gap: 0.75rem;
      transition: all var(--transition);
      animation: slideIn 0.3s ease both;
    }
    .product-card:hover { border-color: rgba(124,109,250,0.4); transform: translateY(-3px); box-shadow: var(--shadow-card); }

    .product-img-wrap {
      background: #fff;
      border-radius: var(--radius-md);
      padding: 1rem;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 140px;
    }
    .product-img { max-height: 110px; max-width: 100%; object-fit: contain; }

    .product-cat {
      font-size: 0.68rem;
      font-family: var(--font-mono);
      font-weight: 700;
      letter-spacing: 0.5px;
      color: var(--clr-accent);
      text-transform: uppercase;
    }
    .product-name {
      font-size: 0.88rem;
      font-weight: 600;
      line-height: 1.4;
      display: -webkit-box;
      -webkit-line-clamp: 2;
      -webkit-box-orient: vertical;
      overflow: hidden;
      flex: 1;
    }
    .product-bottom { display: flex; justify-content: space-between; align-items: center; gap: 0.5rem; margin-top: auto; }
    .product-price { font-size: 1.1rem; font-weight: 700; font-family: var(--font-mono); color: var(--clr-accent-3); }
    .product-rating { font-size: 0.72rem; color: var(--clr-text-muted); }
    .add-to-cart {
      background: var(--clr-accent);
      color: #fff;
      border: none;
      border-radius: var(--radius-sm);
      padding: 0.45rem 0.9rem;
      font-size: 0.8rem;
      font-weight: 600;
      font-family: var(--font-display);
      cursor: pointer;
      transition: all var(--transition);
      white-space: nowrap;
    }
    .add-to-cart:hover { background: #6a5ce8; transform: scale(1.03); }
    .add-to-cart:focus-visible { outline: 2px solid var(--clr-accent); outline-offset: 2px; }
    .add-to-cart.added { background: var(--clr-accent-3); color: #0d0d0f; }

    /* ===== SCROLL REVEAL ===== */
    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.6s ease, transform 0.6s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }
  </style>
</head>
<body>

  <!-- WCAG: Skip navigation -->
  <a href="#main" class="skip-link">Skip to main content</a>

  <!-- TASK 1: Semantic HTML5 Header -->
  <header role="banner">
    <nav aria-label="Primary navigation">
      <a href="#" class="logo" aria-label="Home">dev<span>.</span>portfolio</a>
      <ul class="nav-links" id="navLinks" role="list">
        <li><a href="#skills">Skills</a></li>
        <li><a href="#projects">Projects</a></li>
        <li><a href="#todo">Todo App</a></li>
        <li><a href="#weather">Weather</a></li>
        <li><a href="#shop">Shop</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
      <div style="display:flex;gap:0.5rem;align-items:center;">
        <button class="theme-toggle" id="themeToggle" aria-label="Toggle light/dark mode" title="Toggle theme">🌙</button>
        <button class="hamburger" id="hamburger" aria-expanded="false" aria-controls="navLinks" aria-label="Open navigation menu">☰</button>
      </div>
    </nav>
  </header>

  <!-- TASK 1: Semantic Main -->
  <main id="main">

    <!-- Hero -->
    <section class="hero" aria-labelledby="hero-title">
      <div class="hero-bg" aria-hidden="true"></div>
      <div>
        <p class="hero-badge" aria-hidden="true">Available for work</p>
        <h1 id="hero-title">
          Building the web<br>
          <span class="accent-text">one pixel at a time</span>
        </h1>
        <p class="hero-desc">
          Frontend developer passionate about semantic HTML, accessible design, 
          and crafting interactive experiences that delight users.
        </p>
        <div class="hero-cta">
          <a href="#projects" class="btn btn-primary">View Projects</a>
          <a href="#contact" class="btn btn-secondary">Get in Touch</a>
        </div>
      </div>
    </section>

    <!-- TASK 1 + 2: Skills Section -->
    <section id="skills" aria-labelledby="skills-title">
      <div class="container">
        <p class="section-label">What I know</p>
        <h2 class="section-title" id="skills-title">Skills & Technologies</h2>
        <p class="section-desc">A modern frontend toolkit built for real-world, production-ready projects.</p>

        <div class="skills-grid" role="list">
          <article class="skill-card reveal" role="listitem">
            <div class="skill-icon" aria-hidden="true">🏗️</div>
            <h3>HTML5 Semantic</h3>
            <p>Proper use of semantic tags, ARIA roles, and accessibility-first document structure.</p>
            <div class="skill-bar-wrap" role="progressbar" aria-valuenow="92" aria-valuemin="0" aria-valuemax="100" aria-label="HTML5 skill level 92%">
              <div class="skill-bar-label"><span>HTML5</span><span>92%</span></div>
              <div class="skill-bar"><div class="skill-bar-fill" data-width="92" style="width:0%"></div></div>
            </div>
          </article>

          <article class="skill-card reveal" role="listitem">
            <div class="skill-icon" aria-hidden="true">🎨</div>
            <h3>CSS3 & Layout</h3>
            <p>CSS Grid, Flexbox, custom properties, animations, and fully responsive mobile-first designs.</p>
            <div class="skill-bar-wrap" role="progressbar" aria-valuenow="88" aria-valuemin="0" aria-valuemax="100" aria-label="CSS3 skill level 88%">
              <div class="skill-bar-label"><span>CSS3</span><span>88%</span></div>
              <div class="skill-bar"><div class="skill-bar-fill" data-width="88" style="width:0%"></div></div>
            </div>
          </article>

          <article class="skill-card reveal" role="listitem">
            <div class="skill-icon" aria-hidden="true">⚡</div>
            <h3>JavaScript</h3>
            <p>DOM manipulation, event delegation, localStorage persistence, and clean state management.</p>
            <div class="skill-bar-wrap" role="progressbar" aria-valuenow="80" aria-valuemin="0" aria-valuemax="100" aria-label="JavaScript skill level 80%">
              <div class="skill-bar-label"><span>JavaScript</span><span>80%</span></div>
              <div class="skill-bar"><div class="skill-bar-fill" data-width="80" style="width:0%"></div></div>
            </div>
          </article>

          <article class="skill-card reveal" role="listitem">
            <div class="skill-icon" aria-hidden="true">♿</div>
            <h3>Accessibility</h3>
            <p>WCAG 2.1 guidelines, keyboard navigation, screen reader compatibility, and focus management.</p>
            <div class="skill-bar-wrap" role="progressbar" aria-valuenow="85" aria-valuemin="0" aria-valuemax="100" aria-label="Accessibility skill level 85%">
              <div class="skill-bar-label"><span>WCAG / A11y</span><span>85%</span></div>
              <div class="skill-bar"><div class="skill-bar-fill" data-width="85" style="width:0%"></div></div>
            </div>
          </article>

          <article class="skill-card reveal" role="listitem">
            <div class="skill-icon" aria-hidden="true">📱</div>
            <h3>Responsive Design</h3>
            <p>Mobile-first approach using media queries, fluid typography with clamp(), and flexible layouts.</p>
            <div class="skill-bar-wrap" role="progressbar" aria-valuenow="90" aria-valuemin="0" aria-valuemax="100" aria-label="Responsive design skill level 90%">
              <div class="skill-bar-label"><span>Responsive</span><span>90%</span></div>
              <div class="skill-bar"><div class="skill-bar-fill" data-width="90" style="width:0%"></div></div>
            </div>
          </article>

          <article class="skill-card reveal" role="listitem">
            <div class="skill-icon" aria-hidden="true">🛠️</div>
            <h3>Dev Tools</h3>
            <p>Git/GitHub, Chrome DevTools, Lighthouse audits, VS Code, and performance optimization.</p>
            <div class="skill-bar-wrap" role="progressbar" aria-valuenow="78" aria-valuemin="0" aria-valuemax="100" aria-label="Dev tools skill level 78%">
              <div class="skill-bar-label"><span>Tooling</span><span>78%</span></div>
              <div class="skill-bar"><div class="skill-bar-fill" data-width="78" style="width:0%"></div></div>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- TASK 1: Projects Section -->
    <section id="projects" aria-labelledby="projects-title">
      <div class="container">
        <p class="section-label">What I've built</p>
        <h2 class="section-title" id="projects-title">Internship Projects</h2>
        <p class="section-desc">Five projects built as part of the Thiranex Web Development internship program.</p>

        <div class="projects-grid">
          <article class="project-card reveal">
            <p class="project-num">01 / HTML5</p>
            <h3>Semantic Portfolio Structure</h3>
            <p>Multi-page personal portfolio website built strictly using modern semantic HTML5 standards and WCAG accessibility guidelines. Features ARIA labels, keyboard navigation, and 100/100 Lighthouse accessibility score.</p>
            <div class="project-tags">
              <span class="tag">HTML5</span>
              <span class="tag">WCAG 2.1</span>
              <span class="tag">ARIA</span>
              <span class="tag">SEO</span>
            </div>
          </article>

          <article class="project-card reveal">
            <p class="project-num">02 / CSS3</p>
            <h3>Advanced Responsive Architecture</h3>
            <p>Pixel-perfect, fully responsive website using CSS Grid for 2D layouts, Flexbox for alignment, mobile-first media queries, and dynamic light/dark mode via CSS custom properties.</p>
            <div class="project-tags">
              <span class="tag">CSS Grid</span>
              <span class="tag">Flexbox</span>
              <span class="tag">CSS Variables</span>
              <span class="tag">Dark Mode</span>
            </div>
          </article>

          <article class="project-card reveal">
            <p class="project-num">03 / JavaScript</p>
            <h3>JS Logic & State Management</h3>
            <p>Interactive client-side To-Do List application with full CRUD operations, localStorage data persistence, dynamic filtering (All/Active/Completed), and delegated event listeners.</p>
            <div class="project-tags">
              <span class="tag">DOM API</span>
              <span class="tag">localStorage</span>
              <span class="tag">Events</span>
              <span class="tag">State</span>
            </div>
          </article>

          <article class="project-card reveal">
            <p class="project-num">04 / Async JS</p>
            <h3>Weather Dashboard & REST API</h3>
            <p>Real-time weather dashboard fetching live JSON data from the Open-Meteo public REST API using async/await and the Fetch API. Includes city search, error handling, and dynamic rendering of temperature, humidity, and wind speed.</p>
            <div class="project-tags">
              <span class="tag">Fetch API</span>
              <span class="tag">async/await</span>
              <span class="tag">REST API</span>
              <span class="tag">JSON</span>
            </div>
          </article>

          <article class="project-card reveal">
            <p class="project-num">05 / Capstone</p>
            <h3>Full-Stack E-commerce Catalog</h3>
            <p>Production-ready e-commerce product catalog combining all prior skills: modular frontend architecture, client-side routing, cart state management, and API-driven product listings. Deployed live on GitHub Pages.</p>
            <div class="project-tags">
              <span class="tag">Modular JS</span>
              <span class="tag">Routing</span>
              <span class="tag">Cart State</span>
              <span class="tag">Deployed</span>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- TASK 3: JavaScript To-Do App -->
    <section id="todo" aria-labelledby="todo-title">
      <div class="container">
        <p class="section-label">Live Project 03</p>
        <h2 class="section-title" id="todo-title">Task Manager</h2>
        <p class="section-desc">Fully functional To-Do app with localStorage persistence. Your tasks survive page refreshes!</p>

        <div class="todo-wrapper">
          <!-- Input -->
          <div class="todo-input-group" role="search">
            <label for="todoInput" class="sr-only" style="position:absolute;clip:rect(0 0 0 0);">Add a new task</label>
            <input
              type="text"
              id="todoInput"
              class="todo-input"
              placeholder="Add a new task… (press Enter)"
              aria-label="New task input"
              maxlength="120"
            />
            <button class="todo-add-btn" id="addTodoBtn" aria-label="Add task">+ Add Task</button>
          </div>

          <!-- Filters -->
          <div class="todo-filters" role="group" aria-label="Filter tasks">
            <button class="filter-btn active" data-filter="all" aria-pressed="true">All</button>
            <button class="filter-btn" data-filter="active" aria-pressed="false">Active</button>
            <button class="filter-btn" data-filter="completed" aria-pressed="false">Completed</button>
          </div>

          <!-- Stats -->
          <div class="todo-stats" aria-live="polite" aria-atomic="true">
            <span id="todoCount">0 tasks remaining</span>
            <button class="clear-btn" id="clearCompleted" aria-label="Clear all completed tasks">Clear completed</button>
          </div>

          <!-- List -->
          <ul class="todo-list" id="todoList" aria-label="Task list" aria-live="polite">
            <li class="todo-empty" id="todoEmpty">
              <span aria-hidden="true">📝</span>
              Nothing here yet — add your first task!
            </li>
          </ul>
        </div>
      </div>
    </section>

    <!-- TASK 4: Async JS & RESTful API — Weather Dashboard -->
    <section id="weather" aria-labelledby="weather-title">
      <div class="container">
        <p class="section-label">Live Project 04</p>
        <h2 class="section-title" id="weather-title">Weather Dashboard</h2>
        <p class="section-desc">Real-time weather data via Open-Meteo's free REST API — no API key needed. Search any city!</p>

        <div class="weather-wrapper">
          <!-- Search bar -->
          <div class="weather-search-row">
            <label for="cityInput" style="position:absolute;clip:rect(0 0 0 0);">City name</label>
            <input type="text" id="cityInput" class="todo-input weather-input" placeholder="Enter city name… e.g. Hyderabad" aria-label="City name" maxlength="80" />
            <button class="todo-add-btn" id="weatherSearchBtn" aria-label="Search weather">🔍 Search</button>
          </div>

          <!-- Error -->
          <div id="weatherError" class="weather-error" role="alert" aria-live="polite" style="display:none"></div>

          <!-- Loading -->
          <div id="weatherLoading" class="weather-loading" aria-live="polite" style="display:none">
            <div class="weather-spinner" aria-hidden="true"></div>
            <span>Fetching weather data…</span>
          </div>

          <!-- Result card -->
          <div id="weatherCard" class="weather-card" style="display:none" aria-live="polite">
            <div class="weather-top">
              <div>
                <h3 id="weatherCity" class="weather-city"></h3>
                <p id="weatherDesc" class="weather-desc"></p>
              </div>
              <div class="weather-icon-big" id="weatherIcon" aria-hidden="true"></div>
            </div>
            <div class="weather-metrics">
              <div class="weather-metric">
                <span class="metric-icon" aria-hidden="true">🌡️</span>
                <span class="metric-val" id="wTemp">--</span>
                <span class="metric-label">Temperature</span>
              </div>
              <div class="weather-metric">
                <span class="metric-icon" aria-hidden="true">💧</span>
                <span class="metric-val" id="wHumidity">--</span>
                <span class="metric-label">Humidity</span>
              </div>
              <div class="weather-metric">
                <span class="metric-icon" aria-hidden="true">💨</span>
                <span class="metric-val" id="wWind">--</span>
                <span class="metric-label">Wind Speed</span>
              </div>
              <div class="weather-metric">
                <span class="metric-icon" aria-hidden="true">☔</span>
                <span class="metric-val" id="wRain">--</span>
                <span class="metric-label">Precipitation</span>
              </div>
            </div>
            <p class="weather-source">Data: <a href="https://open-meteo.com" target="_blank" rel="noopener noreferrer">Open-Meteo API</a> + <a href="https://geocoding-api.open-meteo.com" target="_blank" rel="noopener noreferrer">Open-Meteo Geocoding</a></p>
          </div>
        </div>
      </div>
    </section>

    <!-- TASK 5: Full-Stack Deployment — E-commerce Catalog -->
    <section id="shop" aria-labelledby="shop-title">
      <div class="container">
        <p class="section-label">Live Project 05</p>
        <h2 class="section-title" id="shop-title">E-commerce Product Catalog</h2>
        <p class="section-desc">Capstone project — live product catalog with cart, client-side routing, and category filters powered by the FakeStore API.</p>

        <!-- Shop toolbar -->
        <div class="shop-toolbar">
          <div class="shop-filters" role="group" aria-label="Filter by category">
            <button class="shop-filter active" data-cat="all">All</button>
            <button class="shop-filter" data-cat="electronics">Electronics</button>
            <button class="shop-filter" data-cat="jewelery">Jewellery</button>
            <button class="shop-filter" data-cat="men's clothing">Men's</button>
            <button class="shop-filter" data-cat="women's clothing">Women's</button>
          </div>
          <div class="cart-badge-wrap">
            <button class="cart-btn" id="cartToggle" aria-label="Open cart" aria-expanded="false">
              🛒 Cart <span class="cart-count" id="cartCount">0</span>
            </button>
          </div>
        </div>

        <!-- Cart panel -->
        <div id="cartPanel" class="cart-panel" style="display:none" aria-label="Shopping cart" role="region">
          <div class="cart-header">
            <h3>Your Cart</h3>
            <button class="cart-close" id="cartClose" aria-label="Close cart">✕</button>
          </div>
          <ul class="cart-list" id="cartList" aria-label="Cart items"></ul>
          <div class="cart-footer">
            <span class="cart-total-label">Total:</span>
            <span class="cart-total" id="cartTotal">$0.00</span>
            <button class="btn btn-primary" id="checkoutBtn" style="margin-top:0.75rem;width:100%">Checkout →</button>
          </div>
        </div>

        <!-- Shop loading -->
        <div id="shopLoading" class="weather-loading" aria-live="polite">
          <div class="weather-spinner" aria-hidden="true"></div>
          <span>Loading products…</span>
        </div>

        <!-- Product grid -->
        <div id="shopGrid" class="shop-grid" role="list" aria-label="Products" aria-live="polite"></div>
      </div>
    </section>

    <!-- TASK 1: Accessible Contact Form -->
    <section id="contact" aria-labelledby="contact-title">
      <div class="container">
        <p class="section-label">Say hello</p>
        <h2 class="section-title" id="contact-title">Get in Touch</h2>

        <div class="contact-layout">
          <div class="contact-info">
            <h3>Let's work together</h3>
            <p>Open to internship opportunities, freelance projects, and collaborative work. Feel free to reach out!</p>
            <nav class="contact-links" aria-label="Social links">
              <a href="mailto:your@email.com" class="contact-link" aria-label="Send email">
                <span aria-hidden="true">✉️</span> your@email.com
              </a>
              <a href="https://github.com" class="contact-link" target="_blank" rel="noopener noreferrer" aria-label="GitHub profile (opens in new tab)">
                <span aria-hidden="true">🐙</span> github.com/yourname
              </a>
              <a href="https://linkedin.com" class="contact-link" target="_blank" rel="noopener noreferrer" aria-label="LinkedIn profile (opens in new tab)">
                <span aria-hidden="true">💼</span> linkedin.com/in/yourname
              </a>
            </nav>
          </div>

          <!-- TASK 1: Accessible, tab-navigable contact form -->
          <div class="contact-form" role="form" aria-label="Contact form">
            <div id="formSuccess" class="form-success" role="alert" aria-live="polite">
              ✅ Message sent! I'll get back to you soon.
            </div>
            <div class="form-group">
              <label for="contactName">Name <span class="required" aria-label="required">*</span></label>
              <input
                type="text"
                id="contactName"
                class="form-input"
                placeholder="Your full name"
                required
                aria-required="true"
                autocomplete="name"
              />
            </div>
            <div class="form-group">
              <label for="contactEmail">Email <span class="required" aria-label="required">*</span></label>
              <input
                type="email"
                id="contactEmail"
                class="form-input"
                placeholder="your@email.com"
                required
                aria-required="true"
                autocomplete="email"
              />
            </div>
            <div class="form-group">
              <label for="contactMsg">Message <span class="required" aria-label="required">*</span></label>
              <textarea
                id="contactMsg"
                class="form-textarea"
                placeholder="Tell me about your project or opportunity…"
                required
                aria-required="true"
              ></textarea>
            </div>
            <button type="button" class="form-submit" id="formSubmit">Send Message →</button>
          </div>
        </div>
      </div>
    </section>

  </main>

  <!-- TASK 1: Semantic Footer -->
  <footer role="contentinfo">
    <div class="footer-inner">
      <p>© 2026 <a href="#">dev.portfolio</a>. Built with HTML5, CSS3 & JavaScript.</p>
      <p>Internship project for <a href="https://thiranex.in" target="_blank" rel="noopener noreferrer">Thiranex</a></p>
    </div>
  </footer>

  <!-- ===== JAVASCRIPT (TASK 3: DOM, Events, localStorage) ===== -->
  <script>
    /* =============================================
       THEME TOGGLE (TASK 2: CSS Variables / Dark Mode)
    ============================================= */
    const themeBtn = document.getElementById('themeToggle');
    const html = document.documentElement;

    function applyTheme(theme) {
      if (theme === 'light') {
        html.classList.add('light');
        themeBtn.textContent = '☀️';
        themeBtn.setAttribute('aria-label', 'Switch to dark mode');
      } else {
        html.classList.remove('light');
        themeBtn.textContent = '🌙';
        themeBtn.setAttribute('aria-label', 'Switch to light mode');
      }
    }

    const savedTheme = localStorage.getItem('theme') || 'dark';
    applyTheme(savedTheme);

    themeBtn.addEventListener('click', () => {
      const next = html.classList.contains('light') ? 'dark' : 'light';
      localStorage.setItem('theme', next);
      applyTheme(next);
    });

    /* =============================================
       HAMBURGER MENU (TASK 2: Responsive)
    ============================================= */
    const hamburger = document.getElementById('hamburger');
    const navLinks = document.getElementById('navLinks');

    hamburger.addEventListener('click', () => {
      const isOpen = navLinks.classList.toggle('open');
      hamburger.setAttribute('aria-expanded', isOpen);
      hamburger.textContent = isOpen ? '✕' : '☰';
      hamburger.setAttribute('aria-label', isOpen ? 'Close navigation menu' : 'Open navigation menu');
    });

    // Close menu on link click
    navLinks.querySelectorAll('a').forEach(link => {
      link.addEventListener('click', () => {
        navLinks.classList.remove('open');
        hamburger.setAttribute('aria-expanded', 'false');
        hamburger.textContent = '☰';
      });
    });

    /* =============================================
       SCROLL REVEAL
    ============================================= */
    const revealEls = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.classList.add('visible');
          observer.unobserve(e.target);
        }
      });
    }, { threshold: 0.12 });
    revealEls.forEach(el => observer.observe(el));

    /* =============================================
       SKILL BAR ANIMATION
    ============================================= */
    const barObserver = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.querySelectorAll('.skill-bar-fill').forEach(bar => {
            bar.style.width = bar.dataset.width + '%';
          });
          barObserver.unobserve(e.target);
        }
      });
    }, { threshold: 0.3 });
    document.querySelectorAll('.skill-card').forEach(c => barObserver.observe(c));

    /* =============================================
       TODO APP (TASK 3: Full CRUD + localStorage)
    ============================================= */
    const todoInput    = document.getElementById('todoInput');
    const addBtn       = document.getElementById('addTodoBtn');
    const todoList     = document.getElementById('todoList');
    const todoEmpty    = document.getElementById('todoEmpty');
    const todoCount    = document.getElementById('todoCount');
    const clearBtn     = document.getElementById('clearCompleted');
    const filterBtns   = document.querySelectorAll('.filter-btn');

    let todos = JSON.parse(localStorage.getItem('todos') || '[]');
    let currentFilter = 'all';

    // Save to localStorage
    function saveTodos() {
      localStorage.setItem('todos', JSON.stringify(todos));
    }

    // Render tasks based on filter
    function render() {
      const filtered = todos.filter(t => {
        if (currentFilter === 'active') return !t.done;
        if (currentFilter === 'completed') return t.done;
        return true;
      });

      // Remove all items except the empty message
      Array.from(todoList.children).forEach(child => {
        if (child !== todoEmpty) child.remove();
      });

      if (filtered.length === 0) {
        todoEmpty.style.display = 'block';
        todoEmpty.querySelector('span').textContent = currentFilter === 'completed' ? '🎉' : '📝';
        todoEmpty.lastChild.textContent = currentFilter === 'completed'
          ? ' No completed tasks yet!'
          : currentFilter === 'active'
          ? ' No active tasks — you\'re done!'
          : ' Nothing here yet — add your first task!';
      } else {
        todoEmpty.style.display = 'none';
        filtered.forEach(todo => {
          todoList.appendChild(createItem(todo));
        });
      }

      // Update count
      const active = todos.filter(t => !t.done).length;
      todoCount.textContent = `${active} task${active !== 1 ? 's' : ''} remaining`;
    }

    // Create a todo list item element
    function createItem(todo) {
      const li = document.createElement('li');
      li.className = 'todo-item' + (todo.done ? ' completed' : '');
      li.dataset.id = todo.id;

      // Checkbox
      const cb = document.createElement('input');
      cb.type = 'checkbox';
      cb.className = 'todo-checkbox';
      cb.checked = todo.done;
      cb.setAttribute('aria-label', `Mark "${todo.text}" as ${todo.done ? 'incomplete' : 'complete'}`);
      cb.addEventListener('change', () => toggleTodo(todo.id));

      // Text
      const span = document.createElement('span');
      span.className = 'todo-text';
      span.textContent = todo.text;

      // Delete button
      const del = document.createElement('button');
      del.className = 'todo-delete';
      del.textContent = '✕';
      del.setAttribute('aria-label', `Delete task: ${todo.text}`);
      del.addEventListener('click', () => deleteTodo(todo.id));

      li.appendChild(cb);
      li.appendChild(span);
      li.appendChild(del);
      return li;
    }

    // Add new todo
    function addTodo() {
      const text = todoInput.value.trim();
      if (!text) {
        todoInput.focus();
        todoInput.style.borderColor = 'var(--clr-accent-2)';
        setTimeout(() => todoInput.style.borderColor = '', 600);
        return;
      }
      const todo = { id: Date.now(), text, done: false, createdAt: new Date().toISOString() };
      todos.unshift(todo);
      saveTodos();
      todoInput.value = '';
      render();
      todoInput.focus();
    }

    // Toggle done state
    function toggleTodo(id) {
      todos = todos.map(t => t.id === id ? { ...t, done: !t.done } : t);
      saveTodos();
      render();
    }

    // Delete a todo
    function deleteTodo(id) {
      const item = todoList.querySelector(`[data-id="${id}"]`);
      if (item) {
        item.style.opacity = '0';
        item.style.transform = 'translateX(20px)';
        item.style.transition = 'all 0.25s ease';
        setTimeout(() => {
          todos = todos.filter(t => t.id !== id);
          saveTodos();
          render();
        }, 220);
      }
    }

    // Clear completed
    clearBtn.addEventListener('click', () => {
      todos = todos.filter(t => !t.done);
      saveTodos();
      render();
    });

    // Filters
    filterBtns.forEach(btn => {
      btn.addEventListener('click', () => {
        filterBtns.forEach(b => { b.classList.remove('active'); b.setAttribute('aria-pressed', 'false'); });
        btn.classList.add('active');
        btn.setAttribute('aria-pressed', 'true');
        currentFilter = btn.dataset.filter;
        render();
      });
    });

    // Add on button click
    addBtn.addEventListener('click', addTodo);

    // Add on Enter key
    todoInput.addEventListener('keydown', (e) => {
      if (e.key === 'Enter') addTodo();
    });

    // Initial render
    render();

    /* =============================================
       CONTACT FORM (TASK 1: Accessible tab-navigable form)
    ============================================= */
    document.getElementById('formSubmit').addEventListener('click', () => {
      const name  = document.getElementById('contactName').value.trim();
      const email = document.getElementById('contactEmail').value.trim();
      const msg   = document.getElementById('contactMsg').value.trim();

      if (!name || !email || !msg) {
        alert('Please fill in all fields before sending.');
        return;
      }
      if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
        alert('Please enter a valid email address.');
        return;
      }

      const success = document.getElementById('formSuccess');
      success.style.display = 'block';
      document.getElementById('contactName').value = '';
      document.getElementById('contactEmail').value = '';
      document.getElementById('contactMsg').value = '';
      success.scrollIntoView({ behavior: 'smooth', block: 'center' });
      setTimeout(() => { success.style.display = 'none'; }, 5000);
    });
    /* =============================================
       WEATHER DASHBOARD (TASK 4: async/await + REST API)
    ============================================= */
    const cityInput      = document.getElementById('cityInput');
    const weatherBtn     = document.getElementById('weatherSearchBtn');
    const weatherCard    = document.getElementById('weatherCard');
    const weatherLoading = document.getElementById('weatherLoading');
    const weatherError   = document.getElementById('weatherError');

    const WMO_CODES = {
      0:'Clear sky ☀️', 1:'Mainly clear 🌤️', 2:'Partly cloudy ⛅', 3:'Overcast ☁️',
      45:'Foggy 🌫️', 48:'Icy fog 🌫️', 51:'Light drizzle 🌦️', 53:'Drizzle 🌦️', 55:'Heavy drizzle 🌧️',
      61:'Light rain 🌧️', 63:'Rain 🌧️', 65:'Heavy rain 🌧️',
      71:'Light snow ❄️', 73:'Snow ❄️', 75:'Heavy snow ❄️',
      80:'Showers 🌦️', 81:'Heavy showers 🌧️', 82:'Violent showers ⛈️',
      95:'Thunderstorm ⛈️', 96:'Thunderstorm with hail ⛈️', 99:'Thunderstorm with heavy hail ⛈️'
    };

    function showWeatherError(msg) {
      weatherError.textContent = msg;
      weatherError.style.display = 'block';
      weatherCard.style.display = 'none';
      weatherLoading.style.display = 'none';
    }

    async function fetchWeather() {
      const city = cityInput.value.trim();
      if (!city) { cityInput.focus(); return; }

      weatherError.style.display = 'none';
      weatherCard.style.display = 'none';
      weatherLoading.style.display = 'flex';
      weatherBtn.disabled = true;

      try {
        // Step 1: Geocoding — city name → lat/lon
        const geoRes = await fetch(
          `https://geocoding-api.open-meteo.com/v1/search?name=${encodeURIComponent(city)}&count=1&language=en&format=json`
        );
        if (!geoRes.ok) throw new Error('Geocoding service unavailable.');
        const geoData = await geoRes.json();

        if (!geoData.results || geoData.results.length === 0)
          throw new Error(`City "${city}" not found. Try a different spelling.`);

        const { latitude, longitude, name, country } = geoData.results[0];

        // Step 2: Weather — lat/lon → current weather
        const weatherRes = await fetch(
          `https://api.open-meteo.com/v1/forecast?latitude=${latitude}&longitude=${longitude}` +
          `&current=temperature_2m,relative_humidity_2m,wind_speed_10m,precipitation,weather_code` +
          `&wind_speed_unit=kmh&timezone=auto`
        );
        if (!weatherRes.ok) throw new Error('Weather service unavailable. Try again.');
        const wData = await weatherRes.json();
        const c = wData.current;

        // Render
        document.getElementById('weatherCity').textContent  = `${name}, ${country}`;
        document.getElementById('weatherDesc').textContent  = WMO_CODES[c.weather_code] || 'Unknown conditions';
        document.getElementById('weatherIcon').textContent  = (WMO_CODES[c.weather_code] || '🌍').match(/[\u{1F300}-\u{1FFFF}]|\u2600-\u26FF/gu)?.[0] || '🌍';
        document.getElementById('wTemp').textContent        = `${Math.round(c.temperature_2m)}°C`;
        document.getElementById('wHumidity').textContent    = `${c.relative_humidity_2m}%`;
        document.getElementById('wWind').textContent        = `${c.wind_speed_10m} km/h`;
        document.getElementById('wRain').textContent        = `${c.precipitation} mm`;

        weatherLoading.style.display = 'none';
        weatherCard.style.display    = 'block';
      } catch (err) {
        showWeatherError('⚠️ ' + err.message);
      } finally {
        weatherBtn.disabled = false;
      }
    }

    weatherBtn.addEventListener('click', fetchWeather);
    cityInput.addEventListener('keydown', e => { if (e.key === 'Enter') fetchWeather(); });

    // Auto-load Hyderabad on page load
    cityInput.value = 'Hyderabad';
    fetchWeather();

    /* =============================================
       E-COMMERCE SHOP (TASK 5: Modular JS + API + Cart)
    ============================================= */
    let allProducts  = [];
    let cart         = JSON.parse(localStorage.getItem('cart') || '[]');
    let activeCategory = 'all';

    const shopGrid    = document.getElementById('shopGrid');
    const shopLoading = document.getElementById('shopLoading');
    const cartPanel   = document.getElementById('cartPanel');
    const cartList    = document.getElementById('cartList');
    const cartCountEl = document.getElementById('cartCount');
    const cartTotalEl = document.getElementById('cartTotal');
    const cartToggle  = document.getElementById('cartToggle');
    const cartClose   = document.getElementById('cartClose');
    const checkoutBtn = document.getElementById('checkoutBtn');

    // --- Cart helpers ---
    function saveCart() { localStorage.setItem('cart', JSON.stringify(cart)); }

    function getCartTotal() {
      return cart.reduce((sum, item) => sum + item.price * item.qty, 0).toFixed(2);
    }

    function getTotalQty() {
      return cart.reduce((sum, item) => sum + item.qty, 0);
    }

    function updateCartBadge() {
      const qty = getTotalQty();
      cartCountEl.textContent = qty;
      cartToggle.setAttribute('aria-label', `Open cart (${qty} items)`);
    }

    function renderCart() {
      updateCartBadge();
      cartTotalEl.textContent = '$' + getCartTotal();
      cartList.innerHTML = '';
      if (cart.length === 0) {
        cartList.innerHTML = '<li class="cart-empty-msg">Your cart is empty 🛒</li>';
        return;
      }
      cart.forEach(item => {
        const li = document.createElement('li');
        li.className = 'cart-item';
        li.innerHTML = `
          <img class="cart-item-img" src="${item.image}" alt="${item.title}" loading="lazy" />
          <div class="cart-item-info">
            <div class="cart-item-name" title="${item.title}">${item.title}</div>
            <div class="cart-item-price">$${(item.price * item.qty).toFixed(2)}</div>
          </div>
          <div class="cart-item-qty">
            <button class="qty-btn" data-id="${item.id}" data-action="dec" aria-label="Decrease quantity">−</button>
            <span class="qty-num">${item.qty}</span>
            <button class="qty-btn" data-id="${item.id}" data-action="inc" aria-label="Increase quantity">+</button>
          </div>
        `;
        cartList.appendChild(li);
      });
    }

    function addToCart(product) {
      const existing = cart.find(i => i.id === product.id);
      if (existing) { existing.qty++; }
      else { cart.push({ ...product, qty: 1 }); }
      saveCart();
      renderCart();
    }

    function changeQty(id, action) {
      const item = cart.find(i => i.id === id);
      if (!item) return;
      if (action === 'inc') item.qty++;
      else { item.qty--; if (item.qty <= 0) cart = cart.filter(i => i.id !== id); }
      saveCart();
      renderCart();
    }

    // Delegated event for qty buttons inside cart
    cartList.addEventListener('click', e => {
      const btn = e.target.closest('.qty-btn');
      if (!btn) return;
      changeQty(Number(btn.dataset.id), btn.dataset.action);
    });

    // Cart toggle
    cartToggle.addEventListener('click', () => {
      const open = cartPanel.style.display === 'none';
      cartPanel.style.display = open ? 'block' : 'none';
      cartToggle.setAttribute('aria-expanded', open);
    });
    cartClose.addEventListener('click', () => {
      cartPanel.style.display = 'none';
      cartToggle.setAttribute('aria-expanded', 'false');
    });

    // Checkout
    checkoutBtn.addEventListener('click', () => {
      if (cart.length === 0) return;
      cart = [];
      saveCart();
      renderCart();
      cartPanel.style.display = 'none';
      cartToggle.setAttribute('aria-expanded', 'false');
      alert('🎉 Order placed! Thank you for your purchase.');
    });

    // --- Product rendering ---
    function renderProducts(products) {
      shopGrid.innerHTML = '';
      if (products.length === 0) {
        shopGrid.innerHTML = '<p style="color:var(--clr-text-muted);padding:2rem 0;">No products found.</p>';
        return;
      }
      products.forEach((p, i) => {
        const card = document.createElement('div');
        card.className = 'product-card';
        card.setAttribute('role', 'listitem');
        card.style.animationDelay = (i * 0.04) + 's';
        const stars = '★'.repeat(Math.round(p.rating?.rate || 4)) + '☆'.repeat(5 - Math.round(p.rating?.rate || 4));
        card.innerHTML = `
          <div class="product-img-wrap">
            <img class="product-img" src="${p.image}" alt="${p.title}" loading="lazy" />
          </div>
          <span class="product-cat">${p.category}</span>
          <p class="product-name">${p.title}</p>
          <div class="product-bottom">
            <div>
              <div class="product-price">$${p.price}</div>
              <div class="product-rating" aria-label="${p.rating?.rate} out of 5 stars">${stars} (${p.rating?.count})</div>
            </div>
            <button class="add-to-cart" data-id="${p.id}" aria-label="Add ${p.title} to cart">+ Add</button>
          </div>
        `;
        shopGrid.appendChild(card);
      });
    }

    // Delegated click for add-to-cart buttons
    shopGrid.addEventListener('click', e => {
      const btn = e.target.closest('.add-to-cart');
      if (!btn) return;
      const product = allProducts.find(p => p.id === Number(btn.dataset.id));
      if (!product) return;
      addToCart(product);
      btn.textContent = '✓ Added';
      btn.classList.add('added');
      setTimeout(() => { btn.textContent = '+ Add'; btn.classList.remove('added'); }, 1200);
    });

    // Category filters
    document.querySelectorAll('.shop-filter').forEach(btn => {
      btn.addEventListener('click', () => {
        document.querySelectorAll('.shop-filter').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        activeCategory = btn.dataset.cat;
        const filtered = activeCategory === 'all'
          ? allProducts
          : allProducts.filter(p => p.category === activeCategory);
        renderProducts(filtered);
      });
    });

    // Fetch products from FakeStore API
    async function loadProducts() {
      try {
        const res = await fetch('https://fakestoreapi.com/products');
        if (!res.ok) throw new Error('API error');
        allProducts = await res.json();
        shopLoading.style.display = 'none';
        renderProducts(allProducts);
      } catch {
        shopLoading.innerHTML = '<p style="color:var(--clr-accent-2);">⚠️ Could not load products. Check your connection.</p>';
      }
    }

    renderCart();
    loadProducts();

  </script>

</body>
</html>
