<!DOCTYPE html>
<html lang="es">
<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Yo Soy MauriSpide</title>

<!-- FUENTES -->
<link href="https://fonts.googleapis.com/css2?family=Permanent+Marker&family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

<style>

/* RESET */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

/* BODY */

body{
    background:#030303;
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
    box-shadow:0 0 20px #a200ff;

}

/* FONDO */

.bg{

    position:fixed;
    width:100%;
    height:100%;
    overflow:hidden;
    z-index:-5;

    background:
    radial-gradient(circle at top left,
    rgba(162,0,255,0.2), transparent 30%),

    radial-gradient(circle at bottom right,
    rgba(255,255,255,0.05), transparent 30%),

    #030303;

}

/* TEXTURA */

.texture{

    position:fixed;
    width:100%;
    height:100%;
    background:url("https://www.transparenttextures.com/patterns/asfalt-dark.png");
    opacity:0.15;
    z-index:-4;

}

/* PARTÍCULAS */

.particle{

    position:absolute;
    width:3px;
    height:3px;
    background:#fff;
    border-radius:50%;
    opacity:0.3;
    animation:float linear infinite;

}

@keyframes float{

    from{
        transform:translateY(100vh);
    }

    to{
        transform:translateY(-10vh);
    }

}

/* INTRO */

.intro{

    position:fixed;
    width:100%;
    height:100%;
    background:black;
    z-index:999;
    display:flex;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    animation:introFade 4s forwards;

}

.intro h1{

    font-size:70px;
    font-family:'Permanent Marker', cursive;
    color:#a200ff;
    text-shadow:0 0 20px #a200ff;
    animation:glitch 1s infinite;

}

.intro p{

    margin-top:20px;
    letter-spacing:5px;
    color:#999;

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

    position:absolute;
    top:30px;
    left:40px;
    z-index:10;
    font-size:22px;
    font-weight:bold;

}

.header span{

    color:#a200ff;

}

/* SOCIAL */

.socials{

    position:absolute;
    top:30px;
    right:40px;
    display:flex;
    gap:20px;
    z-index:10;

}

.socials a{

    color:white;
    text-decoration:none;
    transition:0.3s;

}

.socials a:hover{

    color:#a200ff;
    transform:scale(1.2);

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

}

/* TITULO */

.title{

    font-family:'Permanent Marker', cursive;
    font-size:120px;
    line-height:0.9;
    text-transform:uppercase;
    margin-bottom:30px;
    animation:titlePulse 3s infinite;

}

.title span{

    color:#a200ff;
    text-shadow:
    0 0 20px #a200ff,
    0 0 50px rgba(162,0,255,0.7);

}

@keyframes titlePulse{

    0%{
        transform:scale(1);
    }

    50%{
        transform:scale(1.02);
    }

    100%{
        transform:scale(1);
    }

}

/* DISCO */

.vinyl-wrapper{

    position:relative;
    margin:50px 0;

}

.glow{

    position:absolute;
    width:420px;
    height:420px;
    background:radial-gradient(circle,
    rgba(162,0,255,0.5), transparent 70%);
    filter:blur(40px);
    z-index:-1;
    animation:glowPulse 3s infinite;

}

@keyframes glowPulse{

    0%{
        transform:scale(1);
    }

    50%{
        transform:scale(1.08);
    }

    100%{
        transform:scale(1);
    }

}

