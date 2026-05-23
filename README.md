<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MauriSpide - Artista Digital</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=Space+Mono:wght@400;700&family=Playfair+Display:wght@700;800;900&display=swap" rel="stylesheet">
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0a0a0a;
            color: #ffffff;
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* CURSOR PERSONALIZADO */
        .cursor {
            width: 8px;
            height: 8px;
            background: #00d4ff;
            border-radius: 50%;
            position: fixed;
            pointer-events: none;
            transform: translate(-50%, -50%);
            z-index: 9999;
            mix-blend-mode: screen;
            filter: blur(1px);
        }

        .cursor.active {
            width: 30px;
            height: 30px;
            border: 2px solid #00d4ff;
            background: transparent;
        }

        /* FONDO DINÁMICO */
        .bg-container {
            position: fixed;
            width: 100%;
            height: 100%;
            z-index: -2;
            overflow: hidden;
        }

        .gradient-bg {
            position: absolute;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, #0a0a0a 0%, #1a1a2e 25%, #16213e 50%, #0f3460 75%, #0a0a0a 100%);
            animation: gradientShift 15s ease infinite;
        }

        @keyframes gradientShift {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(-50px, -50px); }
        }

        .blob {
            position: absolute;
            border-radius: 40% 60% 70% 30% / 40% 50% 60% 50%;
            opacity: 0.1;
            mix-blend-mode: screen;
            animation: blobMove 20s ease-in-out infinite;
        }

        .blob-1 {
            width: 400px;
            height: 400px;
            background: #00d4ff;
            top: -100px;
            left: -100px;
            animation-duration: 25s;
        }

        .blob-2 {
            width: 300px;
            height: 300px;
            background: #ff006e;
            bottom: -50px;
            right: -50px;
            animation-duration: 20s;
            animation-delay: -5s;
        }

        .blob-3 {
            width: 350px;
            height: 350px;
            background: #8338ec;
            top: 50%;
            left: 50%;
            animation-duration: 22s;
            animation-delay: -10s;
        }

        @keyframes blobMove {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            33% { transform: translate(30px, -50px) rotate(120deg); }
            66% { transform: translate(-20px, 30px) rotate(240deg); }
        }

        /* HEADER */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 30px 50px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 100;
            backdrop-filter: blur(10px);
            background: rgba(10, 10, 10, 0.5);
            border-bottom: 1px solid rgba(0, 212, 255, 0.1);
        }

        .logo {
            font-size: 28px;
            font-weight: 900;
            background: linear-gradient(135deg, #00d4ff 0%, #ff006e 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: -1px;
        }

        nav {
            display: flex;
            gap: 50px;
        }

        nav a {
            color: #ffffff;
            text-decoration: none;
            font-size: 14px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
            position: relative;
            transition: color 0.3s;
        }

        nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, #00d4ff, #ff006e);
            transition: width 0.3s;
        }

        nav a:hover {
            color: #00d4ff;
        }

        nav a:hover::after {
            width: 100%;
        }

        /* HERO SECTION */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 120px 20px 80px;
            position: relative;
            overflow: hidden;
        }

        .hero-content {
            max-width: 900px;
            z-index: 1;
            animation: fadeInUp 1.2s ease-out;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero h1 {
            font-family: 'Playfair Display', serif;
            font-size: clamp(50px, 12vw, 120px);
            line-height: 1.1;
            margin-bottom: 20px;
            background: linear-gradient(135deg, #00d4ff 0%, #ff006e 50%, #8338ec 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            font-weight: 900;
        }

        .hero .subtitle {
            font-size: 18px;
            color: #888;
            margin-bottom: 40px;
            text-transform: uppercase;
            letter-spacing: 3px;
            font-weight: 300;
        }

        .hero-description {
            font-size: 16px;
            color: #aaa;
            margin-bottom: 60px;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            line-height: 1.8;
        }

        .cta-buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn {
            padding: 16px 40px;
            border: none;
            border-radius: 50px;
            font-size: 14px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.2);
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .btn:hover::before {
            width: 300px;
            height: 300px;
        }

        .btn-primary {
            background: linear-gradient(135deg, #00d4ff 0%, #ff006e 100%);
            color: #fff;
            box-shadow: 0 20px 60px rgba(0, 212, 255, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 30px 80px rgba(0, 212, 255, 0.5);
        }

        .btn-secondary {
            background: transparent;
            border: 2px solid #00d4ff;
            color: #00d4ff;
        }

        .btn-secondary:hover {
            background: #00d4ff;
            color: #0a0a0a;
            transform: translateY(-3px);
        }

        /* STATS SECTION */
        .stats {
            padding: 100px 50px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            text-align: center;
            position: relative;
            z-index: 1;
        }

        .stat-item {
            backdrop-filter: blur(10px);
            background: rgba(0, 212, 255, 0.05);
            border: 1px solid rgba(0, 212, 255, 0.2);
            padding: 40px;
            border-radius: 20px;
            transition: all 0.3s;
        }

        .stat-item:hover {
            background: rgba(0, 212, 255, 0.1);
            border-color: rgba(0, 212, 255, 0.4);
            transform: translateY(-10px);
        }

        .stat-number {
            font-size: 48px;
            font-weight: 900;
            background: linear-gradient(135deg, #00d4ff, #ff006e);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 15px;
        }

        .stat-label {
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 2px;
            color: #888;
        }

        /* FEATURED SECTION */
        .featured {
            padding: 100px 50px;
            position: relative;
            z-index: 1;
        }

        .section-title {
            font-family: 'Playfair Display', serif;
            font-size: 60px;
            margin-bottom: 60px;
            text-align: center;
            background: linear-gradient(135deg, #00d4ff, #ff006e);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .featured-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 40px;
        }

        .featured-card {
            backdrop-filter: blur(10px);
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(0, 212, 255, 0.2);
            border-radius: 20px;
            overflow: hidden;
            transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
            cursor: pointer;
        }

        .featured-card:hover {
            transform: translateY(-20px);
            border-color: rgba(0, 212, 255, 0.6);
            box-shadow: 0 20px 60px rgba(0, 212, 255, 0.2);
        }

        .featured-header {
            height: 200px;
            background: linear-gradient(135deg, #00d4ff 0%, #8338ec 100%);
            position: relative;
            overflow: hidden;
        }

        .featured-header::after {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200%;
            height: 200%;
            background: repeating-linear-gradient(
                45deg,
                transparent,
                transparent 10px,
                rgba(255, 255, 255, 0.1) 10px,
                rgba(255, 255, 255, 0.1) 20px
            );
            animation: shimmer 3s infinite;
        }

        @keyframes shimmer {
            0% { transform: translate(-100%, -100%); }
            100% { transform: translate(100%, 100%); }
        }

        .featured-content {
            padding: 30px;
        }

        .featured-content h3 {
            font-size: 20px;
            margin-bottom: 10px;
            color: #00d4ff;
        }

        .featured-content p {
            color: #aaa;
            font-size: 14px;
            line-height: 1.6;
        }

        /* FOOTER */
        footer {
            padding: 60px 50px;
            text-align: center;
            border-top: 1px solid rgba(0, 212, 255, 0.1);
            position: relative;
            z-index: 1;
        }

        .footer-content {
            margin-bottom: 30px;
        }

        .social-links {
            display: flex;
            gap: 30px;
            justify-content: center;
            margin-bottom: 30px;
        }

        .social-links a {
            color: #888;
            text-decoration: none;
            font-size: 14px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.3s;
        }

        .social-links a:hover {
            color: #00d4ff;
            transform: translateY(-3px);
        }

        .copyright {
            color: #555;
            font-size: 12px;
            letter-spacing: 1px;
        }

        /* RESPONSIVE */
        @media (max-width: 768px) {
            header {
                padding: 20px 25px;
                flex-direction: column;
                gap: 20px;
            }

            nav {
                flex-direction: column;
                gap: 15px;
            }

            .hero {
                padding: 100px 20px 60px;
            }

            .stats, .featured {
                padding: 60px 25px;
            }

            .stats {
                gap: 20px;
            }

            .featured-grid {
                gap: 20px;
            }

            footer {
                padding: 40px 25px;
            }

            .section-title {
                font-size: 40px;
                margin-bottom: 40px;
            }
        }

        @media (max-width: 480px) {
            .hero h1 {
                font-size: 40px;
            }

            .section-title {
                font-size: 30px;
            }

            .cta-buttons {
                flex-direction: column;
            }

            .btn {
                width: 100%;
            }
        }
    </style>
</head>

<body>
    <!-- CURSOR PERSONALIZADO -->
    <div class="cursor"></div>

    <!-- FONDO DINÁMICO -->
    <div class="bg-container">
        <div class="gradient-bg"></div>
        <div class="blob blob-1"></div>
        <div class="blob blob-2"></div>
        <div class="blob blob-3"></div>
    </div>

    <!-- HEADER -->
    <header>
        <div class="logo">MAURISPIDE</div>
        <nav>
            <a href="#home">Inicio</a>
            <a href="#music">Música</a>
            <a href="#about">Acerca</a>
            <a href="#contact">Contacto</a>
        </nav>
    </header>

    <!-- HERO SECTION -->
    <section class="hero" id="home">
        <div class="hero-content">
            <h1>Esto No Es Solo Música</h1>
            <p class="subtitle">Bienvenido a Mi Universo</p>
            <p class="hero-description">
                Soy MauriSpide, productor y artista digital. Creo experiencias sonoras únicas que mezclan tecnología, 
                creatividad y pasión. Cada producción es un viaje, cada nota es una historia.
            </p>
            <div class="cta-buttons">
                <button class="btn btn-primary">Escuchar Música</button>
                <button class="btn btn-secondary">Explorar Proyectos</button>
            </div>
        </div>
    </section>

    <!-- STATS SECTION -->
    <section class="stats">
        <div class="stat-item">
            <div class="stat-number">150+</div>
            <div class="stat-label">Producciones</div>
        </div>
        <div class="stat-item">
            <div class="stat-number">50K+</div>
            <div class="stat-label">Seguidores</div>
        </div>
        <div class="stat-item">
            <div class="stat-number">5M+</div>
            <div class="stat-label">Reproducciones</div>
        </div>
    </section>

    <!-- FEATURED SECTION -->
    <section class="featured" id="music">
        <h2 class="section-title">Proyectos Destacados</h2>
        <div class="featured-grid">
            <div class="featured-card">
                <div class="featured-header"></div>
                <div class="featured-content">
                    <h3>Proyecto Alpha</h3>
                    <p>Una exploración sónica del futuro. Productor, mezclas digitales y experimentación auditiva sin límites.</p>
                </div>
            </div>
            <div class="featured-card">
                <div class="featured-header"></div>
                <div class="featured-content">
                    <h3>Proyecto Beta</h3>
                    <p>Colaboraciones con artistas internacionales. Ritmos hipnotizantes y synths que transportan mundos.</p>
                </div>
            </div>
            <div class="featured-card">
                <div class="featured-header"></div>
                <div class="featured-content">
                    <h3>Proyecto Gamma</h3>
                    <p>Experimental digital. Donde la tecnología y el arte se fusionan en pura creatividad desenfrenada.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer>
        <div class="footer-content">
            <div class="social-links">
                <a href="#">Instagram</a>
                <a href="#">YouTube</a>
                <a href="#">Spotify</a>
                <a href="#">Twitter</a>
            </div>
            <p class="copyright">© 2026 MauriSpide. Todos los derechos reservados.</p>
        </div>
    </footer>

    <script>
        // Cursor personalizado
        const cursor = document.querySelector('.cursor');
        
        document.addEventListener('mousemove', (e) => {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
        });

        // Efecto hover en elementos interactivos
        const interactiveElements = document.querySelectorAll('a, button');
        
        interactiveElements.forEach(el => {
            el.addEventListener('mouseenter', () => {
                cursor.classList.add('active');
            });
            el.addEventListener('mouseleave', () => {
                cursor.classList.remove('active');
            });
        });

        // Animación de scroll suave
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                }
            });
        });
    </script>
</body>
</html>