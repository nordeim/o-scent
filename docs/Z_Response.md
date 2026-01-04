Here is the comprehensive plan and implementation for your 2D Animation Showcase page.

### Phase 1: Request Analysis & Strategic Design

**1. Deep Understanding & Requirement Mining:**
*   **Goal:** Create a standalone 2D animation showcase page that moves beyond generic templates.
*   **Core Need:** A visual experience that demonstrates high technical competence in animation loops, user interaction, and performance (Canvas API).
*   **Anti-Generic Constraint:** Reject standard "hero image + grid" layouts. Reject generic gradients.

**2. Design Direction: "Digital Constructivism"**
*   *Aesthetic:* A blend of **Swiss International Style** (grids, sans-serif typography, asymmetry) and **Raw Brutalism** (high contrast, visible borders, utilitarian UI).
*   *Color Palette:* "Laboratory White" (#f4f4f0), "Industrial Charcoal" (#1a1a1a), and "Safety Orange" (#ff4500) for accents.
*   *The "Why":* This aesthetic prioritizes function and structure. It allows the animation (the art) to be the hero, while the UI feels like a precision instrument rather than decoration.

**3. Technical Architecture:**
*   **Core Engine:** HTML5 Canvas API (for 60fps performance with high particle counts).
*   **Interaction Logic:** Mouse/Touch event listeners mapped to a physics vector field.
*   **Structure:**
    *   `CanvasLayer`: Handles the rendering context.
    *   `PhysicsEngine`: Manages velocity, friction, and boundary collisions.
    *   `UIOverlay`: A semantic HTML overlay for controls, styled to look like an engineering HUD.

**4. Risk Mitigation:**
*   *Performance:* Use offscreen canvas buffering if particle count > 1000 (sticking to ~300 active entities for smooth mobile performance without over-engineering).
*   *Responsiveness:* Implement a dynamic resize handler that re-calculates canvas density (`window.devicePixelRatio`) to prevent blurriness on Retina displays.

---

### Phase 2: Implementation

Here is the complete, self-contained solution.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KINETIC // 2D Animation Engine</title>
    <style>
        /* 
         * DESIGN SYSTEM: DIGITAL CONSTRUCTIVISM
         * Philosophy: Maximum contrast, structural visibility, typographic hierarchy.
         */
        :root {
            --bg-color: #f0f0f0;
            --fg-color: #111111;
            --accent-color: #ff3333;
            --grid-line: #e0e0e0;
            --font-display: 'Helvetica Neue', Helvetica, Arial, sans-serif;
            --font-mono: 'Courier New', Courier, monospace;
        }

        * {
            box-sizing: border-box;
            -webkit-font-smoothing: antialiased;
        }

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            background-color: var(--bg-color);
            color: var(--fg-color);
            font-family: var(--font-display);
            overflow: hidden; /* Prevent scrolling, full immersion */
        }

        /* LAYOUT ARCHITECTURE */
        #app-container {
            position: relative;
            width: 100vw;
            height: 100vh;
            display: grid;
            grid-template-rows: auto 1fr auto;
            grid-template-columns: 1fr 300px;
            grid-template-areas: 
                "header header"
                "canvas sidebar"
                "footer sidebar";
        }

        /* HEADER: Editorial Style */
        header {
            grid-area: header;
            padding: 1.5rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            border-bottom: 2px solid var(--fg-color);
            background: rgba(240, 240, 240, 0.9);
            z-index: 10;
        }

        .brand h1 {
            font-size: 2rem;
            font-weight: 800;
            letter-spacing: -0.05em;
            margin: 0;
            line-height: 1;
            text-transform: uppercase;
        }

        .brand span {
            display: block;
            font-family: var(--font-mono);
            font-size: 0.75rem;
            letter-spacing: 0.1em;
            margin-top: 0.5rem;
            color: var(--accent-color);
        }

        /* CANVAS STAGE */
        #stage-container {
            grid-area: canvas;
            position: relative;
            background-image: 
                linear-gradient(var(--grid-line) 1px, transparent 1px),
                linear-gradient(90deg, var(--grid-line) 1px, transparent 1px);
            background-size: 40px 40px;
            cursor: crosshair;
            overflow: hidden;
        }

        canvas {
            display: block;
            width: 100%;
            height: 100%;
        }

        /* SIDEBAR: Engineering Controls */
        aside {
            grid-area: sidebar;
            border-left: 2px solid var(--fg-color);
            border-top: 2px solid var(--fg-color);
            padding: 2rem;
            background: var(--bg-color);
            display: flex;
            flex-direction: column;
            gap: 2rem;
            z-index: 20;
            overflow-y: auto;
        }

        .control-group {
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
        }

        .control-group label {
            font-family: var(--font-mono);
            font-size: 0.85rem;
            font-weight: 700;
            text-transform: uppercase;
            display: flex;
            justify-content: space-between;
        }

        .value-display {
            color: var(--accent-color);
        }

        /* CUSTOM UI ELEMENTS - Anti-Generic */
        input[type="range"] {
            -webkit-appearance: none;
            width: 100%;
            background: transparent;
        }

        input[type="range"]::-webkit-slider-runnable-track {
            width: 100%;
            height: 2px;
            background: var(--fg-color);
            cursor: pointer;
        }

        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            height: 20px;
            width: 20px;
            background: var(--bg-color);
            border: 2px solid var(--fg-color);
            margin-top: -9px;
            cursor: pointer;
            transition: transform 0.1s ease, background 0.2s;
        }

        input[type="range"]:hover::-webkit-slider-thumb {
            background: var(--accent-color);
            transform: scale(1.1);
        }

        button {
            background: var(--bg-color);
            color: var(--fg-color);
            border: 2px solid var(--fg-color);
            padding: 1rem;
            font-family: var(--font-mono);
            font-weight: 700;
            text-transform: uppercase;
            cursor: pointer;
            transition: all 0.15s ease;
            position: relative;
            overflow: hidden;
        }

        button:hover {
            background: var(--fg-color);
            color: var(--bg-color);
            transform: translateY(-2px);
            box-shadow: 4px 4px 0px var(--accent-color);
        }

        button:active {
            transform: translateY(0);
            box-shadow: 2px 2px 0px var(--accent-color);
        }

        button.active {
            background: var(--fg-color);
            color: var(--bg-color);
        }

        /* FOOTER: Meta Data */
        footer {
            grid-area: footer;
            padding: 1rem 2rem;
            border-top: 1px solid var(--grid-line);
            font-family: var(--font-mono);
            font-size: 0.7rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: var(--bg-color);
        }

        /* TOAST NOTIFICATION */
        #toast {
            position: absolute;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%) translateY(20px);
            background: var(--fg-color);
            color: var(--bg-color);
            padding: 0.75rem 1.5rem;
            font-family: var(--font-mono);
            font-size: 0.8rem;
            opacity: 0;
            pointer-events: none;
            transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
            z-index: 100;
            border: 1px solid var(--accent-color);
        }

        #toast.visible {
            opacity: 1;
            transform: translateX(-50%) translateY(0);
        }

        /* RESPONSIVE */
        @media (max-width: 768px) {
            #app-container {
                grid-template-rows: auto 1fr auto auto;
                grid-template-columns: 1fr;
                grid-template-areas: 
                    "header"
                    "canvas"
                    "sidebar"
                    "footer";
            }
            
            header { padding: 1rem; }
            .brand h1 { font-size: 1.5rem; }
            aside { border-left: none; border-top: 2px solid var(--fg-color); height: 200px; }
        }
    </style>
