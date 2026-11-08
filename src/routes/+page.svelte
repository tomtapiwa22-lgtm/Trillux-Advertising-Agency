<script>
  const projects = [
    { name: 'Big Village Adeal', icon: '🌐', path: '/big-village' },
    { name: 'Education Forum', icon: '🎓', path: '/education-forum' },
    { name: 'Novella Books', icon: '📖', path: '/novella' },
    { name: 'Bible Connect', icon: '✝️', path: '/bible-connect' },
    { name: 'Aulora TV', icon: '📺', path: '/aulora-tv' },
    { name: 'Trillux Advertising', icon: '✨', path: '/trillux' },
    { name: 'Maximise Health', icon: '❤️‍🩹', path: '/maximise-health' },
    { name: 'BoardX', icon: '🎲', path: '/boardx' }
  ];

  let email = $state('');
  let password = $state('');
  let loading = $state(false);
  let error = $state('');
  let debugLog = $state([]);

  function addDebug(message, data = null) {
    const timestamp = new Date().toLocaleTimeString();
    const entry = `[${timestamp}] ${message}`;
    debugLog = [...debugLog, entry];
    if (data) console.log(message, data);
    else console.log(message);
  }

  async function handleSignIn(e) {
    e.preventDefault();
    if (loading) return;

    loading = true;
    error = '';
    debugLog = [];
    addDebug('▶️ Sign-in started');
    addDebug(`📧 Email: ${email}`);

    try {
      if (!email.trim() || !password.trim()) {
        throw new Error('Please enter both email and password');
      }

      addDebug('📤 Sending request to /api/login...');
      
      const res = await fetch('/api/login', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ email, password })
      });

      addDebug(`📥 Response status: ${res.status} ${res.statusText}`);
      
      const contentType = res.headers.get('content-type') || '';
      if (!contentType.includes('application/json')) {
        throw new Error('Server returned an unexpected response format');
      }

      const data = await res.json();
      addDebug('📦 Response data received', data);

      if (!res.ok) throw new Error(data.error || 'Sign in failed — check your credentials');

      const role = String(data.role || '').toLowerCase().trim();
      addDebug(`🔍 User role detected: "${role}"`);

      let target = '/dashboard';

      switch (role) {
        case 'admin': target = '/dashboard/admin'; break;
        case 'marketer': target = '/dashboard/marketer'; break;
        case 'developer': target = '/dashboard/developer'; break;
        case 'secretary': target = '/dashboard/secretary'; break;
        default: addDebug(`⚠️ Unknown role, using default dashboard`);
      }

      addDebug(`✅ Sign-in successful — redirect to: ${target}`);
      loading = false;
      window.location.href = target;
      
    } catch (err) {
      addDebug(`❌ Error: ${err.message}`);
      console.error('Signin error:', err);
      error = err.message;
      loading = false;
      addDebug('⏹️ Request finished');
    }
  }
</script>

