

This is a challenge of **emotional resonance**. To move from "clean" to "breathtaking," we must move beyond functionality into the realm of **atmosphere** and **cinematic motion**.

Here is the re-imagined "Luxe Nature" edition.

### Design Philosophy: "Quiet Luxury & Fluid Motion"
1.  **Atmosphere:** I have introduced a global **Noise Texture** overlay. This mimics the grain of high-end paper or film, removing the "digital plastic" feel.
2.  **Lighting:** A **Spotlight Effect** follows the mouse cursor, revealing hidden details in the glass panels. This creates an interactive "alive" feeling.
3.  **Typography:** We switch to **Cormorant Garamond** (for that Vogue-esque editorial look) paired with **DM Sans**. Text sizes are massive and asymmetric to break the grid.
4.  **Motion:** We use **Scrollytelling** elements and an infinite Marquee to inject rhythm. The product hover effects are now sophisticated 3D lifts with shadow expansion.

---

### File 1: index.html
**Structure:** Asymmetric layout, marquee integration, and glass-layering.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="The Scent - A sensory journey for the soul. Luxury aromatherapy redefined.">
    <title>The Scent | Sensory Wellness</title>
    
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,400&family=DM+Sans:wght@400;500;700&display=swap" rel="stylesheet">
    
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <!-- Global Noise Overlay for Texture -->
    <div class="noise-overlay"></div>

    <!-- Spotlight Effect Container (Canvas) -->
    <div id="spotlight"></div>

    <!-- Navigation -->
    <nav class="nav-layer">
        <div class="container nav-container">
            <a href="#" class="brand-logo">
                <span>THE SCENT</span>
            </a>
            
            <div class="nav-links desktop">
                <a href="#collection" class="nav-link magnetic">Collection</a>
                <a href="#philosophy" class="nav-link magnetic">Philosophy</a>
                <a href="#journal" class="nav-link magnetic">Journal</a>
            </div>

            <div class="nav-actions">
                <button class="icon-btn magnetic" aria-label="Cart">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M6 2L3 6v14a2 2 0 002 2h14a2 2 0 002-2V6l-3-4z"></path><line x1="3" y1="6" x2="21" y2="6"></line><path d="M16 10a4 4 0 01-8 0"></path></svg>
                    <span class="cart-indicator">2</span>
                </button>
                <button class="menu-toggle magnetic" aria-label="Menu">
                    <span>Menu</span>
                </button>
            </div>
        </div>
    </nav>

    <main>
        
        <!-- Hero Section: Editorial & Asymmetric -->
        <section class="hero">
            <div class="hero-bg">
                <div class="orb orb-1"></div>
                <div class="orb orb-2"></div>
                <div class="orb orb-3"></div>
            </div>

            <div class="container hero-content">
                <div class="hero-text">
                    <span class="eyebrow">Est. 2024 • Los Angeles</span>
                    <h1 class="hero-title">
                        Botanical <br>
                        <span class="italic">Alchemy</span>
                    </h1>
                    <p class="hero-sub">
                        A curated collection of essential oils designed to transform your space and state of mind.
                    </p>
                    <div class="hero-cta-wrapper">
                        <a href="#collection" class="btn-luxe magnetic">
                            <span>Explore the Collection</span>
                            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
                        </a>
                    </div>
                </div>
                
                <!-- CSS Art Product Showcase -->
                <div class="hero-visual">
                    <div class="product-art-container">
                        <!-- Abstract Bottle 1 -->
                        <div class="glass-bottle b-1">
                            <div class="liquid liquid-1"></div>
                            <div class="reflection"></div>
                            <div class="label">
                                <span>No. 01</span>
                                <span>Clarity</span>
                            </div>
                        </div>
                        
                        <!-- Abstract Bottle 2 (Background) -->
                        <div class="glass-bottle b-2">
                            <div class="liquid liquid-2"></div>
                            <div class="reflection"></div>
                        </div>

                        <!-- Leaf Elements -->
                        <div class="floating-leaf l-1">🌿</div>
                        <div class="floating-leaf l-2">🍂</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Marquee: Infinite Rhythm -->
        <div class="marquee-section">
            <div class="marquee-track">
                <span>Pure Essential Oils</span>
                <span>•</span>
                <span>Small Batch Production</span>
                <span>•</span>
                <span>Sustainable Sourcing</span>
                <span>•</span>
                <span>Pure Essential Oils</span>
                <span>•</span>
                <span>Small Batch Production</span>
                <span>•</span>
                <span>Sustainable Sourcing</span>
                <span>•</span>
            </div>
        </div>

        <!-- Philosophy: Large Imagery & Asymmetry -->
        <section id="philosophy" class="philosophy">
            <div class="container">
                <div class="phil-grid">
                    <div class="phil-text sticky-col">
                        <span class="eyebrow">The Philosophy</span>
                        <h2>Rooted in <span class="italic">Nature</span>,<br>Crafted by Hand.</h2>
                        <p>We believe that true wellness begins with intention. Our oils are not manufactured; they are coaxed from the earth using time-honored distillation methods that preserve the plant's soul.</p>
                        <br>
                        <p>Every drop is a promise of purity, designed to bring the serenity of the forest into the chaos of the modern world.</p>
                        <br>
                        <a href="#" class="text-link magnetic">Read our story <span>→</span></a>
                    </div>
                    <div class="phil-images">
                        <!-- CSS Generated "Image" -->
                        <div class="art-card art-1">
                            <div class="art-content">
                                <h3>01. Source</h3>
                                <p>Global botanical farms</p>
                            </div>
                        </div>
                        <div class="art-card art-2">
                            <div class="art-content">
                                <h3>02. Distill</h3>
                                <p>Slow copper extraction</p>
                            </div>
                        </div>
                        <div class="art-card art-3">
                            <div class="art-content">
                                <h3>03. Blend</h3>
                                <p>Master perfumer touch</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Collection: High-End Grid -->
        <section id="collection" class="collection">
            <div class="container">
                <div class="col-header">
                    <h2>The Collection</h2>
                    <div class="filters">
                        <button class="filter active">All</button>
                        <button class="filter">Oils</button>
                        <button class="filter">Diffusers</button>
                    </div>
                </div>

                <div class="product-grid">
                    <!-- Product Card 1 -->
                    <article class="product-card luxe-card">
                        <div class="p-image">
                            <div class="p-art p-art-1"></div>
                            <div class="p-overlay">
                                <button class="btn-circle magnetic" onclick="addToCart()">
                                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 5v14M5 12h14"/></svg>
                                </button>
                                <span>Quick View</span>
                            </div>
                        </div>
                        <div class="p-details">
                            <h3>Forest Ground</h3>
                            <div class="p-meta">
                                <span>$145.00</span>
                                <span>Cedar • Moss</span>
                            </div>
                        </div>
                    </article>

                    <!-- Product Card 2 -->
                    <article class="product-card luxe-card">
                        <div class="p-image">
                            <div class="p-art p-art-2"></div>
                            <div class="p-overlay">
                                <button class="btn-circle magnetic" onclick="addToCart()">
                                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 5v14M5 12h14"/></svg>
                                </button>
                                <span>Quick View</span>
                            </div>
                        </div>
                        <div class="p-details">
                            <h3>Golden Hour</h3>
                            <div class="p-meta">
                                <span>$120.00</span>
                                <span>Bergamot • Amber</span>
                            </div>
                        </div>
                    </article>

                    <!-- Product Card 3 -->
                    <article class="product-card luxe-card">
                        <div class="p-image">
                            <div class="p-art p-art-3"></div>
                            <div class="p-overlay">
                                <button class="btn-circle magnetic" onclick="addToCart()">
                                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 5v14M5 12h14"/></svg>
                                </button>
                                <span>Quick View</span>
                            </div>
                        </div>
                        <div class="p-details">
                            <h3>Driftwood</h3>
                            <div class="p-meta">
                                <span>$135.00</span>
                                <span>Salt • Wood</span>
                            </div>
                        </div>
                    </article>
                </div>
            </div>
        </section>

        <!-- Newsletter: Minimalist & Impactful -->
        <section class="newsletter-luxe">
            <div class="container">
                <div class="newsletter-inner glass-panel">
                    <h2>Join the Inner Circle</h2>
                    <p>Receive first access to limited drops and wellness rituals.</p>
                    <form class="nl-form" onsubmit="event.preventDefault();">
                        <div class="input-wrap">
                            <input type="email" placeholder="Email Address" required>
                            <button type="submit" class="submit-arrow">→</button>
                        </div>
                    </form>
                </div>
            </div>
        </section>

    </main>

    <footer class="footer-luxe">
        <div class="container">
            <div class="footer-grid">
                <div>
                    <span class="brand-logo">THE SCENT.</span>
                </div>
                <div class="footer-links">
                    <a href="#">Instagram</a>
                    <a href="#">Pinterest</a>
                    <a href="#">Contact</a>
                </div>
                <div class="copyright">
                    &copy; 2024. Designed with Intention.
                </div>
            </div>
        </div>
    </footer>

    <script src="main.js"></script>