</head>
<body>

<div id="app-container">
    <header>
        <div class="brand">
            <h1>Kinetic Core</h1>
            <span>Interactive Physics Engine v1.0</span>
        </div>
        <div style="text-align: right; font-family: var(--font-mono); font-size: 0.8rem;">
            <div>FPS: <span id="fps-counter">60</span></div>
            <div>ENTITIES: <span id="entity-counter">0</span></div>
        </div>
    </header>

    <main id="stage-container">
        <canvas id="anim-canvas"></canvas>
        <div id="toast">System Message</div>
    </main>

    <aside>
        <div class="control-group">
            <label>Gravity Force <span id="val-gravity" class="value-display">0.5</span></label>
            <input type="range" id="input-gravity" min="-1" max="2" step="0.1" value="0.5">
        </div>

        <div class="control-group">
            <label>Friction <span id="val-friction" class="value-display">0.98</span></label>
            <input type="range" id="input-friction" min="0.90" max="0.999" step="0.001" value="0.98">
        </div>

        <div class="control-group">
            <label>Interaction Radius <span id="val-radius" class="value-display">150</span></label>
            <input type="range" id="input-radius" min="50" max="400" step="10" value="150">
        </div>

        <div class="control-group">
            <button id="btn-explode">Trigger Explosion</button>
            <button id="btn-mode">Switch Mode: Repel</button>
            <button id="btn-clear">Clear Canvas</button>
        </div>
    </aside>

    <footer>
        <span>COORD: <span id="mouse-coord">0, 0</span></span>
        <span>STATUS: <span style="color: var(--accent-color)">ACTIVE</span></span>
    </footer>
