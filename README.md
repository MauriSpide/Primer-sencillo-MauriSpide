<!DOCTYPE html>
<html lang="es">
<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Yo Soy MauriSpide</title>

<!-- FUENTES -->
<link href="https://fonts.googleapis.com/css2?family=Permanent+Marker&family=Poppins:wght@300;400;600;700;800&display=swap" rel="stylesheet">

<style>

/* RESET */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

/* BODY */

body{
    background:#0a0014;
    overflow-x:hidden;
    color:white;
    font-family:'Poppins', sans-serif;
    cursor:none;
}

/* CURSOR */

.cursor{

    width:20px;
    height:20px;
    border:2px solid #a200ff;
    border-radius:50%;
    position:fixed;
    pointer-events:none;
    transform:translate(-50%, -50%);
    z-index:9999;
    box-shadow:0 0 20px #a200ff, 0 0 40px rgba(162,0,255,0.5);
    transition:all 0.1s ease-out;

}

.cursor.active{
    width:35px;
    height:35px;
    border-width:3px;
    box-shadow:0 0 30px #a200ff, 0 0 60px rgba(162,0,255,0.6);
    background:rgba(162,0,255,0.1);
}

/* FONDO */

.bg{

    position:fixed;
    width:100%;
    height:100%;
    overflow:hidden;
    z-index:-5;

    background:
    radial-gradient(circle at 20% 50%,
    rgba(162,0,255,0.3), transparent 40%),
    
    radial-gradient(circle at 80% 80%,
    rgba(100,50,255,0.2), transparent 50%),

    radial-gradient(circle at 50% 0%,
    rgba(162,0,255,0.15), transparent 50%),

    #0a0014;

}

/* TEXTURA */

.texture{

    position:fixed;
    width:100%;
    height:100%;
    background:url("https://www.transparenttextures.com/patterns/asfalt-dark.png");
    opacity:0.08;
    z-index:-4;

}

/* PARTÍCULAS */

.particle{

    position:absolute;
    width:2px;
    height:2px;
    background:#a200ff;
    border-radius:50%;
    opacity:0.4;
    animation:float linear infinite;
    box-shadow:0 0 10px rgba(162,0,255,0.8);

}

@keyframes float{

    from{
        transform:translateY(100vh) translateX(0);
    }

    to{
        transform:translateY(-10vh) translateX(100px);
    }

}

/* INTRO */

