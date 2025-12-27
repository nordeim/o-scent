

Here is the re-imagined "The Scent" experience. I have stripped away the generic builder artifacts and rebuilt the architecture using a bespoke, component-based approach.

### Design Direction & Rationale
*   **Visual Language:** I moved towards a "Ethereal Botanical" aesthetic. Instead of flat blocks, we use **Glass-morphism** (frosted glass) to create depth between the floating elements and the animated gradient background.
*   **Typography:** `Playfair Display` is used for emotional impact (headings), while `Inter` ensures readability for UI elements and body text.
*   **Motion:** I implemented an **Intersection Observer** system in the JavaScript to trigger `fade-up` and `stagger` animations as the user scrolls, making the page feel alive.
*   **Color Palette:**
    *   *Backgrounds:* `var(--color-bg-cream)` and `var(--color-bg-sage)`.
    *   *Accents:* `var(--color-gold)` for CTAs.
    *   *Glass:* High transparency with blur for the header and cards.

---

### File 1: index.html
**Structure:** Semantic HTML5. Clean DOM tree. No dependency on external CSS/JS files other than the ones specified.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="The Scent - Artisan Aromatherapy & Wellness Essentials. Handcrafted in small batches.">
    <title>The Scent | Artisan Aromatherapy</title>
    
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&display=swap" rel="stylesheet">
    
    <!-- Styles -->
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <!-- Skip Link for Accessibility -->
    <a href="#main-content" class="skip-link">Skip to content</a>

    <!-- Announcement Bar -->
    <div class="announcement-bar">
        <p>Free shipping on orders over $75 — Summer Collection now live</p>
    </div>

    <!-- Header -->
    <header class="header" id="header">
        <div class="container header__inner">
            <!-- Mobile Menu Toggle -->
            <button class="mobile-toggle" aria-label="Toggle Navigation" id="mobileToggle">
                <span></span>
                <span></span>
                <span></span>
            </button>

            <!-- Logo -->
            <a href="#" class="logo">
                <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M20 6C20 6 8 16 8 24C8 29.5228 12.4772 34 18 34C23.5228 34 28 29.5228 28 24C28 16 20 6 20 6Z" fill="currentColor" fill-opacity="0.2"/>
                    <path d="M20 10C20 10 11 18 11 24C11 27.866 14.134 31 18 31C21.866 31 25 27.866 25 24C25 18 20 10 20 10Z" stroke="currentColor" stroke-width="2"/>
                </svg>
                <span class="logo-text">The Scent</span>
            </a>

            <!-- Desktop Nav -->
            <nav class="nav desktop-only">
                <ul class="nav__list">
                    <li><a href="#about" class="nav__link">Philosophy</a></li>
                    <li><a href="#collection" class="nav__link">Collection</a></li>
                    <li><a href="#rituals" class="nav__link">Rituals</a></li>
                    <li><a href="#contact" class="nav__link">Journal</a></li>
                </ul>
            </nav>

            <!-- Icons -->
            <div class="header__actions">
                <button class="icon-btn" aria-label="Search">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line></svg>
                </button>
                <button class="icon-btn" aria-label="Cart">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M6 2L3 6v14a2 2 0 002 2h14a2 2 0 002-2V6l-3-4z"></path><line x1="3" y1="6" x2="21" y2="6"></line><path d="M16 10a4 4 0 01-8 0"></path></svg>
                    <span class="cart-count">0</span>
                </button>
            </div>
        </div>
    </header>

    <main id="main-content">
        
        <!-- Hero Section -->
        <section class="hero">
            <div class="hero-bg-gradient"></div>
            <div class="container hero__container">
                <div class="hero__content">
                    <span class="tag animate-fade-up">New Arrival</span>
                    <h1 class="hero__title animate-fade-up">
                        Nature's Alchemy <br> <em>For the Soul</em>
                    </h1>
                    <p class="hero__text animate-fade-up">
                        Discover our small-batch essential oils and botanical blends designed to restore balance and elevate your daily rituals.
                    </p>
                    <div class="hero__cta animate-fade-up">
                        <a href="#collection" class="btn btn--primary">Shop Collection</a>
                        <a href="#about" class="btn btn--glass">Watch Story</a>
                    </div>
                </div>
                
                <!-- Visual Composition (CSS/SVG Art) -->
                <div class="hero__visual animate-scale-in">
                    <!-- Abstract Blobs -->
                    <div class="blob blob-1"></div>
                    <div class="blob blob-2"></div>
                    
                    <!-- Stylized Bottle SVG -->
                    <svg class="hero-bottle" viewBox="0 0 200 400" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <!-- Liquid -->
                        <path d="M40 180H160L155 380C155 390.5 146.5 399 136 399H64C53.5 399 45 390.5 45 380L40 180Z" fill="url(#liquidGradient)"/>
                        <!-- Glass Body -->
                        <path d="M30 180H170C170 180 165 150 150 120H50C35 150 30 180 30 180Z" stroke="currentColor" stroke-width="2" fill="white" fill-opacity="0.1"/>
                        <!-- Cap -->
                        <rect x="70" y="50" width="60" height="70" rx="4" fill="currentColor" fill-opacity="0.9"/>
                        <!-- Label -->
                        <rect x="60" y="220" width="80" height="120" rx="2" fill="white" fill-opacity="0.8"/>
                        <text x="100" y="280" font-family="Playfair Display" font-size="14" text-anchor="middle" fill="#333">SERENITY</text>
                        
                        <defs>
                            <linearGradient id="liquidGradient" x1="100" y1="180" x2="100" y2="399" gradientUnits="userSpaceOnUse">
                                <stop stop-color="#8FBC8F" stop-opacity="0.8"/>
                                <stop offset="1" stop-color="#2F4F4F" stop-opacity="0.9"/>
                            </linearGradient>
                        </defs>
                    </svg>

                    <!-- Floating Leaf -->
                    <div class="floating-element leaf" style="top: 10%; left: -20px;">🌿</div>
                    <div class="floating-element sparkle" style="bottom: 20%; right: -10px;">✨</div>
                </div>
            </div>
        </section>

        <!-- Features/Philosophy -->
        <section id="about" class="features">
            <div class="container">
                <div class="section-header">
                    <span class="section-label">Our Philosophy</span>
                    <h2>Pure. Potent. <em>Purposeful.</em></h2>
                </div>
                
                <div class="features-grid">
                    <article class="card card--glass feature-card">
                        <div class="icon-box">
                            <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
                        </div>
                        <h3>Organic Sourcing</h3>
                        <p>We partner directly with sustainable farms to ensure the highest vibrational quality of every plant.</p>
                    </article>
                    
                    <article class="card card--glass feature-card">
                        <div class="icon-box">
                            <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="12" r="10"/><path d="M8 14s1.5 2 4 2 4-2 4-2"/><line x1="9" y1="9" x2="9.01" y2="9"/><line x1="15" y1="9" x2="15.01" y2="9"/></svg>
                        </div>
                        <h3>Cruelty Free</h3>
                        <p>Our commitment to wellness extends to every living being. Never tested on animals, always kind.</p>
                    </article>
                    
                    <article class="card card--glass feature-card">
                        <div class="icon-box">
                            <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M20.84 4.61a5.5 5.5 0 00-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 00-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 000-7.78z"/></svg>
                        </div>
                        <h3>Small Batch</h3>
                        <p>Hand-poured in limited quantities to guarantee freshness and potency in every bottle.</p>
                    </article>
                </div>
            </div>
        </section>

        <!-- Product Collection -->
        <section id="collection" class="products">
            <div class="container">
                <div class="products-header">
                    <div class="section-header">
                        <span class="section-label">Curated Essentials</span>
                        <h2>The Collection</h2>
                    </div>
                    
                    <!-- Filter Controls -->
                    <div class="filters">
                        <button class="filter-btn active" data-filter="all">All</button>
                        <button class="filter-btn" data-filter="oil">Oils</button>
                        <button class="filter-btn" data-filter="mist">Mists</button>
                        <button class="filter-btn" data-filter="kit">Ritual Kits</button>
                    </div>
                </div>

                <div class="product-grid">
                    <!-- Product 1 -->
                    <article class="product-card" data-category="oil">
                        <div class="product-image-wrapper">
                            <div class="product-img" style="background: #E8F0E9;"></div>
                            <span class="badge">Bestseller</span>
                            <button class="btn-icon-float" aria-label="Add to wishlist">♡</button>
                            <button class="add-cart-btn" onclick="addToCart()">Add to Cart</button>
                        </div>
                        <div class="product-info">
                            <h3>Forest Bath</h3>
                            <p class="product-desc">Cedarwood, Pine, Balsam</p>
                            <div class="product-footer">
                                <span class="price">$42.00</span>
                                <div class="rating">★★★★★</div>
                            </div>
                        </div>
                    </article>

                    <!-- Product 2 -->
                    <article class="product-card" data-category="mist">
                        <div class="product-image-wrapper">
                            <div class="product-img" style="background: #FDF2E9;"></div>
                            <button class="btn-icon-float" aria-label="Add to wishlist">♡</button>
                            <button class="add-cart-btn" onclick="addToCart()">Add to Cart</button>
                        </div>
                        <div class="product-info">
                            <h3>Linen Mist</h3>
                            <p class="product-desc">Lavender, Chamomile</p>
                            <div class="product-footer">
                                <span class="price">$28.00</span>
                                <div class="rating">★★★★☆</div>
                            </div>
                        </div>
                    </article>

                    <!-- Product 3 -->
                    <article class="product-card" data-category="oil">
                        <div class="product-image-wrapper">
                            <div class="product-img" style="background: #E6E6FA;"></div>
                            <span class="badge">New</span>
                            <button class="btn-icon-float" aria-label="Add to wishlist">♡</button>
                            <button class="add-cart-btn" onclick="addToCart()">Add to Cart</button>
                        </div>
                        <div class="product-info">
                            <h3>Clarity Blend</h3>
                            <p class="product-desc">Rosemary, Lemon, Peppermint</p>
                            <div class="product-footer">
                                <span class="price">$36.00</span>
                                <div class="rating">★★★★★</div>
                            </div>
                        </div>
                    </article>

                    <!-- Product 4 -->
                    <article class="product-card" data-category="kit">
                        <div class="product-image-wrapper">
                            <div class="product-img" style="background: #FAF9F6;"></div>
                            <button class="btn-icon-float" aria-label="Add to wishlist">♡</button>
                            <button class="add-cart-btn" onclick="addToCart()">Add to Cart</button>
                        </div>
                        <div class="product-info">
                            <h3>Travel Ritual Set</h3>
                            <p class="product-desc">3 x 5ml Oils + Roller</p>
                            <div class="product-footer">
                                <span class="price">$55.00</span>
                                <div class="rating">★★★★★</div>
                            </div>
                        </div>
                    </article>
                </div>
                
                <div class="text-center" style="margin-top: 3rem;">
                    <a href="#" class="btn btn--outline">View All Products</a>
                </div>
            </div>
        </section>

        <!-- Testimonials -->
        <section id="rituals" class="testimonials">
            <div class="container">
                <div class="testimonial-wrapper">
                    <div class="testimonial-content glass-panel">
                        <svg class="quote-icon" width="48" height="48" viewBox="0 0 24 24" fill="currentColor"><path d="M14.017 21v-7.391c0-5.704 3.731-9.57 8.983-10.609l.995 2.151c-2.432.917-3.995 3.638-3.995 5.849h4v10h-9.983zm-14.017 0v-7.391c0-5.704 3.748-9.57 9-10.609l.996 2.151c-2.433.917-3.996 3.638-3.996 5.849h3.983v10h-9.983z"/></svg>
                        <p class="testimonial-text">"I've never experienced aromatherapy quite like this. The Forest Bath oil feels like stepping into an ancient grove. It grounds me instantly."</p>
                        <div class="author">
                            <strong>Elena R.</strong>
                            <span>Verified Buyer</span>
                        </div>
                    </div>
                    <!-- Decorative Side Elements -->
                    <div class="testimonial-deco">
                        <div class="circle"></div>
                        <div class="circle small"></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Newsletter -->
        <section id="contact" class="newsletter">
            <div class="container">
                <div class="newsletter-box">
                    <div class="newsletter-content">
                        <h2>Join the Ritual</h2>
                        <p>Receive 10% off your first order and weekly wellness wisdom.</p>
                        <form class="newsletter-form" onsubmit="event.preventDefault(); showToast('Subscribed successfully!');">
                            <div class="input-group">
                                <input type="email" placeholder="Your email address" required>
                                <button type="submit" class="btn btn--primary">Join</button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <div class="footer-grid">
                <div class="footer-brand">
                    <span class="logo-text">The Scent.</span>
                    <p>Harnessing the power of nature for modern wellbeing.</p>
                </div>
                <div class="footer-links">
                    <h4>Shop</h4>
                    <ul>
                        <li><a href="#">Essential Oils</a></li>
                        <li><a href="#">Blends</a></li>
                        <li><a href="#">Gift Cards</a></li>
                    </ul>
                </div>
                <div class="footer-links">
                    <h4>Company</h4>
                    <ul>
                        <li><a href="#">About</a></li>
                        <li><a href="#">Sustainability</a></li>
                        <li><a href="#">Contact</a></li>
                    </ul>
                </div>
                <div class="footer-links">
                    <h4>Follow</h4>
                    <ul>
                        <li><a href="#">Instagram</a></li>
                        <li><a href="#">Pinterest</a></li>
                        <li><a href="#">Twitter</a></li>
                    </ul>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2023 The Scent. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <!-- Toast Notification -->
    <div class="toast" id="toast">
        <span id="toast-message">Item added to cart</span>
    </div>

    <!-- Back to top -->
    <button class="back-to-top" id="backToTop" aria-label="Back to top">↑</button>

    <script src="main.js"></script>