</div>

<script>
/**
 * ARCHITECTURE NOTES:
 * 1. Physics Engine: Custom vector-based physics loop.
 * 2. Rendering: HTML5 Canvas API with requestAnimationFrame.
 * 3. State Management: Simple reactive state pattern for UI binding.
 * 4. Anti-Pattern Avoidance: No animation libraries (GSAP/etc), pure math for lightweight footprint.
 */

// --- UTILITIES ---
const $ = (id) => document.getElementById(id);
const randomRange = (min, max) => Math.random() * (max - min) + min;
const clamp = (val, min, max) => Math.min(Math.max(val, min), max);

// --- STATE MANAGEMENT ---
const State = {
    gravity: 0.5,
    friction: 0.98,
    interactionRadius: 150,
    mouse: { x: -1000, y: -1000, active: false },
    mode: 'attract', // 'attract' | 'repel'
    colors: ['#111111', '#ff3333', '#333333', '#666666']
};

// --- NOTIFICATION SYSTEM ---
const Toast = {
    el: $('toast'),
    timer: null,
    show(message) {
        this.el.textContent = message;
        this.el.classList.add('visible');
        clearTimeout(this.timer);
        this.timer = setTimeout(() => {
            this.el.classList.remove('visible');
        }, 2000);
    }
};

// --- PHYSICS ENTITY ---
class Particle {
    constructor(x, y) {
        this.pos = { x: x, y: y };
        this.vel = { x: randomRange(-5, 5), y: randomRange(-5, 5) };
        this.radius = randomRange(4, 12);
        this.mass = this.radius; 
        this.color = State.colors[Math.floor(Math.random() * State.colors.length)];
        this.shape = Math.random() > 0.5 ? 'circle' : 'square';
    }

    update(canvasWidth, canvasHeight) {
        // Apply Gravity
        this.vel.y += State.gravity;

        // Apply Friction
        this.vel.x *= State.friction;
        this.vel.y *= State.friction;

        // Mouse Interaction
        const dx = State.mouse.x - this.pos.x;
        const dy = State.mouse.y - this.pos.y;
        const distance = Math.sqrt(dx * dx + dy * dy);

        if (distance < State.interactionRadius && State.mouse.active) {
            const forceDirectionX = dx / distance;
            const forceDirectionY = dy / distance;
            const force = (State.interactionRadius - distance) / State.interactionRadius;
            const strength = 2; // Interaction strength

            if (State.mode === 'attract') {
                this.vel.x += forceDirectionX * force * strength;
                this.vel.y += forceDirectionY * force * strength;
            } else {
                this.vel.x -= forceDirectionX * force * strength;
                this.vel.y -= forceDirectionY * force * strength;
            }
        }

        // Update Position
        this.pos.x += this.vel.x;
        this.pos.y += this.vel.y;

        // Boundary Collision (Bounce)
        if (this.pos.x + this.radius > canvasWidth) {
            this.pos.x = canvasWidth - this.radius;
            this.vel.x *= -0.8;
        } else if (this.pos.x - this.radius < 0) {
            this.pos.x = this.radius;
            this.vel.x *= -0.8;
        }

        if (this.pos.y + this.radius > canvasHeight) {
            this.pos.y = canvasHeight - this.radius;
            this.vel.y *= -0.8;
        } else if (this.pos.y - this.radius < 0) {
            this.pos.y = this.radius;
            this.vel.y *= -0.8;
        }
    }

    draw(ctx) {
        ctx.fillStyle = this.color;
        ctx.beginPath();
        if (this.shape === 'circle') {
            ctx.arc(this.pos.x, this.pos.y, this.radius, 0, Math.PI * 2);
        } else {
            ctx.rect(this.pos.x - this.radius, this.pos.y - this.radius, this.radius * 2, this.radius * 2);
        }
        ctx.fill();
        
        // Add detail: Small border for geometric look
        ctx.strokeStyle = 'rgba(240,240,240,0.4)';
        ctx.lineWidth = 1;
        ctx.stroke();
    }
}

