<script>
  let visible = false;
  
  import { onMount } from 'svelte';
  
  onMount(() => {
    setTimeout(() => visible = true, 100);
  });
</script>

<div class="container" class:visible>
  <!-- Background Glow Effects (Adjusted for Light Mode) -->
  <div class="glow glow-1"></div>
  <div class="glow glow-2"></div>
  <div class="glow glow-3"></div>

  <nav>
    <div class="logo">Svelte<span class="highlight">Flow</span></div>
    <div class="links">
      <a href="#features">Features</a>
      <a href="#about">About</a>
      <a href="https://github.com/parkss207/repo" target="_blank" class="btn-small">GitHub</a>
    </div>
  </nav>

  <main>
    <header class="hero">
      <div class="badge">Performance Redefined</div>
      <h1>
        Build something <br />
        <span class="gradient-text">Beautiful.</span>
      </h1>
      <p class="subtitle">
        화사하고 깔끔한 디자인으로 새롭게 태어났습니다.<br>
        SvelteKit과 Cloudflare의 강력한 조합을 경험해보세요.
      </p>
      
      <div class="cta-group">
        <button class="btn-primary">Get Started</button>
        <button class="btn-secondary">Learn More</button>
      </div>
    </header>

    <section id="features" class="grid">
      <div class="card">
        <div class="icon-bg">⚡</div>
        <h3>Lightning Fast</h3>
        <p>Vite와 Svelte의 힘으로 압도적인 속도와 최적화된 빌드를 제공합니다.</p>
      </div>
      <div class="card">
        <div class="icon-bg">🎨</div>
        <h3>Aesthetic Design</h3>
        <p>밝고 화사한 컬러 팔레트와 글래스모피즘으로 세련된 UI를 선사합니다.</p>
      </div>
      <div class="card">
        <div class="icon-bg">🌍</div>
        <h3>Global Scale</h3>
        <p>Cloudflare Edge Network를 통해 전 세계 어디서나 빠르게 접속하세요.</p>
      </div>
    </section>
  </main>
  
  <footer>
    <p>&copy; 2026 Parkss207. All rights reserved.</p>
  </footer>
</div>

