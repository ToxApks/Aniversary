<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy 20th Anniversary</title>
    
    <!-- 1. Typography -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Lato:wght@300;400&family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&display=swap" rel="stylesheet">
    
    <!-- 2. Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <!-- 3. Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'rose-gold': '#B76E79',
                        'rose-light': '#E6CFCF',
                        'warm-cream': '#FDFBF7',
                        'deep-red': '#8A3333',
                        'charcoal': '#4A4A4A'
                    },
                    fontFamily: {
                        serif: ['"Playfair Display"', 'serif'],
                        sans: ['"Lato"', 'sans-serif'],
                    },
                    animation: {
                        'float': 'float 6s ease-in-out infinite',
                        'pulse-slow': 'pulse 3s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                        'pulse-gentle': 'pulse 1.5s ease-in-out infinite',
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0)' },
                            '50%': { transform: 'translateY(-20px)' },
                        }
                    }
                }
            }
        }
    </script>

    <!-- 4. Custom CSS -->
    <style>
        body {
            background-color: #FDFBF7;
            overflow-x: hidden;
            overflow-y: hidden; /* Prevent scrolling during animations */
        }

        .bg-gradient-mesh {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%; z-index: -2;
            background: radial-gradient(circle at 50% 50%, #fff0f0 0%, #fdfbf7 100%);
        }

        .particles-container {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%; z-index: -1;
            pointer-events: none;
        }

        .particle {
            position: absolute;
            color: #E6CFCF; opacity: 0.4;
            animation: float 8s ease-in-out infinite;
        }
        
        /* Stagger animations */
        .particle:nth-child(1) { top: 10%; left: 10%; font-size: 2rem; animation-delay: 0s; }
        .particle:nth-child(2) { top: 20%; right: 15%; font-size: 1.5rem; animation-delay: 2s; }
        .particle:nth-child(3) { bottom: 15%; left: 20%; font-size: 2.5rem; animation-delay: 4s; }
        .particle:nth-child(4) { bottom: 30%; right: 10%; font-size: 1.2rem; animation-delay: 1s; }
        .particle:nth-child(5) { top: 50%; left: 50%; font-size: 1rem; animation-delay: 3s; opacity: 0.2; }

        .gsap-hide { opacity: 0; visibility: hidden; }

        /* Confetti Canvas */
        #confetti-canvas {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            pointer-events: none;
            z-index: 50;
        }

        /* Music Toggle Button */
        .music-toggle {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.8);
            border: 1px solid rgba(183, 110, 121, 0.3);
            color: #B76E79;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 40;
            transition: all 0.3s ease;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }
        .music-toggle:hover {
            transform: scale(1.1);
            background: #fff;
        }

        /* Loading State for Button */
        .btn-loading {
            cursor: not-allowed;
            opacity: 0.9;
            animation: pulse 1s infinite;
        }
    </style>