</body>
</html>
```

---

### File 2: styles.css
**Structure:** Advanced CSS variables, noise generation, smooth easing curves, and complex gradient art.

```css
/* ============================================
   1. FOUNDATION & VARIABLES
   ============================================ */
:root {
    /* Palette: Obsidian, Champagne, Deep Moss */
    --color-bg: #F9F8F6;       /* Warm Off-White */
    --color-text: #1A1A1A;     /* Soft Black */
    --color-text-light: #666;  /* Charcoal */
    --color-accent: #D4AF37;   /* Antique Gold */
    --color-moss: #2F3E30;     /* Deep Green */
    --color-clay: #8D6E63;     /* Muted Earth */
    
    /* Glassmorphism */
    --glass-bg: rgba(255, 255, 255, 0.4);
    --glass-border: rgba(255, 255, 255, 0.8);
    --glass-blur: 20px;

    /* Spacing */
    --container-width: 1400px;
    
    /* Typography */
    --font-display: 'Cormorant Garamond', serif;
    --font-body: 'DM Sans', sans-serif;

    /* Easing (The "Apple" feel) */
    --ease-expo: cubic-bezier(0.19, 1, 0.22, 1);
}

*, *::before, *::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

html { scroll-behavior: smooth; }

body {
    font-family: var(--font-body);
    background-color: var(--color-bg);
    color: var(--color-text);
    overflow-x: hidden;
    line-height: 1.6;
    cursor: none; /* We will use a custom cursor logic or just standard for now, but standard is safer for pure CSS */
}

