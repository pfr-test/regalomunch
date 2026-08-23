<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Una sorpresa para ti ❤️</title>

<style>

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    min-height: 100vh;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #ff9a9e, #fad0c4);
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

.container {
    background: white;
    width: 100%;
    max-width: 850px;
    padding: 35px;
    border-radius: 25px;
    box-shadow: 0 15px 40px rgba(0,0,0,0.15);
}

.header {
    text-align: center;
    margin-bottom: 30px;
}

.header h1 {
    color: #e75480;
    margin-bottom: 10px;
}

.header p {
    color: #666;
    line-height: 1.5;
}


/* =========================
   PRUEBA 1
========================= */

#prueba1 {
    display: block;
}

.question {
    margin-bottom: 28px;
}

.question h3 {
    margin-bottom: 12px;
    color: #333;
}

.options {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.option {
    border: 2px solid #eee;
    border-radius: 12px;
    padding: 12px;
    cursor: pointer;
    transition: 0.2s;
}

.option:hover {
    border-color: #e75480;
    background: #fff5f7;
}

.option input {
    margin-right: 8px;
}


/* =========================
   BOTONES
========================= */

button {
    width: 100%;
    border: none;
    border-radius: 12px;
    padding: 15px;
    font-size: 17px;
    font-weight: bold;
    cursor: pointer;
    background: #e75480;
    color: white;
    transition: 0.2s;
}

button:hover {
    transform: translateY(-2px);
    opacity: 0.9;
}

#continuar1,
#continuar2 {
    display: none;
    margin-top: 15px;
    background: #28a745;
}


/* =========================
   RESULTADOS
========================= */

#resultado1 {
    display: none;
    text-align: center;
    margin-top: 20px;
    padding: 18px;
    border-radius: 15px;
}

.correcto {
    background: #e8f8ee;
    color: #218838;
}

.incorrecto {
    background: #fff0f0;
    color: #c62828;
}


/* =========================
   PRUEBA 2
========================= */

#prueba2 {
    display: none;
}

.rules {
    background: #fff7fa;
    border-radius: 15px;
    padding: 18px;
    margin-bottom: 25px;
    color: #555;
}

.rules ul {
    margin-bottom: 0;
    line-height: 1.8;
}


/* TABLERO */

.board-container {
    display: flex;
    justify-content: center;
    margin: 25px 0;
}

.board {
    display: grid;
    grid-template-columns: repeat(8, 1fr);
    width: min(90vw, 640px);
    aspect-ratio: 1 / 1;
    border: 4px solid #333;
    border-radius: 10px;
    overflow: hidden;
}


/* CASILLAS */

.cell {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;

    border: 1px solid rgba(0,0,0,0.15);

    font-size: clamp(22px, 5vw, 48px);

    cursor: pointer;

    user-select: none;

    transition:
        transform 0.1s,
        filter 0.15s;
}

.cell:hover {
    filter: brightness(1.08);
}

.cell:active {
    transform: scale(0.92);
}


/* =========================
   COLORES DE REGIONES
========================= */

.region0 {
    background: #ffd6e7;
}

.region1 {
    background: #d7ecff;
}

.region2 {
    background: #fff0b8;
}

.region3 {
    background: #d9f7d5;
}

.region4 {
    background: #e5d7ff;
}

.region5 {
    background: #ffd9bd;
}

.region6 {
    background: #cceeea;
}

.region7 {
    background: #f5d5ff;
}


/* =========================
   MARCAS
========================= */

.x {
    color: #555;
    font-size: clamp(18px, 4vw, 32px);
    font-weight: bold;
}

.queen {
    font-size: clamp(25px, 5vw, 48px);
    animation: aparecer 0.2s ease;
}

@keyframes aparecer {

    from {
        transform: scale(0);
    }

    to {
        transform: scale(1);
    }

}


/* CONFLICTO */

.conflict {
    background: #ff8b8b !important;
    animation: parpadeo 0.4s infinite alternate;
}