<style>
  /* Layout & Container */
  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    position: relative;
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 1s cubic-bezier(0.16, 1, 0.3, 1), transform 1s cubic-bezier(0.16, 1, 0.3, 1);
    background: transparent;
  }
  .container.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* Decorative Glows - Soft Pastels */
  .glow {
    position: absolute;
    width: 800px;
    height: 800px;
    border-radius: 50%;
    z-index: -1;
    filter: blur(100px);
    opacity: 0.5;
    animation: drift 15s infinite alternate ease-in-out;
  }
  /* Left Top: Soft Blue/Cyan */
  .glow-1 { 
    top: -300px; 
    left: -200px; 
    background: radial-gradient(circle, #bae6fd 0%, rgba(255,255,255,0) 70%); 
  }
  /* Right Bottom: Soft Pink/Purple */
  .glow-2 { 
    bottom: -300px; 
    right: -200px; 
    background: radial-gradient(circle, #fbcfe8 0%, rgba(255,255,255,0) 70%); 
    animation-delay: -5s; 
  }
  /* Center Accent: Soft Violet */
  .glow-3 {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 600px;
    height: 600px;
    background: radial-gradient(circle, #ddd6fe 0%, rgba(255,255,255,0) 70%);
    animation-delay: -10s;
  }

  @keyframes drift {
    0% { transform: translate(0, 0); }
    100% { transform: translate(40px, 60px); }
  }

  /* Navigation */
  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 0;
    margin-bottom: 5rem;
  }
  .logo {
    font-size: 1.5rem;
    font-weight: 800;
    letter-spacing: -0.05em;
    color: var(--text-color);
  }
  .highlight { 
    background: var(--primary-gradient);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .links { display: flex; gap: 2rem; align-items: center; }
  .links a { 
    font-weight: 600; 
    color: var(--text-secondary);
    transition: color 0.2s; 
    font-size: 0.95rem; 
  }
  .links a:hover { color: var(--text-color); }
  
  .btn-small {
    background: white;
    padding: 0.5rem 1.2rem;
    border-radius: 50px;
    font-size: 0.85rem;
    font-weight: 600;
    color: var(--text-color);
    box-shadow: 0 2px 5px rgba(0,0,0,0.05);
    border: 1px solid #e2e8f0;
    transition: all 0.3s ease;
  }
  .btn-small:hover { 
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.1); 
    border-color: #cbd5e1;
  }

  /* Hero Section */
  .hero {
    text-align: center;
    padding: 2rem 0 6rem;
  }
  .badge {
    display: inline-block;
    padding: 0.5rem 1.2rem;
    background: #eff6ff;
    color: #3b82f6;
    border-radius: 50px;
    font-size: 0.85rem;
    margin-bottom: 2rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
    box-shadow: 0 2px 6px rgba(59, 130, 246, 0.1);
  }
  h1 {
    font-size: 5rem;
    line-height: 1.1;
    font-weight: 800;
    margin-bottom: 1.5rem;
    letter-spacing: -0.04em;
    color: var(--text-color);
  }
  .gradient-text {
    background: var(--primary-gradient);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    padding-bottom: 10px; /* Protect descenders */
  }
  .subtitle {
    font-size: 1.25rem;
    color: var(--text-secondary);
    max-width: 580px;
    margin: 0 auto 3.5rem;
    font-weight: 400;
  }

  /* Buttons */
  .cta-group {
    display: flex;
    gap: 1.5rem;
    justify-content: center;
  }
  button {
    padding: 1rem 2.5rem;
    font-size: 1.05rem;
    font-weight: 700;
    border-radius: 50px;
    cursor: pointer;
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    font-family: inherit;
    border: none;
  }
  button:active { transform: scale(0.96); }
  
  .btn-primary {
    background: var(--primary-gradient);
    color: white;
    box-shadow: 0 10px 25px -5px rgba(99, 102, 241, 0.4);
  }
  .btn-primary:hover {
    box-shadow: 0 15px 35px -5px rgba(99, 102, 241, 0.5);
    transform: translateY(-3px);
  }
  
  .btn-secondary {
    background: white;
    color: var(--text-color);
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05), 0 2px 4px -1px rgba(0, 0, 0, 0.03);
    border: 1px solid #f1f5f9;
  }
  .btn-secondary:hover {
    background: #f8fafc;
    transform: translateY(-3px);
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.05);
  }

  /* Features Grid */
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 2.5rem;
    margin-top: 4rem;
  }
  .card {
    background: var(--glass-bg);
    border: 1px solid var(--glass-border);
    padding: 3rem 2rem;
    border-radius: 24px;
    box-shadow: var(--glass-shadow);
    transition: all 0.4s ease;
    text-align: left;
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
  }
  .card:hover {
    transform: translateY(-8px);
    box-shadow: 0 20px 40px -5px rgba(0, 0, 0, 0.1);
    background: rgba(255, 255, 255, 0.85);
  }
  
  .icon-bg {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 60px;
    height: 60px;
    background: #f0f9ff;
    border-radius: 20px;
    font-size: 1.8rem;
    margin-bottom: 1.5rem;
    box-shadow: inset 0 2px 4px rgba(0,0,0,0.02);
  }
  
  h3 {
    font-size: 1.4rem;
    margin-bottom: 0.8rem;
    font-weight: 700;
    color: var(--text-color);
  }
  .card p {
    color: var(--text-secondary);
    font-size: 1rem;
    line-height: 1.7;
  }

  footer {
    text-align: center;
    margin-top: 8rem;
    padding-bottom: 2rem;
    color: #94a3b8;
    font-size: 0.9rem;
    font-weight: 500;
  }

  /* Mobile Adjustments */
  @media (max-width: 768px) {
    .container { 
      padding: 1.5rem 1rem; 
      overflow-x: hidden;
    }
    
    /* Navigation Stack */
    nav { 
      flex-direction: column; 
      gap: 1.5rem; 
      margin-bottom: 3rem;
    }
    .links { 
      /* Re-enable links for mobile but stack or simplify them if needed. 
         For now, let's keep them visible but smaller */
      display: flex; 
      gap: 1rem; 
      flex-wrap: wrap;
      justify-content: center;
    }
    
    /* Hero Section - Compact */
    .hero { 
      padding: 1rem 0 3rem; 
    }
    h1 { 
      font-size: 2.8rem; 
      margin-bottom: 1rem;
    }
    .subtitle { 
      font-size: 1rem; 
      margin-bottom: 2.5rem;
      padding: 0 1rem;
    }
    
    /* Buttons */
    .cta-group { 
      flex-direction: column; 
      gap: 1rem; 
      padding: 0 1rem;
    }
    button {
      width: 100%;
      padding: 0.9rem 2rem;
    }

    /* Grid - Single Column */
    .grid { 
      grid-template-columns: 1fr; 
      gap: 1.5rem; 
      margin-top: 2rem;
    }
    .card {
      padding: 2rem 1.5rem;
    }
  }
</style>
