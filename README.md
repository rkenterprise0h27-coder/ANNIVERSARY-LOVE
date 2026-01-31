<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>365 Days with Muskan | I Love You Babes ❤️</title>
    
    <!-- Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@300;500;700&family=Birthstone&family=Quicksand:wght@300;500;700&display=swap" rel="stylesheet">
    
    <!-- Libraries -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <style>
        :root {
            --strawberry: #ff85a2;
            --peach: #ffbe0b;
            --lavender: #a5a4ff;
            --sky: #9bf6ff;
            --cream: #fdffb6;
            --text: #4a3f3f;
            --white-glass: rgba(255, 255, 255, 0.6);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            cursor: none; /* Custom interaction cursor */
        }

        body {
            background-color: #fff;
            color: var(--text);
            font-family: 'Fredoka', sans-serif;
            overflow-x: hidden;
            overflow-y: hidden; /* Locked until start */
            transition: background 1s ease;
        }

        /* --- 2026 Liquid Cursor --- */
        #cursor {
            position: fixed;
            width: 30px;
            height: 30px;
            background: var(--strawberry);
            border-radius: 50%;
            pointer-events: none;
            z-index: 10000;
            mix-blend-mode: multiply;
            filter: blur(2px);
            transition: transform 0.1s ease-out;
        }

        /* --- Animated Mesh Background --- */
        .bg-mesh {
            position: fixed;
            inset: 0;
            z-index: -1;
            background: 
                radial-gradient(at 0% 0%, var(--strawberry) 0, transparent 50%),
                radial-gradient(at 100% 0%, var(--sky) 0, transparent 50%),
                radial-gradient(at 100% 100%, var(--lavender) 0, transparent 50%),
                radial-gradient(at 0% 100%, var(--cream) 0, transparent 50%);
            opacity: 0; /* Starts hidden to simulate "Entering with colors" */
            filter: blur(60px);
            transition: opacity 3s ease;
        }

        /* --- Entrance Portal --- */
        #portal {
            position: fixed;
            inset: 0;
            background: #111; /* Starts dark like that February night */
            z-index: 9999;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
        }

        .portal-btn {
            background: var(--strawberry);
            color: white;
            border: none;
            padding: 25px 50px;
            border-radius: 60px;
            font-size: 1.5rem;
            font-weight: 700;
            font-family: 'Fredoka';
            box-shadow: 0 15px 35px rgba(255, 133, 162, 0.3);
            cursor: pointer;
            transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            margin-top: 20px;
        }

        .portal-btn:hover {
            transform: scale(1.1) rotate(-2deg);
        }

        /* --- Typography --- */
        .hero-title {
            font-family: 'Birthstone', cursive;
            font-size: clamp(4rem, 15vw, 10rem);
            color: var(--strawberry);
            line-height: 0.8;
            margin-bottom: 20px;
        }

        .heartfelt-p {
            font-family: 'Quicksand', sans-serif;
            font-size: clamp(1.2rem, 3vw, 2rem);
            font-weight: 500;
            max-width: 800px;
            text-align: center;
            line-height: 1.6;
        }

        /* --- Narrative Cards (Claymorphism) --- */
        section {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 5vw;
            position: relative;
        }

        .clay-card {
            background: var(--white-glass);
            backdrop-filter: blur(25px);
            border: 6px solid white;
            border-radius: 60px;
            padding: 4rem;
            max-width: 900px;
            width: 100%;
            box-shadow: 20px 20px 60px rgba(0,0,0,0.05), 
                        inset 10px 10px 20px rgba(255,255,255,0.5);
            opacity: 0;
            transform: translateY(100px);
            text-align: center;
        }

        /* --- The "Moods" Bento Grid --- */
        .bento-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 20px;
            width: 100%;
            margin-top: 40px;
        }

        .bento-item {
            background: white;
            padding: 30px;
            border-radius: 40px;
            border: 4px solid var(--cream);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-align: center;
        }

        .bento-item:hover {
            transform: scale(1.1) translateY(-10px);
            border-color: var(--strawberry);
        }

        .bento-item .emoji { font-size: 3rem; display: block; margin-bottom: 10px; }
        .bento-item .label { font-weight: 700; font-size: 1.2rem; }

        /* --- Scroll Indicator --- */
        .scroll-hint {
            position: absolute;
            bottom: 30px;
            font-weight: 700;
            color: var(--strawberry);
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {transform: translateY(0);}
            40% {transform: translateY(-10px);}
        }

        /* Floating Stickers */
        .sticker {
            position: absolute;
            font-size: 4rem;
            pointer-events: none;
            z-index: 10;
        }

        @media (max-width: 768px) {
            .clay-card { padding: 2rem; border-radius: 40px; }
            .hero-title { font-size: 4.5rem; }
            .bento-grid { grid-template-columns: repeat(2, 1fr); }
        }
    </style>
