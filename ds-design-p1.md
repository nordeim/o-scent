# **PHASE 1: DEEP ANALYSIS & RENEWED VISION**

## **Critical Self-Assessment**

You're absolutely right. While the previous "laboratory aesthetic" was distinctive, I now realize it wasn't *breathtaking* or *gorgeous* enough. It was intellectual and precise, but not emotionally resonant or visually sublime. I need to think deeper—beyond clever concepts to genuine beauty.

## **Root Problem Analysis:**
1. **Monospace fonts** feel clinical, not luxurious
2. **Slate/Brass palette** is thoughtful but not emotionally warm
3. **Laboratory metaphor** prioritizes intellect over sensuality
4. **Missing that "wow" factor** that makes screenshots get saved

## **New Design Philosophy: "Sensual Alchemy"**

Instead of a sterile laboratory, imagine a **16th-century alchemist's studio at golden hour**—where science meets art, where precision becomes poetry. The aesthetic should feel like discovering a Renaissance master's private workshop: illuminated manuscripts, hand-ground pigments, brass instruments catching firelight, parchment aging to honey tones.

## **The Transformation Principles:**

### **1. TYPOGRAPHY REVOLUTION**
**Old:** IBM Plex Mono (sterile) + Cormorant (elegant but expected)
**New:** **Bespoke pairings that feel discovered, not chosen:**

- **Display Font:** "**Goudy Old Style**" variant or "**Mrs Eaves**" — That perfect Renaissance elegance with delicate flourishes
- **Body Font:** "**Adobe Garamond Pro**" or "**EB Garamond**" — The quintessential book typeface, warm and infinitely readable
- **Accent Font:** "**Bickham Script Pro**" for occasional calligraphic flourishes

*But wait—Google Fonts can't provide these premium fonts.*  
**Solution:** We'll use the most luxurious Google Fonts that capture this essence:

**New Google Fonts Stack:**
- **Headings:** `Cormorant Garamond` (with `font-weight: 300` for that delicate, Renaissance feel)
- **Body:** `Crimson Pro` (the most book-like, warm serif on Google Fonts)
- **Accent:** `Great Vibes` or `Dancing Script` for calligraphic moments

### **2. COLOR PALETTE REINVENTION**
**Old:** Slate/Brass (cool precision)  
**New:** **"Illuminated Manuscript" palette:**

- **Primary:** `#2A2D26` (Deep Charcoal with green undertone — like old ink)
- **Secondary:** `#C9A769` (Warm Gold — gilded manuscript edges)
- **Tertiary:** `#7C6354` (Aged Parchment — natural, warm brown)
- **Accent 1:** `#9A8C6D` (Oxidized Bronze)
- **Accent 2:** `#B87D7D` (Dried Rose — botanical reference)
- **Background:** `#FAF8F5` (Cream Vellum)
- **Highlight:** `#E8D8B6` (Raw Silk)

### **3. VISUAL METAPHOR SHIFT**
From "Laboratory" to **"Alchemist's Atelier"**:
- Not sterile glass but **hand-blown vessels**
- Not molecular diagrams but **illuminated botanical illustrations**
- Not chrome but **patinated brass and oxidized copper**
- Not grid paper but **hand-ruled parchment**

### **4. MOTION & LIGHTING**
- **Golden hour lighting** with soft shadows
- **Parchment texture** that's almost tactile
- **Hand-drawn illustrations** that appear as if being drawn in real-time
- **Gilded elements** that catch virtual light
- **Feather quill writing** animations for headings

---

## **PHASE 2: EXECUTION PLAN**

### **File 1: index.html (Redesigned)**
Complete structural overhaul with new semantic sections and bespoke decorative elements.

### **File 2: styles.css (Reimagined)**
Complete rewrite with:
- New font stack and typographic scale
- Complete color system overhaul
- Custom SVG illustrations and patterns
- Sophisticated animation system
- Texture overlays and lighting effects

### **File 3: main.js (Enhanced)**
- New illustration drawing animations
- Sophisticated scroll-triggered reveals
- Parallax lighting effects
- Interactive manuscript elements

---

# **IMPLEMENTATION**

## **File 1: index.html**
*Complete transformation into "Alchemist's Atelier" aesthetic*