/* Custom Cursor Wrapper (Optional polish) */
body { cursor: default; }

/* ============================================
   2. TEXTURE & ATMOSPHERE
   ============================================ */
.noise-overlay {
    position: fixed;
    top: 0; left: 0; width: 100%; height: 100%;
    pointer-events: none;
    z-index: 9999;
    opacity: 0.04;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E");
}

#spotlight {
    position: fixed;
    width: 600px;
    height: 600px;
    background: radial-gradient(circle, rgba(212, 175, 55, 0.08) 0%, rgba(0,0,0,0) 70%);
    top: 0; left: 0;
    transform: translate(-50%, -50%);
    pointer-events: none;
    z-index: 0;
    transition: opacity 0.3s ease;
}

.container {
    width: 90%;
    max-width: var(--container-width);
    margin: 0 auto;
    position: relative;
    z-index: 1;
}

a { text-decoration: none; color: inherit; transition: color 0.3s ease; }
ul { list-style: none; }
button { cursor: pointer; background: none; border: none; font-family: inherit; }

/* ============================================
   3. TYPOGRAPHY
   ============================================ */
h1, h2, h3 {
    font-family: var(--font-display);
    font-weight: 400;
    line-height: 1.1;
}

.italic { font-style: italic; font-family: var(--font-display); }
.eyebrow {
    font-family: var(--font-body);
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 0.15em;
    margin-bottom: 1.5rem;
    display: block;
    color: var(--color-text-light);
}