.vinyl{

    width:400px;
    height:400px;
    border-radius:50%;

    background:
    radial-gradient(circle, #111 15%, #000 16%,
    #222 30%, #000 31%, #111 45%, #000 46%,
    #222 60%, #000 61%);

    animation:spin 5s linear infinite;

    display:flex;
    justify-content:center;
    align-items:center;

    box-shadow:
    0 0 50px rgba(162,0,255,0.5);

}

.vinyl::before{

    content:"";
    width:110px;
    height:110px;
    background:#a200ff;
    border-radius:50%;
    position:absolute;
    box-shadow:0 0 30px #a200ff;

}

.vinyl::after{

    content:"M";
    position:absolute;
    font-size:50px;
    font-weight:bold;

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
    font-size:25px;
    line-height:1.8;
    color:#d1d1d1;
    margin-bottom:60px;

}

/* COUNTDOWN */

.count-title{

    font-family:'Permanent Marker', cursive;
    color:#a200ff;
    font-size:50px;
    margin-bottom:30px;

}

.countdown{

    display:flex;
    gap:25px;
    flex-wrap:wrap;
    justify-content:center;
    margin-bottom:70px;

}

.box{

    width:160px;
    padding:30px 20px;

    background:rgba(255,255,255,0.05);

    border:1px solid rgba(255,255,255,0.1);

    border-radius:25px;

    backdrop-filter:blur(10px);

    transform:translateY(80px);

    opacity:0;

    animation:reveal 1s forwards;

}

.box:nth-child(1){
    animation-delay:0.2s;
}

.box:nth-child(2){
    animation-delay:0.4s;
}

.box:nth-child(3){
    animation-delay:0.6s;
}

.box:nth-child(4){
    animation-delay:0.8s;
}

@keyframes reveal{

    to{
        transform:translateY(0);
        opacity:1;
    }

}

.box:hover{

    transform:translateY(-10px);
    box-shadow:0 0 25px rgba(162,0,255,0.4);

}

.number{

    font-size:60px;
    font-weight:bold;

}

.label{

    margin-top:10px;
    letter-spacing:3px;
    color:#999;

}

/* BOTONES */

.buttons{

    display:flex;
    gap:25px;
    flex-wrap:wrap;
    justify-content:center;
    margin-bottom:80px;

}

button{

    padding:18px 40px;
    border:none;
    border-radius:18px;
    font-size:18px;
    font-weight:bold;
    cursor:pointer;
    transition:0.3s;

}

.listen{

    background:#a200ff;
    color:white;

    box-shadow:
    0 0 20px rgba(162,0,255,0.5);

}

.listen:hover{

    transform:scale(1.08);

}

.share{

    background:transparent;
    border:2px solid white;
    color:white;

}

.share:hover{

    background:white;
    color:black;
    transform:scale(1.08);

}

/* CREDITOS */

.credits-title{

    font-family:'Permanent Marker', cursive;
    font-size:55px;
    color:#a200ff;
    margin-bottom:30px;

}

.credits{

    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
    gap:25px;
    width:100%;
    max-width:1000px;

}

.credit{

    background:rgba(255,255,255,0.04);
    border:1px solid rgba(255,255,255,0.05);
    padding:30px;
    border-radius:20px;
    transition:0.3s;

}

.credit:hover{

    transform:translateY(-8px);
    box-shadow:0 0 25px rgba(162,0,255,0.2);

}

.credit h3{

    color:#a200ff;
    margin-bottom:10px;

}

/* FOOTER */

.footer{

    margin-top:70px;
    color:#666;
    font-size:14px;

}

/* RESPONSIVE */

@media(max-width:700px){

    .title{
        font-size:70px;
    }

    .vinyl{
        width:260px;
        height:260px;
    }

    .glow{
        width:300px;
        height:300px;
    }

    .description{
        font-size:18px;
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

for(let i = 0; i < 50; i++){

    const particle = document.createElement("div");

    particle.classList.add("particle");

    particle.style.left = Math.random() * 100 + "vw";

    particle.style.animationDuration =
    (Math.random() * 10 + 5) + "s";

    particle.style.opacity = Math.random();

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
            MauriSpide

        </div>

        <div class="credit">

            <h3>Producción</h3>
            LAIP.I Collective

        </div>

        <div class="credit">

            <h3>Composición</h3>
            MauriSpide

        </div>

        <div class="credit">

            <h3>Diseño</h3>
            LAIP.I Collective

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
        color:#a200ff;
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
