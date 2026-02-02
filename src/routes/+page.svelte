<script>
  let visible = false;
  
  import { onMount } from 'svelte';
  
  onMount(() => {
    // Simple fade-in effect on mount
    setTimeout(() => visible = true, 100);
  });
</script>

<div class="container" class:visible>
  <!-- Background Glow Effects -->
  <div class="glow glow-1"></div>
  <div class="glow glow-2"></div>

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
      <div class="badge">Created for performance</div>
      <h1>
        Build something <br />
        <span class="gradient-text">Extraordinary.</span>
      </h1>
      <p class="subtitle">
        배포된 SvelteKit 프로젝트가 정상 작동 중입니다.<br>
        Cloudflare Pages와 함께 무한한 확장성을 경험하세요.
      </p>
      
      <div class="cta-group">
        <button class="btn-primary">Get Started</button>
        <button class="btn-secondary">Learn More</button>
      </div>
    </header>

    <section id="features" class="grid">
      <div class="card">
        <div class="icon">⚡</div>
        <h3>Lightning Fast</h3>
        <p>Powered by Vite and Svelte, offering instant HMR and optimized builds.</p>
      </div>
      <div class="card">
        <div class="icon">🌍</div>
        <h3>Edge Ready</h3>
        <p>Deployed globally on Cloudflare's massive edge network for low latency.</p>
      </div>
      <div class="card">
        <div class="icon">🎨</div>
        <h3>Modern Design</h3>
        <p>Styled with advanced CSS features, glassmorphism, and smooth animations.</p>
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
    transition: opacity 0.8s ease-out, transform 0.8s ease-out;
  }
  .container.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* Decorative Glows */
  .glow {
    position: absolute;
    width: 600px;
    height: 600px;
    background: radial-gradient(circle, rgba(139, 92, 246, 0.3) 0%, rgba(0,0,0,0) 70%);
    border-radius: 50%;
    z-index: -1;
    filter: blur(80px);
    opacity: 0.6;
    animation: drift 10s infinite alternate ease-in-out;
  }
  .glow-1 { top: -200px; left: -200px; background: radial-gradient(circle, rgba(99, 102, 241, 0.3) 0%, rgba(0,0,0,0) 70%); }
  .glow-2 { bottom: -200px; right: -200px; background: radial-gradient(circle, rgba(236, 72, 153, 0.25) 0%, rgba(0,0,0,0) 70%); animation-delay: -5s; }

  @keyframes drift {
    0% { transform: translate(0, 0); }
    100% { transform: translate(30px, 50px); }
  }

  /* Navigation */
  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 0;
    margin-bottom: 4rem;
  }
  .logo {
    font-size: 1.5rem;
    font-weight: 800;
    letter-spacing: -0.05em;
  }
  .highlight { color: #8b5cf6; }
  .links { display: flex; gap: 2rem; align-items: center; }
  .links a { font-weight: 500; opacity: 0.8; transition: opacity 0.2s; font-size: 0.95rem; }
  .links a:hover { opacity: 1; }
  
  .btn-small {
    background: rgba(255,255,255,0.1);
    padding: 0.5rem 1rem;
    border-radius: 20px;
    font-size: 0.85rem;
    border: 1px solid rgba(255,255,255,0.1);
    transition: all 0.3s ease;
  }
  .btn-small:hover { background: rgba(255,255,255,0.2); }

  /* Hero Section */
  .hero {
    text-align: center;
    padding: 4rem 0 6rem;
  }
  .badge {
    display: inline-block;
    padding: 0.5rem 1.2rem;
    background: rgba(139, 92, 246, 0.15);
    color: #a78bfa;
    border-radius: 50px;
    border: 1px solid rgba(139, 92, 246, 0.3);
    font-size: 0.85rem;
    margin-bottom: 1.5rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
  }
  h1 {
    font-size: 4.5rem;
    line-height: 1.1;
    font-weight: 800;
    margin-bottom: 1.5rem;
    letter-spacing: -0.03em;
  }
  .gradient-text {
    background: var(--primary-gradient);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .subtitle {
    font-size: 1.2rem;
    color: #94a3b8;
    max-width: 600px;
    margin: 0 auto 3rem;
  }

  /* Buttons */
  .cta-group {
    display: flex;
    gap: 1rem;
    justify-content: center;
  }
  button {
    padding: 1rem 2rem;
    font-size: 1rem;
    font-weight: 600;
    border-radius: 8px;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
    font-family: inherit;
  }
  button:active { transform: scale(0.98); }
  
  .btn-primary {
    background: var(--primary-gradient);
    border: none;
    color: white;
    box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
  }
  .btn-primary:hover {
    box-shadow: 0 6px 20px rgba(99, 102, 241, 0.6);
    transform: translateY(-2px);
  }
  
  .btn-secondary {
    background: transparent;
    border: 1px solid rgba(255,255,255,0.2);
    color: white;
  }
  .btn-secondary:hover {
    border-color: rgba(255,255,255,0.6);
    background: rgba(255,255,255,0.05);
  }

  /* Features Grid */
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
  }
  .card {
    background: var(--glass-bg);
    border: 1px solid var(--glass-border);
    padding: 2.5rem;
    border-radius: 16px;
    transition: transform 0.3s ease, border-color 0.3s ease;
  }
  .card:hover {
    transform: translateY(-5px);
    border-color: rgba(255,255,255,0.3);
    background: rgba(255, 255, 255, 0.08);
  }
  .icon {
    font-size: 2.5rem;
    margin-bottom: 1rem;
  }
  h3 {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
    font-weight: 600;
  }
  .card p {
    color: #94a3b8;
    font-size: 0.95rem;
  }

  footer {
    text-align: center;
    margin-top: auto;
    padding-top: 4rem;
    color: #64748b;
    font-size: 0.9rem;
  }

  /* Mobile Adjustments */
  @media (max-width: 768px) {
    h1 { font-size: 3rem; }
    .hero { padding: 2rem 0 4rem; }
    .grid { gap: 1rem; }
    .links { display: none; }
  }
</style>