</body>
</html>
```

---

### File 2: styles.css
**Structure:** Custom Properties (Variables) for easy theming. Modern CSS Reset. Flexbox/Grid layouts. Glassmorphism utility classes. Animations.

```css
/* ============================================
   1. Variables & Reset
   ============================================ */
:root {
    /* Palette: Organic, Earthy, Soft */
    --color-bg-cream: #FAF9F6;
    --color-bg-sage: #E8F0E9;
    --color-text-main: #2C3E2D; /* Warm Charcoal Green */
    --color-text-light: #5D6D5E;
    --color-primary: #556B2F; /* Dark Olive/Sage */
    --color-accent: #D4AF37; /* Muted Gold */
    --color-glass: rgba(255, 255, 255, 0.65);
    --color-glass-border: rgba(255, 255, 255, 0.9);
    --shadow-sm: 0 4px 6px rgba(0,0,0,0.02);
    --shadow-lg: 0 20px 40px rgba(0,0,0,0.05);
    --shadow-float: 0 10px 30px rgba(85, 107, 47, 0.15);

    /* Typography */
    --font-serif: 'Playfair Display', serif;
    --font-sans: 'Inter', sans-serif;

    /* Spacing */
    --container-width: 1200px;
    --spacing-xs: 0.5rem;
    --spacing-sm: 1rem;
    --spacing-md: 2rem;
    --spacing-lg: 4rem;
    --spacing-xl: 8rem;
    
    /* Transitions */
    --ease-out: cubic-bezier(0.215, 0.61, 0.355, 1);
}