/* ============================================
   4. COMPONENT: GLASS & BUTTONS
   ============================================ */
.glass-panel {
    background: var(--glass-bg);
    backdrop-filter: blur(var(--glass-blur));
    -webkit-backdrop-filter: blur(var(--glass-blur));
    border: 1px solid var(--glass-border);
    border-radius: 2px; /* Squircle-ish but sharp */
}

.btn-luxe {
    display: inline-flex;
    align-items: center;
    gap: 1rem;
    background: var(--color-text);
    color: white;
    padding: 1.25rem 2.5rem;
    border-radius: 100px;
    font-family: var(--font-body);
    font-size: 0.9rem;
    letter-spacing: 0.05em;
    transition: transform 0.4s var(--ease-expo), background 0.3s ease;
}

.btn-luxe:hover {
    transform: scale(1.05);
    background: var(--color-moss);
}

.text-link {
    border-bottom: 1px solid var(--color-text);
    padding-bottom: 2px;
    transition: border-color 0.3s ease;
}
.text-link:hover { border-color: transparent; }

/* ============================================
   5. NAVIGATION
   ============================================ */
.nav-layer {
    position: fixed;
    top: 0; left: 0; width: 100%;
    padding: 2rem 0;
    z-index: 100;
    transition: background 0.3s ease, padding 0.3s ease;
}

.nav-layer.scrolled {
    background: rgba(249, 248, 246, 0.85);
    backdrop-filter: blur(15px);
    padding: 1rem 0;
    border-bottom: 1px solid rgba(0,0,0,0.05);
}

.nav-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.brand-logo {
    font-family: var(--font-display);
    font-size: 1.5rem;
    letter-spacing: -0.02em;
    z-index: 101;
}

.nav-links { display: flex; gap: 3rem; }
.nav-link {
    font-size: 0.9rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    position: relative;
}
.nav-link::after {
    content: ''; position: absolute;
    bottom: -5px; left: 0; width: 0%; height: 1px;
    background: var(--color-text);
    transition: width 0.3s var(--ease-expo);
}
.nav-link:hover::after { width: 100%; }

.icon-btn { position: relative; font-size: 1.2rem; }
.cart-indicator {
    position: absolute;
    top: -5px; right: -8px;
    width: 16px; height: 16px;
    background: var(--color-accent);
    color: white;
    border-radius: 50%;
    font-size: 0.6rem;
    display: flex; align-items: center; justify-content: center;
}

/* ============================================
   6. HERO: CINEMATIC
   ============================================ */
.hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    position: relative;
    overflow: hidden;
    padding-top: 80px;
}

.hero-bg {
    position: absolute;
    width: 100%; height: 100%;
    top: 0; left: 0;
    z-index: -1;
}

.orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    opacity: 0.6;
    animation: floatOrb 20s infinite alternate;
}

