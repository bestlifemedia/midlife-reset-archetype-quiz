index.html
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#F7F2ED">
<title>The Reclaim &amp; Reset Archetype Quiz | Midlife Reset Studio</title>
<meta name="description" content="Find out which pattern is quietly draining you. A trauma-informed reflection for women in midlife transition.">

<!-- ============================================================
     This is a STANDALONE, hosted version of the quiz, meant to be
     embedded into a Systeme.io funnel page via an <iframe>, not
     pasted directly into a Raw HTML element. Host this file
     externally (GitHub Pages, Vercel, Netlify, etc.) and point an
     iframe at its live URL from the Systeme.io page.
     ============================================================ -->

<style>
  @import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400&family=Jost:wght@300;400;500;600&display=swap');

  :root {
    --bone: #F7F2ED;
    --bone-tint: #FBF8F4;
    --navy: #121826;
    --navy-soft: rgba(18, 24, 38, 0.6);
    --navy-whisper: rgba(18, 24, 38, 0.08);
    --tiffany: #80C7B5;
    --tiffany-soft: rgba(128, 199, 181, 0.15);
    --grey: #D2D1CD;
    --gold: #C9A96E;
    --white: #FFFFFF;
    --shadow-soft: 0 2px 12px rgba(18, 24, 38, 0.04);
    --shadow-lift: 0 8px 32px rgba(18, 24, 38, 0.08);
    --ease: cubic-bezier(0.22, 1, 0.36, 1);
  }

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    -webkit-tap-highlight-color: transparent;
  }

  html, body {
    background: var(--bone);
    color: var(--navy);
    font-family: 'Jost', sans-serif;
    font-weight: 300;
    line-height: 1.6;
    min-height: 100vh;
    min-height: 100dvh;
    overflow-x: hidden;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  body {
    display: flex;
    justify-content: center;
    align-items: flex-start;
    padding: 0;
  }

  /* APP FRAME — centered column, max width for tablet/desktop */
  .app {
    width: 100%;
    max-width: 560px;
    min-height: 100vh;
    min-height: 100dvh;
    position: relative;
    display: flex;
    flex-direction: column;
  }

  /* Subtle decorative side rules on desktop */
  @media (min-width: 768px) {
    body::before, body::after {
      content: '';
      position: fixed;
      top: 50%;
      transform: translateY(-50%);
      width: 1px;
      height: 40vh;
      background: linear-gradient(to bottom, transparent, var(--grey), transparent);
      opacity: 0.4;
    }
    body::before { left: calc(50% - 340px); }
    body::after { right: calc(50% - 340px); }
  }

  /* ============================================================
     PROGRESS BAR
     ============================================================ */
  .progress-wrap {
    position: sticky;
    top: 0;
    z-index: 10;
    background: var(--bone);
    padding: 20px 28px 16px;
    display: flex;
    align-items: center;
    gap: 16px;
    min-height: 56px;
  }

  .progress-back {
    background: none;
    border: none;
    color: var(--navy);
    font-size: 20px;
    cursor: pointer;
    padding: 4px 8px;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.3s var(--ease);
    font-family: inherit;
    line-height: 1;
  }

  .progress-back.visible {
    opacity: 0.6;
    pointer-events: auto;
  }

  .progress-back:hover { opacity: 1; }

  .progress-label {
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--navy-soft);
    font-weight: 500;
    flex: 1;
    text-align: center;
    opacity: 0;
    transition: opacity 0.3s var(--ease);
  }

  .progress-label.visible { opacity: 1; }

  .progress-bar {
    position: absolute;
    bottom: 0;
    left: 28px;
    right: 28px;
    height: 2px;
    background: var(--navy-whisper);
    border-radius: 2px;
    overflow: hidden;
  }

  .progress-fill {
    height: 100%;
    width: 0%;
    background: var(--tiffany);
    transition: width 0.5s var(--ease);
  }

  /* ============================================================
     SCREEN CONTAINER
     ============================================================ */
  .screen {
    flex: 1;
    padding: 24px 28px 140px;
    display: none;
    animation: screenIn 0.5s var(--ease) forwards;
  }

  .screen.active {
    display: flex;
    flex-direction: column;
  }

  @keyframes screenIn {
    from { opacity: 0; transform: translateY(12px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ============================================================
     WELCOME + CLOSING LOGO
     ============================================================ */
  .logo-badge {
    width: 88px;
    height: 88px;
    border-radius: 6px;
    background: var(--navy);
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    box-shadow: var(--shadow-lift);
    margin: 0 auto;
  }

  .logo-badge img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }

  .logo-badge.small {
    width: 64px;
    height: 64px;
  }

  /* ============================================================
     WELCOME SCREEN
     ============================================================ */
  .welcome {
    text-align: center;
    padding-top: 8vh;
  }

  .welcome .logo-badge { margin-bottom: 44px; }

  .welcome-eyebrow {
    font-size: 10px;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 500;
    margin-bottom: 20px;
  }

  .welcome h1 {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(36px, 8vw, 52px);
    line-height: 1.1;
    color: var(--navy);
    margin-bottom: 24px;
    letter-spacing: -0.01em;
  }

  .welcome h1 em {
    font-style: italic;
    color: var(--navy-soft);
  }

  .gold-rule {
    width: 40px;
    height: 1px;
    background: var(--gold);
    margin: 28px auto;
  }

  .welcome-body {
    font-size: 16px;
    color: var(--navy);
    opacity: 0.75;
    line-height: 1.7;
    max-width: 420px;
    margin: 0 auto 40px;
    font-weight: 300;
  }

  .welcome-meta {
    font-size: 11px;
    letter-spacing: 2.5px;
    text-transform: uppercase;
    color: var(--navy-soft);
    font-weight: 500;
    margin-top: 32px;
  }

  .welcome-meta span {
    margin: 0 10px;
    color: var(--grey);
  }

  /* ============================================================
     QUESTION SCREEN
     ============================================================ */
  .question-wrap {
    padding-top: 24px;
  }

  .question-eyebrow {
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 500;
    margin-bottom: 16px;
  }

  .question h2 {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 400;
    font-size: clamp(26px, 5.5vw, 34px);
    line-height: 1.25;
    color: var(--navy);
    margin-bottom: 36px;
    letter-spacing: -0.005em;
  }

  .question-helper {
    font-size: 14px;
    color: var(--navy-soft);
    margin-top: -24px;
    margin-bottom: 32px;
    font-style: italic;
    font-family: 'Cormorant Garamond', serif;
    font-size: 17px;
  }

  /* ============================================================
     ANSWER CARDS
     ============================================================ */
  .answers {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .answer {
    background: var(--white);
    border: 1px solid var(--grey);
    border-radius: 12px;
    padding: 18px 22px;
    font-family: 'Jost', sans-serif;
    font-size: 16px;
    font-weight: 400;
    color: var(--navy);
    line-height: 1.45;
    text-align: left;
    cursor: pointer;
    position: relative;
    transition: all 0.25s var(--ease);
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
    min-height: 62px;
  }

  .answer:hover {
    border-color: var(--tiffany);
    box-shadow: var(--shadow-soft);
  }

  .answer.selected {
    border-color: var(--tiffany);
    border-width: 2px;
    padding: 17px 21px;
    background: var(--tiffany-soft);
  }

  .answer-text {
    flex: 1;
  }

  .answer-check {
    width: 22px;
    height: 22px;
    border-radius: 6px;
    border: 1.5px solid var(--grey);
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    transition: all 0.25s var(--ease);
  }

  .answer.selected .answer-check {
    background: var(--tiffany);
    border-color: var(--tiffany);
  }

  .answer-check svg {
    width: 14px;
    height: 14px;
    stroke: var(--white);
    stroke-width: 3;
    fill: none;
    opacity: 0;
    transition: opacity 0.2s var(--ease);
  }

  .answer.selected .answer-check svg { opacity: 1; }

  /* ============================================================
     BRIDGE SCREENS
     ============================================================ */
  .bridge {
    text-align: center;
    padding-top: 15vh;
  }

  .bridge-section {
    font-size: 10px;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 500;
    margin-bottom: 24px;
  }

  .bridge h2 {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(30px, 6.5vw, 42px);
    line-height: 1.2;
    color: var(--navy);
    margin-bottom: 24px;
    letter-spacing: -0.01em;
  }

  .bridge h2 em {
    font-style: italic;
    color: var(--tiffany);
  }

  .bridge-body {
    font-size: 16px;
    color: var(--navy);
    opacity: 0.75;
    line-height: 1.7;
    max-width: 380px;
    margin: 0 auto;
    font-weight: 300;
  }

  /* ============================================================
     RESULT SCREEN
     ============================================================ */
  .result {
    padding-top: 24px;
  }

  .result-eyebrow {
    font-size: 10px;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 500;
    margin-bottom: 12px;
    text-align: center;
  }

  .result-name {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-weight: 300;
    font-size: 18px;
    color: var(--navy-soft);
    text-align: center;
    margin-bottom: 8px;
  }

  .result-archetype {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 400;
    font-size: clamp(32px, 7vw, 46px);
    line-height: 1.1;
    color: var(--navy);
    text-align: center;
    margin-bottom: 20px;
    letter-spacing: -0.01em;
  }

  .result-secondary {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-weight: 300;
    font-size: 16px;
    color: var(--navy-soft);
    text-align: center;
    margin-bottom: 32px;
  }

  .result-secondary span {
    color: var(--tiffany);
    font-style: normal;
    font-weight: 400;
  }

  .result-body {
    font-size: 16px;
    color: var(--navy);
    line-height: 1.75;
    font-weight: 300;
  }

  .result-body p {
    margin-bottom: 20px;
  }

  .result-body p:last-child {
    margin-bottom: 0;
  }

  .result-next {
    margin: 48px 0 32px;
    padding: 32px 28px;
    background: var(--white);
    border: 1px solid var(--grey);
    border-radius: 12px;
    text-align: center;
  }

  .result-next-label {
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 500;
    margin-bottom: 16px;
  }

  .result-next h3 {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 400;
    font-size: 24px;
    line-height: 1.3;
    color: var(--navy);
    margin-bottom: 16px;
  }

  .result-next p {
    font-size: 15px;
    color: var(--navy);
    opacity: 0.75;
    line-height: 1.7;
    margin-bottom: 24px;
  }

  .result-cta {
    display: inline-block;
    background: var(--navy);
    color: var(--bone);
    text-decoration: none;
    padding: 16px 32px;
    border-radius: 999px;
    font-family: 'Jost', sans-serif;
    font-weight: 500;
    font-size: 13px;
    letter-spacing: 2px;
    text-transform: uppercase;
    transition: all 0.25s var(--ease);
  }

  .result-cta:hover {
    background: var(--tiffany);
    color: var(--navy);
    transform: translateY(-1px);
    box-shadow: var(--shadow-lift);
  }

  .result-signoff {
    text-align: center;
    padding: 40px 0 24px;
    border-top: 1px solid var(--navy-whisper);
    margin-top: 32px;
  }

  .result-signoff .logo-badge { margin: 0 auto 20px; }

  .result-signoff-text {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: 18px;
    color: var(--navy-soft);
    margin-bottom: 8px;
  }

  .result-signoff-studio {
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 500;
  }

  /* ============================================================
     SAFETY SCREEN
     ============================================================ */
  .safety-pause {
    padding-top: 6vh;
  }

  .safety-mark {
    width: 48px;
    height: 48px;
    border: 1px solid var(--tiffany);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 28px;
  }

  .safety-mark::before {
    content: '';
    width: 12px;
    height: 12px;
    background: var(--tiffany);
    border-radius: 50%;
  }

  .safety-pause h2 {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(28px, 6vw, 38px);
    line-height: 1.2;
    color: var(--navy);
    text-align: center;
    margin-bottom: 28px;
    letter-spacing: -0.01em;
  }

  .safety-pause h2 em {
    font-style: italic;
    color: var(--tiffany);
  }

  .safety-body {
    font-size: 16px;
    color: var(--navy);
    line-height: 1.75;
    font-weight: 300;
  }

  .safety-body p {
    margin-bottom: 20px;
  }

  .safety-choice {
    margin-top: 40px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  /* ============================================================
     CTA BUTTON (sticky footer)
     ============================================================ */
  .cta-wrap {
    position: fixed;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 100%;
    max-width: 560px;
    padding: 40px 28px 28px;
    background: linear-gradient(
      to bottom,
      rgba(247, 242, 237, 0) 0%,
      rgba(247, 242, 237, 0.85) 35%,
      var(--bone) 65%
    );
    z-index: 20;
    pointer-events: none;
  }

  .cta-wrap .cta { pointer-events: auto; }

  /* Scroll cue chevron — appears when content extends below fold */
  .scroll-cue {
    position: fixed;
    bottom: 104px;
    left: 50%;
    transform: translateX(-50%);
    width: 32px;
    height: 32px;
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.4s var(--ease);
    z-index: 15;
  }

  .scroll-cue.visible {
    opacity: 0.55;
    animation: bounceCue 2s ease-in-out infinite;
  }

  .scroll-cue svg {
    width: 20px;
    height: 20px;
    stroke: var(--navy);
    stroke-width: 1.5;
    fill: none;
  }

  @keyframes bounceCue {
    0%, 100% { transform: translateX(-50%) translateY(0); }
    50% { transform: translateX(-50%) translateY(6px); }
  }

  @media (min-width: 768px) {
    .scroll-cue { bottom: 116px; }
  }

  .cta {
    width: 100%;
    background: var(--navy);
    color: var(--bone);
    border: none;
    border-radius: 999px;
    padding: 20px;
    font-family: 'Jost', sans-serif;
    font-weight: 500;
    font-size: 13px;
    letter-spacing: 3px;
    text-transform: uppercase;
    cursor: pointer;
    transition: all 0.3s var(--ease);
    position: relative;
  }

  .cta:hover:not(:disabled) {
    background: var(--tiffany);
    color: var(--navy);
    transform: translateY(-1px);
    box-shadow: var(--shadow-lift);
  }

  .cta:disabled {
    background: var(--grey);
    color: var(--white);
    cursor: not-allowed;
    opacity: 0.6;
  }

  .cta.loading {
    color: transparent;
    pointer-events: none;
  }

  .cta.loading::after {
    content: '';
    position: absolute;
    width: 20px;
    height: 20px;
    top: 50%;
    left: 50%;
    margin-top: -10px;
    margin-left: -10px;
    border: 2px solid var(--bone);
    border-top-color: transparent;
    border-radius: 50%;
    animation: spin 0.8s linear infinite;
  }

  @keyframes spin {
    to { transform: rotate(360deg); }
  }

  /* ============================================================
     RESPONSIVE ADJUSTMENTS
     ============================================================ */
  @media (min-width: 768px) {
    .screen {
      padding: 32px 40px 160px;
    }
    .progress-wrap {
      padding: 28px 40px 20px;
    }
    .progress-bar {
      left: 40px;
      right: 40px;
    }
    .cta-wrap {
      padding: 48px 40px 36px;
    }
    .welcome {
      padding-top: 10vh;
    }
    .bridge {
      padding-top: 18vh;
    }
  }

  @media (min-width: 1024px) {
    body {
      background: var(--bone);
    }
    .app {
      background: var(--bone);
      max-width: 600px;
    }
    .cta-wrap {
      max-width: 600px;
    }
  }

  /* Smooth scroll behavior */
  html { scroll-behavior: smooth; }

  /* Remove default button styles */
  button { font: inherit; }

  /* Hide scrollbar but allow scrolling */
  .screen::-webkit-scrollbar { display: none; }
  .screen { -ms-overflow-style: none; scrollbar-width: none; }
</style>
</head>
<body>

<div class="app" id="app">

  <!-- PROGRESS HEADER -->
  <div class="progress-wrap" id="progressWrap">
    <button class="progress-back" id="backBtn" aria-label="Go back">←</button>
    <div class="progress-label" id="progressLabel">Begin</div>
    <div class="progress-bar">
      <div class="progress-fill" id="progressFill"></div>
    </div>
  </div>

  <!-- SCREEN: WELCOME -->
  <section class="screen active welcome" id="screen-welcome" data-screen="welcome">
    <div class="logo-badge">
      <img src="data:image/png;base64,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tzlr3Atdlp5cvAzw5WTZuOURf0nJJOOfkML+LsyIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiD/9k=" alt="Midlife Reset Studio">
    </div>
    <div class="welcome-eyebrow">The Reclaim & Reset Method</div>
    <h1>The Archetype<br><em>Quiz</em></h1>
    <div class="gold-rule"></div>
    <p class="welcome-body">
      A trauma-informed reflection for women in midlife.<br><br>
      This isn't here to define you. It's here to mirror back the pattern that has been quietly draining you, and the one that you're ready to put down.
    </p>
    <div class="welcome-meta">
      25 Questions <span>·</span> 8 Minutes <span>·</span> Results On This Page
    </div>
  </section>

  <!-- SCREEN: SAFETY BRIDGE -->
  <section class="screen" id="screen-bridge-safety" data-screen="bridge">
    <div class="bridge">
      <div class="bridge-section">Part One</div>
      <h2>Before we<br>begin, <em>a few<br>gentle questions</em></h2>
      <div class="gold-rule"></div>
      <p class="bridge-body">
        Your emotional safety matters more than any result. These first four questions help me understand how to hold space for you today.
      </p>
    </div>
  </section>

  <!-- QUESTION SCREENS DYNAMICALLY INSERTED HERE -->
  <div id="question-container"></div>

  <!-- SCREEN: SAFETY PAUSE (conditional) -->
  <section class="screen" id="screen-safety-pause" data-screen="safety">
    <div class="safety-pause">
      <div class="safety-mark"></div>
      <h2>Before anything else —<br><em>your safety matters</em></h2>
      <div class="gold-rule"></div>
      <div class="safety-body">
        <p>
          You've carried so much, often without enough support or acknowledgment. What you're feeling right now isn't a flaw. It's your nervous system signaling that it needs steadiness before anything else.
        </p>
        <p>
          This quiz was made to offer reflection, not pressure. And if you're feeling unsettled, unsafe, or deeply overwhelmed, it's okay to slow everything down. That's the most courageous thing you can do in a moment like this.
        </p>
        <p>
          Before going further, please reach for support that brings you safety in your day to day: a trusted friend, a therapist, a helpline if you need one, or a grounding practice that helps you return to the present moment. You don't have to do any of this alone.
        </p>
        <p>
          When you feel steadier, your results will be here. You are here. That's enough for right now.
        </p>
      </div>
      <div class="safety-choice">
        <button class="answer" id="safety-continue">
          <span class="answer-text">I feel steady enough to see my results</span>
          <div class="answer-check">
            <svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg>
          </div>
        </button>
        <button class="answer" id="safety-pause-btn">
          <span class="answer-text">I'd like to pause here for now</span>
          <div class="answer-check">
            <svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg>
          </div>
        </button>
      </div>
    </div>
  </section>

  <!-- SCREEN: RESULT -->
  <section class="screen" id="screen-result" data-screen="result">
    <div class="result" id="resultContent">
      <!-- Populated by JS -->
    </div>
  </section>

  <!-- SCREEN: PAUSE -->
  <section class="screen" id="screen-paused" data-screen="paused">
    <div class="bridge">
      <div class="bridge-section">A Soft Landing</div>
      <h2>Rest <em>here</em></h2>
      <div class="gold-rule"></div>
      <p class="bridge-body">
        You don't need to complete anything today. When you're ready, the quiz will be waiting. You are not behind. You are here. That's enough.
      </p>
    </div>
  </section>

  <!-- STICKY CTA -->
  <div class="cta-wrap" id="ctaWrap">
    <button class="cta" id="ctaBtn" disabled>Continue</button>
  </div>

  <!-- SCROLL CUE -->
  <div class="scroll-cue" id="scrollCue" aria-hidden="true">
    <svg viewBox="0 0 24 24">
      <polyline points="6 9 12 15 18 9"/>
    </svg>
  </div>

</div>

<script>
  // ============================================================
  // QUIZ DATA
  // ============================================================

  const SAFETY_QUESTIONS = [
    {
      id: 'q1',
      section: 'Safety Check',
      question: 'Before we begin, how are you feeling emotionally today?',
      helper: 'Choose what feels most true.',
      answers: [
        { text: 'Steady enough to reflect', safety: 0 },
        { text: 'A bit activated, but okay to continue', safety: 0 },
        { text: 'Emotionally heavy or overwhelmed', safety: 1 },
        { text: 'Really unsettled or on edge', safety: 1 }
      ]
    },
    {
      id: 'q2',
      section: 'Safety Check',
      question: 'In the past week, how often have you felt emotionally unsafe in your environment or relationships?',
      answers: [
        { text: 'Rarely or never', safety: 0 },
        { text: 'Sometimes', safety: 0 },
        { text: 'Often', safety: 1 },
        { text: 'Almost every day', safety: 1 }
      ]
    },
    {
      id: 'q3',
      section: 'Safety Check',
      question: 'When you feel overwhelmed, how hard is it to come back to baseline?',
      answers: [
        { text: 'I can self-regulate with some effort', safety: 0 },
        { text: 'It takes a while, but I get there', safety: 0 },
        { text: 'It feels almost impossible', safety: 1 },
        { text: "I don't feel like I have a baseline anymore", safety: 1 }
      ]
    },
    {
      id: 'q4',
      section: 'Safety Check',
      question: 'Are you currently in a situation where you feel emotionally or physically unsafe?',
      helper: 'This question is optional but important.',
      answers: [
        { text: 'No', safety: 0 },
        { text: "I'm unsure", safety: 1 },
        { text: 'Yes, emotionally unsafe', safety: 1 },
        { text: 'Yes, emotionally and physically unsafe', safety: 2 }
      ]
    }
  ];

  const CORE_QUESTIONS = [
    {
      id: 'q5',
      question: 'When stress hits, your automatic response is to…',
      answers: [
        { text: 'Take over and handle everything', type: 'overfunctioner' },
        { text: 'Shut down and silently push through', type: 'silentstriver' },
        { text: 'Overthink or fear relational loss', type: 'attachment' },
        { text: 'Feel startled, unsafe, or blindsided', type: 'betrayal' },
        { text: 'Say yes to avoid conflict', type: 'boundaries' }
      ]
    },
    {
      id: 'q6',
      question: "What do you most often feel responsible for, even when it isn't yours?",
      answers: [
        { text: "Everyone's needs and schedules", type: 'overfunctioner' },
        { text: "Keeping myself together so I don't fall behind", type: 'silentstriver' },
        { text: "Others' emotional reactions", type: 'attachment' },
        { text: 'Predicting danger or avoiding conflict', type: 'betrayal' },
        { text: 'Keeping everything calm and drama-free', type: 'boundaries' }
      ]
    },
    {
      id: 'q7',
      question: 'Inside close relationships, you tend to…',
      answers: [
        { text: 'Overfunction and guide everything', type: 'overfunctioner' },
        { text: 'Stay quiet to avoid burdening anyone', type: 'silentstriver' },
        { text: 'Fear being too much or not enough', type: 'attachment' },
        { text: 'Feel unsure who you can trust', type: 'betrayal' },
        { text: 'Put others first at the cost of yourself', type: 'boundaries' }
      ]
    },
    {
      id: 'q8',
      question: 'When someone is disappointed in you, your first instinct is…',
      answers: [
        { text: 'Fix it immediately', type: 'overfunctioner' },
        { text: 'Retreat and replay it quietly', type: 'silentstriver' },
        { text: "Apologize, even when it wasn't your fault", type: 'attachment' },
        { text: 'Feel panic or fear in your body', type: 'betrayal' },
        { text: 'Change your plans to make them comfortable', type: 'boundaries' }
      ]
    },
    {
      id: 'q9',
      question: 'You often wish you could…',
      answers: [
        { text: 'Stop carrying everything alone', type: 'overfunctioner' },
        { text: 'Finally exhale and rest without guilt', type: 'silentstriver' },
        { text: 'Trust yourself and your relationships', type: 'attachment' },
        { text: 'Feel emotionally safe again', type: 'betrayal' },
        { text: 'Say no without fear', type: 'boundaries' }
      ]
    },
    {
      id: 'q10',
      question: "You're most exhausted by…",
      answers: [
        { text: 'Doing everything for everyone', type: 'overfunctioner' },
        { text: "Pretending you're okay", type: 'silentstriver' },
        { text: 'Feeling like you are too much or not enough', type: 'attachment' },
        { text: 'Never feeling fully safe', type: 'betrayal' },
        { text: "Being needed more than you're supported", type: 'boundaries' }
      ]
    },
    {
      id: 'q11',
      question: 'When you feel disconnected, you…',
      answers: [
        { text: 'Try harder and work more', type: 'overfunctioner' },
        { text: 'Withdraw inward', type: 'silentstriver' },
        { text: 'Chase reassurance', type: 'attachment' },
        { text: 'Shut down from fear', type: 'betrayal' },
        { text: 'Over-accommodate', type: 'boundaries' }
      ]
    }
  ];

  const SOMATIC_QUESTIONS = [
    {
      id: 'q12',
      question: 'How do you usually handle emotional pain?',
      answers: [
        { text: 'I stay busy to avoid feeling it', type: 'overfunctioner' },
        { text: 'I go silent and isolate', type: 'silentstriver' },
        { text: 'I internalize it and blame myself', type: 'attachment' },
        { text: 'My body reacts strongly — tight chest, stomach, shaking', type: 'betrayal' },
        { text: 'I smooth things over for others', type: 'boundaries' }
      ]
    },
    {
      id: 'q13',
      question: 'When someone crosses a line with you…',
      answers: [
        { text: 'I take over to prevent it happening again', type: 'overfunctioner' },
        { text: 'I say nothing but feel resentful', type: 'silentstriver' },
        { text: 'I question if I deserved it', type: 'attachment' },
        { text: 'It triggers panic or distrust', type: 'betrayal' },
        { text: 'I minimize it to avoid confrontation', type: 'boundaries' }
      ]
    },
    {
      id: 'q14',
      question: 'Looking back, the emotional climate you grew up in most felt like…',
      answers: [
        { text: 'Being praised for capability over emotions', type: 'overfunctioner' },
        { text: 'Being expected to be the easy child', type: 'silentstriver' },
        { text: 'Feeling unseen or misunderstood', type: 'attachment' },
        { text: 'Feeling destabilized or unsure what to expect', type: 'betrayal' },
        { text: 'Being rewarded for compliance', type: 'boundaries' }
      ]
    },
    {
      id: 'q15',
      question: 'One thing you deeply long for is…',
      answers: [
        { text: "Support you don't have to earn", type: 'overfunctioner' },
        { text: 'Peace without pressure', type: 'silentstriver' },
        { text: 'Secure love and self-trust', type: 'attachment' },
        { text: 'Emotional safety', type: 'betrayal' },
        { text: 'Boundaries that feel aligned', type: 'boundaries' }
      ]
    },
    {
      id: 'q16',
      question: 'Your nervous system feels…',
      answers: [
        { text: 'Always on', type: 'overfunctioner' },
        { text: 'Tired and shut down', type: 'silentstriver' },
        { text: 'Easily activated', type: 'attachment' },
        { text: 'Hypervigilant', type: 'betrayal' },
        { text: 'Drained from people-pleasing', type: 'boundaries' }
      ]
    },
    {
      id: 'q17',
      question: 'When someone needs you urgently, you…',
      answers: [
        { text: 'Move into action before thinking', type: 'overfunctioner' },
        { text: 'Feel pressured but comply silently', type: 'silentstriver' },
        { text: 'Fear disappointing them', type: 'attachment' },
        { text: 'Feel startled or anxious', type: 'betrayal' },
        { text: 'Say yes even when it costs you', type: 'boundaries' }
      ]
    },
    {
      id: 'q18',
      question: 'Your self-talk sounds like…',
      answers: [
        { text: 'I should be able to handle this', type: 'overfunctioner' },
        { text: 'Just push through', type: 'silentstriver' },
        { text: "It's probably my fault", type: 'attachment' },
        { text: "I can't trust anything", type: 'betrayal' },
        { text: "Don't upset anyone", type: 'boundaries' }
      ]
    }
  ];

  const REFINING_QUESTIONS = [
    {
      id: 'q19',
      question: "You're most triggered by…",
      answers: [
        { text: 'Others being unreliable', type: 'overfunctioner' },
        { text: "Expectations you didn't ask for", type: 'silentstriver' },
        { text: 'Pulling away, silence, or conflict', type: 'attachment' },
        { text: 'Emotional abandonment', type: 'betrayal' },
        { text: 'Someone being upset with you', type: 'boundaries' }
      ]
    },
    {
      id: 'q20',
      question: 'What do you rarely allow yourself to do?',
      answers: [
        { text: 'Ask for help', type: 'overfunctioner' },
        { text: 'Be vulnerable', type: 'silentstriver' },
        { text: 'Need others', type: 'attachment' },
        { text: 'Relax your guard', type: 'betrayal' },
        { text: 'Hold a boundary', type: 'boundaries' }
      ]
    },
    {
      id: 'q21',
      question: "You're often caught between…",
      answers: [
        { text: 'Competence and exhaustion', type: 'overfunctioner' },
        { text: 'Strength and invisibility', type: 'silentstriver' },
        { text: 'Independence and longing', type: 'attachment' },
        { text: 'Hope and fear', type: 'betrayal' },
        { text: 'Truth and guilt', type: 'boundaries' }
      ]
    },
    {
      id: 'q22',
      question: 'When someone offers help, you…',
      answers: [
        { text: 'Feel uncomfortable letting go of control', type: 'overfunctioner' },
        { text: "Don't want to impose", type: 'silentstriver' },
        { text: "Worry they'll change their mind", type: 'attachment' },
        { text: 'Scan for hidden motives', type: 'betrayal' },
        { text: 'Feel guilty receiving', type: 'boundaries' }
      ]
    },
    {
      id: 'q23',
      question: 'You often feel…',
      answers: [
        { text: 'Overcommitted', type: 'overfunctioner' },
        { text: 'Emotionally overloaded', type: 'silentstriver' },
        { text: 'Anxious in connection', type: 'attachment' },
        { text: 'Unsteady or mistrustful', type: 'betrayal' },
        { text: "Responsible for everyone's comfort", type: 'boundaries' }
      ]
    },
    {
      id: 'q24',
      question: 'Your emotional pattern is…',
      answers: [
        { text: 'Taking on too much', type: 'overfunctioner' },
        { text: 'Carrying things alone', type: 'silentstriver' },
        { text: 'Feeling insecure or too much', type: 'attachment' },
        { text: 'Feeling unsafe or betrayed', type: 'betrayal' },
        { text: 'Over-accommodating', type: 'boundaries' }
      ]
    },
    {
      id: 'q25',
      question: 'Deep down, you fear…',
      answers: [
        { text: 'Failing those who rely on you', type: 'overfunctioner' },
        { text: 'Not being truly known', type: 'silentstriver' },
        { text: 'Being unloved or left', type: 'attachment' },
        { text: 'Being blindsided again', type: 'betrayal' },
        { text: 'Conflict or rejection', type: 'boundaries' }
      ]
    }
  ];

  // Bridge screens between sections
  const BRIDGE_CORE = {
    id: 'bridge-core',
    isBridge: true,
    section: 'Part Two',
    title: 'The patterns<br><em>underneath</em>',
    body: "Stay with me here. These next questions explore the quiet ways you've been holding everything together."
  };

  const BRIDGE_SOMATIC = {
    id: 'bridge-somatic',
    isBridge: true,
    section: 'Part Three',
    title: 'What your<br><em>body knows</em>',
    body: "Your body has been keeping a record, even when your mind stopped listening. A few questions about what she's been carrying."
  };

  const BRIDGE_REFINING = {
    id: 'bridge-refining',
    isBridge: true,
    section: 'Part Four',
    title: 'The final<br><em>layer</em>',
    body: "Almost there. These last questions help me see the full shape of what you've been navigating."
  };

  // Mid-quiz breath — a quiet pause, not a question
  const BRIDGE_BREATH = {
    id: 'bridge-breath',
    isBridge: true,
    isBreath: true,
    section: "A Quiet Pause",
    title: "You're doing<br><em>the real work</em>",
    body: "Halfway there. There's no rush. Take a breath before you continue, and keep going at your own pace."
  };

  // Full question sequence
  const QUESTION_SEQUENCE = [
    ...SAFETY_QUESTIONS,
    BRIDGE_CORE,
    ...CORE_QUESTIONS,
    BRIDGE_SOMATIC,
    ...SOMATIC_QUESTIONS.slice(0, 2),  // Q12, Q13
    BRIDGE_BREATH,                      // Halfway breath
    ...SOMATIC_QUESTIONS.slice(2),      // Q14–Q18
    BRIDGE_REFINING,
    ...REFINING_QUESTIONS
  ];

  // ============================================================
  // RESULT COPY
  // ============================================================

  const ARCHETYPES = {
    overfunctioner: {
      name: 'The Overfunctioner in Crisis',
      shortName: 'Overfunctioner',
      tag: 'quiz-overfunctioner',
      body: [
        "You have carried the weight of entire rooms, households, relationships, and crises, often without anyone truly recognizing how much effort it takes to hold everything together. You are deeply capable, fiercely responsible, and intuitive about what others need. But the truth is this: you've been functioning at a capacity no single person was ever meant to sustain. Your overfunctioning is not a personal flaw. It is something you learned to do because, at some point in your life, being capable felt like the only safe option.",
        "Somewhere along the way, you internalized the belief that your worth is tied to what you manage, solve, fix, or carry. And while responsibility can be a beautiful strength, it becomes a wound when it's used to protect your deepest fear: that if you slow down, everything will fall apart. Beneath your competence often sits exhaustion, resentment, or loneliness that you rarely admit to anyone, including yourself.",
        "You've been in survival mode for a long time. Constantly scanning for what needs to be done. Stepping into roles you never asked for. Supporting others in ways that have left very little room for you to be held. Your nervous system is over-activated. Your emotional world is under-supported. Your inner voice has been drowned out by the noise of constant doing.",
        "Naming this is your turning point. You're here because something inside you is whispering that it's safe to soften, safe to pause, safe to stop running on fumes. Your Reset Journey begins with unlearning the idea that your value is tied to how much you produce. It begins with you reclaiming space for yourself, gently, imperfectly, and with support when you're ready."
      ]
    },
    silentstriver: {
      name: 'The Silent Striver',
      shortName: 'Silent Striver',
      tag: 'quiz-silent-striver',
      body: [
        "You are the woman who has survived by appearing composed, dependable, accomplished, and strong, even when internally you feel like you're carrying a universe of weight that no one sees. You've learned to swallow your needs, temper your emotions, and present a polished exterior because somewhere along the way, you were taught that being low-maintenance made you lovable, safe, or easier to keep around.",
        "Your exhaustion is a quiet one. A kind that lives in your bones, behind your smile, and in the private moments where you wonder when someone will finally ask how you are doing. It's not that you don't want support. It's that you've been trained to believe you shouldn't need it. You've held everything so close for so long that vulnerability feels foreign, even frightening.",
        "Underneath your stillness sits a tender longing: to be understood without having to explain. To be supported without performing strength. To be allowed to rest without guilt. You are tired, not because you are weak, but because you've lived most of your life inside the tension of appearing fine while carrying the emotional load of three lifetimes.",
        "Your Silent Striver pattern isn't your identity. It's a survival strategy that worked once and is asking to evolve now. You're here because you know something inside you is ready to be witnessed. Healing doesn't begin with big changes. It begins with letting yourself be seen in small, safe ways. You don't have to keep holding everything quietly. You deserve support. You deserve softness. You deserve peace."
      ]
    },
    attachment: {
      name: 'The Attachment-Wounded High Achiever',
      shortName: 'Attachment-Wounded High Achiever',
      tag: 'quiz-attachment-wounded',
      body: [
        "You are deeply intelligent, intuitive, hardworking, and internally driven, but underneath your success and independence lives a younger part of you that learned early on to meet unmet emotional needs through performance, achievement, or self-sufficiency. Your ambition is real. So is the ache beneath it: the fear of being too much, too emotional, too needy, or fundamentally unlovable if your guard slips.",
        "Your drive has protected you. It has kept you moving forward, kept you safe, kept you functioning. But it has also created a pattern where self-worth is tethered to doing instead of being. You may find yourself oscillating between independence and longing, distancing and craving closeness, confidence and sudden spirals of self-doubt. These aren't personal shortcomings. They are echoes of attachment wounds you didn't choose.",
        "You often feel like you're forever managing the gap between who you are and who you believe you should be. The fear of abandonment or rejection, even when subtle, can shape your behaviors, choices, and emotional patterns. And when things go well, the old part of you may still anticipate loss or sabotage the very closeness you long for.",
        "Here is the truth: nothing about you is broken. Your attachment wounds formed in response to what wasn't available, not who you are. And you are not defined by what you learned to do in order to feel safe. You are defined by who you are becoming now. Someone capable of secure connection, grounded confidence, and relational ease. Your Reset begins with tending to the parts of you that had to work so hard to be loved."
      ]
    },
    betrayal: {
      name: 'The Woman in Betrayal Trauma',
      shortName: 'Woman in Betrayal Trauma',
      tag: 'quiz-betrayal-trauma',
      body: [
        "Your system has been shaken in ways that words barely capture. Whether the betrayal was emotional, relational, physical, or the slow erosion of trust over years, your body remembers. The fear, confusion, hypervigilance, anger, grief, and numbness you feel aren't overreactions. They are biological responses to emotional injury.",
        "You've likely found yourself navigating two realities: the part of you that wants to understand what happened, and the part that struggles to believe safety is possible again. This internal split can be exhausting. The mind analyzing every detail while the body remains tense, guarded, and uncertain. Betrayal, in any form, changes the way you relate to yourself, to others, and to the world.",
        "Your experience is not just a relationship issue. It is a whole-body, whole-soul rupture. And you can't logic your way out of it. You can't positive-mindset your way through it. You can't speed up the healing path. What you can do is take one regulated, grounded step at a time as your system relearns safety.",
        "You deserve more than survival. You deserve steadiness, clarity, and spaces where you don't have to question your reality. The fact that you're here, seeking reflection, is a sign of your strength. Your Reset begins with creating emotional safety, rebuilding inner stability, and learning to trust yourself again, gently and without pressure."
      ]
    },
    boundaries: {
      name: 'The Woman Who Finds Boundaries Difficult',
      shortName: 'Boundaries Archetype',
      tag: 'quiz-boundaries',
      body: [
        "You are compassionate, intuitive, and deeply attuned to others, sometimes to the point that you forget to consider yourself. Somewhere in your story, you learned that being agreeable, flexible, or accommodating kept relationships calm and predictable. You learned that your needs could wait, that your discomfort didn't matter as much, or that being easy protected connection.",
        "Because of that, boundaries feel complicated. You often feel guilty, selfish, or afraid of disappointing others when you try to set them. You worry about being misunderstood, rejected, or seen as difficult. So you shrink, soften, or silence yourself to keep the peace, even when it costs you emotionally or physically.",
        "This pattern isn't a flaw. It's a survival instinct. A strategy your younger self created in environments where standing up for yourself didn't feel safe or welcomed. But now, that strategy is becoming too heavy. It's leaving you drained, resentful, or disconnected from your own needs, preferences, and truth.",
        "The good news is that boundaries don't require harshness or conflict. They begin with awareness. Noticing your internal no. Recognizing where you abandon yourself. Learning that your emotional experience matters just as much as anyone else's. Your Reset begins with reclaiming space inside your own life, not through force, but through gentle, steady self-honoring."
      ]
    }
  };

  // ============================================================
  // STATE
  // ============================================================

  const state = {
    currentScreen: 'welcome',
    screenHistory: [],
    firstName: getFirstNameFromURL(),
    answers: {},
    scores: {
      overfunctioner: 0,
      silentstriver: 0,
      attachment: 0,
      betrayal: 0,
      boundaries: 0
    },
    safetyFlag: 0,
    primaryArchetype: null,
    secondaryArchetype: null,
    totalProgressSteps: QUESTION_SEQUENCE.filter(q => !q.isBridge).length // questions only
  };

  // Reads ?name=Jane from the URL. Systeme.io can pass the contact's
  // first name as a URL parameter on the redirect from the opt-in
  // page into this quiz page. Falls back to empty string ('Friend'
  // is used at render time) if not present or not configured yet.
  function getFirstNameFromURL() {
    try {
      const params = new URLSearchParams(window.location.search);
      const raw = params.get('name') || params.get('first_name') || '';
      return raw.trim().slice(0, 40);
    } catch (e) {
      return '';
    }
  }

  // ============================================================
  // ELEMENTS
  // ============================================================

  const app = document.getElementById('app');
  const ctaBtn = document.getElementById('ctaBtn');
  const ctaWrap = document.getElementById('ctaWrap');
  const backBtn = document.getElementById('backBtn');
  const progressFill = document.getElementById('progressFill');
  const progressLabel = document.getElementById('progressLabel');
  const questionContainer = document.getElementById('question-container');
  const scrollCue = document.getElementById('scrollCue');

  // ============================================================
  // BUILD QUESTION SCREENS
  // ============================================================

  function buildQuestionScreens() {
    QUESTION_SEQUENCE.forEach(item => {
      const section = document.createElement('section');
      section.className = 'screen';
      section.id = `screen-${item.id}`;

      if (item.isBridge) {
        section.dataset.screen = 'bridge';
        section.innerHTML = `
          <div class="bridge">
            <div class="bridge-section">${item.section}</div>
            <h2>${item.title}</h2>
            <div class="gold-rule"></div>
            <p class="bridge-body">${item.body}</p>
          </div>
        `;
      } else {
        section.dataset.screen = 'question';
        section.dataset.questionId = item.id;
        const helperHtml = item.helper ? `<p class="question-helper">${item.helper}</p>` : '';
        const sectionHtml = item.section ? `<div class="question-eyebrow">${item.section}</div>` : '';
        section.innerHTML = `
          <div class="question-wrap question">
            ${sectionHtml}
            <h2>${item.question}</h2>
            ${helperHtml}
            <div class="answers">
              ${item.answers.map((a, i) => `
                <button class="answer" data-index="${i}">
                  <span class="answer-text">${a.text}</span>
                  <div class="answer-check">
                    <svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg>
                  </div>
                </button>
              `).join('')}
            </div>
          </div>
        `;
      }

      questionContainer.appendChild(section);

      // Wire up answer buttons
      if (!item.isBridge) {
        const answers = section.querySelectorAll('.answer');
        answers.forEach(btn => {
          btn.addEventListener('click', () => {
            answers.forEach(a => a.classList.remove('selected'));
            btn.classList.add('selected');
            const idx = parseInt(btn.dataset.index);
            state.answers[item.id] = { questionId: item.id, answerIndex: idx, answer: item.answers[idx] };
            ctaBtn.disabled = false;
          });
        });
      }
    });
  }

  // ============================================================
  // NAVIGATION
  // ============================================================

  function showScreen(screenId, pushHistory = true) {
    const currentActive = document.querySelector('.screen.active');
    const nextScreen = document.getElementById(`screen-${screenId}`);

    if (!nextScreen) {
      console.error(`Screen not found: screen-${screenId}`);
      return;
    }

    if (pushHistory && state.currentScreen) {
      state.screenHistory.push(state.currentScreen);
    }

    if (currentActive) currentActive.classList.remove('active');
    nextScreen.classList.add('active');
    state.currentScreen = screenId;

    // Scroll to top
    window.scrollTo({ top: 0, behavior: 'instant' });

    // Update UI based on screen type
    updateUIForScreen(nextScreen);

    // Check scroll cue after screen renders
    setTimeout(checkScrollCue, 100);
  }

  function updateUIForScreen(screen) {
    const type = screen.dataset.screen;

    // Back button visibility
    if (state.screenHistory.length > 0 && type !== 'result' && type !== 'paused' && type !== 'safety') {
      backBtn.classList.add('visible');
    } else {
      backBtn.classList.remove('visible');
    }

    // CTA visibility and state
    if (type === 'result' || type === 'paused' || type === 'safety') {
      ctaWrap.style.display = 'none';
    } else {
      ctaWrap.style.display = 'block';
    }

    // CTA label and enabled state
    if (type === 'welcome') {
      ctaBtn.textContent = 'Begin';
      ctaBtn.disabled = false;
      progressFill.style.width = '0%';
      progressLabel.classList.remove('visible');
    } else if (type === 'bridge') {
      ctaBtn.textContent = 'Continue';
      ctaBtn.disabled = false;
      const questionId = screen.id.replace('screen-', '');
      const item = QUESTION_SEQUENCE.find(q => q.id === questionId);
      if (item) progressLabel.textContent = item.section;
      progressLabel.classList.add('visible');
    } else if (type === 'question') {
      ctaBtn.textContent = 'Continue';
      const qId = screen.dataset.questionId;
      ctaBtn.disabled = !state.answers[qId];
      // Section label
      const questionIndex = QUESTION_SEQUENCE.findIndex(q => q.id === qId);
      let sectionLabel = 'Reflection';
      if (questionIndex < 4) sectionLabel = 'Safety Check';
      else if (questionIndex < 12) sectionLabel = 'Patterns';
      else if (questionIndex < 20) sectionLabel = 'The Body';
      else sectionLabel = 'Your Archetype';
      progressLabel.textContent = sectionLabel;
      progressLabel.classList.add('visible');
    }

    // Progress bar
    updateProgress();
  }

  function checkScrollCue() {
    const activeScreen = document.querySelector('.screen.active');
    if (!activeScreen) {
      scrollCue.classList.remove('visible');
      return;
    }

    const type = activeScreen.dataset.screen;
    // Only show on question screens (where answers can extend below fold)
    if (type !== 'question' && type !== 'safety') {
      scrollCue.classList.remove('visible');
      return;
    }

    // Check if content extends below viewport
    const docHeight = document.documentElement.scrollHeight;
    const viewHeight = window.innerHeight;
    const scrollY = window.scrollY;
    const hasMore = (docHeight - viewHeight - scrollY) > 40;

    if (hasMore) {
      scrollCue.classList.add('visible');
    } else {
      scrollCue.classList.remove('visible');
    }
  }

  function updateProgress() {
    const type = document.querySelector('.screen.active')?.dataset.screen;
    if (!type || type === 'welcome') {
      progressFill.style.width = '0%';
      return;
    }

    let step = 0;
    if (type === 'question') {
      const qId = document.querySelector('.screen.active').dataset.questionId;
      const questionsBefore = QUESTION_SEQUENCE.filter(q => !q.isBridge);
      const idx = questionsBefore.findIndex(q => q.id === qId);
      step = 1 + idx;
    } else if (type === 'bridge') {
      const bridgeId = document.querySelector('.screen.active').id.replace('screen-', '');
      if (bridgeId === 'bridge-safety' || bridgeId === 'screen-bridge-safety') step = 0.5;
      else if (bridgeId === 'bridge-core') step = 4.5;
      else if (bridgeId === 'bridge-somatic') step = 11.5;
      else if (bridgeId === 'bridge-refining') step = 18.5;
    }

    const pct = Math.min((step / state.totalProgressSteps) * 100, 100);
    progressFill.style.width = `${pct}%`;
  }

  function goBack() {
    if (state.screenHistory.length === 0) return;
    const prev = state.screenHistory.pop();
    showScreen(prev, false);
  }

  // ============================================================
  // FLOW LOGIC
  // ============================================================

  function getNextScreen(current) {
    if (current === 'welcome') return 'bridge-safety';
    if (current === 'bridge-safety') return QUESTION_SEQUENCE[0].id;

    // Find next in sequence
    const idx = QUESTION_SEQUENCE.findIndex(q => q.id === current);
    if (idx >= 0 && idx < QUESTION_SEQUENCE.length - 1) {
      return QUESTION_SEQUENCE[idx + 1].id;
    }

    // After last question, calculateResults()/handleCTA() routes
    // directly to 'result' or 'safety-pause' (see handleCTA below).
    return null;
  }

  function handleCTA() {
    const current = state.currentScreen;

    if (current === 'welcome') {
      showScreen('bridge-safety');
      return;
    }

    // Question or bridge
    const next = getNextScreen(current);

    // If we just finished the last question, calculate results first
    if (current === QUESTION_SEQUENCE[QUESTION_SEQUENCE.length - 1].id) {
      calculateResults();
      // Check safety flag
      if (state.safetyFlag >= 2) {
        showScreen('safety-pause');
        return;
      }
      renderResult();
      showScreen('result');
      return;
    }

    if (next) showScreen(next);
  }

  // ============================================================
  // SCORING
  // ============================================================

  function calculateResults() {
    // Reset
    state.scores = { overfunctioner: 0, silentstriver: 0, attachment: 0, betrayal: 0, boundaries: 0 };
    state.safetyFlag = 0;

    Object.values(state.answers).forEach(entry => {
      const a = entry.answer;
      if (a.safety !== undefined) state.safetyFlag += a.safety;
      if (a.type) state.scores[a.type]++;
    });

    // Determine primary and secondary
    const sorted = Object.entries(state.scores).sort((a, b) => b[1] - a[1]);
    state.primaryArchetype = sorted[0][0];
    const primaryScore = sorted[0][1];
    const secondaryScore = sorted[1][1];
    state.secondaryArchetype = (primaryScore - secondaryScore) <= 2 ? sorted[1][0] : null;
  }

  // ============================================================
  // RESULT RENDERING
  // ============================================================

  function renderResult() {
    const primary = ARCHETYPES[state.primaryArchetype];
    const secondary = state.secondaryArchetype ? ARCHETYPES[state.secondaryArchetype] : null;
    const name = state.firstName ? state.firstName : 'Friend';

    const secondaryHtml = secondary
      ? `<div class="result-secondary">with a secondary thread of <span>${secondary.shortName}</span></div>`
      : '';

    const content = `
      <div class="result-eyebrow">Your Archetype</div>
      <div class="result-name">${name},</div>
      <h1 class="result-archetype">${primary.name}</h1>
      ${secondaryHtml}
      <div class="gold-rule"></div>
      <div class="result-body">
        ${primary.body.map(p => `<p>${p}</p>`).join('')}
      </div>

      <div class="result-next">
        <div class="result-next-label">Your Next Step</div>
        <h3>Get your personalized next steps.</h3>
        <p>
          A short note built specifically for what you just read is on its way, with one quiet first step forward.
        </p>
        <a href="https://www.midliferesetstudio.com/quiz-tag/${primary.tag}?archetype=${primary.tag}" class="result-cta" id="archetypeTagLink" target="_blank" rel="noopener">Send me tips for this archetype</a>
      </div>

      <div class="result-signoff">
        <div class="logo-badge small">
          <img src="data:image/png;base64,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tzlr3Atdlp5cvAzw5WTZuOURf0nJJOOfkML+LsyIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiD/9k=" alt="Midlife Reset Studio">
        </div>
        <div class="result-signoff-text">You are not behind. You are here.</div>
        <div class="result-signoff-studio">The Midlife Reset Studio</div>
      </div>
    `;

    document.getElementById('resultContent').innerHTML = content;
  }


  // ============================================================
  // EVENT LISTENERS
  // ============================================================

  ctaBtn.addEventListener('click', handleCTA);
  backBtn.addEventListener('click', goBack);

  // Safety pause screen buttons
  document.getElementById('safety-continue').addEventListener('click', () => {
    renderResult();
    showScreen('result');
  });

  document.getElementById('safety-pause-btn').addEventListener('click', () => {
    showScreen('paused');
  });

  // Scroll cue listeners
  window.addEventListener('scroll', checkScrollCue, { passive: true });
  window.addEventListener('resize', checkScrollCue);

  // ============================================================
  // INITIALIZE
  // ============================================================

  buildQuestionScreens();
  updateUIForScreen(document.getElementById('screen-welcome'));

</script>

</body>
</html>

# midlife-reset-archetype-quiz
