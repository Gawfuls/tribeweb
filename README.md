
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tribe Gang</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    height: 100vh;
    overflow: hidden;
    background: #050505;
    color: white;
    font-family: Arial, Helvetica, sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
}

.scene {
    position: relative;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    isolation: isolate;
}

/* background glow */
.scene::before {
    content: "";
    position: absolute;
    width: 600px;
    height: 600px;
    background: radial-gradient(circle, #292929 0%, #101010 40%, transparent 70%);
    z-index: -2;
}

/* spinning globe */
.globe {
    position: absolute;
    width: min(75vw, 440px);
    aspect-ratio: 1;
    border-radius: 50%;
    border: 1px solid #777;
    background:
        repeating-linear-gradient(
            0deg,
            transparent 0px,
            transparent 35px,
            #ffffff18 36px,
            transparent 37px
        ),
        radial-gradient(circle at 35% 30%, #292929, #080808 65%);
    box-shadow:
        0 0 35px #ffffff12,
        inset 0 0 40px #ffffff12;
    animation: spin 12s linear infinite;
    z-index: -1;
}

/* globe meridians */
.globe::before,
.globe::after {
    content: "";
    position: absolute;
    inset: 0;
    border: 1px solid #888;
    border-radius: 50%;
}

.globe::before {
    transform: scaleX(0.45);
}

.globe::after {
    transform: scaleX(0.8);
    border-color: #555;
}

@keyframes spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
}

/* orbit around globe */
.orbit {
    position: absolute;
    width: min(95vw, 550px);
    aspect-ratio: 1;
    border: 1px solid #ffffff30;
    border-radius: 50%;
    transform: rotateX(68deg) rotateZ(-20deg);
    animation: orbit 9s linear infinite;
}

@keyframes orbit {
    from { transform: rotateX(68deg) rotateZ(0deg); }
    to { transform: rotateX(68deg) rotateZ(360deg); }
}

/* main title */
.title {
    position: relative;
    z-index: 2;
    margin-bottom: 15px;
    font-size: clamp(42px, 9vw, 92px);
    font-weight: 1000;
    text-transform: uppercase;
    letter-spacing: -4px;
    text-align: center;
    color: #fff;
    -webkit-text-stroke: 1px #fff;
    text-shadow:
        1px 1px 0 #aaa,
        2px 2px 0 #888,
        3px 3px 0 #666,
        4px 4px 0 #444,
        5px 5px 0 #292929,
        6px 6px 0 #171717,
        0 0 30px #ffffff25;
    animation: appear 1.2s ease-out both;
}

/* logo */
.logo-container {
    position: relative;
    z-index: 2;
    width: clamp(150px, 30vw, 245px);
    aspect-ratio: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    animation: float 4s ease-in-out infinite;
}

.logo-container img {
    width: 100%;
    height: 100%;
    object-fit: contain;
    filter: drop-shadow(0 0 12px #ffffff25);
}

.subtitle {
    z-index: 2;
    margin-top: 25px;
    color: #aaa;
    font-size: 11px;
    letter-spacing: 7px;
    text-transform: uppercase;
    text-align: center;
}

.line {
    width: 100px;
    height: 1px;
    margin-top: 18px;
    background: linear-gradient(90deg, transparent, white, transparent);
}

@keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-10px); }
}

@keyframes appear {
    from {
        opacity: 0;
        transform: translateY(25px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@media (max-width: 480px) {
    .title {
        letter-spacing: -2px;
    }

    .subtitle {
        letter-spacing: 4px;
    }
}
</style>
</head>

<body>
<div class="scene">

    <div class="globe"></div>
    <div class="orbit"></div>

    <h1 class="title">Tribe Gang</h1>

    <div class="logo-container">
        <img src="logo.png" alt="Tribe Gang logo">
    </div>

    <div class="line"></div>
    <p class="subtitle">United as one</p>

</div>
</body>
</html>