.orb-1 { top: 20%; right: 10%; width: 40vw; height: 40vw; background: #E8E6E1; }
.orb-2 { bottom: 10%; left: -10%; width: 30vw; height: 30vw; background: #D3DED8; animation-delay: -5s; }
.orb-3 { top: 40%; left: 40%; width: 20vw; height: 20vw; background: #F4E4C1; animation-duration: 25s; }

@keyframes floatOrb {
    0% { transform: translate(0, 0); }
    100% { transform: translate(50px, 30px); }
}

.hero-content {
    display: grid;
    grid-template-columns: 1.2fr 1fr;
    align-items: center;
    gap: 4rem;
}

.hero-title {
    font-size: clamp(4rem, 8vw, 8rem);
    letter-spacing: -0.03em;
    margin-bottom: 2rem;
    line-height: 0.9;
}

.hero-sub {
    font-size: 1.25rem;
    color: var(--color-text-light);
    max-width: 500px;
    margin-bottom: 3rem;
}

/* Hero Visual: CSS Art Bottles */
.hero-visual { position: relative; height: 600px; perspective: 1000px; }

.product-art-container {
    position: relative;
    width: 100%; height: 100%;
    display: flex; justify-content: center; align-items: center;
    transform-style: preserve-3d;
}

.glass-bottle {
    width: 180px; height: 350px;
    background: rgba(255,255,255,0.1);
    border: 1px solid rgba(255,255,255,0.4);
    border-radius: 20px;
    position: absolute;
    backdrop-filter: blur(5px);
    box-shadow: 0 20px 50px rgba(0,0,0,0.1);
    overflow: hidden;
    transition: transform 0.1s ease; /* Parallax */
}

.b-1 { z-index: 2; }
.b-2 { 
    z-index: 1; 
    right: 20%; 
    top: 10%; 
    transform: scale(0.9) rotate(-5deg);
    opacity: 0.7;
}

.liquid {
    position: absolute;
    bottom: 0; left: 0; width: 100%;
    height: 70%;
    background: linear-gradient(180deg, var(--color-moss), #1a251b);
    transition: height 2s ease;
}

.liquid-1 { background: linear-gradient(180deg, #4a5d4a, #2F3E30); }
.liquid-2 { background: linear-gradient(180deg, #a89f91, #5d554b); }

.reflection {
    position: absolute;
    top: 0; left: 10%; width: 10px; height: 100%;
    background: rgba(255,255,255,0.2);
    filter: blur(4px);
}

.label {
    position: absolute;
    top: 45%; left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    color: rgba(255,255,255,0.9);
}
.label span:first-child { font-size: 0.8rem; display: block; margin-bottom: 5px; opacity: 0.7; }
.label span:last-child { font-family: var(--font-display); font-size: 1.2rem; }

.floating-leaf {
    position: absolute;
    font-size: 3rem;
    filter: drop-shadow(0 10px 10px rgba(0,0,0,0.1));
    animation: floatLeaf 6s infinite ease-in-out;
}

.l-1 { top: 10%; left: 0; animation-delay: 0s; }
.l-2 { bottom: 20%; right: 0; animation-delay: 2s; }

@keyframes floatLeaf {
    0%, 100% { transform: translateY(0) rotate(0deg); }
    50% { transform: translateY(-20px) rotate(10deg); }
}

/* ============================================
   7. MARQUEE: INFINITE RHYTHM
   ============================================ */
.marquee-section {
    padding: 4rem 0;
    border-top: 1px solid rgba(0,0,0,0.05);
    border-bottom: 1px solid rgba(0,0,0,0.05);
    overflow: hidden;
    white-space: nowrap;
}

.marquee-track {
    display: inline-block;
    animation: marquee 30s linear infinite;
}

.marquee-track span {
    font-family: var(--font-display);
    font-size: 3rem;
    color: rgba(0,0,0,0.1);
    margin: 0 2rem;
    font-style: italic;
}

@keyframes marquee {
    0% { transform: translateX(0); }
    100% { transform: translateX(-50%); }
}

/* ============================================
   8. PHILOSOPHY: SCROLLYTELLING
   ============================================ */
.philosophy { padding: 8rem 0; }

.phil-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
}

.sticky-col {
    position: sticky;
    top: 150px;
    height: fit-content;
}

.phil-text h2 { font-size: 3.5rem; margin-bottom: 2rem; }
.phil-text p { margin-bottom: 1.5rem; font-size: 1.1rem; color: var(--color-text-light); }

.phil-images { display: flex; flex-direction: column; gap: 2rem; }

.art-card {
    height: 300px;
    border-radius: 4px;
    position: relative;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
}

/* CSS Abstract Art for Cards */
.art-1 { background: #E0E5E0; }
.art-2 { background: #F2EBE5; }
.art-3 { background: #DFD6CE; }

.art-content h3 { font-size: 2rem; color: var(--color-text); opacity: 0.2; transition: opacity 0.3s; }
.art-card:hover .art-content h3 { opacity: 1; }

/* ============================================
   9. COLLECTION: LUXE GRID
   ============================================ */
.collection { padding: 6rem 0; background: white; }
.col-header { display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 4rem; }
.col-header h2 { font-size: 3rem; }

.filters button {
    font-family: var(--font-body);
    font-size: 0.9rem;
    margin-left: 2rem;
    opacity: 0.4;
    transition: opacity 0.3s;
}
.filters button.active { opacity: 1; }
.filters button:hover { opacity: 1; }

.product-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 2rem;
}

.luxe-card { group: 'card'; }

.p-image {
    height: 450px;
    background: #f4f4f4;
    position: relative;
    overflow: hidden;
    border-radius: 4px;
    margin-bottom: 1.5rem;
    transition: transform 0.5s var(--ease-expo);
}

.luxe-card:hover .p-image { transform: translateY(-5px); }

/* CSS Art for Products */
.p-art { width: 100%; height: 100%; transition: transform 0.6s var(--ease-expo); }
.luxe-card:hover .p-art { transform: scale(1.05); }

.p-art-1 { background: linear-gradient(135deg, #2F3E30 0%, #1a251b 100%); }
.p-art-2 { background: linear-gradient(135deg, #D4AF37 0%, #8c7320 100%); }
.p-art-3 { background: linear-gradient(135deg, #607D8B 0%, #37474F 100%); }

.p-overlay {
    position: absolute;
    bottom: 0; left: 0; width: 100%;
    background: rgba(255,255,255,0.95);
    padding: 1.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    transform: translateY(100%);
    transition: transform 0.4s var(--ease-expo);
}

.luxe-card:hover .p-overlay { transform: translateY(0); }

.btn-circle {
    width: 45px; height: 45px;
    border-radius: 50%;
    background: var(--color-text);
    color: white;
    display: flex; align-items: center; justify-content: center;
    transition: transform 0.3s ease;
}
.btn-circle:hover { transform: rotate(90deg); background: var(--color-accent); }

.p-details h3 { font-size: 1.5rem; margin-bottom: 0.5rem; }
.p-meta { display: flex; justify-content: space-between; color: var(--color-text-light); font-size: 0.9rem; }

/* ============================================
   10. NEWSLETTER & FOOTER
   ============================================ */
.newsletter-luxe { padding: 6rem 0; }

.newsletter-inner {
    padding: 4rem;
    text-align: center;
    max-width: 800px;
    margin: 0 auto;
}
.newsletter-inner h2 { font-size: 2.5rem; margin-bottom: 1rem; }

.nl-form { max-width: 400px; margin: 2rem auto 0; position: relative; }
.input-wrap { position: relative; }
.nl-form input {
    width: 100%;
    padding: 1rem 0;
    border: none;
    border-bottom: 1px solid var(--color-text);
    background: transparent;
    font-size: 1.1rem;
    font-family: var(--font-body);
    outline: none;
}
.submit-arrow {
    position: absolute;
    right: 0; top: 1rem;
    font-size: 1.5rem;
    background: none;
}

.footer-luxe { padding: 3rem 0; border-top: 1px solid rgba(0,0,0,0.1); }
.footer-grid { display: flex; justify-content: space-between; align-items: center; }
.footer-links a { margin-left: 2rem; font-size: 0.9rem; opacity: 0.7; }
.footer-links a:hover { opacity: 1; }

/* ============================================
   11. RESPONSIVE
   ============================================ */
@media (max-width: 900px) {
    .hero-content { grid-template-columns: 1fr; text-align: center; }
    .hero-visual { height: 400px; }
    .phil-grid { grid-template-columns: 1fr; }
    .sticky-col { position: relative; top: 0; }
    .nav-links { display: none; } /* Simplified for demo, implies hamburger */
    .marquee-section span { font-size: 2rem; }
}
```

---

### File 3: main.js
**Logic:** Enhanced interactivity. Mouse tracking for the spotlight, magnetic button effects, and smooth intersection observers.

```javascript
document.addEventListener('DOMContentLoaded', () => {
    
    // --- 1. The Spotlight Effect (Mouse Tracking) ---
    const spotlight = document.getElementById('spotlight');
    
    document.addEventListener('mousemove', (e) => {
        const x = e.clientX;
        const y = e.clientY;
        
        // Update spotlight position
        spotlight.style.left = `${x}px`;
        spotlight.style.top = `${y}px`;
        
        // Subtle parallax for hero bottles
        const moveX = (window.innerWidth / 2 - x) * 0.01;
        const moveY = (window.innerHeight / 2 - y) * 0.01;
        
        const bottle = document.querySelector('.b-1');
        if(bottle) {
            bottle.style.transform = `translate(${moveX}px, ${moveY}px)`;
        }
    });

    // --- 2. Magnetic Buttons (Premium Feel) ---
    const magneticBtns = document.querySelectorAll('.magnetic');
    
    magneticBtns.forEach(btn => {
        btn.addEventListener('mousemove', (e) => {
            const rect = btn.getBoundingClientRect();
            const x = e.clientX - rect.left - rect.width / 2;
            const y = e.clientY - rect.top - rect.height / 2;
            
            // Move button slightly towards cursor
            btn.style.transform = `translate(${x * 0.2}px, ${y * 0.2}px)`;
        });
        
        btn.addEventListener('mouseleave', () => {
            btn.style.transform = 'translate(0, 0)';
        });
    });

    // --- 3. Smooth Scroll & Sticky Nav ---
    const nav = document.querySelector('.nav-layer');
    
    window.addEventListener('scroll', () => {
        if (window.scrollY > 50) {
            nav.classList.add('scrolled');
        } else {
            nav.classList.remove('scrolled');
        }
    });

    // --- 4. Intersection Observer for Scroll Animations ---
    const observerOptions = {
        threshold: 0.1,
        rootMargin: "0px"
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('animate-in');
                // Optional: Unobserve after animation
                // observer.unobserve(entry.target);
            }
        });
    }, observerOptions);

    // Apply fade-up animation classes dynamically
    const animateElements = document.querySelectorAll('.phil-text, .art-card, .luxe-card, .newsletter-inner');
    
    animateElements.forEach(el => {
        el.style.opacity = '0';
        el.style.transform = 'translateY(30px)';
        el.style.transition = 'opacity 0.8s ease, transform 0.8s ease';
        observer.observe(el);
    });

    // Define the class to trigger animation
    const styleSheet = document.createElement("style");
    styleSheet.innerText = `
        .animate-in {
            opacity: 1 !important;
            transform: translateY(0) !important;
        }
    `;
    document.head.appendChild(styleSheet);

});

// --- 5. Cart Interaction ---
window.addToCart = function() {
    const btn = document.querySelector('.cart-indicator');
    let count = parseInt(btn.innerText);
    
    // Animation
    btn.style.transform = 'scale(1.5)';
    btn.style.background = '#D4AF37'; // Gold flash
    
    setTimeout(() => {
        btn.innerText = count + 1;
        btn.style.transform = 'scale(1)';
        btn.style.background = '#1A1A1A'; // Back to black
    }, 200);
}
```