@keyframes parpadeo {

    from {
        filter: brightness(1);
    }

    to {
        filter: brightness(0.75);
    }

}


/* =========================
   INFORMACIÓN DEL JUEGO
========================= */

.game-info {
    display: flex;
    justify-content: space-between;
    align-items: center;

    background: #f7f7f7;

    padding: 12px 18px;

    border-radius: 12px;

    margin-bottom: 15px;

    font-weight: bold;
}

#mensajeJuego {
    text-align: center;
    min-height: 25px;
    margin: 15px 0;
    font-weight: bold;
}

.reset {
    background: #777;
    margin-top: 10px;
}


/* =========================
   PRUEBA SUPERADA
========================= */

#victoria {
    display: none;
    text-align: center;
    padding: 20px;
}

#victoria h2 {
    color: #28a745;
    font-size: 30px;
}


/* =========================
   RESPONSIVE
========================= */

@media (max-width: 600px) {

    .container {
        padding: 20px;
    }

    .header h1 {
        font-size: 25px;
    }

    .rules {
        font-size: 14px;
    }

}

</style>
</head>


<body>

<div class="container">


<!-- =====================================================
     PRUEBA 1
===================================================== -->

<section id="prueba1">

    <div class="header">

        <h1>❤️ PRUEBA 1 ❤️</h1>

        <p>
            Si quieres descubrir tu sorpresa tendrás que superar
            esta primera prueba...
        </p>

        <p>
            <strong>5 preguntas. 5 respuestas correctas.</strong>
        </p>

    </div>


    <!-- PREGUNTA 1 -->

    <div class="question">

        <h3>1. ¿Cuál es mi comida favorita?</h3>

        <div class="options">

            <label class="option">
                <input type="radio" name="pregunta1" value="a">
                Pizza
            </label>

            <label class="option">
                <input type="radio" name="pregunta1" value="b">
                Sushi
            </label>

            <label class="option">
                <input type="radio" name="pregunta1" value="c">
                Hamburguesa
            </label>

            <label class="option">
                <input type="radio" name="pregunta1" value="d">
                Pasta
            </label>

        </div>

    </div>


    <!-- PREGUNTA 2 -->

    <div class="question">

        <h3>2. ¿Cuál fue nuestro primer plan juntos?</h3>

        <div class="options">

            <label class="option">
                <input type="radio" name="pregunta2" value="a">
                Ir al cine
            </label>

            <label class="option">
                <input type="radio" name="pregunta2" value="b">
                Ir a cenar
            </label>

            <label class="option">
                <input type="radio" name="pregunta2" value="c">
                Dar un paseo
            </label>

            <label class="option">
                <input type="radio" name="pregunta2" value="d">
                Ir de viaje
            </label>

        </div>

    </div>


    <!-- PREGUNTA 3 -->

    <div class="question">

        <h3>3. ¿Cuál es mi mayor vicio?</h3>

        <div class="options">

            <label class="option">
                <input type="radio" name="pregunta3" value="a">
                Dormir
            </label>

            <label class="option">
                <input type="radio" name="pregunta3" value="b">
                Comer
            </label>

            <label class="option">
                <input type="radio" name="pregunta3" value="c">
                Videojuegos
            </label>

            <label class="option">
                <input type="radio" name="pregunta3" value="d">
                Compras
            </label>

        </div>

    </div>


    <!-- PREGUNTA 4 -->

    <div class="question">

        <h3>4. ¿Qué lugar elegiría para pasar unas vacaciones?</h3>

        <div class="options">

            <label class="option">
                <input type="radio" name="pregunta4" value="a">
                La playa 🏖️
            </label>

            <label class="option">
                <input type="radio" name="pregunta4" value="b">
                La montaña 🏔️
            </label>

            <label class="option">
                <input type="radio" name="pregunta4" value="c">
                Una gran ciudad 🌆
            </label>

            <label class="option">
                <input type="radio" name="pregunta4" value="d">
                Un pueblo tranquilo 🌳
            </label>

        </div>

    </div>


    <!-- PREGUNTA 5 -->

    <div class="question">

        <h3>5. ¿Qué prefiero?</h3>

        <div class="options">

            <label class="option">
                <input type="radio" name="pregunta5" value="a">
                Una película 🎬
            </label>

            <label class="option">
                <input type="radio" name="pregunta5" value="b">
                Una serie 📺
            </label>

            <label class="option">
                <input type="radio" name="pregunta5" value="c">
                Un concierto 🎵
            </label>

            <label class="option">
                <input type="radio" name="pregunta5" value="d">
                Un videojuego 🎮
            </label>

        </div>

    </div>


    <button onclick="comprobarRespuestas()">
        🔐 Comprobar respuestas
    </button>


    <div id="resultado1"></div>


    <button id="continuar1" onclick="mostrarPrueba2()">
        👑 Siguiente prueba
    </button>