*, *::before, *::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

html {
    scroll-behavior: smooth;
}

body {
    font-family: var(--font-sans);
    background-color: var(--color-bg-cream);
    color: var(--color-text-main);
    line-height: 1.6;
    overflow-x: hidden;
    -webkit-font-smoothing: antialiased;
}

img { max-width: 100%; display: block; }
a { text-decoration: none; color: inherit; transition: color 0.3s ease; }
ul { list-style: none; }
button { cursor: pointer; border: none; background: none; font-family: inherit; }

/* ============================================
   2. Utilities & Layout
   ============================================ */
.container {
    width: 90%;
    max-width: var(--container-width);
    margin: 0 auto;
    padding: 0 var(--spacing-sm);
}

.text-center { text-align: center; }

/* Glassmorphism Effect */
.glass-panel {
    background: var(--color-glass);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border: 1px solid var(--color-glass-border);
    border-radius: 20px;
}

/* ============================================
   3. Typography
   ============================================ */
h1, h2, h3, h4 {
    font-family: var(--font-serif);
    font-weight: 400;
    line-height: 1.2;
    color: var(--color-text-main);
}

em { font-style: italic; color: var(--color-primary); }

.section-label {
    text-transform: uppercase;
    letter-spacing: 2px;
    font-size: 0.75rem;
    color: var(--color-accent);
    display: block;
    margin-bottom: var(--spacing-xs);
}

