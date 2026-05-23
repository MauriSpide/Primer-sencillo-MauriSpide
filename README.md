            animation: gradientSh<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yo Soy MauriSpide - 7 Frecuencias Urbanas</title>
    <!-- Fuentes Urbanas e Industriales -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Permanent+Marker&family=Rubik+Glitch&family=Sedgwick+Ave+Display&family=Space+Grotesk:wght@500;800&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --primary: #ff0055;
            --secondary: #00ffcc;
            --accent: #ffcc00;
            --bg-dark: #040406;
            --panel-bg: rgba(6, 6, 10, 0.94);
            --glow: var(--primary);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            user-select: none;
        }

        body {
            background-color: var(--bg-dark);
            background-image: 
                radial-gradient(circle at 50% 50%, rgba(255, 0, 85, 0.08) 0%, transparent 75%),
                linear-gradient(rgba(255, 255, 255, 0.01) 1px, transparent 1px),
                linear-gradient(90deg, rgba(255, 255, 255, 0.01) 1px, transparent 1px);
            background-size: 100% 100%, 25px 25px, 25px 25px;
            color: #fff;
            font-family: 'Space Grotesk', sans-serif;
            overflow-x: hidden;
            min-height: 100vh;
        }

        /* TEXTURA CRT */
        body::after {
            content: " ";
            display: block;
            position: fixed;
            top: 0; left: 0; bottom: 0; right: 0;
            background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%), linear-gradient(90deg, rgba(255, 0, 0, 0.06), rgba(0, 255, 0, 0.02), rgba(0, 0, 255, 0.06));
            z-index: 99999;
            background-size: 100% 3px, 6px 100%;
            pointer-events: none;
        }

        #particles-canvas {
            position: fixed;
            top: 0; left: 0; width: 100vw; height: 100vh;
            z-index: 1; pointer-events: none;
        }

        /* INTRO CINEMÁTICA */
        .intro-splash {
            position: fixed;
            top: 0; left: 0; width: 100vw; height: 100vh;
            background: #010102;
            z-index: 9999;
            display: flex;
            justify-content: center;
            align-items: center;
            animation: fadeOutIntro 0.5s cubic-bezier(0.86, 0, 0.07, 1) 4.2s forwards;
        }

        .studio-monitor {
            border: 2px solid #11111a;
            padding: 40px;
            background: #050508;
            border-radius: 12px;
            text-align: center;
            position: relative;
            box-shadow: 0 0 50px rgba(0,0,0,1);
        }

        .studio-monitor::before {
            content: '● REC MODE';
            position: absolute; top: 15px; left: 20px;
            color: var(--primary);
            font-size: 0.75rem; font-weight: 800;
            letter-spacing: 2px;
            animation: blink 0.6s infinite alternate;
        }

        .intro-text {
            font-family: 'Permanent Marker', cursive;
            font-size: clamp(1.8rem, 5vw, 3.5rem);
            color: #fff;
            line-height: 1.3;
            margin-bottom: 25px;
            letter-spacing: 2px;
        }

        .loading-bar-container {
            width: 240px; height: 5px;
            background: #111; border-radius: 3px;
            overflow: hidden; margin: 0 auto;
        }

        .loading-bar {
            width: 0%; height: 100%;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            animation: loadProgress 3.8s cubic-bezier(0.2, 0.8, 0.2, 1) forwards;
        }

        /* CONTENEDOR PRINCIPAL */
        .main-container {
            position: relative;
            z-index: 10;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 30px 20px;
            min-height: 100vh;
            max-width: 1200px;
            margin: 0 auto;
            justify-content: space-between;
            gap: 30px;
            opacity: 0;
            animation: fadeInMain 0.6s ease 4.5s forwards;
        }

        .panel-decorator {
            position: absolute;
            font-family: 'Permanent Marker', cursive;
            font-size: 1.2rem;
            color: var(--accent);
            opacity: 0.6;
            transition: transform 0.3s ease, color 0.3s ease;
        }
        .dec-top-left { top: -12px; left: 10px; }
        .dec-bottom-right { bottom: -12px; right: 10px; }

        /* HEADER */
        .graffiti-header {
            position: relative;
            padding: 20px;
            text-align: center;
            cursor: crosshair;
        }

        .graffiti-halo {
            position: absolute;
            top: -5px; left: 50%;
            transform: translateX(-50%) rotate(-3deg);
            width: 180px; height: 28px;
            border: 4px solid var(--accent);
            border-radius: 50%;
            box-shadow: 0 0 20px var(--accent);
            opacity: 0.85;
            pointer-events: none;
            animation: haloPulse 2s infinite alternate ease-in-out;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .graffiti-header:hover .graffiti-halo {
            width: 230px;
            height: 35px;
            border-color: var(--secondary);
            box-shadow: 0 0 35px var(--secondary);
            transform: translateX(-50%) rotate(5deg);
        }

        .street-star {
            position: absolute;
            font-size: 2.5rem;
            color: var(--secondary);
            text-shadow: 0 0 15px var(--secondary);
            font-family: 'Permanent Marker', cursive;
            animation: starRotate 6s infinite linear;
            transition: color 0.3s;
        }
        .star-left { top: 35px; left: -35px; }
        .star-right { top: 20px; right: -35px; animation-direction: reverse; }

        .graffiti-header:hover .street-star {
            color: var(--primary);
            text-shadow: 0 0 25px var(--primary);
        }

        .graffiti-title {
            font-family: 'Sedgwick Ave Display', cursive;
            font-size: clamp(3.2rem, 9vw, 6.8rem);
            color: #fff;
            letter-spacing: -1px;
            line-height: 0.95;
            text-shadow: 
                4px 4px 0px var(--glow),
                -2px -2px 0px #000,
                10px 10px 20px rgba(0,0,0,0.9);
            transform: rotate(-2deg) skewX(-3deg);
            transition: transform 0.2s ease, text-shadow 0.2s ease;
        }

        .graffiti-header:hover .graffiti-title {
            transform: rotate(1deg) skewX(2deg) scale(1.05);
            text-shadow: 
                -4px 4px 0px var(--secondary),
                4px -4px 0px var(--accent),
                0 0 30px var(--primary);
        }

        .tagline-sencillo {
            font-family: 'Space Grotesk', sans-serif;
            font-weight: 800;
            font-size: 1.1rem;
            color: #fff;
            margin-top: 20px;
            letter-spacing: 8px;
            text-transform: uppercase;
            border: 2px solid var(--glow);
            padding: 6px 20px;
            border-radius: 4px;
            display: inline-block;
            background: rgba(0,0,0,0.6);
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            transition: all 0.3s ease;
        }
        .graffiti-header:hover .tagline-sencillo {
            border-color: #fff;
            background: var(--glow);
            box-shadow: 0 0 20px var(--glow);
        }

        /* ECOSISTEMA DE AUDIO */
        .sound-system-area {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 30px;
            width: 100%;
            position: relative;
        }

        .bass-wave-layer {
            position: absolute;
            width: 340px; height: 340px;
            border: 2px solid var(--primary);
            border-radius: 50%;
            opacity: 0;
            pointer-events: none;
            z-index: 1;
            transition: all 0.1s ease;
        }
        .wave-active {
            animation: shockWave 0.4s cubic-bezier(0.1, 0.8, 0.3, 1);
        }

        /* =======================================================
           NUEVO SISTEMA DE BOCINAS MODULARES MULTI-DISEÑO
        ======================================================= */
        .speaker-box {
            width: 95px; height: 280px;
            background: #0b0b0f;
            border: 3px solid #1a1a24;
            border-radius: 12px;
            display: flex;
            flex-direction: column;
            justify-content: space-around;
            align-items: center;
            padding: 15px 5px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.8);
            z-index: 2;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            transition: border-color 0.3s, transform 0.3s, box-shadow 0.3s;
        }
        .speaker-box:hover {
            border-color: var(--secondary);
            transform: scale(1.05);
            box-shadow: 0 0 20px rgba(0, 255, 204, 0.2);
        }

        /* Etiqueta flotante de la bocina */
        .speaker-box::before {
            content: "TAP TO SWITCH";
            position: absolute; bottom: 2px; left: 0; width: 100%;
            font-size: 0.5rem; text-align: center; color: #444;
            font-weight: 800; letter-spacing: 1px;
        }
        .speaker-box:hover::before { color: var(--accent); }

        /* CONTENEDOR INTERNO DE COMPONENTES ELECTRÓNICOS */
        .speaker-housing {
            width: 100%; height: 100%;
            display: flex; flex-direction: column;
            justify-content: space-around; align-items: center;
            transition: all 0.2s ease;
        }

        /* --- DISEÑO 1: BARRIO SUB-WOOFER CLASSIC --- */
        .design-1 .cone-top {
            width: 55px; height: 55px;
            background: radial-gradient(circle, #020202 30%, #16161f 60%, #252530 80%);
            border-radius: 50%; border: 2px solid #2d2d3a;
        }
        .design-1 .cone-bottom {
            width: 75px; height: 75px;
            background: radial-gradient(circle, #020202 30%, #16161f 60%, #252530 80%);
            border-radius: 50%; border: 2px solid #2d2d3a;
        }
        /* Comportamiento al raspar */
        .bass-vibe-speakers .design-1 .cone-top,
        .bass-vibe-speakers .design-1 .cone-bottom {
            animation: speakerPunch 0.08s infinite alternate;
        }

        /* --- DISEÑO 2: PROFESIONAL ASYMMETRIC --- */
        .design-2 .cone-top {
            width: 30px; height: 30px;
            background: #111; border-radius: 4px;
            border: 2px solid var(--accent);
            box-shadow: inset 0 0 5px #000;
        }
        .design-2 .cone-bottom {
            width: 70px; height: 90px;
            background: linear-gradient(#111, #222); border-radius: 40% 40% 50% 50%;
            border: 2px solid #333;
        }
        .bass-vibe-speakers .design-2 .cone-bottom {
            transform: scaleX(1.1) scaleY(0.9);
            border-color: var(--primary);
        }

        /* --- DISEÑO 3: MPC SAMPLER MATRIX --- */
        .design-3 { justify-content: center; gap: 10px; }
        .design-3 .pad {
            width: 40px; height: 40px; background: #16161f;
            border: 2px solid #252532; border-radius: 6px;
            transition: all 0.2s;
        }
        .design-3 .pad-active { border-color: var(--secondary); background: rgba(0,255,204,0.1); }
        .bass-vibe-speakers .design-3 .pad {
            background: var(--primary);
            box-shadow: 0 0 15px var(--primary);
            border-color: #fff;
        }

        /* --- DISEÑO 4: CYBERPUNK EQUALIZER --- */
        .design-4 { justify-content: center; gap: 8px; width: 100%; padding: 0 15px; }
        .design-4 .eq-bar {
            width: 100%; height: 18px; background: #111;
            border-radius: 3px; border: 1px solid #222;
            transform-origin: left; transition: all 0.1s;
        }
        .bass-vibe-speakers .design-4 .eq-bar:nth-child(odd) {
            background: var(--accent); transform: scaleX(1.2); box-shadow: 0 0 8px var(--accent);
        }
        .bass-vibe-speakers .design-4 .eq-bar:nth-child(even) {
            background: var(--secondary); transform: scaleX(0.8); box-shadow: 0 0 8px var(--secondary);
        }

        /* --- DISEÑO 5: RF CORE NUCLEUS --- */
        .design-5 .core-ring {
            width: 65px; height: 65px; border-radius: 50%;
            border: 3px double #333;
            display: flex; justify-content: center; align-items: center;
            transition: all 0.2s;
        }
        .design-5 .core-dot {
            width: 15px; height: 15px; background: #444; border-radius: 50%;
        }
        .bass-vibe-speakers .design-5 .core-ring {
            border-color: var(--secondary);
            transform: scale(1.15) rotate(45deg);
            border-style: dotted;
        }
        .bass-vibe-speakers .design-5 .core-dot {
            background: #fff; box-shadow: 0 0 12px #fff;
        }


        /* TORNAMESA */
        .deck-scratch-shake {
            animation: deckVibe 0.08s infinite;
        }

        .turntable-deck {
            background: linear-gradient(135deg, #0e0e14 0%, #040407 100%);
            border: 4px solid #1a1a24;
            border-radius: 28px;
            padding: 30px;
            box-shadow: 0 30px 60px rgba(0,0,0,0.9);
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            width: 360px; height: 360px;
            z-index: 2;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        .turntable-deck:hover {
            border-color: var(--primary);
            box-shadow: 0 35px 70px rgba(0,0,0,0.95), 0 0 20px rgba(255, 0, 85, 0.2);
            transform: scale(1.02);
        }

        .turntable-arm {
            position: absolute; top: 25px; right: 25px;
            width: 35px; height: 145px;
            border-right: 4px solid #666; border-top: 4px solid #666;
            border-radius: 0 25px 0 0;
            transform-origin: top right; transform: rotate(14deg);
            z-index: 5; pointer-events: none;
            transition: transform 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .vinyl-wrapper {
            width: 290px; height: 290px;
            position: relative; border-radius: 50%;
        }

        .vinyl {
            width: 100%; height: 100%; border-radius: 50%;
            background: repeating-radial-gradient(circle, #0b0b0f, #0b0b0f 2px, #14141d 5px, #0b0b0f 7px);
            position: relative; cursor: grab; touch-action: none;
            box-shadow: 0 10px 30px rgba(0,0,0,0.8);
        }
        .vinyl:active { cursor: grabbing; }

        .vinyl-center {
            position: absolute; top: 25%; left: 25%; width: 50%; height: 50%;
            background: linear-gradient(45deg, var(--glow), #000000);
            border-radius: 50%; border: 6px solid #040406;
            display: flex; justify-content: center; align-items: center; z-index: 3;
            transition: background 0.3s;
        }

        .vinyl-center-art {
            font-family: 'Permanent Marker', cursive;
            font-size: 1.2rem; color: #fff;
            transform: rotate(-6deg); text-align: center;
            text-shadow: 2px 2px 4px #000;
        }

        /* PANEL DE 7 SECCIONES */
        .rapper-bio-panel {
            width: 100%; max-width: 620px;
            background: var(--panel-bg);
            border: 1px solid rgba(255,255,255,0.03);
            border-left: 6px solid var(--glow);
            padding: 25px; border-radius: 16px;
            backdrop-filter: blur(12px);
            box-shadow: 0 20px 45px rgba(0,0,0,0.6);
            position: relative;
            transition: border-color 0.3s, transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275), box-shadow 0.3s;
        }

        .rapper-bio-panel:hover {
            transform: translateY(-5px);
            border-color: rgba(255,255,255,0.1);
            border-left-color: var(--secondary);
            box-shadow: 0 30px 60px rgba(0,0,0,0.7), 0 0 25px rgba(0, 255, 204, 0.15);
        }
        .rapper-bio-panel:hover .panel-decorator {
            color: var(--secondary);
            transform: scale(1.2) rotate(10deg);
        }

        .bio-title {
            font-weight: 800; color: var(--accent);
            font-size: 0.85rem; letter-spacing: 4px;
            text-transform: uppercase; margin-bottom: 12px;
            display: flex; align-items: center; justify-content: space-between;
        }
        .section-badge {
            background: rgba(255,255,255,0.07);
            padding: 2px 8px; border-radius: 4px; color: #fff; font-size: 0.75rem;
        }

        .bio-text {
            font-size: 1.25rem; color: #f5f5fa;
            line-height: 1.6; font-weight: 500;
            min-height: 95px;
            transition: opacity 0.15s, transform 0.15s;
        }

        .hint-tag {
            font-size: 0.75rem; color: #666;
            text-transform: uppercase; letter-spacing: 2px;
            margin-top: 15px; font-weight: 800; text-align: center;
            animation: pulseText 1s infinite alternate;
        }

        /* CONTADOR INDUSTRIAL */
        .countdown-container {
            background: var(--panel-bg);
            border: 2px solid #121218;
            padding: 18px 40px; border-radius: 14px;
            display: flex; flex-direction: column; align-items: center;
            position: relative;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        .countdown-container:hover {
            transform: translateY(-4px);
            border-color: var(--accent);
            box-shadow: 0 25px 50px rgba(0,0,0,0.7), 0 0 20px rgba(255, 204, 0, 0.1);
        }
        .countdown-container:hover .panel-decorator {
            color: var(--primary);
            transform: scale(1.2) rotate(-10deg);
        }

        .countdown-title {
            font-size: 0.8rem; text-transform: uppercase;
            letter-spacing: 3px; color: #555; margin-bottom: 12px;
            transition: color 0.3s;
        }
        .countdown-container:hover .countdown-title { color: #fff; }

        .timer { display: flex; gap: 30px; }
        .time-number { font-size: clamp(2.5rem, 5vw, 3.5rem); font-weight: 800; color: #fff; transition: text-shadow 0.3s; }
        .countdown-container:hover .time-number {
            text-shadow: 0 0 15px var(--accent);
        }
        .time-label { font-size: 0.65rem; text-transform: uppercase; color: #aa00ff; margin-top: 4px; letter-spacing: 1px; }

        /* TABLA DE CRÉDITOS */
        .credits-board {
            width: 100%; max-width: 720px;
            background: #060608; border: 1px solid #111116;
            padding: 22px; border-radius: 10px;
        }
        .credits-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 15px; }
        
        .credit-item {
            padding: 10px; border-radius: 6px; background: transparent;
            transition: all 0.2s ease;
        }
        .credit-item:hover {
            background: rgba(255,255,255,0.02); transform: scale(1.03);
        }
        .credit-label { color: #3d3d4e; text-transform: uppercase; font-size: 0.7rem; letter-spacing: 2px; font-weight: 800; transition: color 0.2s; }
        .credit-value { color: #fff; font-weight: 800; font-size: 1.1rem; transition: color 0.2s; }
        
        .credit-item:hover .credit-label { color: #fff; }
        .credit-item:hover .credit-value { color: var(--secondary); }

        /* LLAVES DE ANIMACIONES CSS */
        @keyframes loadProgress { to { width: 100%; } }
        @keyframes fadeOutIntro { to { opacity: 0; visibility: hidden; pointer-events: none; } }
        @keyframes fadeInMain { to { opacity: 1; } }
        @keyframes blink { from { opacity: 0.1; } to { opacity: 1; } }
        @keyframes pulseText { from { opacity: 0.4; } to { opacity: 1; } }
        
        @keyframes haloPulse {
            0% { transform: translateX(-50%) rotate(-3deg) scale(0.97); filter: brightness(0.9); }
            100% { transform: translateX(-50%) rotate(-2deg) scale(1.03); filter: brightness(1.2); }
        }
        @keyframes starRotate {
            0% { transform: rotate(0deg) scale(1); }
            50% { transform: rotate(180deg) scale(1.1); }
            100% { transform: rotate(360deg) scale(1); }
        }
        @keyframes speakerPunch {
            0% { transform: scale(1); filter: contrast(1); }
            100% { transform: scale(1.09); filter: contrast(1.4); }
        }
        @keyframes deckVibe {
            0% { transform: translate(1px, 1px) rotate(0deg); }
            100% { transform: translate(-1px, -1px) rotate(0.5deg); }
        }
        @keyframes shockWave {
            0% { transform: scale(1); opacity: 0.8; border-color: var(--primary); }
            100% { transform: scale(1.3); opacity: 0; border-color: var(--secondary); }
        }

        @media (max-width: 680px) {
            .speaker-box { display: none; }
            .turntable-arm { display: none; }
        }
    </style>
</head>
<body>

    <canvas id="particles-canvas"></canvas>

    <!-- INTRO DE ESTUDIO -->
    <div class="intro-splash">
        <div class="studio-monitor">
            <div class="intro-text">
                MAURISPIDE<br>
                <span style="font-size: 1.1rem; color: #444; font-family: 'Space Grotesk'; font-weight:800; letter-spacing: 3px;">INITIALIZING 7-TRACK ENGINE</span><br>
                LAIP.I COLLECTIVE
            </div>
            <div class="loading-bar-container">
                <div class="loading-bar"></div>
            </div>
        </div>
    </div>

    <!-- INTERFAZ COMPLETA -->
    <div class="main-container">
        
        <header class="graffiti-header">
            <div class="graffiti-halo"></div>
            <div class="street-star star-left">★</div>
            <div class="street-star star-right">★</div>
            <h1 class="graffiti-title">Yo Soy MauriSpide</h1>
            <center><div class="tagline-sencillo">PRIMER SENCILLO</div></center>
        </header>

        <!-- AREA DE TRABAJO ACÚSTICA REACTIVA -->
        <div class="sound-system-area" id="sound-area">
            
            <div class="bass-wave-layer" id="shock-wave"></div>

            <!-- Bocina Izquierda -->
            <div class="speaker-box" id="speaker-left">
                <div class="speaker-housing design-1" id="housing-left">
                    <div class="cone-top"></div>
                    <div class="cone-bottom"></div>
                </div>
            </div>

            <!-- Cubierta de Tornamesa -->
            <div class="turntable-deck" id="turntable-deck">
                <div class="turntable-arm" id="turntable-arm"></div>
                <div class="vinyl-wrapper">
                    <div class="vinyl" id="interactive-vinyl">
                        <div class="vinyl-center">
                            <div class="vinyl-center-art">Mauri<br><span style="color:var(--secondary); font-size:0.75rem;">SPIDE</span></div>
                        </div>
                        <div class="vinyl-hole"></div>
                    </div>
                </div>
            </div>

            <!-- Bocina Derecha -->
            <div class="speaker-box" id="speaker-right">
                <div class="speaker-housing design-1" id="housing-right">
                    <div class="cone-top"></div>
                    <div class="cone-bottom"></div>
                </div>
            </div>

        </div>

        <!-- DISPLAY DINÁMICO DE 7 SECCIONES -->
        <section class="rapper-bio-panel" id="bio-panel">
            <div class="panel-decorator dec-top-left">★</div>
            <div class="panel-decorator dec-bottom-right">✦</div>
            <div class="bio-title">
                <span id="bio-header">FRECUENCIA #1: ORIGEN DEL TRACK</span>
                <span class="section-badge" id="section-counter">1 / 7</span>
            </div>
            <div class="bio-text" id="bio-content">
                MauriSpide, representante del rap Mexicano, emergente desde el Estado de México llega con su primer sencillo "Yo soy MauriSpide" de la mano de LAIP.I Music Songs.
            </div>
            <div class="hint-tag">🎛️ GIRA O HAZ SCRATCH EN EL VINILO PARA CONMUTAR 🎛️</div>
        </section>

        <!-- CONTADOR INDUSTRIAL -->
        <div class="countdown-container">
            <div class="panel-decorator dec-top-left">✦</div>
            <div class="panel-decorator dec-bottom-right">★</div>
            <div class="countdown-title">Tiempo restante para la detonación en plataformas</div>
            <div class="timer" id="countdown-timer">
                <div class="time-segment">
                    <div class="time-number" id="days">37</div>
                    <div class="time-label">Días</div>
                </div>
                <div class="time-segment">
                    <div class="time-number" id="hours">00</div>
                    <div class="time-label">Horas</div>
                </div>
                <div class="time-segment">
                    <div class="time-number" id="minutes">00</div>
                    <div class="time-label">Minutos</div>
                </div>
                <div class="time-segment">
                    <div class="time-number" id="seconds">00</div>
                    <div class="time-label">Segundos</div>
                </div>
            </div>
        </div>

        <!-- SECCIÓN FIJA DE CRÉDITOS EJECUTIVOS -->
        <footer class="credits-board">
            <div class="credits-grid">
                <div class="credit-item"><span class="credit-label">Autor Principal</span><div class="credit-value">MauriSpide</div></div>
                <div class="credit-item"><span class="credit-label">Composición</span><div class="credit-value">MaurSpide</div></div>
                <div class="credit-item"><span class="credit-label">Ing. de Mezcla</span><div class="credit-value" style="color:var(--accent);">Mau (Mcra.FtS)</div></div>
                <div class="credit-item"><span class="credit-label">Dirección Artística</span><div class="credit-value">LAIP.I Collective</div></div>
                <div class="credit-item"><span class="credit-label">Distribuidora</span><div class="credit-value" style="color:var(--secondary);">LAIP.I Music Songs</div></div>
            </div>
        </footer>

    </div>

    <script>
        // === 1. ARQUITECTURA DE LAS 7 SECCIONES INFORMATIVAS ===
        const infoSections = [
            {
                title: "FRECUENCIA #1: ORIGEN DE LA ESCENA",
                text: "MauriSpide, representante del rap Mexicano, emergente desde el Estado de México llega con su primer sencillo \"Yo soy MauriSpide\" de la mano de LAIP.I Music Songs."
            },
            {
                title: "FRECUENCIA #2: FILOSOFÍA DE BARRIO",
                text: "Inspirado de barras crudas y callejeras viene a representar su convicción en el hip-hop, retratando la realidad acústica del asfalto mexiquense."
            },
            {
                title: "FRECUENCIA #3: ARQUITECTURA DEL BEAT",
                text: "Respaldado en las frecuencias y arreglos duros por Mau (Mcra.FtS), inyectando samples oscuros de la vieja escuela y un bajo pesado que hace templar las estructuras."
            },
            {
                title: "FRECUENCIA #4: COLECTIVO DE VANGUARDIA",
                text: "El soporte conceptual y la identidad visual corre por cuenta de LAIP.I Collective, fusionando la esencia del graffiti ilegal con el diseño gráfico de alto nivel técnico."
            },
            {
                title: "FRECUENCIA #5: INGENIERÍA DE AUDIO",
                text: "El track cuenta con un tratamiento sonoro agresivo y pulido, diseñado minuciosamente para retumbar tanto en audífonos de calle como en los monitores de un auto."
            },
            {
                title: "FRECUENCIA #6: LANZAMIENTO GLOBAL",
                text: "La distribución corre por parte de LAIP.I Music Songs, asegurando la salida simultánea en todas las plataformas de streaming digital del planeta de forma masiva."
            },
            {
                title: "FRECUENCIA #7: LA CUENTA REGRESIVA",
                text: "37 días nos separan del impacto definitivo. Los motores están encendidos, las maquetas cerradas y el trono listo para ser reclamado por MauriSpide."
            }
        ];
        
        let currentSectionIdx = 0;
        const bioContent = document.getElementById('bio-content');
        const bioHeader = document.getElementById('bio-header');
        const sectionBadge = document.getElementById('section-counter');

        function triggerNextSection() {
            currentSectionIdx = (currentSectionIdx + 1) % infoSections.length;
            
            bioContent.style.opacity = 0;
            bioContent.style.transform = "translateY(5px)";
            
            setTimeout(() => {
                bioHeader.innerText = infoSections[currentSectionIdx].title;
                bioContent.innerText = infoSections[currentSectionIdx].text;
                sectionBadge.innerText = `${currentSectionIdx + 1} / 7`;
                
                bioContent.style.opacity = 1;
                bioContent.style.transform = "translateY(0px)";
                mutateColors();
                triggerShockWave();
            }, 120);
        }

        // === 2. CAMBIO DE COLORES CROMÁTICO ===
        const urbanPalettes = [
            { primary: '#ff0055', secondary: '#00ffcc', accent: '#ffcc00', bg: '#040406' },
            { primary: '#00ffcc', secondary: '#ff00aa', accent: '#ffffff', bg: '#020606' },
            { primary: '#ffcc00', secondary: '#0077ff', accent: '#ff3300', bg: '#060502' },
            { primary: '#b700ff', secondary: '#00ff66', accent: '#ffff00', bg: '#050207' }
        ];
        let paletteIdx = 0;

        function mutateColors() {
            paletteIdx = (paletteIdx + 1) % urbanPalettes.length;
            const p = urbanPalettes[paletteIdx];
            
            document.documentElement.style.setProperty('--primary', p.primary);
            document.documentElement.style.setProperty('--secondary', p.secondary);
            document.documentElement.style.setProperty('--accent', p.accent);
            document.documentElement.style.setProperty('--bg-dark', p.bg);
            document.documentElement.style.setProperty('--glow', p.primary);

            const deck = document.getElementById('turntable-deck');
            deck.style.borderColor = p.primary;
        }

        function triggerShockWave() {
            const wave = document.getElementById('shock-wave');
            wave.classList.remove('wave-active');
            void wave.offsetWidth; 
            wave.classList.add('wave-active');
        }

        // === 3. SISTEMA MODULAR DE INTERCAMBIO DE BOCINAS (5 DISEÑOS) ===
        let currentSpeakerDesign = 1;
        const totalDesigns = 5;
        const housingLeft = document.getElementById('housing-left');
        const housingRight = document.getElementById('housing-right');

        const templates = {
            1: `<div class="cone-top"></div><div class="cone-bottom"></div>`,
            2: `<div class="cone-top"></div><div class="cone-bottom"></div>`,
            3: `<div class="pad pad-active"></div><div class="pad"></div><div class="pad"></div><div class="pad pad-active"></div>`,
            4: `<div class="eq-bar"></div><div class="eq-bar"></div><div class="eq-bar"></div><div class="eq-bar"></div><div class="eq-bar"></div>`,
            5: `<div class="core-ring"><div class="core-dot"></div></div>`
        };

        function cycleSpeakerDesign() {
            currentSpeakerDesign = (currentSpeakerDesign % totalDesigns) + 1;
            
            [housingLeft, housingRight].forEach(housing => {
                housing.style.opacity = 0;
                setTimeout(() => {
                    housing.className = `speaker-housing design-${currentSpeakerDesign}`;
                    housing.innerHTML = templates[currentSpeakerDesign];
                    housing.style.opacity = 1;
                }, 150);
            });
            triggerShockWave();
        }

        document.getElementById('speaker-left').addEventListener('click', cycleSpeakerDesign);
        document.getElementById('speaker-right').addEventListener('click', cycleSpeakerDesign);

        // === 4. RELOJ REGRESIVO ===
        const targetDate = new Date().getTime() + (37 * 24 * 60 * 60 * 1000);
        function updateClock() {
            const diff = targetDate - new Date().getTime();
            if (diff <= 0) return;
            document.getElementById('days').innerText = Math.floor(diff / (1000*60*60*24)).toString().padStart(2, '0');
            document.getElementById('hours').innerText = Math.floor((diff % (1000*60*60*24)) / (1000*60*60)).toString().padStart(2, '0');
            document.getElementById('minutes').innerText = Math.floor((diff % (1000*60*60)) / (1000*60)).toString().padStart(2, '0');
            document.getElementById('seconds').innerText = Math.floor((diff % (1000*60)) / 1000).toString().padStart(2, '0');
        }
        setInterval(updateClock, 1000); updateClock();

        // === 5. CONTROLADOR DE VINILO (GIRO + SCRATCH) ===
        const vinyl = document.getElementById('interactive-vinyl');
        const arm = document.getElementById('turntable-arm');
        const soundArea = document.getElementById('sound-area');
        const deckContainer = document.getElementById('turntable-deck');

        let isInteracting = false;
        let currentAngle = 0;
        let startAngle = 0;
        let lastAngle = 0;
        let scratchAccumulator = 0;

        function getCenter() {
            const box = vinyl.getBoundingClientRect();
            return { x: box.left + box.width/2, y: box.top + box.height/2 };
        }

        function calculateAngle(px, py) {
            const center = getCenter();
            return Math.atan2(py - center.y, px - center.x) * (180 / Math.PI);
        }

        function startInteraction(e) {
            isInteracting = true;
            const x = e.clientX || e.touches[0].clientX;
            const y = e.clientY || e.touches[0].clientY;
            startAngle = calculateAngle(x, y) - currentAngle;
            lastAngle = currentAngle;
            scratchAccumulator = 0;
            
            if(arm) arm.style.transform = "rotate(23deg)";
            soundArea.classList.add('bass-vibe-speakers');
            deckContainer.classList.add('deck-scratch-shake');
        }

        function moveInteraction(e) {
            if (!isInteracting) return;
            const x = e.clientX || (e.touches && e.touches[0].clientX);
            const y = e.clientY || (e.touches && e.touches[0].clientY);
            
            const targetA = calculateAngle(x, y);
            currentAngle = targetA - startAngle;
            
            // Aplicar rotación visual
            vinyl.style.transform = `rotate(${currentAngle}deg)`;
            
            // Calcular acumulación para el scratch
            scratchAccumulator += Math.abs(currentAngle - lastAngle);
            lastAngle = currentAngle;

            if (scratchAccumulator > 150) {
                triggerNextSection();
                scratchAccumulator = 0;
            }
        }

        function endInteraction() {
            isInteracting = false;
            if(arm) arm.style.transform = "rotate(14deg)";
            soundArea.classList.remove('bass-vibe-speakers');
            deckContainer.classList.remove('deck-scratch-shake');
        }

        vinyl.addEventListener('mousedown', startInteraction);
        window.addEventListener('mousemove', moveInteraction);
        window.addEventListener('mouseup', endInteraction);
        vinyl.addEventListener('touchstart', startInteraction, { passive: true });
        window.addEventListener('touchmove', moveInteraction, { passive: false });
        window.addEventListener('touchend', endInteraction);

        // === 6. MOTOR DE PARTÍCULAS SUBTERRÁNEAS ===
        const cnv = document.getElementById('particles-canvas');
        const ctx = cnv.getContext('2d');
        let cW = cnv.width = window.innerWidth;
        let cH = cnv.height = window.innerHeight;

        window.addEventListener('resize', () => { cW = cnv.width = window.innerWidth; cH = cnv.height = window.innerHeight; });

        const assets = ['♫', '★', '⚡', '✦'];
        const particles = [];

        class UrbanParticle {
            constructor() { this.init(); this.y = Math.random()*cH; }
            init() {
                this.x = Math.random()*cW; this.y = cH + 25;
                this.size = Math.random()*11 + 5;
                this.speedY = Math.random()*0.6 + 0.3;
                this.char = assets[Math.floor(Math.random()*assets.length)];
                this.alpha = Math.random()*0.2 + 0.08;
            }
            process() { this.y -= this.speedY; if(this.y < -25) this.init(); }
            render() {
                ctx.save(); ctx.globalAlpha = this.alpha;
                ctx.fillStyle = getComputedStyle(document.documentElement).getPropertyValue('--secondary').trim();
                ctx.font = `800 ${this.size * 1.1}px 'Space Grotesk'`;
                ctx.fillText(this.char, this.x, this.y); ctx.restore();
            }
        }

        for(let i=0; i<35; i++) particles.push(new UrbanParticle());

        function coreLoop() {
            if (!isInteracting) {
                currentAngle += 0.85; // Rotación automática constante
                vinyl.style.transform = `rotate(${currentAngle}deg)`;
            }
            ctx.clearRect(0,0,cW,cH);
            for(let i=0; i<particles.length; i++) { particles[i].process(); particles[i].render(); }
            requestAnimationFrame(coreLoop);
        }
        coreLoop();
    </script>
</body>
</html>ift 15s ease infinite;
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