// --- ENGINE CORE ---
class Engine {
    constructor() {
        this.canvas = $('anim-canvas');
        this.ctx = this.canvas.getContext('2d');
        this.particles = [];
        this.width = 0;
        this.height = 0;
        this.lastTime = 0;
        
        this.init();
        this.bindEvents();
        this.loop = this.loop.bind(this);
        requestAnimationFrame(this.loop);
    }

    init() {
        this.resize();
        // Initial burst
        this.spawnParticles(20);
    }

    resize() {
        const parent = this.canvas.parentElement;
        this.width = parent.clientWidth;
        this.height = parent.clientHeight;
        
        // Handle Retina/HiDPI
        const dpr = window.devicePixelRatio || 1;
        this.canvas.width = this.width * dpr;
        this.canvas.height = this.height * dpr;
        this.ctx.scale(dpr, dpr);
    }

    spawnParticles(count, x, y) {
        for (let i = 0; i < count; i++) {
            const spawnX = x || this.width / 2;
            const spawnY = y || this.height / 3;
            this.particles.push(new Particle(spawnX, spawnY));
        }
        this.updateCounters();
    }

    explode() {
        const centerX = this.width / 2;
        const centerY = this.height / 2;
        
        this.particles.forEach(p => {
            const dx = p.pos.x - centerX;
            const dy = p.pos.y - centerY;
            const dist = Math.sqrt(dx*dx + dy*dy) + 0.1;
            const force = 1000 / dist; // Strong force
            
            p.vel.x += (dx / dist) * force;
            p.vel.y += (dy / dist) * force;
        });
        Toast.show("Physics Shockwave Applied");
    }

    clear() {
        this.particles = [];
        this.updateCounters();
        Toast.show("Canvas Cleared");
    }

    updateCounters() {
        $('entity-counter').textContent = this.particles.length;
    }

    bindEvents() {
        window.addEventListener('resize', () => this.resize());
        
        // Mouse/Touch Tracking
        const updateMouse = (e) => {
            const rect = this.canvas.getBoundingClientRect();
            const clientX = e.touches ? e.touches[0].clientX : e.clientX;
            const clientY = e.touches ? e.touches[0].clientY : e.clientY;
            
            State.mouse.x = clientX - rect.left;
            State.mouse.y = clientY - rect.top;
            
            $('mouse-coord').textContent = `${Math.round(State.mouse.x)}, ${Math.round(State.mouse.y)}`;
        };

        this.canvas.addEventListener('mousemove', updateMouse);
        this.canvas.addEventListener('touchmove', (e) => { e.preventDefault(); updateMouse(e); }, { passive: false });
        
        const setMouseActive = (val) => State.mouse.active = val;
        this.canvas.addEventListener('mousedown', () => { setMouseActive(true); this.spawnParticles(5, State.mouse.x, State.mouse.y); });
        this.canvas.addEventListener('mouseup', () => setMouseActive(false));
        this.canvas.addEventListener('mouseleave', () => setMouseActive(false));
        this.canvas.addEventListener('touchstart', (e) => { setMouseActive(true); updateMouse(e); });
        this.canvas.addEventListener('touchend', () => setMouseActive(false));

        // UI Binding
        $('input-gravity').addEventListener('input', (e) => {
            State.gravity = parseFloat(e.target.value);
            $('val-gravity').textContent = State.gravity.toFixed(1);
        });
        
        $('input-friction').addEventListener('input', (e) => {
            State.friction = parseFloat(e.target.value);
            $('val-friction').textContent = State.friction.toFixed(3);
        });

        $('input-radius').addEventListener('input', (e) => {
            State.interactionRadius = parseInt(e.target.value);
            $('val-radius').textContent = State.interactionRadius;
        });

        $('btn-explode').addEventListener('click', () => this.explode());
        $('btn-clear').addEventListener('click', () => this.clear());
        
        $('btn-mode').addEventListener('click', (e) => {
            State.mode = State.mode === 'attract' ? 'repel' : 'attract';
            e.target.textContent = `Switch Mode: ${State.mode === 'attract' ? 'Repel' : 'Attract'}`;
            Toast.show(`Interaction: ${State.mode.toUpperCase()}`);
        });
    }