/* ============================================
   4. Components: Buttons
   ============================================ */
.btn {
    display: inline-flex;
    align-items: center;
    padding: 1rem 2rem;
    border-radius: 50px;
    font-weight: 500;
    font-size: 0.9rem;
    transition: all 0.4s var(--ease-out);
    position: relative;
    overflow: hidden;
}

.btn--primary {
    background: var(--color-text-main);
    color: white;
}

.btn--primary:hover {
    background: var(--color-primary);
    transform: translateY(-2px);
    box-shadow: var(--shadow-float);
}

.btn--glass {
    background: rgba(255,255,255,0.4);
    border: 1px solid var(--color-text-main);
    color: var(--color-text-main);
}

.btn--glass:hover {
    background: var(--color-text-main);
    color: white;
}

.btn--outline {
    border: 1px solid var(--color-text-main);
    padding: 0.8rem 2rem;
    border-radius: 4px;
}

.btn--outline:hover {
    background: var(--color-text-main);
    color: white;
}

/* ============================================
   5. Header & Nav
   ============================================ */
.announcement-bar {
    background: var(--color-text-main);
    color: white;
    text-align: center;
    padding: 0.5rem;
    font-size: 0.8rem;
    letter-spacing: 0.5px;
}

.header {
    position: fixed;
    top: 30px; /* Below announcement */
    left: 0;
    width: 100%;
    z-index: 1000;
    padding: 1.5rem 0;
    transition: all 0.4s ease;
}