</section>



<!-- =====================================================
     PRUEBA 2
===================================================== -->

<section id="prueba2">

    <div class="header">

        <h1>👑 PRUEBA 2 👑</h1>

        <p>
            Ahora tendrás que demostrar que también tienes
            buena cabeza...
        </p>

    </div>


    <div class="rules">

        <strong>¿Cómo se juega?</strong>

        <ul>

            <li>
                👑 Coloca <strong>8 reinas</strong>.
            </li>

            <li>
                Cada fila debe tener exactamente una reina.
            </li>

            <li>
                Cada columna debe tener exactamente una reina.
            </li>

            <li>
                Cada zona de color debe tener exactamente una reina.
            </li>

            <li>
                Las reinas no pueden tocarse, ni siquiera en diagonal.
            </li>

            <li>
                Haz clic una vez para ❌, otra vez para 👑 y otra vez para limpiar.
            </li>

        </ul>

    </div>


    <div class="game-info">

        <span>
            👑 Reinas:
            <span id="contador">0</span>/8
        </span>

        <span>
            ❌ Casillas marcadas:
            <span id="marcadas">0</span>
        </span>

    </div>


    <div class="board-container">

        <div id="board" class="board"></div>

    </div>


    <div id="mensajeJuego"></div>


    <button class="reset" onclick="reiniciarJuego()">
        🔄 Reiniciar tablero
    </button>


    <div id="victoria">

        <h2>🎉 ¡PRUEBA SUPERADA! 🎉</h2>

        <p>
            Has conseguido colocar las 8 reinas.
        </p>

        <p>
            Pero todavía queda una última prueba...
            👀
        </p>

        <button id="continuar2" onclick="prueba3()">
            🎁 Continuar
        </button>

    </div>

</section>


</div>


<script>

/* =========================================================
   PRUEBA 1
========================================================= */

const respuestasCorrectas = {

    pregunta1: "a",
    pregunta2: "b",
    pregunta3: "c",
    pregunta4: "a",
    pregunta5: "b"

};


function comprobarRespuestas() {

    let aciertos = 0;

    for (let pregunta in respuestasCorrectas) {

        const respuesta =
            document.querySelector(
                `input[name="${pregunta}"]:checked`
            );

        if (
            respuesta &&
            respuesta.value === respuestasCorrectas[pregunta]
        ) {

            aciertos++;

        }

    }


    const resultado =
        document.getElementById("resultado1");

    const continuar =
        document.getElementById("continuar1");


    resultado.style.display = "block";


    if (aciertos === 5) {

        resultado.className = "correcto";

        resultado.innerHTML = `

            <h2>🎉 ¡PERFECTO! 🎉</h2>

            <p>
                Has acertado las 5 preguntas.
            </p>

            <p>
                Pero esto solo acaba de empezar... 👀
            </p>

        `;

        continuar.style.display = "block";

    }

    else {

        resultado.className = "incorrecto";

        resultado.innerHTML = `

            <h2>❌ Todavía no...</h2>

            <p>
                Has acertado
                <strong>${aciertos}/5</strong>.
            </p>

            <p>
                Necesitas acertarlas todas para continuar ❤️
            </p>

        `;

        continuar.style.display = "none";

    }

}


