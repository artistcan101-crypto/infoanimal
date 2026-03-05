<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Majestic Wild: Immersive Info</title>
    <link href="https://fonts.googleapis.com" rel="stylesheet">
    
    <style>
        :root {
            --bg: #030712;
            --accent: #10b981; /* Emerald for nature feel */
            --card-glass: rgba(255, 255, 255, 0.03);
            --text-main: #f9fafb;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            background-color: var(--bg);
            color: var(--text-main);
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
        }

        /* Smooth UI Progress Bar */
        .progress-bar {
            position: fixed;
            top: 0; left: 0;
            width: 0%; height: 5px;
            background: linear-gradient(90deg, var(--accent), #34d399);
            z-index: 1000;
        }

        .section {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 4rem 10%;
        }

        /* Hero Section */
        .hero h1 {
            font-size: clamp(3.5rem, 12vw, 10rem);
            font-weight: 800;
            line-height: 0.9;
            text-align: center;
            background: linear-gradient(to bottom, #fff 40%, rgba(255,255,255,0.1));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 1rem;
        }

        /* Bento Grid: 2026's Top Layout Trend */
        .bento-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            grid-auto-rows: 220px;
            gap: 20px;
            max-width: 1300px;
            width: 100%;
        }

        .bento-item {
            background: var(--card-glass);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 32px;
            padding: 2rem;
            backdrop-filter: blur(15px);
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            position: relative;
            overflow: hidden;
            transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275), border-color 0.3s;
        }

        .bento-item:hover {
            border-color: var(--accent);
            transform: translateY(-5px) scale(1.02);
        }

        .bento-item h3 { font-size: 1.5rem; margin-bottom: 0.5rem; color: var(--accent); }
        .bento-item p { font-size: 0.95rem; opacity: 0.7; font-weight: 300; }

        /* Custom Grid Spanning */
        .large { grid-column: span 2; grid-row: span 2; }
        .wide { grid-column: span 2; }
        .tall { grid-row: span 2; }

        @media (max-width: 900px) {
            .bento-grid { grid-template-columns: repeat(2, 1fr); }
            .large, .wide { grid-column: span 2; }
        }
    </style>
</head>
<body>

    <div class="progress-bar"></div>

    <div id="content">
        <!-- Hero Section -->
        <section class="section hero">
            <h1 class="reveal-h1">WILD.<br>WONDER.</h1>
            <p class="reveal-sub" style="opacity: 0.5;">A journey into the planet's most incredible lifeforms.</p>
        </section>

        <!-- Information Bento Section -->
        <section class="section">
            <div class="bento-grid">
                <!-- Large Card -->
                <div class="bento-item large">
                    <img src =whale.JPG alt="whale" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover; opacity: 0.2;">
                    <h3>The Blue Giant</h3>
                    <p>The blue whale's tongue alone can weigh as much as an entire adult elephant. Its heart is the size of a small car.</p>
                </div>

                <!-- Tall Card -->
                <div class="bento-item tall">
                    <img src =owl.jpeg alt="owl" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover; opacity: 0.2;">
                    <h3>Silent Hunters</h3>
                    <p>Owls have specialized feathers that muffle sound, allowing them to fly in near-perfect silence.</p>
                </div>

                <!-- Standard Cards -->
                <div class="bento-item">
                    <img src =octopus.jpeg alt="octopus" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover; opacity: 0.2;">
                    <h3>Octopus Intelligence</h3>
                    <p>Octopuses possess three hearts and nine brains, with neurons spread through each arm.</p>
                </div>

                <div class="bento-item">
                    <img src =shark.jpeg alt="shark" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover; opacity: 0.2;">
                    <h3>Ancient Survivors</h3>
                    <p>Sharks have inhabited Earth's oceans for over 450 million years—longer than dinosaurs or even trees.</p>
                </div>

                <!-- Wide Card -->
                <div class="bento-item wide">
                    <img src =dolphin.jpeg alt="dolphin" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover; opacity: 0.2;">
                    <h3>Echolocation Masters</h3>
                    <p>Dolphins use signature whistles to identify and call each other by "name," much like humans do.</p>
                </div>

                <div class="bento-item">
                    <img src =flea.jpeg alt="flea" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover; opacity: 0.2;">
                    <h3>Small But Mighty</h3>
                    <p>A tiny flea can jump over 200 times its own body length—the equivalent of a human jumping over the Empire State Building.</p>
                </div>
            </div>
        </section>

        <section class="section">
            <h2 class="reveal-end" style="font-size: 3rem;">Nature is the Ultimate Artist.</h2>
        </section>
    </div>

    <!-- GSAP Core & ScrollTrigger -->
    <script src="https://cdnjs.cloudflare.com"></script>
    <script src="https://cdnjs.cloudflare.com"></script>

    <script>
        gsap.registerPlugin(ScrollTrigger);

        // 1. Smooth Progress Bar
        gsap.to(".progress-bar", {
            width: "100%",
            scrollTrigger: {
                scrub: 0.5,
                trigger: "body",
                start: "top top",
                end: "bottom bottom"
            }
        });

        // 2. Hero Reveal
        const tl = gsap.timeline();
        tl.from(".reveal-h1", { y: 150, opacity: 0, duration: 1.2, ease: "expo.out" })
          .from(".reveal-sub", { y: 20, opacity: 0, duration: 0.8 }, "-=0.6");

        // 3. Staggered Bento Grid Entry
        gsap.from(".bento-item", {
            scrollTrigger: {
                trigger: ".bento-grid",
                start: "top 80%",
            },
            y: 100,
            opacity: 0,
            duration: 1.2,
            stagger: 0.1, // Creates the "pop-in" effect
            ease: "power4.out"
        });

        // 4. Parallax Depth for Text
        gsap.to(".reveal-h1", {
            scrollTrigger: {
                trigger: ".hero",
                start: "top top",
                scrub: true
            },
            y: 200,
            opacity: 0,
            scale: 0.8
        });
    </script>
</body>
</html>