.header.scrolled {
    top: 0;
    padding: 1rem 0;
    background: rgba(250, 249, 246, 0.85);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid rgba(0,0,0,0.05);
}

.header__inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-family: var(--font-serif);
    font-size: 1.5rem;
    color: var(--color-text-main);
}

.nav__list { display: flex; gap: 2rem; }
.nav__link { font-size: 0.95rem; position: relative; }
.nav__link::after {
    content: '';
    position: absolute;
    width: 0;
    height: 1px;
    bottom: -4px;
    left: 0;
    background: var(--color-primary);
    transition: width 0.3s ease;
}
.nav__link:hover::after { width: 100%; }

.header__actions { display: flex; gap: 1rem; align-items: center; }
.icon-btn { position: relative; }
.cart-count {
    position: absolute;
    top: -5px;
    right: -8px;
    background: var(--color-accent);
    color: white;
    font-size: 0.6rem;
    width: 16px;
    height: 16px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.mobile-toggle { display: none; flex-direction: column; gap: 5px; }
.mobile-toggle span { width: 25px; height: 2px; background: var(--color-text-main); transition: 0.3s; }

/* ============================================
   6. Hero Section
   ============================================ */
.hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    position: relative;
    overflow: hidden;
    padding-top: 80px;
}

.hero-bg-gradient {
    position: absolute;
    top: 0; right: 0;
    width: 50%;
    height: 100%;
    background: radial-gradient(circle at 70% 30%, var(--color-bg-sage), transparent 60%);
    z-index: -1;
    opacity: 0.6;
    animation: pulse 10s infinite alternate;
}

.hero__container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    align-items: center;
    gap: var(--spacing-lg);
}

.hero__title {
    font-size: clamp(3rem, 5vw, 5rem);
    margin-bottom: var(--spacing-sm);
    line-height: 1.1;
}

.hero__text {
    font-size: 1.1rem;
    color: var(--color-text-light);
    margin-bottom: var(--spacing-md);
    max-width: 450px;
}

.hero__cta { display: flex; gap: 1rem; }

.hero__visual {
    position: relative;
    height: 500px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.hero-bottle {
    height: 100%;
    filter: drop-shadow(0 20px 30px rgba(0,0,0,0.15));
    animation: float 6s ease-in-out infinite;
    z-index: 2;
}

.blob {
    position: absolute;
    border-radius: 50%;
    filter: blur(60px);
    z-index: 1;
}
.blob-1 { width: 300px; height: 300px; background: rgba(212, 175, 55, 0.2); top: 20%; left: 10%; }
.blob-2 { width: 200px; height: 200px; background: rgba(85, 107, 47, 0.2); bottom: 10%; right: 10%; }

.floating-element {
    position: absolute;
    font-size: 2rem;
    z-index: 3;
    animation: floatDelayed 5s ease-in-out infinite;
}

/* ============================================
   7. Features
   ============================================ */
.features { padding: var(--spacing-xl) 0; }
.section-header { margin-bottom: var(--spacing-lg); max-width: 600px; }
.section-header h2 { font-size: 2.5rem; }

.features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: var(--spacing-md);
}

.card {
    padding: var(--spacing-md);
    transition: transform 0.4s var(--ease-out), box-shadow 0.4s ease;
}

.card:hover {
    transform: translateY(-10px);
    box-shadow: var(--shadow-lg);
}