</head>
<body class="text-charcoal font-sans antialiased h-screen w-screen flex flex-col items-center justify-center relative">

    <!-- AUDIO ELEMENT -->
    <!-- 
      ⚠️ ACTION REQUIRED: 
      Replace the 'src' below with your local file (e.g., 'music.mp3') or a reliable URL.
      Currently using a placeholder link for Gymnopédie No.1 (Public Domain).
    -->
    <audio id="bgMusic" loop>
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_49f1f3c91b.mp3" type="audio/mpeg">
</audio>


    <!-- Music Toggle Button -->
    <button id="musicToggle" class="music-toggle" aria-label="Toggle Music">
        <i class="fa-solid fa-volume-xmark"></i>
    </button>

    <!-- Confetti Canvas -->
    <canvas id="confetti-canvas"></canvas>

    <div class="bg-gradient-mesh"></div>
    <div class="particles-container">
        <i class="fa-solid fa-heart particle"></i>
        <i class="fa-regular fa-heart particle"></i>
        <i class="fa-solid fa-heart particle"></i>
        <i class="fa-solid fa-gift particle"></i>
        <i class="fa-regular fa-heart particle"></i>
    </div>

    <!-- MAIN CONTENT -->
    <main class="w-full max-w-md md:max-w-2xl px-6 relative flex flex-col items-center justify-center text-center min-h-[60vh]">
        
        <!-- SEQUENCE 1 -->
        <div id="sequence-1" class="absolute inset-0 flex flex-col items-center justify-center gsap-hide">
            <div class="w-16 h-1 bg-rose-gold mb-6 rounded-full opacity-50"></div>
            <h1 class="text-4xl md:text-6xl font-serif text-deep-red mb-4 leading-tight">
                20 Years <br>
                <span class="text-rose-gold italic">Completed</span>
            </h1>
        </div>

        <!-- SEQUENCE 2 -->
        <div id="sequence-2" class="absolute inset-0 flex flex-col items-center justify-center gsap-hide">
            <h2 class="text-3xl md:text-5xl font-serif text-charcoal mb-6 leading-relaxed">
                A Journey of <br>
                <span class="text-rose-gold">Togetherness</span>
            </h2>
        </div>

        <!-- SEQUENCE 3 -->
        <div id="sequence-3" class="absolute inset-0 flex flex-col items-center justify-center gsap-hide">
            <p class="text-xl md:text-3xl font-light text-charcoal leading-relaxed max-w-lg">
                Wishing You Many <br>
                <strong class="font-serif text-deep-red text-2xl md:text-4xl">More Years</strong> <br>
                Ahead
            </p>
        </div>

        <!-- GIFT REVEAL -->
        <div id="gift-reveal" class="w-full bg-white/60 backdrop-blur-md border border-white/80 shadow-xl rounded-3xl p-8 md:p-12 relative z-10 gsap-hide transform scale-95">
            <div class="absolute inset-2 border border-rose-gold/20 rounded-2xl pointer-events-none"></div>
            
            <div class="flex flex-col items-center relative z-20">
                <div class="w-20 h-20 bg-gradient-to-br from-rose-light to-white rounded-full flex items-center justify-center shadow-inner mb-6 animate-float">
                    <i class="fa-solid fa-gift text-3xl text-rose-gold"></i>
                </div>

                <h3 class="font-serif text-2xl md:text-3xl text-deep-red mb-3">
                    A Special Memory
                </h3>
                <p class="text-charcoal/80 mb-8 font-light">
                    We’ve created a special digital gift for you to keep forever.
                </p>

                <!-- DOWNLOAD BUTTON -->
                <!-- 
                   ⚠️ ACTION REQUIRED: 
                   Paste your actual download link in data-href below.
                   Example: data-href="https://dropbox.com/..."
                -->
                <a href="https://drive.google.com/uc?export=download&id=1KFO7Ur5wnegxu05rKtuU1pEgmB2OI3VT" 
                   id="downloadBtn"
                   data-href="https://drive.google.com/uc?export=download&id=1KFO7Ur5wnegxu05rKtuU1pEgmB2OI3VT