.intro{

    position:fixed;
    width:100%;
    height:100%;
    background:linear-gradient(135deg, #0a0014 0%, #1a0033 100%);
    z-index:999;
    display:flex;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    animation:introFade 4s forwards;

}

.intro h1{

    font-size:80px;
    font-family:'Permanent Marker', cursive;
    background:linear-gradient(135deg, #a200ff, #ff00ff);
    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;
    background-clip:text;
    text-shadow:0 0 20px rgba(162,0,255,0.5);
    animation:glitch 1s infinite;
    letter-spacing:3px;

}

.intro p{

    margin-top:20px;
    letter-spacing:8px;
    color:#b366ff;
    font-size:16px;
    font-weight:300;

}

@keyframes introFade{

    0%{
        opacity:1;
    }

    80%{
        opacity:1;
    }

    100%{
        opacity:0;
        visibility:hidden;
    }

}

@keyframes glitch{

    0%{
        transform:translate(0);
    }

    20%{
        transform:translate(-2px,2px);
    }

    40%{
        transform:translate(2px,-2px);
    }

    60%{
        transform:translate(-2px,0);
    }

    80%{
        transform:translate(2px,2px);
    }

    100%{
        transform:translate(0);
    }

}

/* HEADER */

.header{

    position:fixed;
    top:30px;
    left:40px;
    z-index:100;
    font-size:22px;
    font-weight:bold;
    background:rgba(162,0,255,0.1);
    padding:12px 25px;
    border-radius:50px;
    border:1px solid rgba(162,0,255,0.3);
    backdrop-filter:blur(10px);
    transition:0.3s;

}

.header:hover{
    background:rgba(162,0,255,0.2);
    border-color:rgba(162,0,255,0.6);
}

.header span{

    color:#a200ff;
    font-weight:700;

}

/* SOCIAL */

.socials{

    position:fixed;
    top:30px;
    right:40px;
    display:flex;
    gap:15px;
    z-index:100;

}

.socials a{

    color:white;
    text-decoration:none;
    transition:0.3s;
    padding:10px 18px;
    border:1px solid rgba(255,255,255,0.2);
    border-radius:25px;
    font-size:14px;
    font-weight:600;
    background:rgba(255,255,255,0.05);

}

.socials a:hover{

    color:#a200ff;
    border-color:#a200ff;
    background:rgba(162,0,255,0.2);
    transform:translateY(-2px);

}

/* CONTENEDOR */

.container{

    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    text-align:center;
    padding:120px 20px;
    position:relative;
    z-index:1;

}

/* TITULO */

.title{

    font-family:'Permanent Marker', cursive;
    font-size:140px;
    line-height:0.9;
    text-transform:uppercase;
    margin-bottom:40px;
    animation:titlePulse 3s infinite;
    letter-spacing:-2px;
    font-weight:900;

}

.title span{

    background:linear-gradient(135deg, #a200ff, #ff00ff, #a200ff);
    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;
    background-clip:text;
    text-shadow:0 0 40px rgba(162,0,255,0.6);
    filter:drop-shadow(0 0 20px rgba(162,0,255,0.5));

}

@keyframes titlePulse{

    0%{
        transform:scale(1);
        filter:drop-shadow(0 0 20px rgba(162,0,255,0.4));
    }

    50%{
        transform:scale(1.03);
        filter:drop-shadow(0 0 30px rgba(162,0,255,0.7));
    }

    100%{
        transform:scale(1);
        filter:drop-shadow(0 0 20px rgba(162,0,255,0.4));
    }

}

/* DISCO */

.vinyl-wrapper{

    position:relative;
    margin:60px 0;

}

.glow{

    position:absolute;
    width:500px;
    height:500px;
    background:radial-gradient(circle,
    rgba(162,0,255,0.6), rgba(100,50,255,0.2), transparent 70%);
    filter:blur(50px);
    z-index:-1;
    animation:glowPulse 3s infinite;
    top:50%;
    left:50%;
    transform:translate(-50%, -50%);

}

@keyframes glowPulse{

    0%{
        transform:translate(-50%, -50%) scale(1);
    }

    50%{
        transform:translate(-50%, -50%) scale(1.12);
    }

    100%{
        transform:translate(-50%, -50%) scale(1);
    }

}

.vinyl{

    width:400px;
    height:400px;
    border-radius:50%;

    background:
    radial-gradient(circle, #1a0033 15%, #0a0014 16%,
    #2d0052 30%, #0a0014 31%, #1a0033 45%, #0a0014 46%,
    #2d0052 60%, #0a0014 61%);

    animation:spin 8s linear infinite;

    display:flex;
    justify-content:center;
    align-items:center;

    box-shadow:
    0 0 60px rgba(162,0,255,0.7),
    inset 0 0 30px rgba(0,0,0,0.8);

}

.vinyl::before{

    content:"";
    width:130px;
    height:130px;
    background:linear-gradient(135deg, #a200ff, #ff00ff);
    border-radius:50%;
    position:absolute;
    box-shadow:0 0 40px #a200ff, inset 0 0 20px rgba(0,0,0,0.5);

}

.vinyl::after{

    content:"M";
    position:absolute;
    font-size:60px;
    font-weight:bold;
    color:white;
    z-index:1;

}

@keyframes spin{

    from{
        transform:rotate(0deg);
    }

    to{
        transform:rotate(360deg);
    }

}

/* TEXTO */

.description{

    max-width:900px;
    font-size:22px;
    line-height:1.9;
    color:#d1d1d1;
    margin-bottom:70px;
    font-weight:300;
    letter-spacing:0.5px;

}

/* COUNTDOWN */

.count-title{

    font-family:'Permanent Marker', cursive;
    background:linear-gradient(135deg, #a200ff, #ff00ff);
    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;
    background-clip:text;
    font-size:55px;
    margin-bottom:40px;
    font-weight:800;

}

.countdown{

    display:flex;
    gap:20px;
    flex-wrap:wrap;
    justify-content:center;
    margin-bottom:80px;

}

.box{

    width:150px;
    padding:35px 20px;

    background:rgba(162,0,255,0.1);

    border:2px solid rgba(162,0,255,0.3);

    border-radius:20px;

    backdrop-filter:blur(15px);

    transform:translateY(80px);

    opacity:0;

    animation:reveal 0.8s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;

    transition:0.3s;

    position:relative;
    overflow:hidden;

}

.box::before{
    content:"";
    position:absolute;
    top:0;
    left:-100%;
    width:100%;
    height:100%;
    background:linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
    transition:0.6s;
}

.box:hover::before{
    left:100%;
}

.box:nth-child(1){
    animation-delay:0.1s;
}

.box:nth-child(2){
    animation-delay:0.2s;
}

.box:nth-child(3){
    animation-delay:0.3s;
}

.box:nth-child(4){
    animation-delay:0.4s;
}

@keyframes reveal{

    to{
        transform:translateY(0);
        opacity:1;
    }

}

.box:hover{

    transform:translateY(-15px) scale(1.05);
    box-shadow:0 10px 40px rgba(162,0,255,0.5);
    border-color:rgba(162,0,255,0.8);
    background:rgba(162,0,255,0.2);

}

.number{

    font-size:65px;
    font-weight:900;
    background:linear-gradient(135deg, #a200ff, #ff00ff);
    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;
    background-clip:text;

}

.label{

    margin-top:15px;
    letter-spacing:4px;
    color:#b366ff;
    font-size:12px;
    font-weight:600;

}

/* BOTONES */

.buttons{

    display:flex;
    gap:30px;
    flex-wrap:wrap;
    justify-content:center;
    margin-bottom:90px;

}

button{

    padding:18px 50px;
    border:none;
    border-radius:50px;
    font-size:18px;
    font-weight:700;
    cursor:pointer;
    transition:all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
    text-transform:uppercase;
    letter-spacing:1px;
    position:relative;
    overflow:hidden;

}

button::before{
    content:"";
    position:absolute;
    top:50%;
    left:50%;
    width:0;
    height:0;
    border-radius:50%;
    background:rgba(255,255,255,0.2);
    transform:translate(-50%, -50%);
    transition:width 0.6s, height 0.6s;
}

button:active::before{
    width:300px;
    height:300px;
}

.listen{

    background:linear-gradient(135deg, #a200ff, #ff00ff);
    color:white;

    box-shadow:
    0 0 30px rgba(162,0,255,0.6),
    0 10px 25px rgba(162,0,255,0.3);

}

.listen:hover{

    transform:translateY(-3px) scale(1.08);
    box-shadow:0 0 40px rgba(162,0,255,0.8), 0 15px 35px rgba(162,0,255,0.5);

}

.share{

    background:transparent;
    border:2px solid #a200ff;
    color:#a200ff;

}

.share:hover{

    background:#a200ff;
    color:white;
    transform:translateY(-3px) scale(1.08);
    box-shadow:0 0 30px rgba(162,0,255,0.5);

}

/* CREDITOS */

.credits-title{

    font-family:'Permanent Marker', cursive;
    font-size:60px;
    background:linear-gradient(135deg, #a200ff, #ff00ff);
    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;
    background-clip:text;
    margin-bottom:40px;
    font-weight:800;

}

.credits{

    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(240px,1fr));
    gap:30px;
    width:100%;
    max-width:1100px;
    margin-bottom:60px;

}

.credit{

    background:rgba(162,0,255,0.08);
    border:1px solid rgba(162,0,255,0.3);
    padding:40px 30px;
    border-radius:20px;
    transition:all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
    backdrop-filter:blur(10px);
    position:relative;
    overflow:hidden;

}

.credit::before{
    content:"";
    position:absolute;
    top:-50%;
    right:-50%;
    width:100%;
    height:100%;
    background:radial-gradient(circle, rgba(162,0,255,0.3), transparent);
    opacity:0;
    transition:0.6s;
}

.credit:hover::before{
    opacity:1;
}

.credit:hover{

    transform:translateY(-12px) scale(1.05);
    box-shadow:0 15px 40px rgba(162,0,255,0.4);
    border-color:rgba(162,0,255,0.7);
    background:rgba(162,0,255,0.15);

}

.credit h3{

    color:#a200ff;
    margin-bottom:15px;
    font-size:18px;
    font-weight:700;
    letter-spacing:1px;

}

.credit p{
    color:#c1a0ff;
    font-weight:300;
    font-size:15px;
}

/* FOOTER */

.footer{

    margin-top:40px;
    color:#666;
    font-size:13px;
    letter-spacing:1px;

}

/* RESPONSIVE */

@media(max-width:900px){

    .title{
        font-size:100px;
    }

    .vinyl{
        width:320px;
        height:320px;
    }

    .glow{
        width:400px;
        height:400px;
    }

}

@media(max-width:700px){

    .title{
        font-size:70px;
    }

    .vinyl{
        width:250px;
        height:250px;
    }

    .vinyl::before{
        width:100px;
        height:100px;
    }

    .vinyl::after{
        font-size:45px;
    }

    .glow{
        width:300px;
        height:300px;
    }

    .description{
        font-size:16px;
    }

    .count-title{
        font-size:40px;
    }

    .number{
        font-size:50px;
    }

    button{
        padding:16px 35px;
        font-size:16px;
    }

    .credits-title{
        font-size:45px;
    }

    .header{
        padding:10px 18px;
        font-size:16px;
    }

    .socials{
        gap:10px;
        right:15px;
        top:15px;
    }

    .socials a{
        padding:8px 14px;
        font-size:12px;
    }

}

@media(max-width:480px){

    .title{
        font-size:50px;
    }

    .vinyl{
        width:200px;
        height:200px;
    }

    .vinyl::before{
        width:80px;
        height:80px;
    }

    .vinyl::after{
        font-size:35px;
    }

    .glow{
        width:250px;
        height:250px;
    }

    .description{
        font-size:14px;
        margin-bottom:40px;
    }

    .count-title{
        font-size:30px;
    }

    .countdown{
        gap:15px;
    }

    .box{
        width:120px;
        padding:25px 15px;
    }

    .number{
        font-size:40px;
    }

    .label{
        font-size:11px;
        letter-spacing:2px;
    }

    button{
        padding:15px 25px;
        font-size:14px;
    }

    .buttons{
        gap:15px;
        flex-direction:column;
    }

    .credits-title{
        font-size:35px;
    }

}

</style>
</head>

<body>

<!-- CURSOR -->
<div class="cursor"></div>

<!-- INTRO -->
<div class="intro">

    <h1>LAIP.I COLLECTIVE</h1>
    <p>PRESENTA</p>

</div>

<!-- FONDO -->
<div class="bg"></div>
<div class="texture"></div>

<!-- PARTÍCULAS -->

<script>

for(let i = 0; i < 60; i++){

    const particle = document.createElement("div");

    particle.classList.add("particle");

    particle.style.left = Math.random() * 100 + "vw";

    particle.style.animationDuration =
    (Math.random() * 12 + 8) + "s";

    particle.style.opacity = Math.random() * 0.5 + 0.2;

    document.body.appendChild(particle);

}

</script>

<!-- HEADER -->

<div class="header">

    LAIP.I <span>Collective</span>

</div>

<!-- REDES -->

<div class="socials">

    <a href="#">Instagram</a>
    <a href="#">YouTube</a>
    <a href="#">Spotify</a>

</div>

<!-- CONTENIDO -->

<div class="container">

    <!-- TITULO -->

    <div class="title">

        YO SOY<br>
        <span>MAURISPIDE</span>

    </div>

    <!-- DISCO -->

    <div class="vinyl-wrapper">

        <div class="glow"></div>

        <div class="vinyl"></div>

    </div>

    <!-- TEXTO -->

    <div class="description">

        Esto no es solo música, es mi historia,
        mi visión y el inicio de algo enorme.
        Gracias por ser parte del comienzo 🚀🔥

    </div>

    <!-- COUNTDOWN -->

    <div class="count-title">

        Falta poco para el lanzamiento

    </div>

    <div class="countdown">

        <div class="box">

            <div class="number" id="days">00</div>
            <div class="label">DÍAS</div>

        </div>

        <div class="box">

            <div class="number" id="hours">00</div>
            <div class="label">HORAS</div>

        </div>

        <div class="box">

            <div class="number" id="minutes">00</div>
            <div class="label">MINUTOS</div>

        </div>

        <div class="box">

            <div class="number" id="seconds">00</div>
            <div class="label">SEGUNDOS</div>

        </div>

    </div>

    <!-- BOTONES -->

    <div class="buttons">

        <button class="listen"
        onclick="window.location.href='https://youtube.com'">

            ESCUCHAR 🎧

        </button>

        <button class="share"
        onclick="shareMusic()">

            COMPARTIR 🔥

        </button>

    </div>

    <!-- CREDITOS -->

    <div class="credits-title">

        Créditos

    </div>

    <div class="credits">

        <div class="credit">

            <h3>Artista</h3>
            <p>MauriSpide</p>

        </div>

        <div class="credit">

            <h3>Producción</h3>
            <p>LAIP.I Collective</p>

        </div>

        <div class="credit">

            <h3>Composición</h3>
            <p>MauriSpide</p>

        </div>

        <div class="credit">

            <h3>Diseño</h3>
            <p>LAIP.I Collective</p>

        </div>

    </div>

    <div class="footer">

        © 2026 LAIP.I Collective —
        Todos los derechos reservados.

    </div>

</div>

<script>

/* CURSOR */

const cursor = document.querySelector(".cursor");

document.addEventListener("mousemove", e => {

    cursor.style.left = e.clientX + "px";
    cursor.style.top = e.clientY + "px";

});

document.addEventListener("mousedown", () => {
    cursor.classList.add("active");
});

document.addEventListener("mouseup", () => {
    cursor.classList.remove("active");
});

/* COUNTDOWN */

const releaseDate =
new Date("Jun 30, 2026 00:00:00").getTime();

const timer = setInterval(function(){

    const now = new Date().getTime();

    const distance = releaseDate - now;

    const days = Math.floor(distance /
    (1000 * 60 * 60 * 24));

    const hours = Math.floor(
    (distance % (1000 * 60 * 60 * 24))
    / (1000 * 60 * 60));

    const minutes = Math.floor(
    (distance % (1000 * 60 * 60))
    / (1000 * 60));

    const seconds = Math.floor(
    (distance % (1000 * 60))
    / 1000);

    document.getElementById("days").innerHTML = days;
    document.getElementById("hours").innerHTML = hours;
    document.getElementById("minutes").innerHTML = minutes;
    document.getElementById("seconds").innerHTML = seconds;

    if(distance < 0){

        clearInterval(timer);

        document.querySelector(".countdown").innerHTML = `

        <h1 style="
        background:linear-gradient(135deg, #a200ff, #ff00ff);
        -webkit-background-clip:text;
        -webkit-text-fill-color:transparent;
        background-clip:text;
        font-family:'Permanent Marker', cursive;
        font-size:70px;
        text-shadow:0 0 25px #a200ff;
        ">

        🎶 YA DISPONIBLE 🔥

        </h1>

        `;

    }

}, 1000);

/* SHARE */

function shareMusic(){

    navigator.share({

        title:"Yo Soy MauriSpide",

        text:"Escucha este nuevo lanzamiento 🚀🔥",

        url:window.location.href

    });

}

</script>

</body>
</html>
