<svelte:head>
  <title>Grown Together — A Friendship Blossomed 🌿✨</title>
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
      background: linear-gradient(135deg, #f0fdf4 0%, #dcfce7 35%, #bbf7d0 70%, #86efac 100%);
      font-family: 'Segoe UI', Garamond, Georgia, serif;
      overflow-x: hidden;
      color: #14532d;
    }

    .container {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      padding: 3rem 1.5rem 4rem;
      position: relative;
    }

    /* 🌳 Giant Animated Plant — Centerpiece */
    .plant-wrapper {
      position: relative;
      margin-bottom: 3rem;
      margin-top: 1rem;
    }

    .plant {
      position: relative;
      width: 220px;
      height: 320px;
      opacity: 0;
      transform: translateY(40px) scale(0.8);
      animation: plantGrow 2.5s ease-out forwards;
    }

    @keyframes plantGrow {
      0% {
        opacity: 0;
        transform: translateY(40px) scale(0.7);
      }
      60% {
        transform: translateY(-5px) scale(1.05);
      }
      100% {
        opacity: 1;
        transform: translateY(0) scale(1);
      }
    }

    .stem {
      position: absolute;
      bottom: 0;
      left: 50%;
      width: 14px;
      height: 180px;
      margin-left: -7px;
      background: linear-gradient(to right, #166534, #22c55e, #166534);
      border-radius: 7px;
      transform-origin: bottom center;
      animation: stemRise 2s ease-out forwards;
    }

    @keyframes stemRise {
      from { transform: scaleY(0); }
      to { transform: scaleY(1); }
    }

    .leaf {
      position: absolute;
      width: 90px;
      height: 50px;
      background: linear-gradient(135deg, #22c55e, #16a34a, #15803d);
      border-radius: 0 100% 0 100%;
      transform-origin: bottom left;
      opacity: 0;
      box-shadow: 0 4px 12px rgba(22,163,74,0.2);
    }

    .leaf:nth-child(2) {
      transform: scaleX(-1);
      right: 0;
      border-radius: 0 100% 100% 0;
      transform-origin: bottom right;
    }

    .leaf-1 { bottom: 40px; left: -60px; animation: leafUnfurl 1.5s ease-out 0.5s forwards; transform: rotate(-20deg); }
    .leaf-2 { bottom: 40px; right: -60px; animation: leafUnfurl 1.5s ease-out 0.6s forwards; transform: rotate(20deg) scaleX(-1); }
    .leaf-3 { bottom: 90px; left: -50px; animation: leafUnfurl 1.5s ease-out 0.8s forwards; transform: rotate(-35deg); }
    .leaf-4 { bottom: 90px; right: -50px; animation: leafUnfurl 1.5s ease-out 0.9s forwards; transform: rotate(35deg) scaleX(-1); }
    .leaf-5 { bottom: 140px; left: -35px; animation: leafUnfurl 1.5s ease-out 1.1s forwards; transform: rotate(-15deg); }
    .leaf-6 { bottom: 140px; right: -35px; animation: leafUnfurl 1.5s ease-out 1.2s forwards; transform: rotate(15deg) scaleX(-1); }

    @keyframes leafUnfurl {
      0% { transform: rotate(0deg) scale(0.3); opacity: 0; }
      100% { opacity: 1; }
    }

    .flower-bloom {
      position: absolute;
      top: 0;
      left: 50%;
      margin-left: -45px;
      width: 90px;
      height: 90px;
      opacity: 0;
      transform: scale(0.2);
      animation: bloomOpen 2s ease-out 1.5s forwards;
    }

    .petal {
      position: absolute;
      width: 36px;
      height: 54px;
      background: linear-gradient(to top, #fef08a, #fef9c3, #fffbeb);
      border-radius: 50%;
      transform-origin: center bottom;
      box-shadow: 0 2px 8px rgba(253,224,71,0.3);
    }

    .petal:nth-child(1) { transform: rotate(0deg) translateY(-18px); }
    .petal:nth-child(2) { transform: rotate(45deg) translateY(-18px); }
    .petal:nth-child(3) { transform: rotate(90deg) translateY(-18px); }
    .petal:nth-child(4) { transform: rotate(135deg) translateY(-18px); }
    .petal:nth-child(5) { transform: rotate(180deg) translateY(-18px); }
    .petal:nth-child(6) { transform: rotate(225deg) translateY(-18px); }
    .petal:nth-child(7) { transform: rotate(270deg) translateY(-18px); }
    .petal:nth-child(8) { transform: rotate(315deg) translateY(-18px); }

    .flower-center {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 24px;
      height: 24px;
      margin: -12px;
      background: linear-gradient(135deg, #facc15, #eab308);
      border-radius: 50%;
      box-shadow: 0 0 12px rgba(234,179,8,0.5);
    }

    @keyframes bloomOpen {
      0% { transform: scale(0.2); opacity: 0; }
      70% { transform: scale(1.15); }
      100% { transform: scale(1); opacity: 1; }
    }

    .glow-ring {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 260px;
      height: 260px;
      margin: -130px;
      border-radius: 50%;
      border: 2px solid rgba(34,197,94,0.2);
      animation: ringPulse 3s ease-in-out infinite;
      opacity: 0;
      animation-delay: 2s;
      animation-fill-mode: forwards;
    }

    @keyframes ringPulse {
      0%, 100% { transform: scale(1); opacity: 0.3; }
      50% { transform: scale(1.1); opacity: 0.6; }
    }

    /* Floating elements */
    .leaf-float {
      position: absolute;
      width: 20px;
      height: 12px;
      background: linear-gradient(135deg, #86efac, #4ade80);
      border-radius: 50% 50% 0 50%;
      opacity: 0.7;
      animation: floatDown 10s ease-in-out infinite;
      pointer-events: none;
    }

    @keyframes floatDown {
      0% { transform: translateY(-20px) rotate(0deg); opacity: 0; }
      15% { opacity: 0.7; }
      85% { opacity: 0.7; }
      100% { transform: translateY(100vh) rotate(360deg); opacity: 0; }
    }

    /* Card & layout */
    .heading {
      text-align: center;
      margin-bottom: 2rem;
      opacity: 0;
      animation: fadeInUp 1.2s ease-out 0.3s forwards;
    }

    .heading h1 {
      font-size: 2.2rem;
      color: #14532d;
      margin-bottom: 0.5rem;
      letter-spacing: 1px;
    }

    .heading p {
      color: #166534;
      font-size: 1.1rem;
      font-style: italic;
    }

    .quotes-container {
      display: flex;
      flex-direction: column;
      gap: 2.5rem;
      width: 100%;
      max-width: 850px;
    }

    .quote-card {
      background: rgba(255,255,255,0.85);
      border-radius: 20px;
      padding: 2rem;
      display: flex;
      align-items: center;
      gap: 2rem;
      box-shadow: 0 8px 32px rgba(22,163,74,0.12);
      opacity: 0;
      transform: translateY(30px);
      animation: cardSlideIn 1s ease-out forwards;
      backdrop-filter: blur(6px);
      border-left: 4px solid #22c55e;
    }

    .quote-card:nth-child(1) { animation-delay: 0.8s; }
    .quote-card:nth-child(2) { animation-delay: 1.2s; }

    @keyframes cardSlideIn {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .quote-card.reverse {
      flex-direction: row-reverse;
      border-left: none;
      border-right: 4px solid #16a34a;
    }

    .photo-frame {
      width: 150px;
      height: 150px;
      border-radius: 50%;
      overflow: hidden;
      border: 5px solid white;
      box-shadow: 0 0 0 3px #86efac, 0 8px 20px rgba(22,163,74,0.2);
      flex-shrink: 0;
      transition: transform 0.5s ease, box-shadow 0.5s ease;
    }

    .photo-frame:hover {
      transform: scale(1.05);
      box-shadow: 0 0 0 4px #4ade80, 0 12px 28px rgba(22,163,74,0.25);
    }

    .photo-frame img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .quote-block {
      flex: 1;
    }

    .quote-text {
      font-size: 1.1rem;
      line-height: 1.9;
      color: #1f2937;
      font-style: italic;
      margin-bottom: 1rem;
      position: relative;
      padding-left: 1rem;
      border-left: 2px solid #86efac;
    }

    .quote-text::before {
      content: '"';
      font-size: 2.5rem;
      color: #86efac;
      position: absolute;
      top: -0.5rem;
      left: -0.5rem;
      font-family: Georgia, serif;
    }

    .quote-author {
      text-align: right;
      color: #15803d;
      font-weight: 600;
      font-size: 1rem;
    }

    .closing-note {
      margin-top: 3rem;
      text-align: center;
      padding: 2rem;
      background: rgba(255,255,255,0.8);
      border-radius: 20px;
      max-width: 600px;
      opacity: 0;
      animation: fadeInUp 1.2s ease-out 1.8s forwards;
      border-top: 3px solid #4ade80;
    }

    .closing-note h3 {
      color: #14532d;
      margin-bottom: 1rem;
      font-size: 1.3rem;
    }

    .closing-note p {
      color: #374151;
      line-height: 1.8;
    }

    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @media (max-width: 768px) {
      .quote-card, .quote-card.reverse {
        flex-direction: column;
        text-align: center;
      }
      .quote-text {
        padding-left: 0;
        border-left: none;
        padding-top: 1rem;
        border-top: 2px solid #86efac;
      }
      .quote-author {
        text-align: center;
      }
      .photo-frame {
        width: 130px;
        height: 130px;
      }
      .heading h1 { font-size: 1.7rem; }
      .plant { transform: scale(0.85); }
    }

    @media (max-width: 480px) {
      .photo-frame {
        width: 110px;
        height: 110px;
      }
      .quote-text { font-size: 1rem; }
      .container { padding: 2rem 1rem 3rem; }
    }
  </style>
</svelte:head>

<div class="container">
  <!-- Floating background leaves -->
  {#each floatingLeaves as fl}
    <div
      class="leaf-float"
      style="
        left: {fl.x}%;
        animation-delay: {fl.delay}s;
        animation-duration: {fl.dur}s;
        transform: rotate({fl.rotate}deg);
      "
    ></div>
  {/each}

  <!-- Heading -->
  <div class="heading">
    <h1>🌿 A Friendship Grown & Cherished 🌿</h1>
    <p>Rooted in respect, blossomed through time, nurtured with care</p>
  </div>

  <!-- 🌳 Animated Plant Centerpiece -->
  <div class="plant-wrapper">
    <div class="glow-ring"></div>
    <div class="plant">
      <div class="stem"></div>
      <div class="leaf leaf-1"></div>
      <div class="leaf leaf-2"></div>
      <div class="leaf leaf-3"></div>
      <div class="leaf leaf-4"></div>
      <div class="leaf leaf-5"></div>
      <div class="leaf leaf-6"></div>
      <div class="flower-bloom">
        <div class="petal"></div>
        <div class="petal"></div>
        <div class="petal"></div>
        <div class="petal"></div>
        <div class="petal"></div>
        <div class="petal"></div>
        <div class="petal"></div>
        <div class="petal"></div>
        <div class="flower-center"></div>
      </div>
    </div>
  </div>

  <!-- Quotes & Photos -->
  <div class="quotes-container">
    <!-- Person 1 -->
    <div class="quote-card">
      <div class="photo-frame">
        <img src="/person1.jpg" alt="Person 1" loading="lazy" />
      </div>
      <div class="quote-block">
        <p class="quote-text">
          True friendship is not about who you've known the longest, but who walked in and never walked out — especially when the seasons changed. We did not rush this; we let it take root, and what grew is stronger than I ever imagined.
        </p>
        <p class="quote-author">— Person One</p>
      </div>
    </div>

    <!-- Person 2 -->
    <div class="quote-card reverse">
      <div class="photo-frame">
        <img src="/person2.jpg" alt="Person 2" loading="lazy" />
      </div>
      <div class="quote-block">
        <p class="quote-text">
          Maturity is realizing that rare connection is worth protecting, not testing. We don't need to perform for each other; we simply are. And that quiet, steady acceptance is the most beautiful gift two friends can offer.
        </p>
        <p class="quote-author">— Person Two</p>
      </div>
    </div>
  </div>

  <!-- Closing Note -->
  <div class="closing-note">
    <h3>🌱 What We Have Built</h3>
    <p>
      Some bonds do not need to be loud to be strong. They do not need to be constant to be real. They simply need to be true — and what has grown between us is true. May it deepen, season after season, rooted in trust, watered with kindness, and sheltered by respect. Always.
    </p>
  </div>
</div>

<script>
  let floatingLeaves = [];

  function addFloatingLeaf() {
    floatingLeaves = [...floatingLeaves, {
      x: Math.random() * 90 + 5,
      delay: Math.random() * 10,
      dur: 7 + Math.random() * 5,
      rotate: Math.random() * 360
    }];
  }

  import { onMount } from 'svelte';

  onMount(() => {
    // Initial leaves
    for (let i = 0; i < 12; i++) addFloatingLeaf();

    // Continuously add new ones
    const interval = setInterval(() => {
      if (floatingLeaves.length < 25) addFloatingLeaf();
    }, 2000);

    return () => clearInterval(interval);
  });
</script>