<div class="page-container">
  <header class="top-header">
    <h1 class="brand-name">TOM <span>ENTERPRISE</span></h1>
    <p class="tagline">The Central Hub</p>
  </header>

  <div class="content-row">
    <div class="orbit-section">
      <div class="orbit-wrapper">
        <div class="center-logo">
          <div class="logo-ring-outer"></div>
          <div class="logo-ring-inner"></div>
          <div class="monogram">
            <span class="big-t">T</span>
            <span class="small-t">t</span>
          </div>
        </div>

        <div class="orbit-rotation">
          {#each projects as proj, i}
            <a 
              href={proj.path}
              class="orbit-item"
              style="--i: {i}; --total: {projects.length}"
              aria-label={`Go to ${proj.name}`}
            >
              <div class="project-circle">
                <span class="icon" aria-hidden="true">{proj.icon}</span>
                <span class="label">{proj.name}</span>
              </div>
            </a>
          {/each}
        </div>
      </div>
      <p class="motto">Building across media, health, tech & creativity</p>
    </div>

    <div class="auth-section">
      <div class="signin-card">
        <h2>Welcome Back</h2>
        <p class="subheading">Sign in to access your projects</p>

        {#if error}
          <div class="error-banner" role="alert">{error}</div>
        {/if}

        <form class="signin-form" on:submit={handleSignIn} novalidate>
          <div class="input-group">
            <label for="email">Email Address</label>
            <input
              type="email"
              id="email"
              bind:value={email}
              placeholder="you@example.com"
              required
              disabled={loading}
              autocomplete="email"
            />
          </div>

          <div class="input-group">
            <label for="password">Password</label>
            <input
              type="password"
              id="password"
              bind:value={password}
              placeholder="••••••••"
              required
              disabled={loading}
              autocomplete="current-password"
            />
          </div>

          <div class="form-options">
            <label class="remember">
              <input type="checkbox" /> Remember me
            </label>
            <a href="/forgot-password" class="forgot-link">Forgot password?</a>
          </div>

          <button type="submit" class="signin-btn" disabled={loading}>
            {loading ? 'Signing in…' : 'Sign In'}
          </button>
        </form>
      </div>

      {#if debugLog.length > 0}
        <div class="debug-panel">
          <h4>Debug Log</h4>
          <div class="debug-content">
            {#each debugLog as line}
              <div class="debug-line">{line}</div>
            {/each}
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>

<style>
  :root {
    --gold: linear-gradient(135deg, #d4af37, #f6e27a, #d4af37);
    --gold-soft: rgba(212, 175, 55, 0.35);
    --blue-deep: linear-gradient(135deg, #1e6af4, #4fa3ff, #1e6af4);
    --blue-soft: rgba(30, 106, 244, 0.25);
    --card-bg: rgba(12, 12, 20, 0.75);
    --input-bg: rgba(25, 25, 35, 0.8);
    --orbit-radius: 185px;
    --error-red: #e5484d;
    --debug-bg: rgba(0, 0, 0, 0.6);
    --debug-border: rgba(100, 100, 100, 0.4);
  }

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  .page-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    padding: 1.5rem 2rem;
    max-width: 1400px;
    background: radial-gradient(circle at top right, #1A1A24 0%, #0F0F12 70%);
    color: #fff;
    font-family: 'Segoe UI', system-ui, sans-serif;
  }

  .top-header {
    text-align: center;
    margin-bottom: 2rem;
    z-index: 5;
  }

  .brand-name {
    font-size: clamp(2rem, 5vw, 3.2rem);
    font-weight: 800;
    letter-spacing: 0.05em;
    margin-bottom: 0.25rem;
  }

  .brand-name span {
    background: var(--gold);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .tagline {
    color: #999;
    font-size: 1.05rem;
    letter-spacing: 0.15em;
  }

  .content-row {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 3rem;
    width: 100%;
    flex-wrap: wrap;
  }

  .orbit-section {
    flex: 1.2;
    text-align: center;
  }

  .orbit-wrapper {
    position: relative;
    width: calc(var(--orbit-radius) * 2);
    height: calc(var(--orbit-radius) * 2);
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .center-logo {
    position: absolute;
    width: 150px;
    height: 150px;
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .logo-ring-outer {
    position: absolute;
    inset: 0;
    border-radius: 50%;
    background: var(--blue-deep);
    opacity: 0.12;
    animation: pulse 5s ease-in-out infinite;
  }

  .logo-ring-inner {
    position: absolute;
    inset: 12px;
    border-radius: 50%;
    border: 1px solid var(--blue-soft);
  }

  .monogram {
    position: relative;
    font-size: 4.2rem;
    font-weight: 900;
    letter-spacing: -0.08em;
    line-height: 1;
  }

  .big-t {
    background: var(--blue-deep);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .small-t {
    position: absolute;
    top: 24px;
    left: 32px;
    font-size: 2.3rem;
    background: var(--gold);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .orbit-rotation {
    position: absolute;
    width: 100%;
    height: 100%;
    animation: orbitRotate 80s linear infinite;
    will-change: transform;
  }

  @keyframes orbitRotate {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }

  .orbit-item {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 110px;
    height: 110px;
    margin-top: -55px;
    margin-left: -55px;
    text-decoration: none;
    color: inherit;
    transform-origin: center center;
    transform: rotate(calc(var(--i) * 360deg / var(--total))) translate(var(--orbit-radius));
    transition: transform 0.35s ease;
    will-change: transform;
  }

  .project-circle {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: var(--card-bg);
    border: 1px solid rgba(212, 175, 55, 0.18);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 0.3rem;
    transform: rotate(calc(var(--i) * -360deg / var(--total)));
    transition: all 0.3s ease;
  }

  .orbit-item:hover {
    transform: rotate(calc(var(--i) * 360deg / var(--total))) translate(calc(var(--orbit-radius) + 12px));
    z-index: 5;
  }

  .orbit-item:hover .project-circle {
    border-color: var(--gold-soft);
    box-shadow: 0 0 20px rgba(212, 175, 55, 0.15), inset 0 0 15px rgba(0,0,0,0.4);
  }

  .project-circle .icon {
    font-size: 1.4rem;
    margin-bottom: 0.2rem;
  }

  .project-circle .label {
    font-size: 0.65rem;
    color: #ccc;
    font-weight: 500;
    line-height: 1.2;
    padding: 0 0.3rem;
    text-align: center;
  }

  .motto {
    margin-top: 1.5rem;
    color: #666;
    font-size: 0.85rem;
    letter-spacing: 0.08em;
  }

  .auth-section {
    flex: 0 0 380px;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .signin-card {
    background: var(--card-bg);
    border: 1px solid rgba(212, 175, 55, 0.15);
    border-radius: 16px;
    padding: 2.5rem 2rem;
    box-shadow: 0 15px 40px rgba(0,0,0,0.4);
  }

  .signin-card h2 {
    font-size: 1.6rem;
    margin-bottom: 0.3rem;
    color: #f0f0f0;
  }

  .subheading {
    color: #777;
    font-size: 0.9rem;
    margin-bottom: 1.2rem;
  }

  .error-banner {
    background: rgba(229, 72, 77, 0.1);
    border: 1px solid var(--error-red);
    border-radius: 6px;
    padding: 0.75rem;
    margin-bottom: 1.2rem;
    color: #ff8a8a;
    font-size: 0.85rem;
  }

  .signin-form {
    display: flex;
    flex-direction: column;
    gap: 1.2rem;
  }

  .input-group label {
    display: block;
    font-size: 0.85rem;
    color: #aaa;
    margin-bottom: 0.4rem;
  }

  .input-group input {
    width: 100%;
    padding: 0.9rem 1rem;
    background: var(--input-bg);
    border: 1px solid rgba(212, 175, 55, 0.15);
    border-radius: 8px;
    color: #fff;
    font-size: 0.95rem;
    transition: border-color 0.3s ease;
  }

  .input-group input:focus {
    outline: none;
    border-color: var(--gold-soft);
  }

  .input-group input:disabled {
    opacity: 0.6;
    cursor: not-allowed;
  }

  .form-options {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 0.8rem;
  }

  .remember {
    color: #999;
    display: flex;
    align-items: center;
    gap: 0.4rem;
    cursor: pointer;
  }

  .forgot-link {
    color: #d4af37;
    text-decoration: none;
  }

  .signin-btn {
    margin-top: 0.5rem;
    padding: 0.95rem;
    background: var(--gold);
    border: none;
    border-radius: 8px;
    color: #000;
    font-weight: 700;
    font-size: 1rem;
    cursor: pointer;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }

  .signin-btn:hover:not(:disabled) {
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(212, 175, 55, 0.25);
  }

  .signin-btn:disabled {
    opacity: 0.7;
    cursor: wait;
  }

  .debug-panel {
    background: var(--debug-bg);
    border: 1px solid var(--debug-border);
    border-radius: 10px;
    padding: 1rem;
    max-height: 300px;
    overflow-y: auto;
  }

  .debug-panel h4 {
    color: #aaa;
    font-size: 0.85rem;
    margin-bottom: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .debug-content {
    display: flex;
    flex-direction: column;
    gap: 0.35rem;
    font-family: 'Courier New', monospace;
    font-size: 0.78rem;
  }

  .debug-line {
    color: #9f9;
    padding: 0.25rem 0.5rem;
    background: rgba(0,0,0,0.3);
    border-radius: 4px;
  }

  @keyframes pulse {
    0%, 100% { transform: scale(1); opacity: 0.12; }
    50% { transform: scale(1.05); opacity: 0.18; }
  }

  @media (max-width: 1024px) {
    .content-row { flex-direction: column; gap: 2rem; }
    .auth-section { flex: none; width: 100%; max-width: 380px; }
    :root { --orbit-radius: 165px; }
  }

  @media (max-width: 480px) {
    :root { --orbit-radius: 140px; }
    .orbit-item { width: 90px; height: 90px; margin-top: -45px; margin-left: -45px; }
    .center-logo { width: 120px; height: 120px; }
    .monogram { font-size: 3.2rem; }
    .small-t { font-size: 1.8rem; top: 18px; left: 25px; }
    .project-circle .label { font-size: 0.55rem; }
  }
</style>
