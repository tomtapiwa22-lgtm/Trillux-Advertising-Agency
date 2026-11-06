<svelte:head>
  <title>Friendship Hearts 💛🤍💙</title>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      min-height: 100vh;
      background:
        radial-gradient(circle at 10% 10%, rgba(255,255,255,0.8) 0%, transparent 50%),
        radial-gradient(circle at 90% 18%, rgba(255,255,255,0.6) 0%, transparent 45%),
        linear-gradient(135deg, #fffaf0 0%, #fff3cd 35%, #ffe066 70%, #ffcc00 100%);
      font-family: 'Segoe UI', Georgia, serif;
      color: #6b4226;
      overflow-x: hidden;
    }

    .page {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 2.5rem 2rem;
      max-width: 1000px;
      margin: 0 auto;
      position: relative;
    }

    .hearts-bg {
      position: absolute;
      inset: 0;
      overflow: hidden;
      pointer-events: none;
    }

    .heart {
      position: absolute;
      color: rgba(255, 100, 150, 0.35);
      font-size: 1.6rem;
      animation: floatHeart 8s ease-in-out infinite;
    }

    .heart:nth-child(odd) {
      color: rgba(255, 180, 80, 0.35);
    }

    .heart:nth-child(3n) {
      color: rgba(255, 100, 100, 0.35);
    }

    @keyframes floatHeart {
      0% { transform: translateY(0) translateX(0) rotate(0deg); opacity: 0.4; }
      25% { transform: translateY(-50px) translateX(25px) rotate(10deg); opacity: 0.8; }
      50% { transform: translateY(-30px) translateX(-20px) rotate(-8deg); opacity: 0.5; }
      75% { transform: translateY(-60px) translateX(15px) rotate(5deg); opacity: 0.7; }
      100% { transform: translateY(0) translateX(0) rotate(0deg); opacity: 0.4; }
    }

    .heading {
      text-align: center;
      margin-bottom: 2.5rem;
      z-index: 1;
    }

    h1 {
      font-size: 2.4rem;
      letter-spacing: 2px;
      text-transform: uppercase;
      opacity: 0;
      transform: translateY(30px) scale(0.9);
      animation: grandReveal 1.5s ease-out forwards;
      text-shadow: 0 4px 20px rgba(107, 66, 38, 0.15);
    }

    .subtitle {
      font-size: 1.15rem;
      color: #a67c52;
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

    .main-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 2.5rem;
      width: 100%;
      margin-bottom: 2.5rem;
      align-items: stretch;
      z-index: 1;
    }

    .photo-card {
      position: relative;
      background: rgba(255,255,255,0.95);
      border-radius: 26px;
      padding: 1.2rem;
      box-shadow:
        0 10px 30px rgba(107, 66, 38, 0.12),
        inset 0 0 0 1px rgba(255, 255, 255, 0.8);
      opacity: 0;
      transform: translateY(50px) scale(0.95);
      animation: cardSweepIn 1.2s cubic-bezier(0.17, 0.67, 0.23, 0.99) forwards;
      overflow: hidden;
    }

    .photo-card:nth-child(2) {
      animation-delay: 0.3s;
    }

    @keyframes cardSweepIn {
      to {
        opacity: 1;
        transform: translateY(0) scale(1);
      }
    }

    .photo-frame {
      width: 100%;
      aspect-ratio: 4/5;
      border-radius: 20px;
      overflow: hidden;
      position: relative;
    }

    .photo-frame img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 6s ease;
    }

    .photo-card:hover .photo-frame img {
      transform: scale(1.08);
    }

    .card-heart {
      position: absolute;
      top: 0.6rem;
      right: 0.8rem;
      font-size: 1.4rem;
      color: #ff4d6d;
      animation: heartBeat 2s ease-in-out infinite;
      filter: drop-shadow(0 0 6px rgba(255, 77, 109, 0.4));
    }

    .photo-label {
      margin-top: 1rem;
      text-align: center;
      font-size: 1rem;
      font-weight: 600;
      color: #6b4226;
      letter-spacing: 1px;
    }

    .circle-hearts-section {
      width: 100%;
      max-width: 750px;
      margin: 2rem 0 2.5rem;
      position: relative;
      z-index: 1;
    }

    .circle-hearts-title {
      text-align: center;
      font-size: 1.2rem;
      color: #a67c52;
      margin-bottom: 1.5rem;
      font-weight: 600;
      letter-spacing: 1px;
      text-transform: uppercase;
    }

    .circle-hearts-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1.2rem;
    }

    .heart-pic {
      position: relative;
      width: 90px;
      height: 90px;
      opacity: 0;
      transform: translateY(30px) scale(0.8);
      animation: popHeartPic 0.8s ease-out forwards;
    }

    .heart-pic:nth-child(1) { animation-delay: 0.6s; }
    .heart-pic:nth-child(2) { animation-delay: 0.75s; }
    .heart-pic:nth-child(3) { animation-delay: 0.9s; }
    .heart-pic:nth-child(4) { animation-delay: 1.05s; }
    .heart-pic:nth-child(5) { animation-delay: 1.2s; }
    .heart-pic:nth-child(6) { animation-delay: 1.35s; }

    @keyframes popHeartPic {
      to {
        opacity: 1;
        transform: translateY(0) scale(1);
      }
    }

    .heart-pic img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      clip-path: path('M50% 15% C65% 0%, 90% 0%, 90% 25% C90% 50%, 50% 85%, 50% 85% C50% 85%, 10% 50%, 10% 25% C10% 0%, 35% 0%, 50% 15% Z');
      border: 3px solid #fff;
      box-shadow: 0 4px 15px rgba(107, 66, 38, 0.15);
    }

    .divider {
      display: flex;
      align-items: center;
      gap: 1rem;
      margin: 0.5rem 0 2.5rem;
      opacity: 0;
      animation: fadeIn 1s ease-out 0.8s forwards;
      z-index: 1;
    }

    .divider-line {
      height: 2px;
      flex: 1;
      max-width: 100px;
      background: linear-gradient(90deg, transparent, #ff4d6d, transparent);
    }

    .divider-heart {
      font-size: 2.2rem;
      color: #ff4d6d;
      animation: heartBeat 2s ease-in-out infinite;
      filter: drop-shadow(0 0 8px rgba(255, 77, 109, 0.35));
    }

    @keyframes heartBeat {
      0%,100% { transform: scale(1); }
      15% { transform: scale(1.25); }
      30% { transform: scale(1); }
      45% { transform: scale(1.2); }
      60% { transform: scale(1); }
    }

    @keyframes fadeIn {
      to { opacity: 1; }
    }

    .quote-wrapper {
      max-width: 750px;
      width: 100%;
      opacity: 0;
      transform: translateY(30px);
      animation: quoteRise 1.5s ease-out 1.1s forwards;
      z-index: 1;
    }

    .quote-card {
      background: rgba(255,255,255,0.96);
      border-radius: 24px;
      padding: 2.5rem;
      box-shadow:
        0 10px 40px rgba(107, 66, 38, 0.12),
        inset 0 0 0 1px rgba(255, 255, 255, 0.8);
      position: relative;
      overflow: hidden;
    }

    .quote-card::before,
    .quote-card::after {
      content: '';
      position: absolute;
      width: 40px;
      height: 40px;
      border-color: rgba(255, 77, 109, 0.35);
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
      color: rgba(255, 77, 109, 0.15);
      font-family: Georgia, serif;
      position: absolute;
      top: 0.5rem;
      left: 1.5rem;
      pointer-events: none;
    }

    .quote-text {
      font-size: 1.35rem;
      line-height: 2;
      color: #6b4226;
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
      color: #a67c52;
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

    .shimmer {
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(
        90deg,
        transparent,
        rgba(255, 255, 255, 0.4),
        transparent
      );
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
      h1 {
        font-size: 1.8rem;
        letter-spacing: 1px;
      }

      .quote-text {
        font-size: 1.1rem;
      }

      .page {
        padding: 2rem 1.25rem;
      }

      .main-grid {
        gap: 2rem;
      }

      .quote-card {
        padding: 2rem 1.5rem;
      }

      .heart-pic {
        width: 70px;
        height: 70px;
      }
    }
  </style>
</svelte:head>

<div class="page">
  <div class="hearts-bg">
    {#each hearts as h}
      <span
        class="heart"
        style="
          left: {h.x}%;
          top: {h.y}%;
          font-size: {h.size}rem;
          animation-delay: {h.delay}s;
          animation-duration: {h.dur}s;
        "
        >♥</span
      >
    {/each}
  </div>

  <div class="heading">
    <h1>Friendship Hearts 💛🤍💙</h1>
    <p class="subtitle">True friendship is the heart that stays with you through every season</p>
  </div>

  <div class="main-grid">
    <div class="photo-card">
      <div class="photo-frame">
        <img src="/WhatsApp Image 2026-11-06 at 19.00.58 (2).jpeg" alt="Friend 1" loading="lazy" />
      </div>
      <span class="card-heart">♥</span>
      <p class="photo-label">Friend One</p>
    </div>

    <div class="photo-card">
      <div class="photo-frame">
        <img src="/WhatsApp Image 2026-11-06 at 19.00.59.jpeg" alt="Friend 2" loading="lazy" />
      </div>
      <span class="card-heart">♥</span>
      <p class="photo-label">Friend Two</p>
    </div>
  </div>

  <div class="circle-hearts-section">
    <p class="circle-hearts-title">Our Friendship in Little Hearts</p>
    <div class="circle-hearts-grid">
      <div class="heart-pic"><img src="/WhatsApp Image 2026-11-06 at 19.00.58 (2).jpeg" alt="Memory 1" /></div>
      <div class="heart-pic"><img src="/WhatsApp Image 2026-11-06 at 19.00.59.jpeg" alt="Memory 2" /></div>
      <div class="heart-pic"><img src="/WhatsApp Image 2026-11-06 at 19.00.58 (2).jpeg" alt="Memory 3" /></div>
      <div class="heart-pic"><img src="/WhatsApp Image 2026-11-06 at 19.00.59.jpeg" alt="Memory 4" /></div>
      <div class="heart-pic"><img src="/WhatsApp Image 2026-11-06 at 19.00.58 (2).jpeg" alt="Memory 5" /></div>
      <div class="heart-pic"><img src="/WhatsApp Image 2026-11-06 at 19.00.59.jpeg" alt="Memory 6" /></div>
    </div>
  </div>

  <div class="divider">
    <span class="divider-line"></span>
    <span class="divider-heart">♥</span>
    <span class="divider-line"></span>
  </div>

  <div class="quote-wrapper">
    <div class="quote-card">
      <div class="shimmer"></div>
      <span class="quote-mark">"</span>
      <div class="quote-text">
        <p>Friendship begins with a simple hello, but it grows into something that feels like home — a heart that understands yours even when words are few.</p>
        <p>True friends don't need to be together every day. What matters is that when life changes, when days get heavy, and when joy comes around, you still know someone is there, cheering you on from their heart.</p>
        <p>Every laugh shared, every quiet moment, and every little memory becomes a small heart circling around your story — reminding you that some bonds are not just made, but felt forever.</p>
      </div>
      <p class="author-line">— Friendship Tribute</p>
    </div>
  </div>
</div>

<script>
  import { onMount } from 'svelte';

  let hearts = [];

  function createHeart() {
    return {
      x: Math.random() * 100,
      y: Math.random() * 100,
      size: 1 + Math.random() * 1.5,
      delay: Math.random() * 8,
      dur: 6 + Math.random() * 6
    };
  }

  onMount(() => {
    hearts = Array.from({ length: 35 }, createHeart);
  });
</script>