```html
<!DOCTYPE html>
<html lang="en" class="no-js">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Aromatherapy elevated to artisanal alchemy. Handcrafted botanical essences from our atelier, where ancient wisdom meets modern sensibility.">
  
  <!-- Open Graph -->
  <meta property="og:type" content="website">
  <meta property="og:title" content="Atelier Arôme | Artisanal Alchemy for the Senses">
  <meta property="og:description" content="Where botanical science becomes sensory poetry. Experience our handcrafted aromatic compounds.">
  <meta property="og:image" content="/social-preview.jpg">
  
  <title>Atelier Arôme | Artisanal Alchemy for the Senses</title>
  
  <!-- Google Fonts - Luxurious Renaissance Pairing -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;0,700;1,300;1,400;1,500&family=Crimson+Pro:ital,wght@0,300;0,400;0,500;0,600;0,700;1,300;1,400&family=Great+Vibes&family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400&display=swap" rel="stylesheet">
  
  <!-- Styles -->
  <link rel="stylesheet" href="styles.css">
  
  <!-- Favicon - Alchemical Symbol -->
  <link rel="icon" type="image/svg+xml" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><path d='M50 20 L80 50 L50 80 L20 50 Z' fill='%23C9A769' stroke='%232A2D26' stroke-width='2'/><circle cx='50' cy='50' r='15' fill='%232A2D26'/></svg>">
  
  <!-- Theme Color -->
  <meta name="theme-color" content="#2A2D26">
  
  <!-- Modern CSS Features Detection -->
  <script>
    document.documentElement.classList.remove('no-js');
    document.documentElement.classList.add('js');
  </script>
</head>
<body>
  <!-- Parchment Texture Overlay -->
  <div class="texture-overlay" aria-hidden="true"></div>
  
  <!-- Gold Leaf Accents -->
  <div class="gold-leaf gold-leaf--1" aria-hidden="true"></div>
  <div class="gold-leaf gold-leaf--2" aria-hidden="true"></div>
  <div class="gold-leaf gold-leaf--3" aria-hidden="true"></div>
  
  <!-- Skip Navigation -->
  <a href="#main-content" class="skip-link">Skip to main content</a>
  
  <!-- Atelier Hours Banner -->
  <div class="atelier-banner" role="banner">
    <div class="atelier-banner__container">
      <span class="atelier-banner__icon" aria-hidden="true">✷</span>
      <span class="atelier-banner__text">The Atelier is Open</span>
      <span class="atelier-banner__subtext">Current Batch: <em>N° 724 • Lavandula × intermedia</em></span>
      <span class="atelier-banner__icon" aria-hidden="true">✷</span>
    </div>
  </div>
  
  <!-- Header - Atelier Studio -->
  <header class="header" id="header">
    <div class="header__container">
      <!-- Atelier Seal -->
      <a href="#hero" class="header__seal" aria-label="Atelier Arôme - Home">
        <div class="header__seal-inner">
          <svg class="header__seal-svg" viewBox="0 0 100 100" aria-hidden="true">
            <circle cx="50" cy="50" r="48" fill="none" stroke="currentColor" stroke-width="1" stroke-dasharray="2,2"/>
            <path d="M50 20 Q70 30 80 50 Q70 70 50 80 Q30 70 20 50 Q30 30 50 20 Z" fill="none" stroke="currentColor" stroke-width="1.5"/>
            <circle cx="50" cy="50" r="15" fill="none" stroke="currentColor" stroke-width="1"/>
            <path d="M50 35 L50 65 M35 50 L65 50" stroke="currentColor" stroke-width="1.5"/>
          </svg>
          <div class="header__seal-text">
            <span class="header__seal-name">Atelier</span>
            <span class="header__seal-name">Arôme</span>
          </div>
        </div>
        <span class="header__seal-tagline">Est. 2024</span>
      </a>
      
      <!-- Navigation - Atelier Sections -->
      <nav class="header__nav" aria-label="Atelier navigation">
        <ul class="header__nav-list">
          <li class="header__nav-item">
            <a href="#compounds" class="header__nav-link">
              <span class="header__nav-number">— I —</span>
              <span class="header__nav-label">Compendium</span>
            </a>
          </li>
          <li class="header__nav-item">
            <a href="#process" class="header__nav-link">
              <span class="header__nav-number">— II —</span>
              <span class="header__nav-label">Alchemy</span>
            </a>
          </li>
          <li class="header__nav-item">
            <a href="#atelier" class="header__nav-link">
              <span class="header__nav-number">— III —</span>
              <span class="header__nav-label">The Atelier</span>
            </a>
          </li>
          <li class="header__nav-item">
            <a href="#manuscript" class="header__nav-link">
              <span class="header__nav-number">— IV —</span>
              <span class="header__nav-label">Manuscript</span>
            </a>
          </li>
        </ul>
      </nav>
      
      <!-- Atelier Tools -->
      <div class="header__tools">
        <button class="header__tool" aria-label="Search the compendium" data-tooltip="Magnifying Glass">
          <svg class="header__tool-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
            <circle cx="11" cy="11" r="8"/>
            <path d="M21 21l-4.35-4.35"/>
          </svg>
        </button>
        
        <button class="header__tool" id="cartButton" aria-label="Collection Vial" data-count="0" data-tooltip="Vial">
          <svg class="header__tool-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
            <path d="M6 2L3 6v14a2 2 0 002 2h14a2 2 0 002-2V6l-3-4z"/>
            <path d="M3 6h18"/>
            <path d="M16 10a4 4 0 01-8 0"/>
          </svg>
        </button>
        
        <!-- Mobile Menu Toggle - Quill Pen -->
        <button class="header__menu-toggle" id="menuToggle" aria-label="Open atelier menu" aria-expanded="false" data-tooltip="Menu">
          <span class="header__menu-quill"></span>
        </button>
      </div>
    </div>
    
    <!-- Mobile Navigation - Manuscript Pages -->
    <nav class="mobile-nav" id="mobileNav" aria-label="Mobile navigation" aria-hidden="true">
      <div class="mobile-nav__container">
        <div class="mobile-nav__header">
          <div class="mobile-nav__seal" aria-hidden="true"></div>
          <span class="mobile-nav__title">Atelier Folio</span>
        </div>
        
        <ul class="mobile-nav__list">
          <li class="mobile-nav__item">
            <a href="#compounds" class="mobile-nav__link">
              <span class="mobile-nav__ornament">❖</span>
              <span class="mobile-nav__label">Compendium</span>
              <span class="mobile-nav__page">Folio I</span>
            </a>
          </li>
          <li class="mobile-nav__item">
            <a href="#process" class="mobile-nav__link">
              <span class="mobile-nav__ornament">❖</span>
              <span class="mobile-nav__label">Alchemy</span>
              <span class="mobile-nav__page">Folio II</span>
            </a>
          </li>
          <li class="mobile-nav__item">
            <a href="#atelier" class="mobile-nav__link">
              <span class="mobile-nav__ornament">❖</span>
              <span class="mobile-nav__label">The Atelier</span>
              <span class="mobile-nav__page">Folio III</span>
            </a>
          </li>
          <li class="mobile-nav__item">
            <a href="#manuscript" class="mobile-nav__link">
              <span class="mobile-nav__ornament">❖</span>
              <span class="mobile-nav__label">Manuscript</span>
              <span class="mobile-nav__page">Folio IV</span>
            </a>
          </li>
        </ul>
        
        <div class="mobile-nav__colophon">
          <span class="mobile-nav__colophon-text">Atelier Arôme</span>
          <span class="mobile-nav__colophon-year">Anno MMXXIV</span>
        </div>
      </div>
    </nav>
  </header>
  
  <!-- Main Content -->
  <main id="main-content">
    
    <!-- Hero Section - Illuminated Manuscript -->
    <section class="hero" id="hero">
      <!-- Hand-drawn Border -->
      <div class="hero__border" aria-hidden="true">
        <div class="hero__border-corner hero__border-corner--tl"></div>
        <div class="hero__border-corner hero__border-corner--tr"></div>
        <div class="hero__border-corner hero__border-corner--bl"></div>
        <div class="hero__border-corner hero__border-corner--br"></div>
      </div>
      
      <!-- Watermark Illustration -->
      <div class="hero__watermark" aria-hidden="true">
        <svg class="hero__watermark-svg" viewBox="0 0 400 400">
          <path d="M200 100 Q300 150 300 250 Q250 350 200 350 Q150 350 100 250 Q100 150 200 100 Z" fill="none" stroke="currentColor" stroke-width="2" opacity="0.1"/>
          <path d="M200 120 Q280 160 280 240 Q240 320 200 320 Q160 320 120 240 Q120 160 200 120 Z" fill="none" stroke="currentColor" stroke-width="1" opacity="0.08"/>
        </svg>
      </div>
      
      <div class="hero__container">
        <!-- Illuminated Initial -->
        <div class="hero__initial" aria-hidden="true">
          <span class="hero__initial-letter">A</span>
          <div class="hero__initial-flourish"></div>
        </div>
        
        <div class="hero__content">
          <!-- Calligraphic Title -->
          <h1 class="hero__title">
            <span class="hero__title-line hero__title-line--1">
              <span class="hero__title-word">The</span>
              <span class="hero__title-word">Art</span>
            </span>
            <span class="hero__title-line hero__title-line--2">
              <span class="hero__title-word">of</span>
              <span class="hero__title-word hero__title-word--emph">Scent</span>
            </span>
            <span class="hero__title-line hero__title-line--3">
              <span class="hero__title-word">as</span>
              <span class="hero__title-word">Alchemy</span>
            </span>
          </h1>
          
          <!-- Subtitle with Flourish -->
          <div class="hero__subtitle">
            <div class="hero__subtitle-flourish hero__subtitle-flourish--left"></div>
            <span class="hero__subtitle-text">Where Botany Becomes Poetry</span>
            <div class="hero__subtitle-flourish hero__subtitle-flourish--right"></div>
          </div>
          
          <!-- Manuscript Excerpt -->
          <div class="hero__excerpt">
            <p class="hero__excerpt-text">
              Within our atelier, time slows to the rhythm of distillation. Each botanical is treated as a verse in nature's manuscript, its essence carefully extracted and preserved. Our practice honors the ancient alchemical tradition—transforming raw botanical matter into olfactory gold through patience, precision, and profound respect for the natural world.
            </p>
            <div class="hero__excerpt-rule"></div>
            <cite class="hero__excerpt-citation">— Master Perfumer's Journal</cite>
          </div>
          
          <!-- Atelier Actions -->
          <div class="hero__actions">
            <a href="#compounds" class="btn btn--primary" data-hover-text="Explore the Compendium">
              <span class="btn__text">Enter the Atelier</span>
              <svg class="btn__icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                <path d="M5 12h14M12 5l7 7-7 7"/>
              </svg>
            </a>
            <a href="#process" class="btn btn--secondary" data-hover-text="Witness the Alchemy">
              <span class="btn__text">Our Alchemy</span>
              <span class="btn__ornament">❧</span>
            </a>
          </div>
          
          <!-- Atelier Credentials -->
          <div class="hero__credentials">
            <div class="hero__credential">
              <span class="hero__credential-number">72</span>
              <span class="hero__credential-label">Hour Distillation</span>
            </div>
            <div class="hero__credential">
              <span class="hero__credential-number">∞</span>
              <span class="hero__credential-label">Patience</span>
            </div>
            <div class="hero__credential">
              <span class="hero__credential-number">100%</span>
              <span class="hero__credential-label">Artisanal</span>
            </div>
          </div>
        </div>
        
        <!-- Hero Visual - Hand-blown Vessel -->
        <div class="hero__visual">
          <div class="hero__vessel-container">
            <!-- Vessel -->
            <div class="hero__vessel">
              <div class="hero__vessel-neck"></div>
              <div class="hero__vessel-body">
                <div class="hero__vessel-liquid">
                  <div class="vessel__meniscus"></div>
                  <div class="vessel__reflection"></div>
                </div>
                <div class="hero__vessel-label">
                  <span class="vessel-label__n">N°</span>
                  <span class="vessel-label__number">724</span>
                </div>
              </div>
              <div class="hero__vessel-base"></div>
            </div>
            
            <!-- Vessel Stand -->
            <div class="hero__vessel-stand"></div>
            
            <!-- Botanical Specimens -->
            <div class="hero__botanicals">
              <div class="hero__botanical hero__botanical--lavender">
                <div class="botanical__stem"></div>
                <div class="botanical__blossom"></div>
              </div>
              <div class="hero__botanical hero__botanical--rose">
                <div class="botanical__stem"></div>
                <div class="botanical__petals"></div>
              </div>
              <div class="hero__botanical hero__botanical--eucalyptus">
                <div class="botanical__stem"></div>
                <div class="botanical__leaves"></div>
              </div>
            </div>
          </div>
          
          <!-- Alchemical Symbol -->
          <div class="hero__symbol" aria-hidden="true">
            <svg class="hero__symbol-svg" viewBox="0 0 100 100">
              <circle cx="50" cy="50" r="40" fill="none" stroke="currentColor" stroke-width="1" stroke-dasharray="1,2"/>
              <path d="M50 20 L80 50 L50 80 L20 50 Z" fill="none" stroke="currentColor" stroke-width="2"/>
              <circle cx="50" cy="50" r="15" fill="none" stroke="currentColor" stroke-width="1.5"/>
            </svg>
          </div>
        </div>
      </div>
      
      <!-- Scroll Indicator - Quill -->
      <div class="hero__scroll-indicator">
        <div class="scroll-indicator__quill">
          <div class="quill__nib"></div>
          <div class="quill__shaft"></div>
          <div class="quill__feather"></div>
        </div>
        <span class="scroll-indicator__label">Continue Reading</span>
      </div>
    </section>
    
    <!-- Compounds Section - Botanical Compendium -->
    <section class="compendium" id="compounds">
      <!-- Section Border -->
      <div class="section-border" aria-hidden="true">
        <span class="section-border__ornament">❦</span>
      </div>
      
      <div class="compendium__container">
        <!-- Compendium Header -->
        <div class="compendium__header">
          <span class="section-label">First Folio</span>
          <h2 class="section-title">
            <span class="section-title__line">The Botanical</span>
            <span class="section-title__line section-title__line--emph">Compendium</span>
          </h2>
          <div class="compendium__rule"></div>
          <p class="section-description">
            A curated collection of botanical essences, each documented with the care of an illuminated manuscript. These are not merely scents, but captured moments of nature's poetry.
          </p>
        </div>
        
        <!-- Botanical Filter - Renaissance Style -->
        <div class="compendium__filters">
          <div class="compendium__filter-group">
            <div class="compendium__filter-label">Filter by Humour:</div>
            <div class="compendium__filter-buttons">
              <button class="compendium__filter" data-filter="all" aria-pressed="true">
                <span class="compendium__filter-text">All Essences</span>
                <span class="compendium__filter-ornament">✦</span>
              </button>
              <button class="compendium__filter" data-filter="calming">
                <span class="compendium__filter-text">Calming</span>
                <span class="compendium__filter-icon">☾</span>
              </button>
              <button class="compendium__filter" data-filter="uplifting">
                <span class="compendium__filter-text">Uplifting</span>
                <span class="compendium__filter-icon">☀</span>
              </button>
              <button class="compendium__filter" data-filter="grounding">
                <span class="compendium__filter-text">Grounding</span>
                <span class="compendium__filter-icon">♁</span>
              </button>
              <button class="compendium__filter" data-filter="clarifying">
                <span class="compendium__filter-text">Clarifying</span>
                <span class="compendium__filter-icon">☁</span>
              </button>
            </div>
          </div>
          
          <!-- Manuscript Sort -->
          <div class="compendium__sort">
            <select class="compendium__sort-select" aria-label="Sort compendium">
              <option value="folio">Folio Order</option>
              <option value="humour">By Humour</option>
              <option value="rarity">By Rarity</option>
              <option value="season">By Season</option>
            </select>
            <div class="compendium__sort-ornament"></div>
          </div>
        </div>
        
        <!-- Botanical Cards - Illuminated Style -->
        <div class="compendium__grid">
          <!-- Essence 1 - Featured -->
          <article class="essence-card essence-card--featured" data-humour="calming" data-rarity="rare" data-season="spring">
            <div class="essence-card__illumination">
              <!-- Hand-drawn Botanical Illustration -->
              <div class="essence-card__illustration">
                <svg class="essence-card__botanical-svg" viewBox="0 0 200 200" aria-hidden="true">
                  <!-- Lavender stem and flowers -->
                  <path d="M100 180 L100 80" stroke="currentColor" stroke-width="3" stroke-linecap="round"/>
                  <g transform="translate(100 60)">
                    <circle cx="0" cy="0" r="8" fill="currentColor" opacity="0.6"/>
                    <circle cx="15" cy="-10" r="6" fill="currentColor" opacity="0.5"/>
                    <circle cx="-15" cy="-10" r="6" fill="currentColor" opacity="0.5"/>
                    <circle cx="0" cy="-20" r="5" fill="currentColor" opacity="0.4"/>
                  </g>
                </svg>
              </div>
              
              <!-- Gold Leaf Number -->
              <div class="essence-card__folio">
                <span class="essence-card__folio-number">I</span>
              </div>
              
              <!-- Rarity Badge -->
              <div class="essence-card__badge" aria-label="Rare essence">
                <span class="essence-card__badge-text">Rare</span>
                <div class="essence-card__badge-ornament"></div>
              </div>
            </div>
            
            <div class="essence-card__content">
              <!-- Latin Name with Calligraphy -->
              <div class="essence-card__latin">
                <span class="essence-card__latin-name">Lavandula × intermedia</span>
                <div class="essence-card__latin-rule"></div>
              </div>
              
              <!-- Common Name -->
              <h3 class="essence-card__title">Provence Lavender</h3>
              
              <!-- Humour Symbol -->
              <div class="essence-card__humour">
                <span class="essence-card__humour-icon" aria-label="Calming essence">☾</span>
                <span class="essence-card__humour-label">Calming</span>
              </div>
              
              <!-- Description -->
              <p class="essence-card__description">
                Harvested at dawn in the Provençal hills, this lavender possesses a sweetness found only in blossoms kissed by the morning's first light. Its effect is one of profound calm, like the silence between breaths.
              </p>
              
              <!-- Season & Notes -->
              <div class="essence-card__notes">
                <div class="essence-card__note">
                  <span class="essence-card__note-label">Season</span>
                  <span class="essence-card__note-value">Early Summer</span>
                </div>
                <div class="essence-card__note">
                  <span class="essence-card__note-label">Notes</span>
                  <span class="essence-card__note-value">Floral • Herbaceous • Sweet</span>
                </div>
                <div class="essence-card__note">
                  <span class="essence-card__note-label">Extraction</span>
                  <span class="essence-card__note-value">Steam Distillation</span>
                </div>
              </div>
              
              <!-- Footer with Price and Action -->
              <div class="essence-card__footer">
                <div class="essence-card__pricing">
                  <span class="essence-card__price">$42</span>
                  <span class="essence-card__measure">per 5ml phial</span>
                </div>
                <button class="essence-card__action" aria-label="Add Provence Lavender to collection">
                  <svg class="essence-card__action-icon" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                    <path d="M12 5v14M5 12h14"/>
                  </svg>
                  <span class="essence-card__action-text">To Vial</span>
                </button>
              </div>
            </div>
          </article>
          
          <!-- Additional essence cards would follow similar structure -->
          <!-- Essence 2 -->
          <article class="essence-card" data-humour="clarifying" data-rarity="common" data-season="autumn">
            <div class="essence-card__illumination">
              <div class="essence-card__illustration">
                <!-- Eucalyptus illustration -->
              </div>
              <div class="essence-card__folio">
                <span class="essence-card__folio-number">II</span>
              </div>
            </div>
            
            <div class="essence-card__content">
              <div class="essence-card__latin">
                <span class="essence-card__latin-name">Eucalyptus globulus</span>
                <div class="essence-card__latin-rule"></div>
              </div>
              <h3 class="essence-card__title">Tasmanian Eucalyptus</h3>
              <div class="essence-card__humour">
                <span class="essence-card__humour-icon" aria-label="Clarifying essence">☁</span>
                <span class="essence-card__humour-label">Clarifying</span>
              </div>
              <p class="essence-card__description">
                The crisp, clean scent of Tasmania's ancient forests. This essence clears the mind as morning mist clears from mountain valleys.
              </p>
              <div class="essence-card__notes">
                <div class="essence-card__note">
                  <span class="essence-card__note-label">Season</span>
                  <span class="essence-card__note-value">Autumn</span>
                </div>
                <div class="essence-card__note">
                  <span class="essence-card__note-label">Notes</span>
                  <span class="essence-card__note-value">Camphorous • Fresh • Clean</span>
                </div>
              </div>
              <div class="essence-card__footer">
                <div class="essence-card__pricing">
                  <span class="essence-card__price">$36</span>
                  <span class="essence-card__measure">per 5ml phial</span>
                </div>
                <button class="essence-card__action" aria-label="Add Tasmanian Eucalyptus to collection">
                  <svg class="essence-card__action-icon" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                    <path d="M12 5v14M5 12h14"/>
                  </svg>
                  <span class="essence-card__action-text">To Vial</span>
                </button>
              </div>
            </div>
          </article>
          
          <!-- Essence 3 -->
          <article class="essence-card" data-humour="uplifting" data-rarity="limited" data-season="spring">
            <div class="essence-card__illumination">
              <div class="essence-card__illustration">
                <!-- Bergamot illustration -->
              </div>
              <div class="essence-card__folio">
                <span class="essence-card__folio-number">III</span>
              </div>
              <div class="essence-card__badge" aria-label="Limited edition">
                <span class="essence-card__badge-text">Limited</span>
              </div>
            </div>
            
            <div class="essence-card__content">
              <div class="essence-card__latin">
                <span class="essence-card__latin-name">Citrus bergamia</span>
                <div class="essence-card__latin-rule"></div>
              </div>
              <h3 class="essence-card__title">Calabrian Bergamot</h3>
              <div class="essence-card__humour">
                <span class="essence-card__humour-icon" aria-label="Uplifting essence">☀</span>
                <span class="essence-card__humour-label">Uplifting</span>
              </div>
              <p class="essence-card__description">
                From Italy's sun-drenched Calabrian coast, this essence captures the joyful brightness of citrus groves at harvest. A note of pure sunlight.
              </p>
              <div class="essence-card__notes">
                <div class="essence-card__note">
                  <span class="essence-card__note-label">Season</span>
                  <span class="essence-card__note-value">Late Winter</span>
                </div>
                <div class="essence-card__note">
                  <span class="essence-card__note-label">Notes</span>
                  <span class="essence-card__note-value">Citrus • Bright • Spicy</span>
                </div>
              </div>
              <div class="essence-card__footer">
                <div class="essence-card__pricing">
                  <span class="essence-card__price">$48</span>
                  <span class="essence-card__measure">per 5ml phial</span>
                </div>
                <button class="essence-card__action" aria-label="Add Calabrian Bergamot to collection">
                  <svg class="essence-card__action-icon" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                    <path d="M12 5v14M5 12h14"/>
                  </svg>
                  <span class="essence-card__action-text">To Vial</span>
                </button>
              </div>
            </div>
          </article>
          
          <!-- Additional cards... -->
        </div>
        
        <!-- Compendium Footer -->
        <div class="compendium__footer">
          <div class="compendium__counter">
            <span class="compendium__counter-current">3</span>
            <span class="compendium__counter-separator">of</span>
            <span class="compendium__counter-total">12</span>
            <span class="compendium__counter-label">Essences Documented</span>
          </div>
          <button class="btn btn--outline" id="loadMoreEssences">
            <span class="btn__text">Continue Reading</span>
            <svg class="btn__icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M5 12h14M12 5l7 7-7 7"/>
            </svg>
          </button>
        </div>
      </div>
    </section>
    
    <!-- Process Section - The Alchemy -->
    <section class="alchemy" id="process">
      <!-- Watermark -->
      <div class="alchemy__watermark" aria-hidden="true">
        <span class="alchemy__watermark-text">Ars Magna</span>
      </div>
      
      <div class="alchemy__container">
        <div class="alchemy__header">
          <span class="section-label">Second Folio</span>
          <h2 class="section-title">
            <span class="section-title__line">The Art of</span>
            <span class="section-title__line section-title__line--emph">Alchemical Transformation</span>
          </h2>
          <div class="alchemy__rule"></div>
          <p class="section-description">
            Our practice follows the ancient alchemical principle: solve et coagula. To dissolve and reconstitute. To transform base botanical matter into olfactory gold through time, heat, and intention.
          </p>
        </div>
        
        <!-- Alchemical Process Steps -->
        <div class="alchemy__process">
          <!-- Step 1 -->
          <article class="alchemy-step">
            <div class="alchemy-step__number">
              <span class="alchemy-step__roman">I</span>
            </div>
            <div class="alchemy-step__content">
              <h3 class="alchemy-step__title">Nigredo • The Blackening</h3>
              <p class="alchemy-step__description">
                The raw botanical material undergoes its initial transformation through careful drying and preparation. This stage represents the dissolution of the material's original form, a necessary darkness before illumination.
              </p>
              <div class="alchemy-step__details">
                <div class="alchemy-step__detail">
                  <span class="alchemy-step__detail-label">Duration</span>
                  <span class="alchemy-step__detail-value">7-14 Days</span>
                </div>
                <div class="alchemy-step__detail">
                  <span class="alchemy-step__detail-label">Temperature</span>
                  <span class="alchemy-step__detail-value">Ambient</span>
                </div>
              </div>
            </div>
            <div class="alchemy-step__symbol" aria-hidden="true">♁</div>
          </article>
          
          <!-- Step 2 -->
          <article class="alchemy-step">
            <div class="alchemy-step__number">
              <span class="alchemy-step__roman">II</span>
            </div>
            <div class="alchemy-step__content">
              <h3 class="alchemy-step__title">Albedo • The Whitening</h3>
              <p class="alchemy-step__description">
                Through gentle steam distillation at precisely 40°C, the volatile aromatic compounds are released. This careful extraction preserves the most delicate notes that higher temperatures would destroy.
              </p>
              <div class="alchemy-step__details">
                <div class="alchemy-step__detail">
                  <span class="alchemy-step__detail-label">Duration</span>
                  <span class="alchemy-step__detail-value">72 Hours</span>
                </div>
                <div class="alchemy-step__detail">
                  <span class="alchemy-step__detail-label">Temperature</span>
                  <span class="alchemy-step__detail-value">40°C ±0.1</span>
                </div>
              </div>
            </div>
            <div class="alchemy-step__symbol" aria-hidden="true">☁</div>
          </article>
          
          <!-- Step 3 -->
          <article class="alchemy-step">
            <div class="alchemy-step__number">
              <span class="alchemy-step__roman">III</span>
            </div>
            <div class="alchemy-step__content">
              <h3 class="alchemy-step__title">Citrinitas • The Yellowing</h3>
              <p class="alchemy-step__description">
                The separated essential oil undergoes a period of maturation in hand-blown glass vessels. During this stage, the aromatic profile deepens and complexifies, much like wine aging in oak barrels.
              </p>
              <div class="alchemy-step__details">
                <div class="alchemy-step__detail">
                  <span class="alchemy-step__detail-label">Duration</span>
                  <span class="alchemy-step__detail-value">30-90 Days</span>
                </div>
                <div class="alchemy-step__detail">
                  <span class="alchemy-step__detail-label">Vessel</span>
                  <span class="alchemy-step__detail-value">Hand-blown Glass</span>
                </div>
              </div>
            </div>
            <div class="alchemy-step__symbol" aria-hidden="true">☀</div>
          </article>
          
          <!-- Step 4 -->
          <article class="alchemy-step">
            <div class="alchemy-step__number">
              <span class="alchemy-step__roman">IV</span>
            </div>
            <div class="alchemy-step__content">
              <h3 class="alchemy-step__title">Rubedo • The Reddening</h3>
              <p class="alchemy-step__description">
                The final essence is evaluated, filtered, and bottled by hand. Each phial receives our wax seal, marking the completion of the transformation from raw botanical to perfected essence.
              </p>
              <div class="alchemy-step__details">
                <div class="alchemy-step__detail">
                  <span class="alchemy-step__detail-label">Process</span>
                  <span class="alchemy-step__detail-value">Hand-bottling</span>
                </div>
                <div class="alchemy-step__detail">
                  <span class="alchemy-step__detail-label">Seal</span>
                  <span class="alchemy-step__detail-value">Beeswax</span>
                </div>
              </div>
            </div>
            <div class="alchemy-step__symbol" aria-hidden="true">❤</div>
          </article>
        </div>
        
        <!-- Alchemical Apparatus -->
        <div class="alchemy__apparatus">
          <div class="apparatus__item apparatus__item--still">
            <div class="apparatus__illustration"></div>
            <div class="apparatus__caption">Copper Alembic Still</div>
          </div>
          <div class="apparatus__item apparatus__item--vessel">
            <div class="apparatus__illustration"></div>
            <div class="apparatus__caption">Maturation Vessels</div>
          </div>
          <div class="apparatus__item apparatus__item--tools">
            <div class="apparatus__illustration"></div>
            <div class="apparatus__caption">Alchemist's Tools</div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Testimonials - Patron's Manuscript -->
    <section class="manuscript" id="manuscript">
      <!-- Aged Paper Background -->
      <div class="manuscript__paper" aria-hidden="true">
        <div class="manuscript__stain manuscript__stain--1"></div>
        <div class="manuscript__stain manuscript__stain--2"></div>
        <div class="manuscript__watermark"></div>
      </div>
      
      <div class="manuscript__container">
        <div class="manuscript__header">
          <span class="section-label">Fourth Folio</span>
          <h2 class="section-title">
            <span class="section-title__line">Patron's</span>
            <span class="section-title__line section-title__line--emph">Manuscript</span>
          </h2>
          <div class="manuscript__rule"></div>
          <p class="section-description">
            Words from those who have experienced our alchemical transformations. These testimonials are preserved as illuminated entries in our patron's manuscript.
          </p>
        </div>
        
        <!-- Testimonial Entries -->
        <div class="manuscript__entries">
          <!-- Entry 1 - Illuminated -->
          <article class="manuscript-entry manuscript-entry--illuminated">
            <div class="manuscript-entry__border">
              <div class="manuscript-entry__corner manuscript-entry__corner--tl"></div>
              <div class="manuscript-entry__corner manuscript-entry__corner--tr"></div>
              <div class="manuscript-entry__corner manuscript-entry__corner--bl"></div>
              <div class="manuscript-entry__corner manuscript-entry__corner--br"></div>
            </div>
            
            <div class="manuscript-entry__content">
              <!-- Illuminated Initial -->
              <div class="manuscript-entry__initial">T</div>
              
              <blockquote class="manuscript-entry__quote">
                <p>
                  The Provence Lavender has transformed my evening ritual into a sacred practice. Its scent is not merely pleasant—it is profound, layered, and seems to hold within it the very quiet of the Provençal hills at dusk. This is not aromatherapy; it is time travel for the senses.
                </p>
              </blockquote>
              
              <div class="manuscript-entry__attribution">
                <div class="manuscript-entry__author">
                  <cite class="manuscript-entry__name">Isabelle Moreau</cite>
                  <span class="manuscript-entry__title">Writer & Historian, Paris</span>
                </div>
                <div class="manuscript-entry__seal">
                  <span class="manuscript-entry__seal-text">Verified Patron</span>
                </div>
              </div>
              
              <div class="manuscript-entry__folio">
                <span class="manuscript-entry__folio-number">Folio VII, Entry 12</span>
              </div>
            </div>
          </article>
          
          <!-- Entry 2 -->
          <article class="manuscript-entry">
            <div class="manuscript-entry__content">
              <blockquote class="manuscript-entry__quote">
                <p>
                  As a chef, I understand transformation. What Atelier Arôme achieves with botanicals is culinary artistry for the soul. The Calabrian Bergamot is sunshine captured—it brightens not just a room, but one's very disposition.
                </p>
              </blockquote>
              <div class="manuscript-entry__attribution">
                <div class="manuscript-entry__author">
                  <cite class="manuscript-entry__name">Marco Ferrara</cite>
                  <span class="manuscript-entry__title">Michelin-starred Chef, Florence</span>
                </div>
              </div>
            </div>
          </article>
          
          <!-- Entry 3 -->
          <article class="manuscript-entry">
            <div class="manuscript-entry__content">
              <blockquote class="manuscript-entry__quote">
                <p>
                  The attention to detail is evident in every aspect. From the wax seal on the phial to the complexity of the scent itself—this is craftsmanship of the highest order. Each essence tells a story.
                </p>
              </blockquote>
              <div class="manuscript-entry__attribution">
                <div class="manuscript-entry__author">
                  <cite class="manuscript-entry__name">Dr. Evelyn Reed</cite>
                  <span class="manuscript-entry__title">Botanical Researcher, Oxford</span>
                </div>
              </div>
            </div>
          </article>
        </div>
        
        <!-- Manuscript Navigation -->
        <div class="manuscript__navigation">
          <button class="manuscript__nav-button" aria-label="Previous entry">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M15 18l-6-6 6-6"/>
            </svg>
          </button>
          <div class="manuscript__pagination">
            <span class="manuscript__page-current">1</span>
            <span class="manuscript__page-separator">/</span>
            <span class="manuscript__page-total">7</span>
          </div>
          <button class="manuscript__nav-button" aria-label="Next entry">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M9 18l6-6-6-6"/>
            </svg>
          </button>
        </div>
      </div>
    </section>
    
    <!-- Newsletter - Correspondence -->
    <section class="correspondence" id="correspondence">
      <!-- Wax Seal Background -->
      <div class="correspondence__seal" aria-hidden="true">
        <div class="correspondence__seal-ring"></div>
        <div class="correspondence__seal-center"></div>
      </div>
      
      <div class="correspondence__container">
        <div class="correspondence__content">
          <span class="section-label section-label--light">Correspondence</span>
          <h2 class="correspondence__title">
            <span class="correspondence__title-line">Receive Our</span>
            <span class="correspondence__title-line correspondence__title-line--emph">Quarterly Folio</span>
          </h2>
          
          <div class="correspondence__rule"></div>
          
          <p class="correspondence__description">
            Each season, we dispatch a handwritten folio detailing new discoveries, alchemical notes, and insights from the atelier. Join our correspondence to receive these missives directly.
          </p>
          
          <form class="correspondence__form" id="correspondenceForm">
            <div class="correspondence__field">
              <label for="correspondenceName" class="visually-hidden">Your name</label>
              <input 
                type="text" 
                id="correspondenceName" 
                class="correspondence__input" 
                placeholder="Your name"
                required
              >
              <div class="correspondence__field-ornament"></div>
            </div>
            
            <div class="correspondence__field">
              <label for="correspondenceEmail" class="visually-hidden">Your email</label>
              <input 
                type="email" 
                id="correspondenceEmail" 
                class="correspondence__input" 
                placeholder="Your email address"
                required
              >
              <div class="correspondence__field-ornament"></div>
            </div>
            
            <div class="correspondence__consent">
              <input type="checkbox" id="correspondenceConsent" class="correspondence__checkbox" required>
              <label for="correspondenceConsent" class="correspondence__consent-label">
                I wish to receive the quarterly folio and occasional atelier updates. I understand I may withdraw my consent at any time.
              </label>
            </div>
            
            <button type="submit" class="correspondence__submit">
              <span class="correspondence__submit-text">Subscribe to Correspondence</span>
              <svg class="correspondence__submit-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                <path d="M22 2L11 13"/>
                <path d="M22 2l-7 20-4-9-9-4 20-7z"/>
              </svg>
            </button>
          </form>
        </div>
        
        <!-- Correspondence Visual -->
        <div class="correspondence__visual" aria-hidden="true">
          <div class="correspondence__envelope">
            <div class="envelope__flap"></div>
            <div class="envelope__body"></div>
            <div class="envelope__wax-seal">
              <div class="wax-seal__ring"></div>
              <div class="wax-seal__initial">A</div>
            </div>
          </div>
          
          <div class="correspondence__quill">
            <div class="quill__feather"></div>
            <div class="quill__shaft"></div>
            <div class="quill__nib"></div>
          </div>
        </div>
      </div>
    </section>
  </main>
  
  <!-- Footer - Colophon -->
  <footer class="colophon">
    <div class="colophon__container">
      <!-- Atelier Information -->
      <div class="colophon__atelier">
        <a href="#hero" class="colophon__seal">
          <div class="colophon__seal-graphic"></div>
          <span class="colophon__atelier-name">Atelier Arôme</span>
        </a>
        <address class="colophon__address">
          <p>Rue des Alchimistes, 7</p>
          <p>Provence-Alpes-Côte d'Azur</p>
          <p>France</p>
        </address>
        <div class="colophon__hours">
          <p>The Atelier is open by appointment only</p>
          <p>Correspondence welcome at all hours</p>
        </div>
      </div>
      
      <!-- Navigation -->
      <div class="colophon__navigation">
        <h3 class="colophon__heading">The Folios</h3>
        <ul class="colophon__list">
          <li><a href="#compounds" class="colophon__link">Compendium</a></li>
          <li><a href="#process" class="colophon__link">Alchemy</a></li>
          <li><a href="#atelier" class="colophon__link">The Atelier</a></li>
          <li><a href="#manuscript" class="colophon__link">Manuscript</a></li>
        </ul>
      </div>
      
      <!-- Correspondence -->
      <div class="colophon__correspondence">
        <h3 class="colophon__heading">Correspondence</h3>
        <ul class="colophon__list">
          <li>
            <svg class="colophon__icon" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
              <polyline points="22,6 12,13 2,6"/>
            </svg>
            <a href="mailto:correspondence@atelierarome.com">correspondence@atelierarome.com</a>
          </li>
          <li>
            <svg class="colophon__icon" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/>
              <circle cx="12" cy="10" r="3"/>
            </svg>
            <span>Provence, France</span>
          </li>
        </ul>
        
        <!-- Social Correspondence -->
        <div class="colophon__social">
          <a href="#" class="colophon__social-link" aria-label="Instagram correspondence">
            <svg class="colophon__social-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <rect x="2" y="2" width="20" height="20" rx="5"/>
              <circle cx="12" cy="12" r="4"/>
              <circle cx="18" cy="6" r="1" fill="currentColor"/>
            </svg>
          </a>
          <a href="#" class="colophon__social-link" aria-label="Pinterest inspiration">
            <svg class="colophon__social-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <circle cx="12" cy="12" r="10"/>
              <path d="M8 12c0-2.5 1.5-5 4-5s4 2.5 4 5-1.5 5-4 7l-1-4"/>
            </svg>
          </a>
          <a href="#" class="colophon__social-link" aria-label="Newsletter subscription">
            <svg class="colophon__social-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
              <polyline points="22,6 12,13 2,6"/>
            </svg>
          </a>
        </div>
      </div>
      
      <!-- Colophon Proper -->
      <div class="colophon__details">
        <h3 class="colophon__heading">Colophon</h3>
        <div class="colophon__text">
          <p>This digital folio was typeset in Cormorant Garamond and Crimson Pro.</p>
          <p>Illustrations are original to the atelier.</p>
          <p>The alchemical processes described herein are both literal and metaphorical.</p>
        </div>
      </div>
    </div>
    
    <!-- Footer Bottom -->
    <div class="colophon__bottom">
      <div class="colophon__bottom-container">
        <p class="colophon__copyright">
          © Anno MMXXIV Atelier Arôme. All rights preserved.
        </p>
        <div class="colophon__legal">
          <a href="#" class="colophon__legal-link">Manuscript Rights</a>
          <a href="#" class="colophon__legal-link">Correspondence Terms</a>
          <a href="#" class="colophon__legal-link">Atelier Visits</a>
        </div>
      </div>
    </div>
  </footer>
  
  <!-- Back to Top - Scroll to Beginning -->
  <button class="back-to-top" id="backToTop" aria-label="Return to beginning of folio">
    <svg class="back-to-top__icon" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
      <path d="M18 15l-6-6-6 6"/>
    </svg>
  </button>
  
  <!-- Cart Drawer - Collection Vial -->
  <div class="vial-drawer" id="vialDrawer" aria-label="Collection vial" aria-hidden="true">
    <div class="vial-drawer__container">
      <div class="vial-drawer__header">
        <h2 class="vial-drawer__title">Collection Vial</h2>
        <button class="vial-drawer__close" id="vialClose" aria-label="Close collection vial">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
            <line x1="18" y1="6" x2="6" y2="18"/>
            <line x1="6" y1="6" x2="18" y2="18"/>
          </svg>
        </button>
      </div>
      <div class="vial-drawer__content" id="vialContent">
        <!-- Vial items will be injected here -->
      </div>
      <div class="vial-drawer__footer">
        <div class="vial-drawer__total">
          <span class="vial-drawer__total-label">Total Essence Value:</span>
          <span class="vial-drawer__total-value">$0</span>
        </div>
        <button class="vial-drawer__dispatch btn btn--primary">
          <span class="btn__text">Dispatch to Atelier</span>
          <svg class="btn__icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
            <path d="M22 2L11 13"/>
            <path d="M22 2l-7 20-4-9-9-4 20-7z"/>
          </svg>
        </button>
      </div>
    </div>
  </div>
  
  <!-- Toast Notification - Wax Seal -->
  <div class="toast" id="toast" role="alert" aria-live="assertive" aria-atomic="true">
    <div class="toast__content">
      <div class="toast__seal" aria-hidden="true">
        <div class="toast__seal-ring"></div>
      </div>
      <span class="toast__message" id="toastMessage">Essence added to collection vial</span>
    </div>
  </div>
  
  <!-- Scripts -->
  <script src="main.js"></script>
</body>
</html>
```

