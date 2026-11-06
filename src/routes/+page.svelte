<svelte:head>
  <title>Bound in Truth 💙</title>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      min-height: 100vh;
      background: linear-gradient(135deg, #eff6ff 0%, #dbeafe 35%, #93c5fd 70%, #3b82f6 100%);
      font-family: 'Segoe UI', Georgia, serif;
      color: #1e3a8a;
      overflow-x: hidden;
    }

    .page {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 2.5rem 2rem;
      max-width: 950px;
      margin: 0 auto;
      position: relative;
    }

    /* Floating particles */
    .particle {
      position: absolute;
      border-radius: 50%;
      background: rgba(255,255,255,0.6);
      pointer-events: none;
      animation: floatParticle 12s ease-in-out infinite;
    }

    @keyframes floatParticle {
      0% { transform: translateY(0) translateX(0) scale(1); opacity: 0.6; }
      25% { transform: translateY(-40px) translateX(20px) scale(1.1); opacity: 0.8; }
      50% { transform: translateY(-20px) translateX(-15px) scale(0.9); opacity: 0.5; }
      75% { transform: translateY(-50px) translateX(10px) scale(1.05); opacity: 0.7; }
      100% { transform: translateY(0) translateX(0) scale(1); opacity: 0.6; }
    }

    /* Heading dramatic reveal */
    .heading {
      text-align: center;
      margin-bottom: 2.5rem;
      position: relative;
    }

    h1 {
      font-size: 2.4rem;
      letter-spacing: 2px;
      text-transform: uppercase;
      opacity: 0;
      transform: translateY(30px) scale(0.9);
      animation: grandReveal 1.5s ease-out forwards;
      text-shadow: 0 4px 20px rgba(30, 64, 175, 0.15);
    }

    .subtitle {
      font-size: 1.15rem;
      color: #1e40af;
      font-style: italic;
      margin-top: 0.8rem;
      opacity: 0;
      letter-spacing: 1px;
      animation: fadeGlow 1.5s ease-out 0.4s forwards;
    }

    @keyframes grandReveal {
      0% { opacity: 0; transform: translateY(40px) scale(0.8); letter-spacing: 8px; }
      100% { opacity: 1; transform: translateY(0) scale(1); letter-spacing: 2px; }
    }

    @keyframes fadeGlow {
      to { opacity: 1; }
    }

    /* Photos dramatic styling */
    .photos-row {
      display: flex;
      gap: 3rem;
      justify-content: center;
      width: 100%;
      margin-bottom: 3rem;
      flex-wrap: wrap;
    }

    .photo-wrap {
      flex: 1;
      min-width: 300px;
      max-width: 380px;
      position: relative;
      opacity: 0;
      transform: translateY(50px) rotate(-3deg);
      animation: photoSweepIn 1.2s cubic-bezier(0.17, 0.67, 0.23, 0.99) forwards;
    }

    .photo-wrap:nth-child(2) {
      transform: translateY(50px) rotate(3deg);
      animation-delay: 0.3s;
    }

    @keyframes photoSweepIn {
      to {
        opacity: 1;
        transform: translateY(0) rotate(0deg);
      }
    }

    .photo-frame {
      width: 100%;
      aspect-ratio: 4/5;
      border-radius: 24px;
      overflow: hidden;
      border: 7px solid white;
      box-shadow: 
        0 15px 40px rgba(30, 64, 175, 0.2),
        inset 0 0 0 2px rgba(220, 38, 38, 0.12);
      transition: all 0.5s cubic-bezier(0.17, 0.67, 0.23, 0.99);
      position: relative;
    }

    /* Red accent border pulse */
    .photo-frame::before {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: 18px;
      border: 2px solid transparent;
      animation: redPulse 3s ease-in-out infinite;
    }

    @keyframes redPulse {
      0%, 100% { border-color: rgba(220, 38, 38, 0.1); }
      50% { border-color: rgba(220, 38, 38, 0.3); }
    }

    .photo-frame:hover {
      transform: translateY(-12px) scale(1.03);
      box-shadow: 
        0 25px 60px rgba(30, 64, 175, 0.3),
        inset 0 0 0 2px rgba(220, 38, 38, 0.2);
    }

    .photo-frame img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 6s ease;
    }

    .photo-frame:hover img {
      transform: scale(1.08);
    }

    /* Central divider */
    .divider {
      display: flex;
      align-items: center;
      gap: 1rem;
      margin: 0.5rem 0 2.5rem;
      opacity: 0;
      animation: fadeIn 1s ease-out 0.8s forwards;
    }

    .divider-line {
      height: 2px;
      flex: 1;
      max-width: 100px;
      background: linear-gradient(90deg, transparent, #3b82f6, transparent);
    }

    .heart-icon {
      font-size: 2.2rem;
      color: #dc2626;
      animation: heartBeat 2s ease-in-out infinite;
      filter: drop-shadow(0 0 8px rgba(220, 38, 38, 0.3));
    }

    @keyframes heartBeat {
      0%, 100% { transform: scale(1); }
      15% { transform: scale(1.25); }
      30% { transform: scale(1); }
      45% { transform: scale(1.2); }
      60% { transform: scale(1); }
    }

    /* Quote dramatic styling */
    .quote-wrapper {
      max-width: 750px;
      width: 100%;
      opacity: 0;
      transform: translateY(30px);
      animation: quoteRise 1.5s ease-out 1.1s forwards;
    }

    .quote-card {
      background: rgba(255, 255, 255, 0.92);
      border-radius: 24px;
      padding: 2.5rem;
      box-shadow: 
        0 10px 40px rgba(59, 130, 246, 0.15),
        0 0 0 1px rgba(255, 255, 255, 0.8) inset;
      position: relative;
      overflow: hidden;
    }

    /* Corner red accents — exactly 1% usage */
    .quote-card::before,
    .quote-card::after {
      content: '';
      position: absolute;
      width: 40px;
      height: 40px;
      border-color: rgba(220, 38, 38, 0.35);
      border-style: solid;
      opacity: 0;
      animation: cornerPop 1.2s ease-out 1.5s forwards;
    }

    .quote-card::before {
      top: 1.5rem;
      left: 1.5rem;
      border-width: 3px 0 0 3px;
    }

    .quote-card::after {
      bottom: 1.5rem;
      right: 1.5rem;
      border-width: 0 3px 3px 0;
      animation-delay: 1.7s;
    }

    @keyframes cornerPop {
      to { opacity: 1; }
    }

    .quote-mark {
      font-size: 4rem;
      line-height: 1;
      color: rgba(59, 130, 246, 0.2);
      font-family: Georgia, serif;
      position: absolute;
      top: 0.5rem;
      left: 1.5rem;
      pointer-events: none;
    }

    .quote-text {
      font-size: 1.35rem;
      line-height: 2;
      color: #1e293b;
      font-style: italic;
      text-align: center;
      position: relative;
      z-index: 1;
    }

    .quote-text p {
      margin-bottom: 1.8rem;
      opacity: 0;
      transform: translateY(15px);
      animation: lineFade 1s ease-out forwards;
    }

    .quote-text p:nth-child(1) { animation-delay: 1.4s; }
    .quote-text p:nth-child(2) { animation-delay: 1.7s; }
    .quote-text p:nth-child(3) { animation-delay: 2.0s; }

    @keyframes lineFade {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .author-line {
      text-align: center;
      margin-top: 2rem;
      font-size: 1.1rem;
      color: #1e40af;
      font-weight: 600;
      letter-spacing: 2px;
      opacity: 0;
      animation: fadeIn 1s ease-out 2.3s forwards;
    }

    @keyframes quoteRise {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes fadeIn {
      to { opacity: 1; }
    }

    /* Shimmer effect */
    .shimmer {
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
      animation: shimmerSweep 4s ease-in-out infinite;
      animation-delay: 2s;
      pointer-events: none;
    }

    @keyframes shimmerSweep {
      0% { left: -100%; }
      50% { left: 100%; }
      100% { left: 100%; }
    }

    @media (max-width: 640px) {
      h1 { font-size: 1.8rem; letter-spacing: 1px; }
      .quote-text { font-size: 1.1rem; }
      .page { padding: 2rem 1.25rem; }
      .photos-row { gap: 2rem; }
      .quote-card { padding: 2rem 1.5rem; }
    }
  </style>
</svelte:head>

<div class="page">
  <!-- Floating background particles -->
  {#each particles as p}
    <div
      class="particle"
      style="
        left: {p.x}%;
        top: {p.y}%;
        width: {p.size}px;
        height: {p.size}px;
        animation-delay: {p.delay}s;
        animation-duration: {p.dur}s;
      "
    ></div>
  {/each}

  <div class="heading">
    <h1>When Two Souls Find Their Way 💙</h1>
    <p class="subtitle">Silence speaks louder than words when the foundation is true</p>
  </div>

  <div class="photos-row">
    <div class="photo-wrap">
      <div class="photo-frame">
        <!-- Uses your file exactly as named in your repo -->
        <img src="/WhatsApp Image 2026-11-06 at 19.00.58 (2).jpeg" alt="First" loading="lazy" />
      </div>
    </div>

    <div class="photo-wrap">
      <div class="photo-frame">
        <!-- Uses your file exactly as named in your repo -->
        <img src="/WhatsApp Image 2026-11-06 at 19.00.59.jpeg" alt="Second" loading="lazy" />
      </div>
    </div>
  </div>

  <div class="divider">
    <span class="divider-line"></span>
    <span class="heart-icon">♥</span>
    <span class="divider-line"></span>
  </div>

  <div class="quote-wrapper">
    <div class="quote-card">
      <div class="shimmer"></div>
      <span class="quote-mark">"</span>
      <div class="quote-text">
        <p>You caught me off guard with a simple greeting — and one quiet moment unfolded into another, until I find myself thinking of you in every breath I take.</p>
        <p>When a foundation is built with nothing but truth — no masks, no pretense, no shadows — something rare and magnificent takes root. It is a wonder how effortlessly our spirits align, how naturally the connection flows, as if we were always meant to find one another.</p>
        <p>What began as a whisper has grown into something unshakable — a bond that does not need to shout to be heard, for it is written in the language of the heart, and that never fades.</p>
      </div>
      <p class="author-line">— Anonymous</p>
    </div>
  </div>
</div>

<script>
  import { onMount } from 'svelte';

  let particles = [];

  function createParticle() {
    return {
      x: Math.random() * 100,
      y: Math.random() * 100,
      size: 4 + Math.random() * 8,
      delay: Math.random() * 8,
      dur: 8 + Math.random() * 6
    };
  }

  onMount(() => {
    particles = Array.from({ length: 25 }, createParticle);
  });
</script>
