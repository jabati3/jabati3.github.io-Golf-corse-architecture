<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>The Art & Science of Golf Course Architecture</title>
  <link rel="preconnect" href="https://googleapis.com">
  <link rel="preconnect" href="https://gstatic.com" crossorigin>
  <link href="https://googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg-cream: #F6F4EE;
      --bg-card: #FFFFFF;
      --turf-dark: #1B3022;
      --turf-mid: #2E4F38;
      --sand-gold: #C2A878;
      --sand-light: #EAE3D2;
      --ink-main: #1F2421;
      --ink-muted: #5A625D;
      --border-subtle: rgba(27, 48, 34, 0.12);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      background-color: var(--bg-cream);
      color: var(--ink-main);
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
      line-height: 1.75;
      overflow-x: hidden;
    }

    /* Progress Bar */
    .progress-container {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 4px;
      background: rgba(27, 48, 34, 0.08);
      z-index: 1000;
    }

    .progress-bar {
      height: 100%;
      background: linear-gradient(90deg, var(--turf-dark), var(--sand-gold));
      width: 0%;
      transition: width 0.1s ease-out;
    }

    /* Top Navigation */
    nav {
      position: sticky;
      top: 4px;
      background: rgba(246, 244, 238, 0.9);
      backdrop-filter: blur(10px);
      border-bottom: 1px solid var(--border-subtle);
      z-index: 999;
      padding: 0.9rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .nav-brand {
      font-family: 'Cormorant Garamond', serif;
      font-weight: 700;
      font-size: 1.25rem;
      letter-spacing: 0.04em;
      color: var(--turf-dark);
      text-transform: uppercase;
    }

    .nav-links {
      display: flex;
      gap: 1.5rem;
      list-style: none;
    }

    .nav-links a {
      text-decoration: none;
      color: var(--ink-muted);
      font-size: 0.85rem;
      font-weight: 500;
      letter-spacing: 0.03em;
      transition: color 0.2s;
    }

    .nav-links a:hover {
      color: var(--turf-dark);
    }

    /* Hero Header */
    header.hero {
      position: relative;
      background-color: var(--turf-dark);
      color: var(--bg-cream);
      padding: 6rem 2rem 5rem;
      text-align: center;
      overflow: hidden;
    }

    /* Topographic SVG background pattern */
    .topo-bg {
      position: absolute;
      inset: 0;
      opacity: 0.12;
      pointer-events: none;
      background-image: url("data:image/svg+xml,%3Csvg width='600' height='600' viewBox='0 0 600 600' xmlns='http://w3.org d='M0 120 Q 150 60, 300 140 T 600 110 M0 240 Q 180 180, 340 260 T 600 220 M0 380 Q 140 440, 310 350 T 600 390 M0 500 Q 200 450, 380 520 T 600 490' fill='none' stroke='%23C2A878' stroke-width='2'/%3E%3Ccircle cx='440' cy='180' r='90' fill='none' stroke='%23C2A878' stroke-width='1.5'/%3E%3Ccircle cx='440' cy='180' r='55' fill='none' stroke='%23C2A878' stroke-width='1.5'/%3E%3Ccircle cx='160' cy='410' r='110' fill='none' stroke='%23C2A878' stroke-width='1.5'/%3E%3C/svg%3E");
    }

    .hero-inner {
      position: relative;
      max-width: 820px;
      margin: 0 auto;
    }

    .eyebrow {
      display: inline-block;
      font-size: 0.78rem;
      text-transform: uppercase;
      letter-spacing: 0.2em;
      color: var(--sand-gold);
      margin-bottom: 1.2rem;
      font-weight: 600;
    }

    h1 {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2.6rem, 5vw, 4.2rem);
      font-weight: 600;
      line-height: 1.12;
      margin-bottom: 1.5rem;
    }

    .hero-lead {
      font-size: 1.15rem;
      color: rgba(246, 244, 238, 0.88);
      font-weight: 300;
      max-width: 700px;
      margin: 0 auto 2.5rem;
    }

    .scroll-cue {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      color: var(--sand-gold);
      text-decoration: none;
      font-size: 0.85rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      border: 1px solid rgba(194, 168, 120, 0.4);
      padding: 0.65rem 1.4rem;
      border-radius: 999px;
      transition: all 0.25s ease;
    }

    .scroll-cue:hover {
      background: var(--sand-gold);
      color: var(--turf-dark);
    }

    /* Main Editorial Container */
    main {
      max-width: 860px;
      margin: 0 auto;
      padding: 4rem 1.5rem 6rem;
    }

    /* Section Styling */
    section.chapter {
      margin-bottom: 5rem;
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }

    section.chapter.visible {
      opacity: 1;
      transform: translateY(0);
    }

    .chapter-header {
      display: flex;
      align-items: baseline;
      gap: 1rem;
      margin-bottom: 1.25rem;
      border-bottom: 1px solid var(--border-subtle);
      padding-bottom: 0.75rem;
    }

    .chapter-num {
      font-family: 'Cormorant Garamond', serif;
      font-style: italic;
      font-size: 1.5rem;
      color: var(--sand-gold);
      font-weight: 700;
    }

    h2 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 2rem;
      color: var(--turf-dark);
      font-weight: 700;
    }

    .prose {
      font-size: 1.08rem;
      color: var(--ink-main);
      margin-bottom: 1.75rem;
    }

    .dropcap::first-letter {
      font-family: 'Cormorant Garamond', serif;
      float: left;
      font-size: 4.1rem;
      line-height: 0.82;
      padding-right: 0.75rem;
      padding-top: 0.2rem;
      color: var(--turf-dark);
      font-weight: 700;
    }

    /* Feature Grid Cards */
    .pill-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 1rem;
      margin-top: 1.5rem;
    }

    .info-card {
      background: var(--bg-card);
      border: 1px solid var(--border-subtle);
      border-left: 3px solid var(--turf-mid);
      padding: 1.15rem 1.25rem;
      border-radius: 6px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.02);
    }

    .info-card h3 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.25rem;
      color: var(--turf-dark);
      margin-bottom: 0.35rem;
    }

    .info-card p {
      font-size: 0.9rem;
      color: var(--ink-muted);
      line-height: 1.55;
    }

    /* Interactive Philosophy Tabs */
    .tabs-wrapper {
      background: var(--bg-card);
      border: 1px solid var(--border-subtle);
      border-radius: 8px;
      overflow: hidden;
      margin-top: 1.5rem;
    }

    .tab-buttons {
      display: flex;
      background: var(--sand-light);
      border-bottom: 1px solid var(--border-subtle);
    }

    .tab-btn {
      flex: 1;
      padding: 0.9rem 1rem;
      border: none;
      background: transparent;
      font-family: 'Inter', sans-serif;
      font-weight: 600;
      font-size: 0.9rem;
      color: var(--ink-muted);
      cursor: pointer;
      transition: all 0.2s;
    }

    .tab-btn.active {
      background: var(--bg-card);
      color: var(--turf-dark);
      box-shadow: inset 0 3px 0 var(--turf-dark);
    }

    .tab-content {
      padding: 1.5rem;
      display: none;
    }

    .tab-content.active {
      display: block;
    }

    .tab-content h4 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.4rem;
      color: var(--turf-dark);
      margin-bottom: 0.4rem;
    }

    /* Architect Badges */
    .architect-group {
      margin-top: 1.5rem;
      background: var(--bg-card);
      padding: 1.5rem;
      border-radius: 8px;
      border: 1px solid var(--border-subtle);
    }

    .era-label {
      font-size: 0.75rem;
      text-transform: uppercase;
      letter-spacing: 0.14em;
      color: var(--ink-muted);
      font-weight: 600;
      margin-bottom: 0.75rem;
      display: block;
    }

    .badge-list {
      display: flex;
      flex-wrap: wrap;
      gap: 0.6rem;
      margin-bottom: 1.25rem;
    }

    .badge-list:last-child {
      margin-bottom: 0;
    }

    .badge {
      background: var(--bg-cream);
      border: 1px solid var(--border-subtle);
      color: var(--turf-dark);
      padding: 0.4rem 0.85rem;
      border-radius: 999px;
      font-size: 0.88rem;
      font-weight: 500;
    }

    .badge.modern {
      background: rgba(27, 48, 34, 0.06);
      border-color: rgba(27, 48, 34, 0.2);
    }

    /* Pull Quote */
    blockquote.pull-quote {
      margin: 3rem 0;
      padding: 2rem 2.25rem;
      background: var(--turf-dark);
      color: var(--bg-cream);
      border-radius: 8px;
      position: relative;
    }

    blockquote.pull-quote p {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.65rem;
      font-style: italic;
      line-height: 1.45;
      color: var(--sand-light);
    }

    /* Full Unabridged Toggle */
    .unabridged-box {
      margin-top: 4rem;
      border-top: 2px solid var(--turf-dark);
      padding-top: 2rem;
    }

    details summary {
      cursor: pointer;
      font-weight: 600;
      color: var(--turf-dark);
      font-size: 0.95rem;
      letter-spacing: 0.03em;
      user-select: none;
      padding: 0.75rem 1rem;
      background: var(--sand-light);
      border-radius: 6px;
    }

    details[open] summary {
      margin-bottom: 1.25rem;
    }

    .raw-text {
      background: var(--bg-card);
      padding: 1.75rem;
      border-radius: 6px;
      border: 1px solid var(--border-subtle);
      font-size: 1rem;
      color: var(--ink-main);
    }

    footer {
      text-align: center;
      padding: 2.5rem 1.5rem;
      border-top: 1px solid var(--border-subtle);
      color: var(--ink-muted);
      font-size: 0.85rem;