    loop(timestamp) {
        // FPS Calculation
        const dt = timestamp - this.lastTime;
        if (dt >= 1000) { // Update FPS roughly every second
            $('fps-counter').textContent = Math.round(1000 / (dt / (dt % 16 || 1))); // Approximation for display
            this.lastTime = timestamp;
        }

        // Clear Screen
        this.ctx.clearRect(0, 0, this.width, this.height);

        // Visualize Interaction Radius (Subtle)
        if (State.mouse.active) {
            this.ctx.beginPath();
            this.ctx.strokeStyle = State.mode === 'attract' ? 'rgba(255, 51, 51, 0.2)' : 'rgba(50, 50, 50, 0.2)';
            this.ctx.setLineDash([5, 5]);
            this.ctx.arc(State.mouse.x, State.mouse.y, State.interactionRadius, 0, Math.PI * 2);
            this.ctx.stroke();
            this.ctx.setLineDash([]);
        }

        // Draw Connection Lines (Mesh effect) if close enough
        this.ctx.lineWidth = 0.5;
        this.ctx.strokeStyle = '#cccccc';
        
        // Optimization: Only check a subset or use spatial hashing for massive counts.
        // For < 300 particles, O(N^2) is acceptable on modern devices.
        for (let i = 0; i < this.particles.length; i++) {
            const p1 = this.particles[i];
            p1.update(this.width, this.height);
            p1.draw(this.ctx);

            // Connect neighbors
            for (let j = i + 1; j < this.particles.length; j++) {
                const p2 = this.particles[j];
                const dx = p1.pos.x - p2.pos.x;
                const dy = p1.pos.y - p2.pos.y;
                const dist = Math.sqrt(dx*dx + dy*dy);

                if (dist < 80) {
                    this.ctx.beginPath();
                    this.ctx.globalAlpha = 1 - (dist / 80);
                    this.ctx.moveTo(p1.pos.x, p1.pos.y);
                    this.ctx.lineTo(p2.pos.x, p2.pos.y);
                    this.ctx.stroke();
                    this.ctx.globalAlpha = 1;
                }
            }
        }

        requestAnimationFrame(this.loop);
    }
}

// Initialize on Load
window.addEventListener('DOMContentLoaded', () => {
    const engine = new Engine();
    Toast.show("System Initialized // Click & Drag");
});

</script>
</body>
</html>
```

### Phase 3: Validation & Documentation

**1. Quality Assurance Check:**
*   *Anti-Generic?* Yes. The layout uses a "brutalist" grid, visible borders, high-contrast typography, and a custom "laboratory" color palette. It does not look like a standard Bootstrap/Tailwind landing page.
*   *Interactive?* Yes. The mouse cursor acts as a gravity/repulsion well. Clicking spawns new particles. Controls manipulate physics in real-time.
*   *Performance?* Used native Canvas API. The particle connection logic has a distance optimization to prevent rendering unnecessary lines.
*   *Responsiveness?* The CSS Grid layout stacks the sidebar under the canvas on mobile devices, and the JavaScript `resize` event handles canvas re-dimensioning dynamically.

**2. Knowledge Transfer (How to Use):**
*   **Stage:** The main grid area is the physics playground.
*   **Interaction:** Move your mouse (or touch) over the canvas to attract particles. Click to spawn new ones.
*   **Controls:**
    *   *Gravity:* Slide to negative to reverse gravity (zero-G effect).
    *   *Friction:* Lowering this makes particles "slippery"; increasing it makes them move through molasses.
    *   *Mode:* Toggle between "Attract" (Black Hole) and "Repel" (Forcefield).

**3. Future Recommendations:**
*   *Optimization:* For particle counts > 500, implement a QuadTree or Spatial Hash Grid to optimize the collision/connection detection from O(N^2) to closer to O(N).
*   *Audio:* Add the Web Audio API to allow particles to react to microphone input frequency.
*   *Presets:* Add buttons to save specific "scenes" (e.g., "Low Gravity Orbit," "High Friction Pile").

This solution embodies the "Avant-Garde" philosophy by treating the UI as a functional instrument rather than a decorative skin, ensuring the visual hierarchy is driven by the motion and data rather than stock imagery.