.icon-box {
    width: 50px; height: 50px;
    background: var(--color-bg-sage);
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--color-primary);
    margin-bottom: 1.5rem;
}

.card h3 { margin-bottom: 1rem; font-size: 1.25rem; }
.card p { color: var(--color-text-light); font-size: 0.95rem; }

/* ============================================
   8. Products
   ============================================ */
.products { padding: var(--spacing-xl) 0; background: white; }

.products-header {
    display: flex;
    justify-content: space-between;
    align-items: end;
    margin-bottom: var(--spacing-lg);
    flex-wrap: wrap;
    gap: 2rem;
}

.filters { display: flex; gap: 1rem; }
.filter-btn {
    font-family: var(--font-sans);
    font-size: 0.9rem;
    color: var(--color-text-light);
    padding-bottom: 5px;
    position: relative;
}
.filter-btn.active { color: var(--color-text-main); font-weight: 600; }
.filter-btn.active::after {
    content: ''; position: absolute; bottom: 0; left: 0; width: 100%; height: 2px; background: var(--color-primary);
}

.product-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 2rem;
}

.product-card {
    background: white;
    transition: all 0.3s ease;
}
.product-card:hover { transform: translateY(-5px); }

.product-image-wrapper {
    position: relative;
    height: 320px;
    border-radius: 12px;
    overflow: hidden;
    margin-bottom: 1rem;
    background: #f0f0f0;
}

.product-img {
    width: 100%; height: 100%;
    transition: transform 0.6s ease;
}
.product-card:hover .product-img { transform: scale(1.05); }

.badge {
    position: absolute;
    top: 10px; left: 10px;
    background: white;
    padding: 4px 10px;
    font-size: 0.7rem;
    border-radius: 20px;
    z-index: 2;
}

.btn-icon-float {
    position: absolute;
    top: 10px; right: 10px;
    width: 32px; height: 32px;
    background: white;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transform: translateY(10px);
    transition: all 0.3s ease;
    z-index: 2;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}
.product-card:hover .btn-icon-float { opacity: 1; transform: translateY(0); }

.add-cart-btn {
    position: absolute;
    bottom: 10px; left: 10px; right: 10px;
    background: rgba(44, 62, 45, 0.9);
    color: white;
    padding: 12px;
    border-radius: 8px;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.3s ease;
    z-index: 2;
    text-align: center;
}
.product-card:hover .add-cart-btn { opacity: 1; transform: translateY(0); }

.product-info h3 { font-size: 1.1rem; margin-bottom: 0.2rem; }
.product-desc { font-size: 0.85rem; color: var(--color-text-light); margin-bottom: 0.5rem; }
.product-footer { display: flex; justify-content: space-between; align-items: center; }
.price { font-weight: 600; font-family: var(--font-serif); font-size: 1.1rem; }
.rating { color: var(--color-accent); font-size: 0.9rem; }

/* ============================================
   9. Testimonials & Misc
   ============================================ */
.testimonials { padding: var(--spacing-xl) 0; background: var(--color-bg-sage); }
.testimonial-wrapper {
    max-width: 800px;
    margin: 0 auto;
    position: relative;
}
.testimonial-content {
    padding: var(--spacing-lg);
    text-align: center;
}
.quote-icon { color: var(--color-primary); opacity: 0.3; margin-bottom: 1rem; }
.testimonial-text {
    font-family: var(--font-serif);
    font-size: 1.5rem;
    font-style: italic;
    margin-bottom: 2rem;
}
.author strong { display: block; font-family: var(--font-sans); font-size: 0.9rem; }
.author span { font-size: 0.8rem; color: var(--color-text-light); }

.testimonial-deco { display: none; } /* Hidden on mobile */

/* Newsletter */
.newsletter { padding: var(--spacing-xl) 0; }
.newsletter-box {
    background: var(--color-text-main);
    color: white;
    border-radius: 20px;
    padding: var(--spacing-lg);
    text-align: center;
}
.newsletter-box h2 { color: white; margin-bottom: 1rem; }
.newsletter-box p { opacity: 0.8; margin-bottom: 2rem; }

.newsletter-form { max-width: 500px; margin: 0 auto; }
.input-group {
    display: flex;
    background: rgba(255,255,255,0.1);
    border: 1px solid rgba(255,255,255,0.2);
    padding: 5px;
    border-radius: 50px;
}
.input-group input {
    flex: 1;
    background: transparent;
    border: none;
    padding: 1rem 1.5rem;
    color: white;
    outline: none;
}
.input-group input::placeholder { color: rgba(255,255,255,0.6); }
.input-group .btn { padding: 0.8rem 2rem; border-radius: 40px; }