" 
                   class="group relative inline-flex items-center justify-center px-8 py-4 bg-gradient-to-r from-rose-gold to-[#c0808b] text-white font-serif text-lg tracking-wide rounded-full shadow-lg hover:shadow-rose-gold/40 hover:-translate-y-1 transition-all duration-300 w-full md:w-auto overflow-hidden">
                    
                    <span class="absolute inset-0 w-full h-full bg-white/20 group-hover:bg-white/0 transition-all rounded-full"></span>
                    
                    <i class="fa-solid fa-download mr-3 group-hover:animate-bounce transition-transform" id="btnIcon"></i>
                    <span id="btnText">Download Gift</span>
                </a>

                <p class="text-xs text-charcoal/40 mt-6 uppercase tracking-widest">
                    Tap to save your gift
                </p>
            </div>
        </div>

    </main>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>

    <script>
        document.addEventListener("DOMContentLoaded", () => {
            
            // --- 1. ANIMATION SEQUENCE (GSAP) ---
            const tl = gsap.timeline({ defaults: { ease: "power2.out" } });
            gsap.set("#gift-reveal", { autoAlpha: 0, scale: 0.9 });
            gsap.set(".gsap-hide", { autoAlpha: 0 });

            tl.to("#sequence-1", { autoAlpha: 1, duration: 1.5, y: 0, startAt: { y: 20 } })
              .to("#sequence-1", { autoAlpha: 0, y: -20, duration: 1, delay: 2.5 })
              .to("#sequence-2", { autoAlpha: 1, scale: 1, duration: 1.5, startAt: { scale: 0.95 } })
              .to("#sequence-2", { autoAlpha: 0, blur: 5, duration: 1, delay: 3 })
              .to("#sequence-3", { autoAlpha: 1, duration: 1.5 })
              .to("#sequence-3", { autoAlpha: 0, duration: 1, delay: 3.5 })
              .to("#gift-reveal", { autoAlpha: 1, scale: 1, duration: 1.2, ease: "back.out(1.7)" });


            // --- 2. MUSIC HANDLING ---
            const audio = document.getElementById('bgMusic');
            const musicToggle = document.getElementById('musicToggle');
            const musicIcon = musicToggle.querySelector('i');
            let musicStarted = false;

            audio.volume = 0.3; // Low volume rule

            function toggleMusic() {
                if (audio.paused) {
                    audio.play().then(() => {
                        musicIcon.className = "fa-solid fa-volume-high";
                    }).catch(e => console.log("Audio play failed:", e));
                } else {
                    audio.pause();
                    musicIcon.className = "fa-solid fa-volume-xmark";
                }
            }

            // Attempt to start music on first body interaction (Mobile safe)
            function initMusic() {
                if (!musicStarted) {
                    audio.play().then(() => {
                        musicStarted = true;
                        musicIcon.className = "fa-solid fa-volume-high";
                    }).catch(() => {
                        // Autoplay prevented, wait for explicit toggle
                    });
                    document.body.removeEventListener('click', initMusic);
                    document.body.removeEventListener('touchstart', initMusic);
                }
            }

            document.body.addEventListener('click', initMusic);
            document.body.addEventListener('touchstart', initMusic);
            musicToggle.addEventListener('click', (e) => {
                e.stopPropagation(); // Don't trigger initMusic again
                toggleMusic();
            });


            // --- 3. DOWNLOAD LOGIC & COUNTDOWN ---
            const downloadBtn = document.getElementById('downloadBtn');
            const btnText = document.getElementById('btnText');
            const btnIcon = document.getElementById('btnIcon');

            downloadBtn.addEventListener('click', function(e) {
                e.preventDefault(); // Stop immediate download
                
                // If already counting down, ignore
                if(this.classList.contains('btn-loading')) return;

                const originalLink = this.getAttribute('data-href');
                let count = 3;

                // Visual State: Loading
                this.classList.add('btn-loading');
                this.classList.remove('hover:-translate-y-1', 'hover:shadow-rose-gold/40'); // Remove hover effects
                btnIcon.style.display = 'none'; // Hide icon
                
                // Initial Text
                btnText.textContent = `Preparing Gift... ${count}`;

                const timer = setInterval(() => {
                    count--;
                    if (count > 0) {
                        btnText.textContent = `Preparing Gift... ${count}`;
                    } else {
                        clearInterval(timer);
                        
                        // FINISH
                        btnText.textContent = "Downloading...";
                        
                        // 1. Fire Confetti
                        fireConfettiFromElement(downloadBtn);

                        // 2. Trigger Download (after slight delay for effect)
                        setTimeout(() => {
                            // Create temporary link to force download
                            const link = document.createElement('a');
                            link.href = originalLink;
                            link.download = 'Anniversary_Gift'; // Suggest filename
                            document.body.appendChild(link);
                            link.click();
                            document.body.removeChild(link);
                            
                            // Reset button state (optional)
                            btnText.textContent = "Gift Downloaded";
                            this.classList.remove('btn-loading');
                        }, 1000);
                    }
                }, 1000);
            });


            // --- 4. LIGHTWEIGHT CONFETTI SYSTEM ---
            const canvas = document.getElementById('confetti-canvas');
            const ctx = canvas.getContext('2d');
            let particles = [];
            
            // Resize canvas
            function resizeCanvas() {
                canvas.width = window.innerWidth;
                canvas.height = window.innerHeight;
            }
            window.addEventListener('resize', resizeCanvas);
            resizeCanvas();

            function fireConfettiFromElement(element) {
                const rect = element.getBoundingClientRect();
                const startX = rect.left + rect.width / 2;
                const startY = rect.top; // Start from top of button

                // Create particles
                const colors = ['#B76E79', '#FDFBF7', '#FFD700']; // Rose, Cream, Gold
                
                for (let i = 0; i < 60; i++) {
                    particles.push({
                        x: startX,
                        y: startY,
                        vx: (Math.random() - 0.5) * 10,     // Spread X
                        vy: (Math.random() - 1) * 15 - 5,   // Upward velocity
                        gravity: 0.5,
                        color: colors[Math.floor(Math.random() * colors.length)],
                        size: Math.random() * 8 + 4,
                        rotation: Math.random() * 360,
                        rotationSpeed: (Math.random() - 0.5) * 10,
                        life: 100, // Frames to live
                        decay: Math.random() * 0.5 + 0.5 // visual decay
                    });
                }
                
                requestAnimationFrame(updateConfetti);
            }

            function updateConfetti() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                
                for (let i = 0; i < particles.length; i++) {
                    let p = particles[i];
                    
                    p.x += p.vx;
                    p.y += p.vy;
                    p.vy += p.gravity; // Gravity
                    p.rotation += p.rotationSpeed;
                    p.life -= p.decay;

                    if (p.life > 0) {
                        ctx.save();
                        ctx.translate(p.x, p.y);
                        ctx.rotate(p.rotation * Math.PI / 180);
                        ctx.fillStyle = p.color;
                        ctx.fillRect(-p.size/2, -p.size/2, p.size, p.size);
                        ctx.restore();
                    }
                }

                // Remove dead particles
                particles = particles.filter(p => p.life > 0);

                if (particles.length > 0) {
                    requestAnimationFrame(updateConfetti);
                } else {
                    ctx.clearRect(0, 0, canvas.width, canvas.height);
                }
            }

        });
    </script>
</body>
</html>
