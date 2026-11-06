<svelte:head>
  <title>Rooted in Truth 💙</title>
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
      background: linear-gradient(180deg, #eff6ff 0%, #dbeafe 50%, #bfdbfe 100%);
      font-family: 'Segoe UI', Georgia, serif;
      color: #1e3a5f;
    }

    .page {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 3rem 2rem;
      max-width: 900px;
      margin: 0 auto;
    }

    h1 {
      font-size: 2rem;
      text-align: center;
      margin-bottom: 0.5rem;
      opacity: 0;
      animation: fadeIn 1s ease-out forwards;
      color: #1e3a8a;
    }

    .subtitle {
      font-size: 1.1rem;
      color: #3b5998;
      font-style: italic;
      margin-bottom: 3rem;
      opacity: 0;
      animation: fadeIn 1s ease-out 0.2s forwards;
    }

    .photos-row {
      display: flex;
      gap: 2.5rem;
      justify-content: center;
      width: 100%;
      margin-bottom: 3rem;
      flex-wrap: wrap;
    }

    .photo-wrap {
      flex: 1;
      min-width: 280px;
      max-width: 360px;
      opacity: 0;
      transform: translateY(20px);
      animation: photoUp 1s ease-out forwards;
    }

    .photo-wrap:nth-child(1) { animation-delay: 0.3s; }
    .photo-wrap:nth-child(2) { animation-delay: 0.5s; }

    .photo-frame {
      width: 100%;
      aspect-ratio: 4/5;
      border-radius: 20px;
      overflow: hidden;
      border: 6px solid white;
      box-shadow: 0 10px 30px rgba(30, 58, 138, 0.15);
      transition: transform 0.4s ease, box-shadow 0.4s ease;
      position: relative;
    }

    /* 1% red accent — thin inner glow line */
    .photo-frame::after {
      content: '';
      position: absolute;
      inset: 4px;
      border-radius: 16px;
      border: 1px solid rgba(220, 38, 38, 0.15);
      pointer-events: none;
    }

    .photo-frame:hover {
      transform: translateY(-6px);
      box-shadow: 0 16px 40px rgba(30, 58, 138, 0.22), 0 0 0 2px rgba(220, 38, 38, 0.12);
    }

    .photo-frame img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .name {
      text-align: center;
      margin-top: 1.2rem;
      font-size: 1.3rem;
      font-weight: 600;
      color: #1e40af;
    }

    .quotes-section {
      display: flex;
      flex-direction: column;
      gap: 2.5rem;
      max-width: 700px;
      width: 100%;
    }

    .quote-card {
      background: rgba(255, 255, 255, 0.9);
      border-radius: 20px;
      padding: 2rem;
      opacity: 0;
      transform: translateY(15px);
      animation: quoteFade 1s ease-out forwards;
      border-left: 4px solid #3b82f6;
      box-shadow: 0 6px 20px rgba(59, 130, 246, 0.1);
      position: relative;
    }

    /* 1% red accent — tiny top-right dot */
    .quote-card::after {
      content: '';
      position: absolute;
      top: 1rem;
      right: 1rem;
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: rgba(220, 38, 38, 0.6);
    }

    .quote-card:nth-child(1) { animation-delay: 0.8s; }
    .quote-card:nth-child(2) { animation-delay: 1.1s; }

    .quote-card.reverse {
      border-left: none;
      border-right: 4px solid #1d4ed8;
      text-align: right;
    }

    .quote-card.reverse::after {
      right: auto;
      left: 1rem;
    }

    .quote-text {
      font-size: 1.2rem;
      line-height: 1.9;
      color: #1e293b;
      font-style: italic;
      margin-bottom: 1rem;
    }

    .quote-author {
      font-size: 1rem;
      font-weight: 600;
      color: #1e40af;
    }

    .accent-heart {
      font-size: 2rem;
      text-align: center;
      margin: 1rem 0;
      opacity: 0;
      animation: fadeIn 1s ease-out 1.4s forwards, gentleBeat 2.5s ease-in-out infinite;
      color: #dc2626;
    }

    @keyframes fadeIn {
      to { opacity: 1; }
    }

    @keyframes photoUp {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes quoteFade {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes gentleBeat {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.15); }
    }

    @media (max-width: 640px) {
      h1 { font-size: 1.6rem; }
      .quote-text { font-size: 1.05rem; }
      .page { padding: 2rem 1.25rem; }
      .photos-row { gap: 1.5rem; }
      .quote-card.reverse { text-align: left; border-right: none; border-left: 4px solid #3b82f6; }
      .quote-card.reverse::after { left: auto; right: 1rem; }
    }
  </style>
</svelte:head>

<div class="page">
  <h1>Truth. Connection. Ours.</h1>
  <p class="subtitle">Where a simple greeting grew into something truly beautiful</p>

  <div class="photos-row">
    <div class="photo-wrap">
      <div class="photo-frame">
        <img src="/tapiwanshe.jpg" alt="Tapiwanshe" loading="lazy" />
      </div>
      <p class="name">Tapiwanshe</p>
    </div>

    <div class="photo-wrap">
      <div class="photo-frame">
        <img src="/ruth.jpg" alt="Ruth" loading="lazy" />
      </div>
      <p class="name">Ruth</p>
    </div>
  </div>

  <div class="accent-heart">♥</div>

  <div class="quotes-section">
    <!-- From Tapiwanshe -->
    <div class="quote-card">
      <p class="quote-text">
        You caught me off guard with a simple "hi" — and one thing led to another, until now I find I cannot spend a single moment without you crossing my mind. What began as a whisper has grown into something my heart carries, always.
      </p>
      <p class="quote-author">— Tapiwanshe</p>
    </div>

    <!-- From Ruth -->
    <div class="quote-card reverse">
      <p class="quote-text">
        When a foundation is laid in truth — no pretense, no shadows, no lies — something rare takes root. It is wondrous how effortlessly our spirits meet, how naturally the chemistry flows, unforced and unfeigned. This is the kind of bond that lasts.
      </p>
      <p class="quote-author">— Ruth</p>
    </div>
  </div>
</div>