/* Footer */
.footer { background: white; padding: var(--spacing-lg) 0; border-top: 1px solid #eee; }
.footer-grid {
    display: grid;
    grid-template-columns: 1.5fr 1fr 1fr 1fr;
    gap: 2rem;
    margin-bottom: 3rem;
}
.footer-brand p { margin-top: 1rem; color: var(--color-text-light); font-size: 0.9rem; max-width: 250px; }
.footer-links h4 { font-family: var(--font-sans); font-size: 0.9rem; text-transform: uppercase; margin-bottom: 1.5rem; letter-spacing: 1px; }
.footer-links li { margin-bottom: 0.8rem; }
.footer-links a { color: var(--color-text-light); font-size: 0.9rem; }
.footer-links a:hover { color: var(--color-primary); }
.footer-bottom {
    text-align: center;
    border-top: 1px solid #eee;
    padding-top: 2rem;
    font-size: 0.8rem;
    color: #999;
}

/* Back to Top & Toast */
.back-to-top {
    position: fixed;
    bottom: 30px;
    right: 30px;
    width: 45px; height: 45px;
    background: var(--color-primary);
    color: white;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    pointer-events: none;
    transition: all 0.3s ease;
    z-index: 900;
}
.back-to-top.visible { opacity: 1; pointer-events: all; }

.toast {
    position: fixed;
    bottom: 30px;
    left: 50%;
    transform: translateX(-50%) translateY(50px);
    background: var(--color-text-main);
    color: white;
    padding: 12px 24px;
    border-radius: 50px;
    font-size: 0.9rem;
    opacity: 0;
    transition: all 0.4s ease;
    z-index: 2000;
    box-shadow: 0 10px 20px rgba(0,0,0,0.2);
}
.toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }

/* ============================================
   10. Animations
   ============================================ */
@keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-15px); }
}
@keyframes floatDelayed {
    0%, 100% { transform: translateY(0) rotate(0deg); }
    50% { transform: translateY(-10px) rotate(5deg); }
}
@keyframes pulse {
    0% { opacity: 0.5; transform: scale(1); }
    100% { opacity: 0.8; transform: scale(1.1); }
}

/* Scroll Animation Classes */
.animate-on-scroll {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.8s ease-out, transform 0.8s ease-out;
}
.animate-on-scroll.is-visible {
    opacity: 1;
    transform: translateY(0);
}

/* Stagger delays */
.animate-fade-up { transition-delay: 0.1s; }
.animate-scale-in { transition-delay: 0.3s; }

/* ============================================
   11. Responsive
   ============================================ */
@media (min-width: 768px) {
    .testimonial-deco {
        display: block;
        position: absolute;
        right: -100px;
        top: 50%;
        transform: translateY(-50%);
    }
    .circle {
        width: 200px; height: 200px;
        border-radius: 50%;
        background: var(--color-accent);
        opacity: 0.2;
    }
    .circle.small {
        width: 100px; height: 100px;
        position: absolute;
        top: -50px; right: 50px;
        background: var(--color-primary);
    }
}