/* =========================================================
   CAMBIAR A PRUEBA 2
========================================================= */

function mostrarPrueba2() {

    document.getElementById("prueba1").style.display = "none";

    document.getElementById("prueba2").style.display = "block";

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });

    crearTablero();

}


/* =========================================================
   TABLERO QUEENS
========================================================= */


/*
    Cada número representa una región.

    Hay exactamente 8 regiones.

    El tablero tiene una solución única.
*/

const regiones = [

    [2,2,2,0,3,3,3,3],

    [2,0,0,0,3,3,3,3],

    [2,2,6,6,4,3,3,3],

    [6,2,6,6,1,3,3,3],

    [6,6,6,6,1,3,3,3],

    [6,6,6,5,1,1,3,3],

    [6,1,1,1,1,1,7,7],

    [6,6,1,1,7,7,7,7]

];


/*
    Solución del puzzle.

    IMPORTANTE:

    No se muestra al jugador.
*/

const solucion = [

    [0,0],

    [1,2],

    [2,4],

    [3,6],

    [4,1],

    [5,3],

    [6,5],

    [7,7]

];


/*
    Estado de cada casilla:

    0 = vacía
    1 = X
    2 = reina
*/

let estado = [];


/* =========================================================
   CREAR TABLERO
========================================================= */

function crearTablero() {

    const board =
        document.getElementById("board");

    board.innerHTML = "";

    estado = [];


    for (let fila = 0; fila < 8; fila++) {

        estado[fila] = [];

        for (let columna = 0; columna < 8; columna++) {

            estado[fila][columna] = 0;


            const celda =
                document.createElement("div");


            celda.className =
                "cell region" +
                regiones[fila][columna];


            celda.dataset.fila = fila;

            celda.dataset.columna = columna;


            celda.addEventListener(
                "click",
                () => {

                    cambiarCasilla(
                        fila,
                        columna
                    );

                }
            );


            board.appendChild(celda);

        }

    }


    actualizarTablero();

}


/* =========================================================
   CAMBIAR ESTADO DE CASILLA
========================================================= */

function cambiarCasilla(fila, columna) {

    /*
        Ciclo:

        vacío → X
        X → reina
        reina → vacío
    */

    estado[fila][columna]++;

    if (estado[fila][columna] > 2) {

        estado[fila][columna] = 0;

    }


    actualizarTablero();

    comprobarTablero();

}


/* =========================================================
   ACTUALIZAR TABLERO
========================================================= */

function actualizarTablero() {

    const celdas =
        document.querySelectorAll(".cell");


    let contadorReinas = 0;

    let contadorX = 0;


    celdas.forEach((celda, indice) => {

        const fila =
            Math.floor(indice / 8);

        const columna =
            indice % 8;


        celda.innerHTML = "";

        celda.classList.remove("conflict");


        if (estado[fila][columna] === 1) {

            celda.innerHTML = "×";

            celda.classList.add("x");

            contadorX++;

        }


        if (estado[fila][columna] === 2) {

            celda.innerHTML = "👑";

            celda.classList.add("queen");

            contadorReinas++;

        }

    });


    document.getElementById("contador").textContent =
        contadorReinas;

    document.getElementById("marcadas").textContent =
        contadorX;

}


/* =========================================================
   COMPROBAR CONFLICTOS
========================================================= */

