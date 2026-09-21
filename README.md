# MrDrummondTeaches.github.io
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simulation Showcase</title>
    <style>
        :root {
            --bg-color: #0f172a;
            --card-bg: #1e293b;
            --text-primary: #f8fafc;
            --text-secondary: #94a3b8;
            --accent-color: #38bdf8;
            --accent-hover: #0284c7;
            --border-color: #334155;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-primary);
            line-height: 1.6;
            padding: 2rem 1rem;
        }

        header {
            max-width: 1100px;
            margin: 0 auto 3rem auto;
            text-align: center;
        }

        header h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
            color: var(--accent-color);
        }

        header p {
            color: var(--text-secondary);
            font-size: 1.1rem;
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
        }

        .sim-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .sim-card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        .sim-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.4);
        }

        .sim-preview {
            width: 100%;
            height: 180px;
            background-color: #090d16;
            display: flex;
            align-items: center;
            justify-content: center;
            border-bottom: 1px solid var(--border-color);
        }

        .sim-preview canvas {
            width: 100%;
            height: 100%;
        }

        .sim-content {
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }

        .sim-title {
            font-size: 1.25rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .sim-description {
            color: var(--text-secondary);
            font-size: 0.95rem;
            margin-bottom: 1.5rem;
            flex-grow: 1;
        }

        .sim-actions {
            display: flex;
            gap: 0.75rem;
        }

        .btn {
            display: inline-block;
            padding: 0.5rem 1rem;
            border-radius: 6px;
            text-decoration: none;
            font-weight: 500;
            font-size: 0.9rem;
            text-align: center;
            transition: background-color 0.2s;
        }

        .btn-primary {
            background-color: var(--accent-color);
            color: #0f172a;
        }

        .btn-primary:hover {
            background-color: var(--accent-hover);
            color: #ffffff;
        }

        .btn-secondary {
            background-color: transparent;
            color: var(--text-secondary);
            border: 1px solid var(--border-color);
        }

        .btn-secondary:hover {
            background-color: var(--border-color);
            color: var(--text-primary);
        }

        footer {
            max-width: 1100px;
            margin: 4rem auto 0 auto;
            text-align: center;
            color: var(--text-secondary);
            font-size: 0.875rem;
            border-top: 1px solid var(--border-color);
            padding-top: 1.5rem;
        }
    </style>
</head>
<body>

    <header>
        <h1>Interactive Simulations</h1>
        <p>A work in progress that will hopefully include a series of simulations useful in Middle and High school across a range of curricula.</p>
    </header>

    <div class="container">
        <main class="sim-grid">
            
            <!-- Simulation Card 1 -->
            <article class="sim-card">
                <div class="sim-preview">
                    <canvas id="canvas1"></canvas>
                </div>
                <div class="sim-content">
                    <h2 class="sim-title">Diffusion in a test tube</h2>
                    <p class="sim-description">2D N-body gravitational interaction model with adjustable mass and velocity vectors.</p>
                    <div class="sim-actions">
                        <a href="simulations/gravity.html" class="btn btn-primary">Launch</a>
                        <a href="https://github.com/yourusername/your-repo/blob/main/simulations/gravity.html" class="btn btn-secondary">Source</a>
                    </div>
                </div>
            </article>

            <!-- Simulation Card 2 -->
            <article class="sim-card">
                <div class="sim-preview">
                    <canvas id="canvas2"></canvas>
                </div>
                <div class="sim-content">
                    <h2 class="sim-title">Simulating Light, colours and how they interact with filters</h2>
                    <p class="sim-description">Chaotic motion simulation solved using numerical integration techniques.</p>
                    <div class="sim-actions">
                        <a href="ColourSim" class="btn btn-primary">Launch</a>
                        <a href="" class="btn btn-secondary">Source</a>
                    </div>
                </div>
            </article>

            <!-- Simulation Card 3 -->
            <article class="sim-card">
                <div class="sim-preview">
                    <canvas id="canvas3"></canvas>
                </div>
                <div class="sim-content">
                    <h2 class="sim-title">Grid Fluid Dynamics</h2>
                    <p class="sim-description">Eulerian grid-based fluid simulation with real-time velocity vector field controls.</p>
                    <div class="sim-actions">
                        <a href="simulations/fluid.html" class="btn btn-primary">Launch</a>
                        <a href="https://github.com/yourusername/your-repo/blob/main/simulations/fluid.html" class="btn btn-secondary">Source</a>
                    </div>
                </div>
            </article>

        </main>
    </div>

    <footer>
        <p>Hosted on GitHub Pages • Open Source</p>
    </footer>

    <script>
        // Light animation script for background previews inside cards
        function initPreviewCanvas(canvasId, particleColor) {
            const canvas = document.getElementById(canvasId);
            if (!canvas) return;

            const ctx = canvas.getContext('2d');
            canvas.width = canvas.parentElement.clientWidth;
            canvas.height = canvas.parentElement.clientHeight;

            const particles = Array.from({ length: 20 }, () => ({
                x: Math.random() * canvas.width,
                y: Math.random() * canvas.height,
                vx: (Math.random() - 0.5) * 1.2,
                vy: (Math.random() - 0.5) * 1.2,
                radius: Math.random() * 2.5 + 1
            }));

            function render() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);

                particles.forEach(p => {
                    p.x += p.vx;
                    p.y += p.vy;

                    if (p.x < 0 || p.x > canvas.width) p.vx *= -1;
                    if (p.y < 0 || p.y > canvas.height) p.vy *= -1;

                    ctx.beginPath();
                    ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
                    ctx.fillStyle = particleColor;
                    ctx.fill();
                });

                requestAnimationFrame(render);
            }

            render();
        }

        window.addEventListener('DOMContentLoaded', () => {
            initPreviewCanvas('canvas1', '#38bdf8');
            initPreviewCanvas('canvas2', '#f43f5e');
            initPreviewCanvas('canvas3', '#34d399');
        });
    </script>

</body>
</html>