@media (max-width: 768px) {
    .mobile-toggle { display: flex; z-index: 1001; }
    
    .nav {
        position: fixed;
        top: 0; left: 0;
        width: 100%; height: 100vh;
        background: var(--color-bg-cream);
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        transform: translateX(100%);
        transition: transform 0.4s ease;
    }
    .nav.active { transform: translateX(0); }
    .nav__list { flex-direction: column; text-align: center; gap: 2rem; }
    .nav__link { font-size: 1.5rem; }

    .hero__container { grid-template-columns: 1fr; text-align: center; }
    .hero__text { margin: 0 auto 2rem; }
    .hero__cta { justify-content: center; }
    .hero__visual { height: 350px; margin-top: 2rem; }

    .products-header { flex-direction: column; align-items: flex-start; }
    
    .footer-grid { grid-template-columns: 1fr 1fr; }
}
```

---

### File 3: main.js
**Logic:** Vanilla JavaScript. No heavy frameworks.
1.  **Intersection Observer:** Handles the scroll animations (`animate-on-scroll`).
2.  **Sticky Header:** Toggles the glass effect on scroll.
3.  **Mobile Menu:** Smooth toggling with class manipulation.
4.  **Filtering:** Simple category filtering for products.
5.  **Cart/Toast:** Feedback mechanisms.

```javascript
document.addEventListener('DOMContentLoaded', () => {
    
    // --- 1. Header Scroll Effect ---
    const header = document.getElementById('header');
    const announcementHeight = document.querySelector('.announcement-bar').offsetHeight;
    
    // Adjust initial position
    header.style.top = `${announcementHeight}px`;

    window.addEventListener('scroll', () => {
        if (window.scrollY > 50) {
            header.classList.add('scrolled');
            header.style.top = '0px'; // Snap to top when scrolled
        } else {
            header.classList.remove('scrolled');
            header.style.top = `${announcementHeight}px`;
        }
    });

    // --- 2. Mobile Menu Toggle ---
    const mobileToggle = document.getElementById('mobileToggle');
    const nav = document.querySelector('.nav');
    const mobileLinks = document.querySelectorAll('.nav__link');

    mobileToggle.addEventListener('click', () => {
        nav.classList.toggle('active');
        
        // Animate hamburger lines if desired (optional visual cue)
        const spans = mobileToggle.querySelectorAll('span');
        if (nav.classList.contains('active')) {
            spans[0].style.transform = 'rotate(45deg) translate(5px, 5px)';
            spans[1].style.opacity = '0';
            spans[2].style.transform = 'rotate(-45deg) translate(5px, -5px)';
        } else {
            spans[0].style.transform = 'none';
            spans[1].style.opacity = '1';
            spans[2].style.transform = 'none';
        }
    });

    // Close mobile menu when a link is clicked
    mobileLinks.forEach(link => {
        link.addEventListener('click', () => {
            nav.classList.remove('active');
            // Reset hamburger
            const spans = mobileToggle.querySelectorAll('span');
            spans[0].style.transform = 'none';
            spans[1].style.opacity = '1';
            spans[2].style.transform = 'none';
        });
    });

    // --- 3. Scroll Animations (Intersection Observer) ---
    const observerOptions = {
        threshold: 0.1,
        rootMargin: "0px 0px -50px 0px"
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('is-visible');
                observer.unobserve(entry.target); // Only animate once
            }
        });
    }, observerOptions);

    const scrollElements = document.querySelectorAll('.animate-on-scroll, .card, .product-card');
    scrollElements.forEach(el => {
        el.classList.add('animate-on-scroll');
        observer.observe(el);
    });

    // --- 4. Product Filtering ---
    const filterBtns = document.querySelectorAll('.filter-btn');
    const productCards = document.querySelectorAll('.product-card');

    filterBtns.forEach(btn => {
        btn.addEventListener('click', () => {
            // Remove active class from all
            filterBtns.forEach(b => b.classList.remove('active'));
            btn.classList.add('active');

            const filterValue = btn.getAttribute('data-filter');

            productCards.forEach(card => {
                const category = card.getAttribute('data-category');
                if (filterValue === 'all' || filterValue === category) {
                    card.style.display = 'block';
                    setTimeout(() => card.style.opacity = '1', 10); // Fade in
                } else {
                    card.style.display = 'none';
                    card.style.opacity = '0';
                }
            });
        });
    });

    // --- 5. Back to Top Button ---
    const backToTop = document.getElementById('backToTop');

    window.addEventListener('scroll', () => {
        if (window.scrollY > 500) {
            backToTop.classList.add('visible');
        } else {
            backToTop.classList.remove('visible');
        }
    });

    backToTop.addEventListener('click', () => {
        window.scrollTo({
            top: 0,
            behavior: 'smooth'
        });
    });

});

// --- 6. Cart & Toast Interactions ---
let cartCount = 0;
const cartCountEl = document.querySelector('.cart-count');

// Global function for onclick in HTML
window.addToCart = function() {
    cartCount++;
    cartCountEl.textContent = cartCount;
    
    // Bump animation
    cartCountEl.style.transform = 'scale(1.2)';
    setTimeout(() => cartCountEl.style.transform = 'scale(1)', 200);

    showToast('Added to your ritual bag');
}

window.showToast = function(message) {
    const toast = document.getElementById('toast');
    const toastMsg = document.getElementById('toast-message');
    
    toastMsg.textContent = message;
    toast.classList.add('show');
    
    setTimeout(() => {
        toast.classList.remove('show');
    }, 3000);
}
```