</head>
<body>

    <div id="cursor"></div>
    <div class="bg-mesh" id="mesh"></div>

    <!-- Entrance Portal -->
    <div id="portal">
        <div style="font-size: 5rem; margin-bottom: 20px;">🌙</div>
        <h2 style="font-family: 'Fredoka'; font-weight: 300; letter-spacing: 5px;">FEBRUARY 1, NIGHT</h2>
        <p style="margin-top: 10px; opacity: 0.7;">Everything was dark until I saw you...</p>
        <button class="portal-btn" onclick="startJourney()">Tap to Enter our World 🎀</button>
    </div>

    <main id="main-content" style="display:none;">
        
        <!-- Hero: I Love You -->
        <section>
            <h1 class="hero-title">I love you Babes ❤️</h1>
            <p class="heartfelt-p">My love is totally mixed in your life, Muskan.</p>
            <div class="scroll-hint">Scroll for your surprise! 👇</div>
        </section>

        <!-- Chapter 1: The Healer -->
        <section>
            <div class="sticker" style="top: 10%; right: 10%;">💖</div>
            <div class="clay-card reveal">
                <div style="font-size: 5rem; margin-bottom: 20px;">🍭</div>
                <h2 style="font-family: 'Fredoka'; font-size: 3rem; color: var(--strawberry); margin-bottom: 20px;">My Stress Buster</h2>
                <p class="heartfelt-p" style="font-size: 1.4rem;">
                    "Your <b>shararat</b> and that childish <b>babyness</b> are the only things that make my stress go away. No matter how hard my day is, seeing you makes it perfect."
                </p>
            </div>
        </section>

        <!-- Chapter 2: The Moods -->
        <section>
            <h2 class="hero-title" style="font-size: 4rem;">I Love You for All...</h2>
            <div class="bento-grid" style="max-width: 1000px;">
                <div class="bento-item reveal">
                    <span class="emoji">😡</span>
                    <span class="label">Gussa</span>
                </div>
                <div class="bento-item reveal">
                    <span class="emoji">😤</span>
                    <span class="label">Nakhra</span>
                </div>
                <div class="bento-item reveal">
                    <span class="emoji">😂</span>
                    <span class="label">Hasna</span>
                </div>
                <div class="bento-item reveal">
                    <span class="emoji">🥺</span>
                    <span class="label">Rona</span>
                </div>
                <div class="bento-item reveal">
                    <span class="emoji">🫂</span>
                    <span class="label">Clingy</span>
                </div>
                <div class="bento-item reveal">
                    <span class="emoji">🍼</span>
                    <span class="label">Baby</span>
                </div>
            </div>
            <p style="margin-top: 40px; font-weight: 600; font-style: italic; opacity: 0.7;">Yes, I love every single version of you!</p>
        </section>

        <!-- Chapter 3: The Proposal Night -->
        <section>
            <div class="clay-card reveal" style="background: linear-gradient(135deg, #fff, var(--sky));">
                <div style="font-size: 5rem; margin-bottom: 20px;">🎨</div>
                <h2 style="font-family: 'Fredoka'; font-size: 2.5rem; margin-bottom: 20px;">February 1st Night</h2>
                <p class="heartfelt-p" style="font-size: 1.3rem;">
                    "When I proposed to you that night, I was entering your life as the <b>colors</b>. In this one year, we've become so attached that I can never stop loving you."
                </p>
            </div>
        </section>

        <!-- Chapter 4: Soulful / The Main Person -->
        <section>
            <div class="clay-card reveal" style="border-color: var(--lavender);">
                <div style="font-size: 5rem; margin-bottom: 20px;">✨</div>
                <h2 style="font-family: 'Fredoka'; font-size: 3rem; color: var(--lavender);">God's Blessing</h2>
                <p class="heartfelt-p" style="font-size: 1.5rem;">
                    "God has made us for feeling what He wanted to bless us with. Muskan, you are the <b>precious main person</b> of my life. I promise to keep making you feel special forever."
                </p>
            </div>
        </section>

        <!-- Finale -->
        <section>
            <div style="font-size: 8rem;">👩‍❤️‍👨</div>
            <h1 class="hero-title">Happy 1 Year, <br>Muskan!</h1>
            <button class="portal-btn" style="background: var(--text); padding: 15px 40px;" onclick="celebrate()">Seal our Love Forever ❤️</button>
        </section>

    </main>

    <script>
        // --- 1. Liquid Cursor Engine ---
        const cursor = document.getElementById('cursor');
        document.addEventListener('mousemove', e => {
            gsap.to(cursor, {
                x: e.clientX - 15,
                y: e.clientY - 15,
                duration: 0.2,
                ease: "power2.out"
            });
        });

        // --- 2. Start Experience Flow ---
        function startJourney() {
            // Animate portal away
            gsap.to("#portal", {
                y: "-100%",
                duration: 1.5,
                ease: "power4.inOut",
                onComplete: () => {
                    document.getElementById('portal').style.display = 'none';
                    document.getElementById('main-content').style.display = 'block';
                    document.body.style.overflowY = 'auto';
                    document.getElementById('mesh').style.opacity = '0.6';
                    initAnimations();
                }
            });
        }

        // --- 3. Scroll Trigger Magic ---
        function initAnimations() {
            gsap.registerPlugin(ScrollTrigger);

            // Stagger Cards
            gsap.utils.toArray(".reveal").forEach(el => {
                gsap.to(el, {
                    scrollTrigger: {
                        trigger: el,
                        start: "top 85%",
                    },
                    opacity: 1,
                    y: 0,
                    duration: 1.5,
                    ease: "power4.out"
                });
            });

            // Float Stickers
            gsap.to(".sticker", {
                y: -50,
                x: 20,
                rotation: 15,
                duration: 3,
                repeat: -1,
                yoyo: true,
                ease: "sine.inOut"
            });
        }

        // --- 4. Celebration Finale ---
        function celebrate() {
            const duration = 15 * 1000;
            const animationEnd = Date.now() + duration;
            const defaults = { startVelocity: 30, spread: 360, ticks: 60, zIndex: 0 };

            function randomInRange(min, max) {
                return Math.random() * (max - min) + min;
            }

            const interval = setInterval(function() {
                const timeLeft = animationEnd - Date.now();

                if (timeLeft <= 0) {
                    return clearInterval(interval);
                }

                const particleCount = 50 * (timeLeft / duration);
                
                // Pastel iOS Style Colors
                confetti(Object.assign({}, defaults, { 
                    particleCount, 
                    origin: { x: randomInRange(0.1, 0.3), y: Math.random() - 0.2 },
                    colors: ['#ff85a2', '#ffbe0b', '#a5a4ff']
                }));
                confetti(Object.assign({}, defaults, { 
                    particleCount, 
                    origin: { x: randomInRange(0.7, 0.9), y: Math.random() - 0.2 },
                    colors: ['#9bf6ff', '#fdffb6', '#ff85a2']
                }));
            }, 250);

            // Pop effect
            gsap.to(".portal-btn", { scale: 1.2, duration: 0.2, yoyo: true, repeat: 1 });
        }
    </script>
</body>
</html>