function comprobarTablero() {

    const reinas = [];


    for (let fila = 0; fila < 8; fila++) {

        for (let columna = 0; columna < 8; columna++) {

            if (estado[fila][columna] === 2) {

                reinas.push({
                    fila: fila,
                    columna: columna
                });

            }

        }

    }


    /*
        Comprobar parejas de reinas.
    */

    let hayConflicto = false;


    for (let i = 0; i < reinas.length; i++) {

        for (let j = i + 1; j < reinas.length; j++) {

            const a = reinas[i];

            const b = reinas[j];


            /*
                Misma fila
            */

            if (a.fila === b.fila) {

                hayConflicto = true;

                marcarConflicto(a, b);

            }


            /*
                Misma columna
            */

            if (a.columna === b.columna) {

                hayConflicto = true;

                marcarConflicto(a, b);

            }


            /*
                Misma región
            */

            if (
                regiones[a.fila][a.columna] ===
                regiones[b.fila][b.columna]
            ) {

                hayConflicto = true;

                marcarConflicto(a, b);

            }


            /*
                Las reinas no pueden tocarse
                diagonalmente.
            */

            if (
                Math.abs(a.fila - b.fila) === 1 &&
                Math.abs(a.columna - b.columna) === 1
            ) {

                hayConflicto = true;

                marcarConflicto(a, b);

            }


            /*
                Tampoco pueden estar pegadas
                horizontal o verticalmente.
            */

            if (
                Math.abs(a.fila - b.fila) <= 1 &&
                Math.abs(a.columna - b.columna) <= 1 &&
                (
                    a.fila !== b.fila ||
                    a.columna !== b.columna
                )
            ) {

                hayConflicto = true;

                marcarConflicto(a, b);

            }

        }

    }


    const mensaje =
        document.getElementById("mensajeJuego");


    /*
        Si hay conflicto
    */

    if (hayConflicto) {

        mensaje.textContent =
            "❌ Hay una o más reinas en conflicto.";

        mensaje.style.color = "#c62828";

        return;

    }


    /*
        Si todavía no hay 8 reinas
    */

    if (reinas.length < 8) {

        mensaje.textContent =
            "🧠 Sigue pensando...";

        mensaje.style.color = "#666";

        return;

    }


    /*
        Si hay 8 y no hay conflictos,
        comprobamos las regiones.
    */

    const regionesUsadas = new Set();

    const filasUsadas = new Set();

    const columnasUsadas = new Set();


    reinas.forEach(reina => {

        regionesUsadas.add(
            regiones[reina.fila][reina.columna]
        );

        filasUsadas.add(
            reina.fila
        );

        columnasUsadas.add(
            reina.columna
        );

    });


    if (
        regionesUsadas.size === 8 &&
        filasUsadas.size === 8 &&
        columnasUsadas.size === 8
    ) {

        ganarJuego();

    }

}


/* =========================================================
   MARCAR CONFLICTO
========================================================= */

function marcarConflicto(a, b) {

    const indiceA =
        a.fila * 8 + a.columna;

    const indiceB =
        b.fila * 8 + b.columna;


    const celdas =
        document.querySelectorAll(".cell");


    celdas[indiceA]
        .classList.add("conflict");


    celdas[indiceB]
        .classList.add("conflict");

}


/* =========================================================
   GANAR
========================================================= */

function ganarJuego() {

    const mensaje =
        document.getElementById("mensajeJuego");


    mensaje.textContent =
        "🎉 ¡TABLERO COMPLETADO! 🎉";

    mensaje.style.color =
        "#218838";


    document.getElementById("victoria")
        .style.display = "block";


    /*
        Desactivamos el tablero.
    */

    const celdas =
        document.querySelectorAll(".cell");


    celdas.forEach(celda => {

        celda.style.pointerEvents =
            "none";

    });

}


/* =========================================================
   REINICIAR
========================================================= */

function reiniciarJuego() {

    document.getElementById("victoria")
        .style.display = "none";


    document.getElementById("mensajeJuego")
        .textContent = "";


    crearTablero();

}


/* =========================================================
   PRUEBA 3
========================================================= */

function prueba3() {

    alert(
        "🎁 ¡PRUEBA 3 DESBLOQUEADA! 🎁"
    );

    /*
        Aquí añadiremos posteriormente
        la tercera prueba.

        Por ejemplo:

        document.getElementById("prueba2").style.display = "none";
        document.getElementById("prueba3").style.display = "block";
    */

}

</script>

</body>
</html>