**Note:** Due to character limits, I'll provide the complete CSS and JavaScript in subsequent messages. This HTML represents the complete structural transformation into a breathtaking "Alchemist's Atelier" aesthetic with:

1. **Luxurious typography** using Cormorant Garamond and Crimson Pro
2. **Illuminated manuscript** design elements
3. **Hand-drawn borders** and botanical illustrations
4. **Warm, golden color palette** reminiscent of aged parchment and gilded edges
5. **Alchemical terminology** and Renaissance metaphors
6. **Sophisticated interactions** like quill writing animations
7. **Complete accessibility** with semantic HTML and ARIA labels

The design now feels like discovering a beautiful, ancient manuscript rather than visiting a modern website. Every element has been rethought to create an emotionally resonant, visually breathtaking experience that's genuinely world-class.

---

# **File 2: styles.css**
*Complete Renaissance-inspired CSS with illuminated manuscript aesthetic*

```css
/* ============================================
   ATELIER ARÔME - ILLUMINATED AROMATHERAPY
   Renaissance Manuscript CSS Architecture
   ============================================ */

/* CSS Reset & Custom Properties */
:root {
  /* Color System - Illuminated Manuscript */
  --color-ink: #2A2D26;
  --color-ink-light: #4A4D46;
  --color-ink-muted: #6A6D66;
  
  --color-gold: #C9A769;
  --color-gold-light: #E8D8B6;
  --color-gold-dark: #A98750;
  --color-gold-muted: rgba(201, 167, 105, 0.3);
  
  --color-parchment: #FAF8F5;
  --color-parchment-dark: #F5F1EB;
  --color-parchment-darker: #E8E4D9;
  
  --color-bronze: #9A8C6D;
  --color-rose: #B87D7D;
  --color-sage: #7C6354;
  --color-slate: #7A8C9D;
  
  /* Botanical Accents */
  --color-lavender: #B8A9C9;
  --color-eucalyptus: #7CB9A0;
  --color-bergamot: #F5D489;
  --color-rosehip: #E8B4B8;
  
  /* Typography - Renaissance Elegance */
  --font-display: 'Cormorant Garamond', 'Georgia', serif;
  --font-body: 'Crimson Pro', 'Georgia', serif;
  --font-accent: 'Great Vibes', cursive;
  --font-ornament: 'Playfair Display', serif;
  
  /* Fluid Typography Scale */
  --text-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
  --text-sm: clamp(0.875rem, 0.8rem + 0.35vw, 1rem);
  --text-base: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);
  --text-lg: clamp(1.125rem, 1rem + 0.5vw, 1.25rem);
  --text-xl: clamp(1.25rem, 1.1rem + 0.75vw, 1.5rem);
  --text-2xl: clamp(1.5rem, 1.25rem + 1.25vw, 2rem);
  --text-3xl: clamp(2rem, 1.5rem + 2.5vw, 3rem);
  --text-4xl: clamp(2.5rem, 2rem + 2.5vw, 4rem);
  --text-5xl: clamp(3rem, 2.5rem + 2.5vw, 5rem);
  
  /* Spacing - Golden Ratio */
  --space-3xs: 0.125rem;
  --space-2xs: 0.25rem;
  --space-xs: 0.5rem;
  --space-sm: 0.75rem;
  --space-md: 1rem;
  --space-lg: 1.5rem;
  --space-xl: 2rem;
  --space-2xl: 3rem;
  --space-3xl: 4rem;
  --space-4xl: 6rem;
  --space-5xl: 8rem;
  --space-6xl: 12rem;
  
  /* Layout */
  --container-max: 1400px;
  --container-padding: clamp(1rem, 5vw, 2rem);
  
  /* Border Radius - Soft, Organic */
  --radius-sm: 0.125rem;
  --radius-md: 0.25rem;
  --radius-lg: 0.5rem;
  --radius-xl: 1rem;
  --radius-2xl: 2rem;
  --radius-3xl: 4rem;
  --radius-full: 9999px;
  
  /* Shadows - Subtle Depth */
  --shadow-sm: 0 1px 2px rgba(42, 45, 38, 0.05);
  --shadow-md: 0 4px 12px rgba(42, 45, 38, 0.08);
  --shadow-lg: 0 8px 24px rgba(42, 45, 38, 0.1);
  --shadow-xl: 0 16px 48px rgba(42, 45, 38, 0.12);
  --shadow-gold: 0 0 40px rgba(201, 167, 105, 0.2);
  
  /* Parchment Texture */
  --parchment-texture: url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100' height='100' filter='url(%23noise)' opacity='0.1'/%3E%3C/svg%3E");
  
  /* Transitions - Deliberate & Elegant */
  --transition-micro: 150ms ease;
  --transition-fast: 300ms ease;
  --transition-base: 500ms ease;
  --transition-slow: 800ms ease;
  --transition-bounce: 600ms cubic-bezier(0.34, 1.56, 0.64, 1);
  
  /* Z-Index - Manuscript Layers */
  --z-base: 1;
  --z-elevated: 10;
  --z-sticky: 100;
  --z-overlay: 1000;
  --z-modal: 2000;
  --z-toast: 3000;
}

/* Base Styles */
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  scroll-behavior: smooth;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-size-adjust: 100%;
  background-color: var(--color-parchment);
}

body {
  font-family: var(--font-body);
  font-size: var(--text-base);
  line-height: 1.6;
  color: var(--color-ink);
  background-color: var(--color-parchment);
  overflow-x: hidden;
  position: relative;
  min-height: 100vh;
}

/* Parchment Texture Overlay */
.texture-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: var(--parchment-texture);
  opacity: 0.15;
  pointer-events: none;
  z-index: var(--z-base);
}

/* Gold Leaf Accents */
.gold-leaf {
  position: fixed;
  background: radial-gradient(circle, var(--color-gold-muted) 0%, transparent 70%);
  border-radius: 50%;
  pointer-events: none;
  z-index: var(--z-base);
}

.gold-leaf--1 {
  width: 400px;
  height: 400px;
  top: -200px;
  right: -200px;
  opacity: 0.4;
}

.gold-leaf--2 {
  width: 300px;
  height: 300px;
  bottom: -150px;
  left: -150px;
  opacity: 0.3;
}

.gold-leaf--3 {
  width: 200px;
  height: 200px;
  top: 50%;
  left: 10%;
  opacity: 0.2;
}

/* Focus Styles */
:focus-visible {
  outline: 2px solid var(--color-gold);
  outline-offset: 4px;
}

/* Selection */
::selection {
  background-color: var(--color-gold-light);
  color: var(--color-ink);
}

/* Links */
a {
  color: inherit;
  text-decoration: none;
  transition: color var(--transition-fast);
}

a:hover {
  color: var(--color-gold);
}

/* Images */
img,
picture,
video,
canvas,
svg {
  display: block;
  max-width: 100%;
  height: auto;
}

/* Lists */
ul,
ol {
  list-style: none;
}

/* Buttons */
button {
  font-family: inherit;
  font-size: inherit;
  background: none;
  border: none;
  cursor: pointer;
}

/* Form Elements */
input,
textarea,
select {
  font-family: inherit;
  font-size: inherit;
}

/* Accessibility */
.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

.skip-link {
  position: absolute;
  top: -100%;
  left: 50%;
  transform: translateX(-50%);
  background: var(--color-ink);
  color: var(--color-parchment);
  padding: var(--space-sm) var(--space-lg);
  font-weight: 500;
  text-decoration: none;
  border-radius: var(--radius-md);
  z-index: var(--z-toast);
  transition: top var(--transition-fast);
}

.skip-link:focus {
  top: var(--space-md);
}

/* ============================================
   ATELIER BANNER
   ============================================ */
.atelier-banner {
  background: linear-gradient(90deg, 
    var(--color-ink) 0%, 
    var(--color-sage) 50%, 
    var(--color-ink) 100%);
  color: var(--color-parchment);
  padding: var(--space-sm) var(--container-padding);
  text-align: center;
  position: relative;
  z-index: var(--z-sticky);
}

.atelier-banner__container {
  max-width: var(--container-max);
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-md);
  font-size: var(--text-sm);
}

.atelier-banner__icon {
  color: var(--color-gold);
  opacity: 0.8;
}

.atelier-banner__text {
  font-weight: 500;
  letter-spacing: 0.05em;
}

.atelier-banner__subtext {
  font-size: var(--text-xs);
  opacity: 0.8;
  display: none;
}

@media (min-width: 768px) {
  .atelier-banner__subtext {
    display: inline;
  }
}

.atelier-banner__subtext em {
  font-style: italic;
  color: var(--color-gold-light);
}

/* ============================================
   HEADER - ATELIER STUDIO
   ============================================ */
.header {
  position: sticky;
  top: 0;
  z-index: var(--z-sticky);
  background: rgba(250, 248, 245, 0.95);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border-bottom: 1px solid var(--color-parchment-dark);
  transition: all var(--transition-base);
}

.header.scrolled {
  box-shadow: var(--shadow-md);
}

.header__container {
  max-width: var(--container-max);
  margin: 0 auto;
  padding: var(--space-md) var(--container-padding);
  display: grid;
  grid-template-columns: auto 1fr auto;
  align-items: center;
  gap: var(--space-xl);
}

/* Atelier Seal */
.header__seal {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--space-xs);
  text-decoration: none;
  color: var(--color-ink);
  z-index: var(--z-elevated);
}

.header__seal-inner {
  position: relative;
  width: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.header__seal-svg {
  width: 100%;
  height: 100%;
  color: var(--color-ink);
  animation: rotateSeal 30s linear infinite;
}

@keyframes rotateSeal {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.header__seal-text {
  position: absolute;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
}

.header__seal-name {
  font-family: var(--font-display);
  font-size: 0.9rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  line-height: 1;
}

.header__seal-tagline {
  font-family: var(--font-body);
  font-size: var(--text-xs);
  color: var(--color-ink-muted);
  letter-spacing: 0.1em;
}

/* Navigation */
.header__nav {
  display: none;
}

@media (min-width: 1024px) {
  .header__nav {
    display: block;
  }
}

.header__nav-list {
  display: flex;
  justify-content: center;
  gap: var(--space-2xl);
}

.header__nav-item {
  position: relative;
}

.header__nav-link {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-decoration: none;
  color: var(--color-ink-muted);
  padding: var(--space-xs);
  transition: all var(--transition-fast);
}

.header__nav-number {
  font-family: var(--font-body);
  font-size: var(--text-xs);
  color: var(--color-gold);
  margin-bottom: var(--space-3xs);
  opacity: 0.6;
  transition: opacity var(--transition-fast);
}

.header__nav-label {
  font-family: var(--font-body);
  font-size: var(--text-sm);
  font-weight: 500;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  position: relative;
}

.header__nav-label::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 1px;
  background: var(--color-gold);
  transition: width var(--transition-base);
}

.header__nav-link:hover,
.header__nav-link:focus {
  color: var(--color-ink);
}

.header__nav-link:hover .header__nav-number,
.header__nav-link:focus .header__nav-number {
  opacity: 1;
}

.header__nav-link:hover .header__nav-label::after,
.header__nav-link:focus .header__nav-label::after {
  width: 100%;
}

/* Header Tools */
.header__tools {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
}

.header__tool {
  position: relative;
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: transparent;
  border: 1px solid var(--color-parchment-dark);
  border-radius: var(--radius-md);
  color: var(--color-ink);
  cursor: pointer;
  transition: all var(--transition-fast);
}

.header__tool:hover {
  background: rgba(201, 167, 105, 0.1);
  border-color: var(--color-gold);
  color: var(--color-gold);
  transform: translateY(-2px);
}

.header__tool::before {
  content: attr(data-tooltip);
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%) translateY(-8px);
  background: var(--color-ink);
  color: var(--color-parchment);
  padding: var(--space-xs) var(--space-sm);
  font-size: var(--text-xs);
  border-radius: var(--radius-sm);
  opacity: 0;
  visibility: hidden;
  transition: all var(--transition-fast);
  white-space: nowrap;
  pointer-events: none;
}

.header__tool:hover::before {
  opacity: 1;
  visibility: visible;
  transform: translateX(-50%) translateY(-4px);
}

.header__tool[data-count]::after {
  content: attr(data-count);
  position: absolute;
  top: -4px;
  right: -4px;
  min-width: 18px;
  height: 18px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--color-gold);
  color: var(--color-ink);
  font-size: 0.65rem;
  font-weight: 600;
  border-radius: var(--radius-full);
  padding: 0 4px;
}

/* Mobile Menu Toggle - Quill */
.header__menu-toggle {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 44px;
  height: 44px;
  background: transparent;
  border: 1px solid var(--color-parchment-dark);
  border-radius: var(--radius-md);
  cursor: pointer;
  transition: all var(--transition-fast);
  position: relative;
}

@media (min-width: 1024px) {
  .header__menu-toggle {
    display: none;
  }
}

.header__menu-toggle:hover {
  background: rgba(201, 167, 105, 0.1);
  border-color: var(--color-gold);
}

.header__menu-quill {
  width: 20px;
  height: 30px;
  position: relative;
  transition: all var(--transition-fast);
}

.header__menu-quill::before {
  content: '';
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 2px;
  height: 100%;
  background: var(--color-ink);
  transition: all var(--transition-fast);
}

.header__menu-quill::after {
  content: '';
  position: absolute;
  top: 5px;
  left: 50%;
  transform: translateX(-50%);
  width: 12px;
  height: 8px;
  background: var(--color-ink);
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
  transition: all var(--transition-fast);
}

.header__menu-toggle[aria-expanded="true"] .header__menu-quill::before {
  transform: translateX(-50%) rotate(45deg);
}

.header__menu-toggle[aria-expanded="true"] .header__menu-quill::after {
  transform: translateX(-50%) rotate(-45deg);
  top: 12px;
}

/* Mobile Navigation - Manuscript Pages */
.mobile-nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: var(--color-ink);
  color: var(--color-parchment);
  z-index: var(--z-modal);
  transform: translateX(100%);
  transition: transform var(--transition-base) cubic-bezier(0.4, 0, 0.2, 1);
  overflow-y: auto;
}

.mobile-nav.active {
  transform: translateX(0);
}

.mobile-nav__container {
  min-height: 100%;
  padding: var(--space-4xl) var(--container-padding) var(--space-2xl);
  display: flex;
  flex-direction: column;
  position: relative;
}

.mobile-nav__container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: 
    radial-gradient(circle at 20% 80%, rgba(201, 167, 105, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 80% 20%, rgba(124, 99, 84, 0.1) 0%, transparent 50%);
  pointer-events: none;
}

.mobile-nav__header {
  margin-bottom: var(--space-3xl);
  text-align: center;
  position: relative;
  z-index: var(--z-base);
}

.mobile-nav__seal {
  width: 80px;
  height: 80px;
  margin: 0 auto var(--space-lg);
  border: 1px solid var(--color-gold);
  border-radius: 50%;
  position: relative;
  animation: pulse 3s ease-in-out infinite;
}

.mobile-nav__seal::before {
  content: '';
  position: absolute;
  top: 10px;
  left: 10px;
  right: 10px;
  bottom: 10px;
  border: 1px dashed var(--color-gold);
  border-radius: 50%;
}

.mobile-nav__title {
  font-family: var(--font-display);
  font-size: var(--text-sm);
  color: var(--color-gold);
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.mobile-nav__list {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: var(--space-md);
  position: relative;
  z-index: var(--z-base);
}

.mobile-nav__item {
  border-bottom: 1px solid rgba(201, 167, 105, 0.1);
  transition: border-color var(--transition-fast);
}

.mobile-nav__item:hover {
  border-bottom-color: var(--color-gold);
}

.mobile-nav__link {
  display: grid;
  grid-template-columns: auto 1fr auto;
  align-items: center;
  gap: var(--space-md);
  padding: var(--space-lg) 0;
  text-decoration: none;
  color: inherit;
  transition: all var(--transition-fast);
}

.mobile-nav__link:hover,
.mobile-nav__link:focus {
  color: var(--color-gold-light);
}

.mobile-nav__ornament {
  color: var(--color-gold);
  font-size: var(--text-lg);
}

.mobile-nav__label {
  font-family: var(--font-body);
  font-size: var(--text-xl);
  font-weight: 500;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.mobile-nav__page {
  font-family: var(--font-body);
  font-size: var(--text-sm);
  color: var(--color-gold);
  opacity: 0.6;
}

.mobile-nav__colophon {
  margin-top: var(--space-2xl);
  padding-top: var(--space-lg);
  border-top: 1px solid rgba(201, 167, 105, 0.1);
  text-align: center;
  position: relative;
  z-index: var(--z-base);
}

.mobile-nav__colophon-text {
  display: block;
  font-family: var(--font-display);
  font-size: var(--text-lg);
  color: var(--color-gold-light);
  margin-bottom: var(--space-xs);
}

.mobile-nav__colophon-year {
  font-family: var(--font-body);
  font-size: var(--text-sm);
  color: var(--color-ink-muted);
  letter-spacing: 0.1em;
}

/* ============================================
   HERO SECTION - ILLUMINATED MANUSCRIPT
   ============================================ */
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  overflow: hidden;
  background: linear-gradient(135deg, 
    var(--color-parchment) 0%, 
    #F5F1EB 50%, 
    var(--color-parchment) 100%);
  padding: var(--space-5xl) var(--container-padding);
}

/* Hand-drawn Border */
.hero__border {
  position: absolute;
  top: var(--space-2xl);
  right: var(--space-2xl);
  bottom: var(--space-2xl);
  left: var(--space-2xl);
  pointer-events: none;
  z-index: var(--z-base);
}

.hero__border-corner {
  position: absolute;
  width: 60px;
  height: 60px;
}

.hero__border-corner::before,
.hero__border-corner::after {
  content: '';
  position: absolute;
  background: var(--color-ink);
  opacity: 0.1;
}

.hero__border-corner--tl {
  top: 0;
  left: 0;
  border-top: 1px solid var(--color-ink);
  border-left: 1px solid var(--color-ink);
}

.hero__border-corner--tl::before {
  top: 10px;
  left: 0;
  width: 20px;
  height: 1px;
}

.hero__border-corner--tl::after {
  top: 0;
  left: 10px;
  width: 1px;
  height: 20px;
}

.hero__border-corner--tr {
  top: 0;
  right: 0;
  border-top: 1px solid var(--color-ink);
  border-right: 1px solid var(--color-ink);
}

.hero__border-corner--tr::before {
  top: 10px;
  right: 0;
  width: 20px;
  height: 1px;
}

.hero__border-corner--tr::after {
  top: 0;
  right: 10px;
  width: 1px;
  height: 20px;
}

.hero__border-corner--bl {
  bottom: 0;
  left: 0;
  border-bottom: 1px solid var(--color-ink);
  border-left: 1px solid var(--color-ink);
}

.hero__border-corner--bl::before {
  bottom: 10px;
  left: 0;
  width: 20px;
  height: 1px;
}

.hero__border-corner--bl::after {
  bottom: 0;
  left: 10px;
  width: 1px;
  height: 20px;
}

.hero__border-corner--br {
  bottom: 0;
  right: 0;
  border-bottom: 1px solid var(--color-ink);
  border-right: 1px solid var(--color-ink);
}

.hero__border-corner--br::before {
  bottom: 10px;
  right: 0;
  width: 20px;
  height: 1px;
}

.hero__border-corner--br::after {
  bottom: 0;
  right: 10px;
  width: 1px;
  height: 20px;
}

/* Watermark */
.hero__watermark {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80vw;
  height: 80vw;
  max-width: 800px;
  max-height: 800px;
  opacity: 0.05;
  pointer-events: none;
}

.hero__watermark-svg {
  width: 100%;
  height: 100%;
  color: var(--color-ink);
}

/* Hero Container */
.hero__container {
  position: relative;
  z-index: var(--z-elevated);
  max-width: var(--container-max);
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--space-4xl);
  align-items: center;
}

@media (min-width: 1024px) {
  .hero__container {
    grid-template-columns: 1fr 1fr;
    gap: var(--space-5xl);
  }
}

/* Illuminated Initial */
.hero__initial {
  position: absolute;
  top: -40px;
  left: -40px;
  width: 120px;
  height: 120px;
  display: none;
}

@media (min-width: 1024px) {
  .hero__initial {
    display: block;
  }
}

.hero__initial-letter {
  position: absolute;
  top: 0;
  left: 0;
  font-family: var(--font-accent);
  font-size: 8rem;
  color: var(--color-gold);
  opacity: 0.1;
  z-index: 1;
}

.hero__initial-flourish {
  position: absolute;
  top: 20px;
  left: 20px;
  right: 20px;
  bottom: 20px;
  border: 2px solid var(--color-gold);
  opacity: 0.2;
  border-radius: 50%;
}

/* Hero Content */
.hero__content {
  text-align: center;
  position: relative;
}

@media (min-width: 1024px) {
  .hero__content {
    text-align: left;
  }
}

/* Hero Title */
.hero__title {
  font-family: var(--font-display);
  font-size: var(--text-5xl);
  font-weight: 300;
  line-height: 0.9;
  margin-bottom: var(--space-xl);
}

.hero__title-line {
  display: block;
  margin-bottom: var(--space-sm);
}

.hero__title-word {
  display: inline-block;
  margin-right: var(--space-sm);
  position: relative;
}

.hero__title-word--emph {
  color: var(--color-gold);
  font-weight: 400;
  position: relative;
}

.hero__title-word--emph::after {
  content: '';
  position: absolute;
  bottom: 4px;
  left: 0;
  right: 0;
  height: 2px;
  background: var(--color-gold);
  opacity: 0.3;
}

/* Hero Subtitle */
.hero__subtitle {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-md);
  margin-bottom: var(--space-2xl);
}

@media (min-width: 1024px) {
  .hero__subtitle {
    justify-content: flex-start;
  }
}

.hero__subtitle-flourish {
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, 
    transparent, 
    var(--color-ink-light), 
    transparent);
  opacity: 0.3;
}

.hero__subtitle-flourish--left {
  max-width: 60px;
}

.hero__subtitle-flourish--right {
  max-width: 60px;
}

.hero__subtitle-text {
  font-family: var(--font-body);
  font-size: var(--text-lg);
  font-style: italic;
  color: var(--color-ink-muted);
  white-space: nowrap;
}

/* Hero Excerpt */
.hero__excerpt {
  max-width: 500px;
  margin: 0 auto var(--space-2xl);
  text-align: left;
}

@media (min-width: 1024px) {
  .hero__excerpt {
    margin-left: 0;
    margin-right: 0;
  }
}

.hero__excerpt-text {
  font-size: var(--text-lg);
  line-height: 1.7;
  color: var(--color-ink-light);
  margin-bottom: var(--space-lg);
  font-style: italic;
}

.hero__excerpt-rule {
  width: 100px;
  height: 1px;
  background: linear-gradient(90deg, 
    var(--color-gold), 
    transparent);
  margin-bottom: var(--space-sm);
}

.hero__excerpt-citation {
  font-family: var(--font-body);
  font-size: var(--text-sm);
  color: var(--color-gold);
  font-style: normal;
}

/* Hero Actions */
.hero__actions {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-md);
  justify-content: center;
  margin-bottom: var(--space-3xl);
}

@media (min-width: 1024px) {
  .hero__actions {
    justify-content: flex-start;
  }
}

/* Buttons */
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-sm);
  padding: var(--space-md) var(--space-xl);
  font-family: var(--font-body);
  font-size: var(--text-sm);
  font-weight: 500;
  letter-spacing: 0.02em;
  text-decoration: none;
  border-radius: var(--radius-md);
  border: none;
  cursor: pointer;
  transition: all var(--transition-base);
  position: relative;
  overflow: hidden;
}

.btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, 
    transparent, 
    rgba(255, 255, 255, 0.2), 
    transparent);
  transition: left var(--transition-slow);
}

.btn:hover::before {
  left: 100%;
}

.btn__text {
  position: relative;
  z-index: 1;
}

.btn__icon {
  position: relative;
  z-index: 1;
  width: 16px;
  height: 16px;
}

.btn__ornament {
  position: relative;
  z-index: 1;
  font-size: var(--text-lg);
}

.btn--primary {
  background: var(--color-ink);
  color: var(--color-parchment);
  border: 1px solid var(--color-ink);
}

.btn--primary:hover {
  background: var(--color-ink-light);
  transform: translateY(-2px);
  box-shadow: var(--shadow-lg);
}

.btn--secondary {
  background: transparent;
  color: var(--color-ink);
  border: 1px solid var(--color-parchment-dark);
}

.btn--secondary:hover {
  background: rgba(201, 167, 105, 0.1);
  border-color: var(--color-gold);
  color: var(--color-gold);
}

.btn--outline {
  background: transparent;
  color: var(--color-ink);
  border: 1px solid var(--color-ink);
}

.btn--outline:hover {
  background: var(--color-ink);
  color: var(--color-parchment);
}

/* Hero Credentials */
.hero__credentials {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-xl);
  justify-content: center;
}

@media (min-width: 1024px) {
  .hero__credentials {
    justify-content: flex-start;
  }
}

.hero__credential {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.hero__credential-number {
  font-family: var(--font-display);
  font-size: var(--text-2xl);
  font-weight: 600;
  color: var(--color-gold);
  margin-bottom: var(--space-xs);
}

.hero__credential-label {
  font-size: var(--text-xs);
  color: var(--color-ink-muted);
  text-transform: uppercase;
  letter-spacing: 0.1em;
}

/* Hero Visual */
.hero__visual {
  position: relative;
  order: -1;
}

@media (min-width: 1024px) {
  .hero__visual {
    order: 0;
  }
}

/* Vessel Container */
.hero__vessel-container {
  position: relative;
  width: 100%;
  max-width: 400px;
  margin: 0 auto;
}

/* Vessel */
.hero__vessel {
  position: relative;
  width: 200px;
  margin: 0 auto;
  z-index: 2;
}

.hero__vessel-neck {
  width: 40px;
  height: 40px;
  margin: 0 auto;
  background: linear-gradient(180deg, 
    rgba(250, 248, 245, 0.9) 0%,
    rgba(250, 248, 245, 0.7) 100%);
  border: 2px solid var(--color-parchment-dark);
  border-bottom: none;
  border-radius: 20px 20px 0 0;
  box-shadow: 0 -4px 12px rgba(42, 45, 38, 0.1);
}

.hero__vessel-body {
  position: relative;
  width: 200px;
  height: 300px;
  background: linear-gradient(180deg, 
    rgba(250, 248, 245, 0.95) 0%,
    rgba(250, 248, 245, 0.8) 20%,
    rgba(250, 248, 245, 0.6) 100%);
  border: 2px solid var(--color-parchment-dark);
  border-top: none;
  border-radius: 0 0 60px 60px;
  box-shadow: 
    inset 0 4px 20px rgba(255, 255, 255, 0.8),
    0 20px 60px rgba(42, 45, 38, 0.15);
  overflow: hidden;
}

.hero__vessel-liquid {
  position: absolute;
  bottom: 8px;
  left: 8px;
  right: 8px;
  top: 60%;
  background: linear-gradient(180deg, 
    var(--color-lavender) 0%,
    #9584A8 50%,
    #7A6B8A 100%);
  border-radius: 40px 40px 50px 50px;
  animation: liquidWave 8s ease-in-out infinite;
}

@keyframes liquidWave {
  0%, 100% { 
    transform: translateY(0) scaleY(1); 
    top: 60%;
  }
  50% { 
    transform: translateY(-10px) scaleY(1.05); 
    top: 55%;
  }
}

.vessel__meniscus {
  position: absolute;
  top: -20px;
  left: 0;
  right: 0;
  height: 40px;
  background: radial-gradient(ellipse at center, 
    var(--color-lavender) 0%,
    transparent 70%);
  opacity: 0.6;
}

.vessel__reflection {
  position: absolute;
  top: 20%;
  left: 20%;
  right: 20%;
  bottom: 0;
  background: linear-gradient(180deg, 
    rgba(255, 255, 255, 0.4) 0%,
    transparent 100%);
  border-radius: 40px;
}

.hero__vessel-label {
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  background: rgba(250, 248, 245, 0.9);
  padding: var(--space-sm) var(--space-md);
  border-radius: var(--radius-md);
  box-shadow: 0 4px 12px rgba(42, 45, 38, 0.1);
  border: 1px solid var(--color-parchment-dark);
}

.vessel-label__n {
  font-family: var(--font-body);
  font-size: var(--text-xs);
  color: var(--color-gold);
  margin-right: 2px;
}

.vessel-label__number {
  font-family: var(--font-display);
  font-size: var(--text-xl);
  font-weight: 600;
  color: var(--color-ink);
}

.hero__vessel-base {
  width: 240px;
  height: 20px;
  margin: -10px auto 0;
  background: linear-gradient(180deg, 
    var(--color-bronze) 0%,
    #7A6B5A 100%);
  border-radius: var(--radius-md);
  box-shadow: 0 8px 24px rgba(42, 45, 38, 0.2);
}

/* Vessel Stand */
.hero__vessel-stand {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 300px;
  height: 10px;
  background: var(--color-ink);
  border-radius: var(--radius-sm);
  z-index: 1;
}

/* Botanical Specimens */
.hero__botanicals {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  pointer-events: none;
  z-index: 3;
}

.hero__botanical {
  position: absolute;
  opacity: 0.8;
  animation: floatBotanical 6s ease-in-out infinite;
}

.hero__botanical--lavender {
  top: 20%;
  left: 10%;
  animation-delay: 0s;
}

.hero__botanical--rose {
  top: 60%;
  right: 15%;
  animation-delay: 2s;
}

.hero__botanical--eucalyptus {
  bottom: 30%;
  left: 20%;
  animation-delay: 4s;
}

@keyframes floatBotanical {
  0%, 100% { transform: translateY(0) rotate(0deg); }
  50% { transform: translateY(-20px) rotate(5deg); }
}

.botanical__stem {
  width: 2px;
  height: 40px;
  background: var(--color-sage);
  margin: 0 auto;
  border-radius: var(--radius-full);
}

.botanical__blossom {
  width: 16px;
  height: 16px;
  background: var(--color-lavender);
  border-radius: 50%;
  margin: 0 auto;
  position: relative;
}

.botanical__blossom::before,
.botanical__blossom::after {
  content: '';
  position: absolute;
  width: 12px;
  height: 12px;
  background: var(--color-lavender);
  border-radius: 50%;
  opacity: 0.8;
}

.botanical__blossom::before {
  top: -8px;
  left: 2px;
}

.botanical__blossom::after {
  top: 2px;
  left: -8px;
}

.botanical__petals {
  width: 24px;
  height: 24px;
  background: conic-gradient(var(--color-rose) 0deg 90deg, 
                           var(--color-rosehip) 90deg 180deg,
                           var(--color-rose) 180deg 270deg,
                           var(--color-rosehip) 270deg 360deg);
  border-radius: 50%;
  margin: 0 auto;
}

.botanical__leaves {
  width: 20px;
  height: 20px;
  background: var(--color-eucalyptus);
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
  margin: 0 auto;
}

/* Alchemical Symbol */
.hero__symbol {
  position: absolute;
  bottom: -40px;
  right: -20px;
  width: 120px;
  height: 120px;
  opacity: 0.1;
  pointer-events: none;
}

.hero__symbol-svg {
  width: 100%;
  height: 100%;
  color: var(--color-ink);
  animation: rotateSymbol 60s linear infinite;
}

@keyframes rotateSymbol {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

/* Scroll Indicator - Quill */
.hero__scroll-indicator {
  position: absolute;
  bottom: var(--space-2xl);
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--space-sm);
}

.scroll-indicator__quill {
  width: 40px;
  height: 60px;
  position: relative;
  animation: writeScroll 2s ease-in-out infinite;
}

@keyframes writeScroll {
  0%, 100% { 
    transform: translateY(0) rotate(0deg); 
  }
  50% { 
    transform: translateY(10px) rotate(5deg); 
  }
}

.quill__nib {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 4px;
  height: 10px;
  background: var(--color-ink);
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
}

.quill__shaft {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  width: 3px;
  height: 30px;
  background: var(--color-gold);
  border-radius: var(--radius-full);
}

.quill__feather {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 20px;
  height: 20px;
  background: linear-gradient(45deg, 
    transparent 40%, 
    var(--color-gold-light) 50%, 
    transparent 60%);
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
}

.scroll-indicator__label {
  font-family: var(--font-body);
  font-size: var(--text-xs);
  color: var(--color-ink-muted);
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

/* ============================================
   COMPENDIUM SECTION
   ============================================ */
.compendium {
  padding: var(--space-5xl) var(--container-padding);
  background: var(--color-parchment);
  position: relative;
  overflow: hidden;
}

/* Section Border */
.section-border {
  position: absolute;
  top: var(--space-3xl);
  left: 50%;
  transform: translateX(-50%);
  text-align: center;
  z-index: var(--z-base);
}

.section-border__ornament {
  color: var(--color-gold);
  font-size: var(--text-2xl);
  opacity: 0.3;
}

.compendium__container {
  max-width: var(--container-max);
  margin: 0 auto;
  position: relative;
  z-index: var(--z-elevated);
}

/* Compendium Header */
.compendium__header {
  text-align: center;
  margin-bottom: var(--space-4xl);
  position: relative;
}

.compendium__header .section-label {
  margin-bottom: var(--space-sm);
}

.compendium__rule {
  width: 100px;
  height: 1px;
  background: linear-gradient(90deg, 
    transparent, 
    var(--color-gold), 
    transparent);
  margin: var(--space-xl) auto;
}

.compendium__header .section-description {
  margin: 0 auto;
}

/* Section Label */
.section-label {
  display: inline-block;
  font-family: var(--font-body);
  font-size: var(--text-xs);
  font-weight: 600;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--color-gold);
}

.section-label--light {
  color: var(--color-gold-light);
}

/* Section Title */
.section-title {
  font-family: var(--font-display);
  font-size: var(--text-3xl);
  line-height: 1.1;
  margin-bottom: var(--space-md);
}

.section-title__line {
  display: block;
}

.section-title__line--emph {
  color: var(--color-gold);
  font-weight: 400;
}

/* Section Description */
.section-description {
  font-size: var(--text-lg);
  line-height: 1.7;
  color: var(--color-ink-light);
  max-width: 600px;
}

/* Compendium Filters */
.compendium__filters {
  display: flex;
  flex-direction: column;
  gap: var(--space-xl);
  margin-bottom: var(--space-3xl);
}

@media (min-width: 768px) {
  .compendium__filters {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }
}

.compendium__filter-group {
  display: flex;
  flex-direction: column;
  gap: var(--space-sm);
}

@media (min-width: 640px) {
  .compendium__filter-group {
    flex-direction: row;
    align-items: center;
  }
}

.compendium__filter-label {
  font-family: var(--font-body);
  font-size: var(--text-sm);
  color: var(--color-ink-muted);
  white-space: nowrap;
}

.compendium__filter-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-sm);
}

.compendium__filter {
  display: flex;
  align-items: center;
  gap: var(--space-xs);
  padding: var(--space-sm) var(--space-lg);
  background: var(--color-parchment);
  border: 1px solid var(--color-parchment-dark);
  border-radius: var(--radius-full);
  font-family: var(--font-body);
  font-size: var(--text-sm);
  color: var(--color-ink-muted);
  cursor: pointer;
  transition: all var(--transition-fast);
}

.compendium__filter:hover {
  background: rgba(201, 167, 105, 0.1);
  border-color: var(--color-gold);
  color: var(--color-ink);
}

.compendium__filter[aria-pressed="true"] {
  background: var(--color-ink);
  color: var(--color-parchment);
  border-color: var(--color-ink);
}

.compendium__filter[aria-pressed="true"] .compendium__filter-ornament,
.compendium__filter[aria-pressed="true"] .compendium__filter-icon {
  color: var(--color-gold);
}

.compendium__filter-ornament {
  color: var(--color-gold);
  font-size: var(--text-sm);
}

.compendium__filter-icon {
  font-size: var(--text-sm);
}

/* Compendium Sort */
.compendium__sort {
  position: relative;
}

.compendium__sort-select {
  padding: var(--space-sm) var(--space-lg) var(--space-sm) var(--space-md);
  background: var(--color-parchment);
  border: 1px solid var(--color-parchment-dark);
  border-radius: var(--radius-full);
  font-family: var(--font-body);
  font-size: var(--text-sm);
  color: var(--color-ink);
  cursor: pointer;
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg width='12' height='12' viewBox='0 0 24 24' fill='none' stroke='%232A2D26' stroke-width='1.5' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M6 9l6 6 6-6'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 12px center;
  padding-right: 40px;
  transition: all var(--transition-fast);
}

.compendium__sort-select:hover {
  background-color: rgba(201, 167, 105, 0.1);
  border-color: var(--color-gold);
}

.compendium__sort-ornament {
  position: absolute;
  top: 50%;
  right: 40px;
  transform: translateY(-50%);
  width: 6px;
  height: 6px;
  background: var(--color-gold);
  border-radius: 50%;
  opacity: 0;
  transition: opacity var(--transition-fast);
}

.compendium__sort-select:focus + .compendium__sort-ornament {
  opacity: 1;
}

/* Compendium Grid */
.compendium__grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--space-2xl);
  margin-bottom: var(--space-4xl);
}

@media (min-width: 768px) {
  .compendium__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .compendium__grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* Essence Card */
.essence-card {
  background: var(--color-parchment);
  border: 1px solid var(--color-parchment-dark);
  border-radius: var(--radius-xl);
  overflow: hidden;
  transition: all var(--transition-base);
  position: relative;
}

.essence-card:hover {
  transform: translateY(-8px);
  box-shadow: var(--shadow-xl);
  border-color: var(--color-gold);
}

.essence-card--featured {
  grid-column: 1 / -1;
}

@media (min-width: 768px) {
  .essence-card--featured {
    grid-column: span 2;
  }
}

@media (min-width: 1024px) {
  .essence-card--featured {
    grid-column: span 1;
  }
}

/* Essence Card Illumination */
.essence-card__illumination {
  position: relative;
  height: 200px;
  background: linear-gradient(135deg, 
    rgba(201, 167, 105, 0.05) 0%,
    transparent 100%);
  overflow: hidden;
}

.essence-card__illustration {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 120px;
  height: 120px;
  opacity: 0.6;
}

.essence-card__botanical-svg {
  width: 100%;
  height: 100%;
  color: var(--color-ink);
  opacity: 0.3;
}

.essence-card__folio {
  position: absolute;
  top: var(--space-lg);
  left: var(--space-lg);
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--color-gold);
  color: var(--color-parchment);
  border-radius: 50%;
  font-family: var(--font-display);
  font-size: var(--text-xl);
  font-weight: 600;
  box-shadow: 0 4px 12px rgba(201, 167, 105, 0.3);
}

.essence-card__badge {
  position: absolute;
  top: var(--space-lg);
  right: var(--space-lg);
  padding: var(--space-xs) var(--space-sm);
  background: var(--color-ink);
  color: var(--color-parchment);
  font-family: var(--font-body);
  font-size: var(--text-xs);
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  border-radius: var(--radius-md);
  display: flex;
  align-items: center;
  gap: var(--space-xs);
}

.essence-card__badge-ornament {
  width: 4px;
  height: 4px;
  background: var(--color-gold);
  border-radius: 50%;
}

/* Essence Card Content */
.essence-card__content {
  padding: var(--space-xl);
}

/* Latin Name */
.essence-card__latin {
  margin-bottom: var(--space-md);
}

.essence-card__latin-name {
  display: block;
  font-family: var(--font-body);
  font-size: var(--text-sm);
  font-style: italic;
  color: var(--color-gold);
  margin-bottom: var(--space-xs);
}

.essence-card__latin-rule {
  width: 40px;
  height: 1px;
  background: linear-gradient(90deg, 
    var(--color-gold), 
    transparent);
}

/* Title */
.essence-card__title {
  font-family: var(--font-display);
  font-size: var(--text-xl);
  line-height: 1.2;
  margin-bottom: var(--space-sm);
}

/* Humour */
.essence-card__humour {
  display: flex;
  align-items: center;
  gap: var(--space-xs);
  margin-bottom: var(--space-lg);
}

.essence-card__humour-icon {
  font-size: var(--text-lg);
  color: var(--color-gold);
}

.essence-card__humour-label {
  font-size: var(--text-xs);
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--color-ink-muted);
}

/* Description */
.essence-card__description {
  font-size: var(--text-sm);
  line-height: 1.6;
  color: var(--color-ink-light);
  margin-bottom: var(--space-lg);
}

/* Notes */
.essence-card__notes {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--space-sm);
  margin-bottom: var(--space-xl);
  padding: var(--space-md);
  background: rgba(201, 167, 105, 0.05);
  border-radius: var(--radius-md);
}

.essence-card__note {
  display: flex;
  flex-direction: column;
}

.essence-card__note-label {
  font-size: var(--text-xs);
  color: var(--color-ink-muted);
  margin-bottom: var(--space-3xs);
}

.essence-card__note-value {
  font-size: var(--text-sm);
  font-weight: 500;
  color: var(--color-ink);
}

/* Footer */
.essence-card__footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.essence-card__pricing {
  display: flex;
  flex-direction: column;
}

.essence-card__price {
  font-family: var(--font-display);
  font-size: var(--text-xl);
  font-weight: 600;
  color: var(--color-ink);
}

.essence-card__measure {
  font-size: var(--text-xs);
  color: var(--color-ink-muted);
}

.essence-card__action {
  display: flex;
  align-items: center;
  gap: var(--space-xs);
  padding: var(--space-sm) var(--space-lg);
  background: var(--color-ink);
  color: var(--color-parchment);
  border: none;
  border-radius: var(--radius-md);
  font-family: var(--font-body);
  font-size: var(--text-sm);
  font-weight: 500;
  cursor: pointer;
  transition: all var(--transition-fast);
}

.essence-card__action:hover {
  background: var(--color-ink-light);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(42, 45, 38, 0.2);
}

.essence-card__action-icon {
  width: 16px;
  height: 16px;
}

.essence-card__action-text {
  font-size: var(--text-sm);
  font-weight: 500;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

/* Compendium Footer */
.compendium__footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--space-xl);
  padding-top: var(--space-2xl);
  border-top: 1px solid var(--color-parchment-dark);
}

.compendium__counter {
  display: flex;
  align-items: center;
  gap: var(--space-xs);
  font-family: var(--font-body);
  font-size: var(--text-sm);
  color: var(--color-ink-light);
}

.compendium__counter-current {
  font-weight: 600;
  color: var(--color-ink);
}

.compendium__counter-separator {
  opacity: 0.5;
}

.compendium__counter-total {
  font-weight: 600;
  color: var(--color-gold);
}

.compendium__counter-label {
  margin-left: var(--space-sm);
  font-size: var(--text-xs);
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

/* ============================================
   ALCHEMY SECTION
   ============================================ */
.alchemy {
  padding: var(--space-5xl) var(--container-padding);
  background: var(--color-ink);
  color: var(--color-parchment);
  position: relative;
  overflow: hidden;
}

/* Watermark */
.alchemy__watermark {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: var(--font-accent);
  font-size: 40vw;
  color: rgba(201, 167, 105, 0.03);
  white-space: nowrap;
  pointer-events: none;
  z-index: var(--z-base);
}

.alchemy__container {
  max-width: var(--container-max);
  margin: 0 auto;
  position: relative;
  z-index: var(--z-elevated);
}

/* Alchemy Header */
.alchemy__header {
  text-align: center;
  margin-bottom: var(--space-4xl);
}

.alchemy__header .section-label {
  color: var(--color-gold-light);
}

.alchemy__rule {
  width: 100px;
  height: 1px;
  background: linear-gradient(90deg, 
    transparent, 
    var(--color-gold), 
    transparent);
  margin: var(--space-xl) auto;
}

/* Alchemy Process */
.alchemy__process {
  display: flex;
  flex-direction: column;
  gap: var(--space-2xl);
  margin-bottom: var(--space-4xl);
}

.alchemy-step {
  display: grid;
  grid-template-columns: auto 1fr auto;
  gap: var(--space-xl);
  align-items: start;
  padding: var(--space-xl);
  background: rgba(201, 167, 105, 0.05);
  border: 1px solid rgba(201, 167, 105, 0.1);
  border-radius: var(--radius-xl);
  transition: all var(--transition-base);
}

.alchemy-step:hover {
  background: rgba(201, 167, 105, 0.1);
  border-color: var(--color-gold);
  transform: translateX(8px);
}

.alchemy-step__number {
  width: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--color-gold);
  color: var(--color-ink);
  border-radius: 50%;
  font-family: var(--font-display);
  font-size: var(--text-2xl);
  font-weight: 600;
}

.alchemy-step__content {
  flex: 1;
}

.alchemy-step__title {
  font-family: var(--font-display);
  font-size: var(--text-xl);
  margin-bottom: var(--space-sm);
  color: var(--color-gold-light);
}

.alchemy-step__title::after {
  content: '•';
  margin-left: var(--space-sm);
  color: var(--color-gold);
  opacity: 0.5;
}

.alchemy-step__description {
  font-size: var(--text-lg);
  line-height: 1.7;
  color: var(--color-gold-light);
  opacity: 0.8;
  margin-bottom: var(--space-lg);
}

.alchemy-step__details {
  display: flex;
  gap: var(--space-xl);
}

.alchemy-step__detail {
  display: flex;
  flex-direction: column;
}

.alchemy-step__detail-label {
  font-size: var(--text-xs);
  color: var(--color-gold-light);
  opacity: 0.6;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: var(--space-3xs);
}

.alchemy-step__detail-value {
  font-family: var(--font-body);
  font-size: var(--text-sm);
  font-weight: 600;
  color: var(--color-gold-light);
}

.alchemy-step__symbol {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: var(--text-2xl);
  color: var(--color-gold);
  opacity: 0.5;
}

/* Alchemy Apparatus */
.alchemy__apparatus {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-xl);
  text-align: center;
}

.apparatus__item {
  padding: var(--space-xl);
  background: rgba(201, 167, 105, 0.05);
  border: 1px solid rgba(201, 167, 105, 0.1);
  border-radius: var(--radius-xl);
  transition: all var(--transition-base);
}

.apparatus__item:hover {
  background: rgba(201, 167, 105, 0.1);
  border-color: var(--color-gold);
  transform: translateY(-4px);
}

.apparatus__illustration {
  width: 80px;
  height: 80px;
  margin: 0 auto var(--space-lg);
  background: linear-gradient(135deg, 
    rgba(201, 167, 105, 0.2) 0%,
    transparent 100%);
  border: 1px solid rgba(201, 167, 105, 0.3);
  border-radius: 50%;
  position: relative;
}

.apparatus__illustration::before {
  content: '';
  position: absolute;
  top: 20px;
  left: 20px;
  right: 20px;
  bottom: 20px;
  border: 1px dashed rgba(201, 167, 105, 0.3);
  border-radius: 50%;
}

.apparatus__caption {
  font-family: var(--font-body);
  font-size: var(--text-sm);
  color: var(--color-gold-light);
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

/* ============================================
   MANUSCRIPT SECTION
   ============================================ */
.manuscript {
  padding: var(--space-5xl) var(--container-padding);
  background: var(--color-parchment);
  position: relative;
  overflow: hidden;
}

/* Aged Paper Background */
.manuscript__paper {
  position: absolute;
  top: var(--space-3xl);
  right: var(--space-3xl);
  bottom: var(--space-3xl);
  left: var(--space-3xl);
  background: var(--color-parchment-dark);
  border-radius: var(--radius-xl);
  opacity: 0.3;
  pointer-events: none;
  z-index: var(--z-base);
}

.manuscript__stain {
  position: absolute;
  background: rgba(201, 167, 105, 0.1);
  border-radius: 50%;
  filter: blur(20px);
}

.manuscript__stain--1 {
  top: 20%;
  left: 10%;
  width: 200px;
  height: 200px;
}

.manuscript__stain--2 {
  bottom: 20%;
  right: 10%;
  width: 150px;
  height: 150px;
}

.manuscript__watermark {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, 
    rgba(201, 167, 105, 0.05) 0%,
    transparent 70%);
  border-radius: 50%;
}

.manuscript__container {
  max-width: var(--container-max);
  margin: 0 auto;
  position: relative;
  z-index: var(--z-elevated);
}

/* Manuscript Header */
.manuscript__header {
  text-align: center;
  margin-bottom: var(--space-4xl);
}

.manuscript__rule {
  width: 100px;
  height: 1px;
  background: linear-gradient(90deg, 
    transparent, 
    var(--color-gold), 
    transparent);
  margin: var(--space-xl) auto;
}

/* Manuscript Entries */
.manuscript__entries {
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--space-2xl);
  margin-bottom: var(--space-3xl);
}

@media (min-width: 768px) {
  .manuscript__entries {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .manuscript__entries {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* Manuscript Entry */
.manuscript-entry {
  background: var(--color-parchment);
  border: 1px solid var(--color-parchment-dark);
  border-radius: var(--radius-xl);
  padding: var(--space-xl);
  transition: all var(--transition-base);
  position: relative;
}

.manuscript-entry:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-lg);
  border-color: var(--color-gold);
}

.manuscript-entry--illuminated {
  grid-column: 1 / -1;
}

@media (min-width: 768px) {
  .manuscript-entry--illuminated {
    grid-column: span 2;
  }
}

@media (min-width: 1024px) {
  .manuscript-entry--illuminated {
    grid-column: span 1;
  }
}

/* Manuscript Entry Border */
.manuscript-entry__border {
  position: absolute;
  top: 16px;
  right: 16px;
  bottom: 16px;
  left: 16px;
  pointer-events: none;
}

.manuscript-entry__corner {
  position: absolute;
  width: 20px;
  height: 20px;
}

.manuscript-entry__corner--tl {
  top: 0;
  left: 0;
  border-top: 1px solid var(--color-gold);
  border-left: 1px solid var(--color-gold);
  opacity: 0.3;
}

.manuscript-entry__corner--tr {
  top: 0;
  right: 0;
  border-top: 1px solid var(--color-gold);
  border-right: 1px solid var(--color-gold);
  opacity: 0.3;
}

.manuscript-entry__corner--bl {
  bottom: 0;
  left: 0;
  border-bottom: 1px solid var(--color-gold);
  border-left: 1px solid var(--color-gold);
  opacity: 0.3;
}

.manuscript-entry__corner--br {
  bottom: 0;
  right: 0;
  border-bottom: 1px solid var(--color-gold);
  border-right: 1px solid var(--color-gold);
  opacity: 0.3;
}

/* Manuscript Entry Content */
.manuscript-entry__content {
  position: relative;
  z-index: 1;
}

/* Illuminated Initial */
.manuscript-entry__initial {
  position: absolute;
  top: -20px;
  left: -20px;
  font-family: var(--font-accent);
  font-size: 6rem;
  color: var(--color-gold);
  opacity: 0.1;
  z-index: -1;
}

/* Quote */
.manuscript-entry__quote {
  margin-bottom: var(--space-xl);
}

.manuscript-entry__quote p {
  font-size: var(--text-lg);
  line-height: 1.7;
  color: var(--color-ink-light);
  font-style: italic;
  position: relative;
  padding-left: var(--space-lg);
}

.manuscript-entry__quote p::before {
  content: '"';
  position: absolute;
  top: -10px;
  left: 0;
  font-family: var(--font-accent);
  font-size: var(--text-3xl);
  color: var(--color-gold);
  opacity: 0.3;
}

/* Attribution */
.manuscript-entry__attribution {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  flex-wrap: wrap;
  gap: var(--space-md);
}

.manuscript-entry__author {
  display: flex;
  flex-direction: column;
}

.manuscript-entry__name {
  font-family: var(--font-display);
  font-size: var(--text-lg);
  font-weight: 600;
  color: var(--color-ink);
  font-style: normal;
  margin-bottom: var(--space-3xs);
}

.manuscript-entry__title {
  font-size: var(--text-sm);
  color: var(--color-ink-muted);
}

.manuscript-entry__seal {
  padding: var(--space-xs) var(--space-sm);
  background: rgba(201, 167, 105, 0.1);
  border-radius: var(--radius-full);
}

.manuscript-entry__seal-text {
  font-size: var(--text-xs);
  font-weight: 600;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  color: var(--color-gold);
}

/* Folio */
.manuscript-entry__folio {
  margin-top: var(--space-xl);
  padding-top: var(--space-md);
  border-top: 1px solid var(--color-parchment-dark);
}

.manuscript-entry__folio-number {
  font-family: var(--font-body);
  font-size: var(--text-xs);
  color: var(--color-ink-muted);
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

/* Manuscript Navigation */
.manuscript__navigation {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-xl);
}

.manuscript__nav-button {
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--color-parchment);
  border: 1px solid var(--color-parchment-dark);
  border-radius: var(--radius-md);
  color: var(--color-ink);
  cursor: pointer;
  transition: all var(--transition-fast);
}

.manuscript__nav-button:hover {
  background: rgba(201, 167, 105, 0.1);
  border-color: var(--color-gold);
  color: var(--color-gold);
  transform: translateY(-2px);
}

.manuscript__nav-button svg {
  width: 20px;
  height: 20px;
}

.manuscript__pagination {
  display: flex;
  align-items: center;
  gap: var(--space-xs);
  font-family: var(--font-body);
  font-size: var(--text-sm);
  color: var(--color-ink);
}

.manuscript__page-current {
  font-weight: 600;
}

.manuscript__page-separator {
  opacity: 0.5;
}

.manuscript__page-total {
  color: var(--color-gold);
  font-weight: 600;
}

/* ============================================
   CORRESPONDENCE SECTION
   ============================================ */
.correspondence {
  padding: var(--space-5xl) var(--container-padding);
  background: var(--color-ink);
  color: var(--color-parchment);
  position: relative;
  overflow: hidden;
}

/* Wax Seal Background */
.correspondence__seal {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 400px;
  height: 400px;
  opacity: 0.05;
  pointer-events: none;
  z-index: var(--z-base);
}

.correspondence__seal-ring {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border: 2px solid var(--color-gold);
  border-radius: 50%;
}

.correspondence__seal-center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 100px;
  height: 100px;
  background: var(--color-gold);
  border-radius: 50%;
}

.correspondence__container {
  max-width: var(--container-max);
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--space-4xl);
  align-items: center;
  position: relative;
  z-index: var(--z-elevated);
}

@media (min-width: 1024px) {
  .correspondence__container {
    grid-template-columns: 1fr 1fr;
    gap: var(--space-5xl);
  }
}

/* Correspondence Content */
.correspondence__content {
  text-align: center;
}

@media (min-width: 1024px) {
  .correspondence__content {
    text-align: left;
  }
}

.correspondence__title {
  font-family: var(--font-display);
  font-size: var(--text-3xl);
  line-height: 1.1;
  margin-bottom: var(--space-md);
}

.correspondence__title-line {
  display: block;
}

.correspondence__title-line--emph {
  color: var(--color-gold);
  font-weight: 400;
}

.correspondence__rule {
  width: 100px;
  height: 1px;
  background: linear-gradient(90deg, 
    var(--color-gold), 
    transparent);
  margin: var(--space-xl) 0;
}

@media (min-width: 1024px) {
  .correspondence__rule {
    margin-left: 0;
  }
}

.correspondence__description {
  font-size: var(--text-lg);
  line-height: 1.7;
  color: var(--color-gold-light);
  margin-bottom: var(--space-2xl);
  max-width: 500px;
}

@media (min-width: 1024px) {
  .correspondence__description {
    margin-left: 0;
  }
}

/* Correspondence Form */
.correspondence__form {
  max-width: 500px;
}

@media (min-width: 1024px) {
  .correspondence__form {
    margin-left: 0;
  }
}

.correspondence__field {
  position: relative;
  margin-bottom: var(--space-lg);
}

.correspondence__input {
  width: 100%;
  padding: var(--space-md) var(--space-lg);
  background: rgba(250, 248, 245, 0.1);
  border: 1px solid rgba(201, 167, 105, 0.3);
  border-radius: var(--radius-md);
  font-family: var(--font-body);
  font-size: var(--text-sm);
  color: var(--color-parchment);
  transition: all var(--transition-fast);
}

.correspondence__input:focus {
  outline: none;
  background: rgba(250, 248, 245, 0.15);
  border-color: var(--color-gold);
  box-shadow: 0 0 0 2px rgba(201, 167, 105, 0.2);
}

.correspondence__input::placeholder {
  color: rgba(201, 167, 105, 0.6);
}

.correspondence__field-ornament {
  position: absolute;
  top: 50%;
  right: var(--space-lg);
  transform: translateY(-50%);
  width: 6px;
  height: 6px;
  background: var(--color-gold);
  border-radius: 50%;
  opacity: 0;
  transition: opacity var(--transition-fast);
}

.correspondence__input:focus + .correspondence__field-ornament {
  opacity: 1;
}

.correspondence__consent {
  display: flex;
  align-items: flex-start;
  gap: var(--space-sm);
  margin-bottom: var(--space-2xl);
}

.correspondence__checkbox {
  margin-top: 4px;
  accent-color: var(--color-gold);
}

.correspondence__consent-label {
  font-size: var(--text-sm);
  line-height: 1.5;
  color: var(--color-gold-light);
  cursor: pointer;
}

.correspondence__submit {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-sm);
  width: 100%;
  padding: var(--space-md) var(--space-xl);
  background: var(--color-gold);
  color: var(--color-ink);
  border: none;
  border-radius: var(--radius-md);
  font-family: var(--font-body);
  font-size: var(--text-sm);
  font-weight: 500;
  cursor: pointer;
  transition: all var(--transition-base);
}

.correspondence__submit:hover {
  background: var(--color-gold-light);
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(201, 167, 105, 0.3);
}

.correspondence__submit-text {
  font-weight: 500;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.correspondence__submit-icon {
  width: 20px;
  height: 20px;
}

/* Correspondence Visual */
.correspondence__visual {
  display: none;
}

@media (min-width: 1024px) {
  .correspondence__visual {
    display: block;
    position: relative;
    height: 400px;
  }
}

/* Envelope */
.correspondence__envelope {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 300px;
  height: 200px;
}

.envelope__flap {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 100px;
  background: var(--color-parchment);
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
  border: 1px solid rgba(201, 167, 105, 0.3);
  border-bottom: none;
}

.envelope__body {
  position: absolute;
  top: 50px;
  left: 0;
  right: 0;
  bottom: 0;
  background: var(--color-parchment);
  border: 1px solid rgba(201, 167, 105, 0.3);
  border-top: none;
  border-radius: 0 0 var(--radius-lg) var(--radius-lg);
}

.envelope__wax-seal {
  position: absolute;
  top: 30px;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 60px;
  z-index: 2;
}

.wax-seal__ring {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: var(--color-rose);
  border-radius: 50%;
  box-shadow: 0 4px 12px rgba(184, 125, 125, 0.3);
}

.wax-seal__initial {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: var(--font-accent);
  font-size: var(--text-2xl);
  color: var(--color-parchment);
}

/* Quill */
.correspondence__quill {
  position: absolute;
  bottom: 20px;
  right: 40px;
  width: 40px;
  height: 120px;
  animation: writeQuill 4s ease-in-out infinite;
}

@keyframes writeQuill {
  0%, 100% { 
    transform: translateY(0) rotate(0deg); 
  }
  50% { 
    transform: translateY(-20px) rotate(-10deg); 
  }
}

.quill__feather {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 30px;
  height: 40px;
  background: linear-gradient(45deg, 
    var(--color-gold) 0%,
    var(--color-gold-light) 50%,
    var(--color-gold) 100%);
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
  border-radius: 50% 50% 0 0;
}

.quill__shaft {
  position: absolute;
  top: 40px;
  left: 50%;
  transform: translateX(-50%);
  width: 4px;
  height: 60px;
  background: var(--color-sage);
  border-radius: var(--radius-full);
}

.quill__nib {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 6px;
  height: 20px;
  background: var(--color-ink);
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
}

/* ============================================
   COLOPHON (FOOTER)
   ============================================ */
.colophon {
  background: var(--color-ink);
  color: var(--color-parchment);
  padding: var(--space-4xl) var(--container-padding) 0;
  position: relative;
}

.colophon__container {
  max-width: var(--container-max);
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--space-3xl);
  margin-bottom: var(--space-3xl);
}

@media (min-width: 768px) {
  .colophon__container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .colophon__container {
    grid-template-columns: repeat(4, 1fr);
  }
}

/* Atelier Information */
.colophon__atelier {
  display: flex;
  flex-direction: column;
  gap: var(--space-lg);
}

.colophon__seal {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
  text-decoration: none;
  color: inherit;
}

.colophon__seal-graphic {
  width: 40px;
  height: 40px;
  border: 1px solid var(--color-gold);
  border-radius: 50%;
  position: relative;
}

.colophon__seal-graphic::before {
  content: '';
  position: absolute;
  top: 10px;
  left: 10px;
  right: 10px;
  bottom: 10px;
  border: 1px dashed var(--color-gold);
  border-radius: 50%;
  opacity: 0.5;
}

.colophon__atelier-name {
  font-family: var(--font-display);
  font-size: var(--text-xl);
  font-weight: 600;
}

.colophon__address {
  font-style: normal;
  line-height: 1.6;
  color: var(--color-gold-light);
}

.colophon__address p {
  margin-bottom: var(--space-xs);
}

.colophon__hours {
  line-height: 1.6;
  color: var(--color-ink-muted);
  font-size: var(--text-sm);
}

.colophon__hours p {
  margin-bottom: var(--space-xs);
}

/* Navigation */
.colophon__navigation,
.colophon__correspondence,
.colophon__details {
  display: flex;
  flex-direction: column;
  gap: var(--space-lg);
}

.colophon__heading {
  font-family: var(--font-display);
  font-size: var(--text-lg);
  font-weight: 600;
  color: var(--color-gold-light);
  margin-bottom: var(--space-sm);
}

.colophon__list {
  display: flex;
  flex-direction: column;
  gap: var(--space-sm);
}

.colophon__link {
  color: var(--color-gold-light);
  text-decoration: none;
  transition: color var(--transition-fast);
  font-size: var(--text-sm);
}

.colophon__link:hover {
  color: var(--color-gold);
}

.colophon__list li {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
}

.colophon__icon {
  flex-shrink: 0;
  color: var(--color-gold);
}

/* Social */
.colophon__social {
  display: flex;
  gap: var(--space-md);
  margin-top: var(--space-lg);
}

.colophon__social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background: rgba(201, 167, 105, 0.1);
  border-radius: var(--radius-md);
  color: var(--color-gold-light);
  transition: all var(--transition-fast);
}

.colophon__social-link:hover {
  background: var(--color-gold);
  color: var(--color-ink);
  transform: translateY(-2px);
}

.colophon__social-icon {
  width: 20px;
  height: 20px;
}

/* Colophon Details */
.colophon__text {
  font-size: var(--text-sm);
  line-height: 1.6;
  color: var(--color-ink-muted);
}

.colophon__text p {
  margin-bottom: var(--space-sm);
}

/* Colophon Bottom */
.colophon__bottom {
  background: rgba(0, 0, 0, 0.2);
  padding: var(--space-xl) var(--container-padding);
}

.colophon__bottom-container {
  max-width: var(--container-max);
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: var(--space-lg);
  align-items: center;
  text-align: center;
}

@media (min-width: 768px) {
  .colophon__bottom-container {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    text-align: left;
  }
}

.colophon__copyright {
  font-size: var(--text-sm);
  color: var(--color-ink-muted);
}

.colophon__legal {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-lg);
  justify-content: center;
}

@media (min-width: 768px) {
  .colophon__legal {
    justify-content: flex-end;
  }
}

.colophon__legal-link {
  font-size: var(--text-sm);
  color: var(--color-gold-light);
  text-decoration: none;
  transition: color var(--transition-fast);
}

.colophon__legal-link:hover {
  color: var(--color-gold);
}

/* ============================================
   BACK TO TOP
   ============================================ */
.back-to-top {
  position: fixed;
  bottom: var(--space-xl);
  right: var(--space-xl);
  width: 56px;
  height: 56px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--color-ink);
  color: var(--color-parchment);
  border: 1px solid var(--color-parchment-dark);
  border-radius: var(--radius-md);
  cursor: pointer;
  opacity: 0;
  visibility: hidden;
  transform: translateY(20px);
  transition: all var(--transition-base);
  z-index: var(--z-overlay);
}

.back-to-top.visible {
  opacity: 1;
  visibility: visible;
  transform: translateY(0);
}

.back-to-top:hover {
  background: var(--color-ink-light);
  border-color: var(--color-gold);
  transform: translateY(-4px);
}

.back-to-top__icon {
  width: 24px;
  height: 24px;
}

/* ============================================
   VIAL DRAWER (CART)
   ============================================ */
.vial-drawer {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  max-width: 400px;
  background: var(--color-parchment);
  box-shadow: var(--shadow-xl);
  transform: translateX(100%);
  transition: transform var(--transition-base) cubic-bezier(0.4, 0, 0.2, 1);
  z-index: var(--z-modal);
  display: flex;
  flex-direction: column;
}

@media (min-width: 640px) {
  .vial-drawer {
    width: 400px;
  }
}

.vial-drawer.active {
  transform: translateX(0);
}

.vial-drawer__container {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.vial-drawer__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--space-xl);
  border-bottom: 1px solid var(--color-parchment-dark);
}

.vial-drawer__title {
  font-family: var(--font-display);
  font-size: var(--text-xl);
  font-weight: 600;
  color: var(--color-ink);
}

.vial-drawer__close {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: transparent;
  border: none;
  color: var(--color-ink);
  cursor: pointer;
  border-radius: var(--radius-md);
  transition: all var(--transition-fast);
}

.vial-drawer__close:hover {
  background: rgba(201, 167, 105, 0.1);
}

.vial-drawer__content {
  flex: 1;
  overflow-y: auto;
  padding: var(--space-xl);
}

.vial-drawer__footer {
  padding: var(--space-xl);
  border-top: 1px solid var(--color-parchment-dark);
}

.vial-drawer__total {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: var(--space-lg);
}

.vial-drawer__total-label {
  font-size: var(--text-sm);
  color: var(--color-ink-muted);
}

.vial-drawer__total-value {
  font-family: var(--font-display);
  font-size: var(--text-2xl);
  font-weight: 600;
  color: var(--color-ink);
}

/* ============================================
   TOAST NOTIFICATION
   ============================================ */
.toast {
  position: fixed;
  bottom: var(--space-xl);
  left: 50%;
  transform: translateX(-50%) translateY(100px);
  display: flex;
  align-items: center;
  gap: var(--space-sm);
  padding: var(--space-md) var(--space-lg);
  background: var(--color-ink);
  color: var(--color-parchment);
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-lg);
  opacity: 0;
  visibility: hidden;
  transition: all var(--transition-base);
  z-index: var(--z-toast);
  max-width: calc(100% - var(--space-xl) * 2);
}

.toast.active {
  opacity: 1;
  visibility: visible;
  transform: translateX(-50%) translateY(0);
}

.toast__content {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
}

.toast__seal {
  position: relative;
  width: 20px;
  height: 20px;
}

.toast__seal-ring {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border: 2px solid var(--color-gold);
  border-radius: 50%;
}

.toast__message {
  font-size: var(--text-sm);
  font-weight: 500;
}

/* ============================================
   UTILITY CLASSES & ANIMATIONS
   ============================================ */
@keyframes pulse {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.7; transform: scale(1.05); }
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .hero__title {
    font-size: var(--text-4xl);
  }
  
  .section-title {
    font-size: var(--text-2xl);
  }
  
  .alchemy-step {
    grid-template-columns: 1fr;
    gap: var(--space-lg);
  }
  
  .alchemy-step__symbol {
    display: none;
  }
  
  .alchemy__apparatus {
    grid-template-columns: 1fr;
  }
}

/* Print Styles */
@media print {
  .header,
  .atelier-banner,
  .hero__scroll-indicator,
  .back-to-top,
  .correspondence,
  .colophon__social,
  .vial-drawer,
  .toast,
  .texture-overlay,
  .gold-leaf {
    display: none !important;
  }
  
  body {
    color: #000;
    background: #fff;
  }
  
  .essence-card {
    break-inside: avoid;
    border: 1px solid #ddd;
  }
  
  .hero {
    min-height: auto;
    padding: var(--space-2xl) 0;
  }
}
```
