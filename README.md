<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Una sorpresa para ti ❤️</title>

    <style>

        /* =====================================================
           GENERAL
        ===================================================== */

        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            min-height: 100vh;
            font-family: Arial, sans-serif;

            background: linear-gradient(
                135deg,
                #ff7b8a,
                #ffc4b8
            );

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

            box-shadow:
                0 15px 40px rgba(0, 0, 0, 0.15);
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


        /* =====================================================
           BOTONES
        ===================================================== */

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
        #continuar2,
        #continuar3,
        #continuar4 {
            display: none;
            margin-top: 15px;
            background: #28a745;
        }


        /* =====================================================
           RESULTADOS
        ===================================================== */

        #resultado1,
        #resultado3,
        #resultado4 {
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


        /* =====================================================
           PRUEBA 1
        ===================================================== */

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


        /* =====================================================
           PRUEBA 2
        ===================================================== */

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


        /* =====================================================
           INFORMACIÓN DEL JUEGO
        ===================================================== */

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


        /* =====================================================
           TABLERO QUEENS
        ===================================================== */

        .board-container {
            display: flex;
            justify-content: center;
            align-items: center;

            width: 100%;

            margin: 25px 0;
        }

        .board {
            display: grid;

            grid-template-columns: repeat(6, 1fr);
            grid-template-rows: repeat(6, 1fr);

            width: min(90vw, 570px);

            aspect-ratio: 1 / 1;

            border: 5px solid #222;

            border-radius: 12px;

            overflow: hidden;

            flex-shrink: 0;
        }


        /* =====================================================
           CASILLAS
        ===================================================== */

        .cell {
            width: 100%;
            height: 100%;

            min-width: 0;
            min-height: 0;

            display: flex;
            justify-content: center;
            align-items: center;

            border: 2px solid rgba(0, 0, 0, 0.22);

            font-size: clamp(25px, 5vw, 48px);

            line-height: 1;

            cursor: pointer;

            user-select: none;

            transition: filter 0.15s ease;

            overflow: hidden;
        }

        .cell:hover {
            filter: brightness(1.08);
        }


        /* =====================================================
           COLORES DE LAS REGIONES
        ===================================================== */

        .region0 {
            background: #ff4d6d;
        }

        .region1 {
            background: #2979ff;
        }

        .region2 {
            background: #ffd600;
        }

        .region3 {
            background: #00c853;
        }

        .region4 {
            background: #8e24aa;
        }

        .region5 {
            background: #ff6d00;
        }


        /* =====================================================
           X
        ===================================================== */

        .x {
            color: #202020;

            font-size: clamp(22px, 4vw, 38px);

            font-weight: 900;

            width: 100%;
            height: 100%;

            display: flex;
            justify-content: center;
            align-items: center;

            line-height: 1;
        }


        /* =====================================================
           REINA
        ===================================================== */

        .queen {
            font-size: clamp(27px, 5vw, 48px);

            width: 100%;
            height: 100%;

            display: flex;
            justify-content: center;
            align-items: center;

            line-height: 1;

            animation: aparecer 0.15s ease;
        }

        @keyframes aparecer {

            from {
                opacity: 0;
                transform: scale(0.7);
            }

            to {
                opacity: 1;
                transform: scale(1);
            }

        }


        /* =====================================================
           CONFLICTOS
        ===================================================== */

        .conflict {
            background: #ff3b3b !important;

            box-shadow:
                inset 0 0 0 4px #b00000;

            animation:
                parpadeo 0.4s infinite alternate;
        }

        @keyframes parpadeo {

            from {
                filter: brightness(1);
            }

            to {
                filter: brightness(0.72);
            }

        }


        /* =====================================================
           MENSAJE DEL JUEGO
        ===================================================== */

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


        /* =====================================================
           VICTORIA PRUEBA 2
        ===================================================== */

        #victoria {
            display: none;

            text-align: center;

            padding: 20px;
        }

        #victoria h2 {
            color: #28a745;
            font-size: 30px;
        }


        /* =====================================================
           PRUEBA 3
        ===================================================== */

        #prueba3 {
            display: none;
        }

        .answer-question {
            margin-bottom: 25px;
        }

        .answer-question h3 {
            color: #333;
            margin-bottom: 10px;
        }

        .answer-input {
            width: 100%;

            padding: 14px;

            border: 2px solid #ddd;

            border-radius: 12px;

            font-size: 16px;

            outline: none;

            transition: 0.2s;
        }

        .answer-input:focus {
            border-color: #e75480;

            box-shadow:
                0 0 0 3px
                rgba(231, 84, 128, 0.15);
        }


       /* =====================================================
           PRUEBA 4 - TARJETAS DE FOTOS
        ===================================================== */
        
        .photo-board {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin: 25px 0;
        }
        
        
        /* TARJETA */
        
        .photo-card {
            display: flex;
            align-items: center;
            gap: 18px;
        
            background: white;
        
            border: 3px solid #ddd;
            border-radius: 15px;
        
            padding: 12px;
        
            cursor: grab;
        
            transition:
                transform 0.2s,
                border-color 0.2s,
                box-shadow 0.2s;
        
            user-select: none;
        
            min-height: 150px;
        }
        
        
        .photo-card:hover {
            border-color: #e75480;
        
            box-shadow:
                0 5px 15px rgba(0,0,0,0.1);
        }
        
        
        .photo-card.dragging {
            opacity: 0.5;
            transform: scale(0.98);
        }
        
        
        .photo-card.correct-position {
            border-color: #28a745;
        }
        
        
        /* =====================================================
           NÚMERO DE POSICIÓN
        ===================================================== */
        
        .photo-number {
        
            width: 42px;
            height: 42px;
        
            min-width: 42px;
        
            display: flex;
        
            justify-content: center;
            align-items: center;
        
            background: #e75480;
        
            color: white;
        
            border-radius: 50%;
        
            font-weight: bold;
        
            font-size: 19px;
        }
        
        
        /* =====================================================
           FOTOGRAFÍA
        ===================================================== */
        
        .photo-card img {
        
            width: 240px;
            height: 150px;
        
            object-fit: cover;
        
            border-radius: 12px;
        
            background: #eee;
        
            flex-shrink: 0;
        
            display: block;
        }
        
        
        /* =====================================================
           BOTONES DE LAS FOTOS
        ===================================================== */
        
        .photo-buttons {
        
            display: flex;
        
            flex-direction: column;
        
            gap: 6px;
        
            margin-left: auto;
        }
        
        
        .photo-buttons button {
        
            width: 42px;
            height: 38px;
        
            padding: 0;
        
            border-radius: 8px;
        
            font-size: 18px;
        
            background: #777;
        }
        
        
        .photo-buttons button:hover {
        
            background: #e75480;
        
        }


        /* =====================================================
           RESPONSIVE
        ===================================================== */

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

            .board {
                width: min(92vw, 500px);
                border-width: 4px;
            }

            .cell {
                border-width: 1.5px;
            }

            .photo-card img {
                width: 100px;
                height: 75px;
            }

            .photo-title {
                font-size: 14px;
            }

            .photo-number {
                width: 32px;
                height: 32px;

                min-width: 32px;

                font-size: 15px;
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
                Si quieres descubrir tu sorpresa tendrás que
                superar esta primera prueba...
            </p>

            <p>
                <strong>
                    5 preguntas. 5 respuestas correctas.
                </strong>
            </p>

        </div>


        <div class="question">

            <h3>
                1. ¿Cuál es mi comida favorita?
            </h3>

            <div class="options">

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta1"
                        value="a"
                    >
                    Pizza
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta1"
                        value="b"
                    >
                    Sushi
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta1"
                        value="c"
                    >
                    Hamburguesa
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta1"
                        value="d"
                    >
                    Pasta
                </label>

            </div>

        </div>


        <div class="question">

            <h3>
                2. ¿Cuál fue nuestro primer plan juntos?
            </h3>

            <div class="options">

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta2"
                        value="a"
                    >
                    Ir al cine
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta2"
                        value="b"
                    >
                    Ir a cenar
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta2"
                        value="c"
                    >
                    Dar un paseo
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta2"
                        value="d"
                    >
                    Ir de viaje
                </label>

            </div>

        </div>


        <div class="question">

            <h3>
                3. ¿Cuál es mi mayor vicio?
            </h3>

            <div class="options">

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta3"
                        value="a"
                    >
                    Dormir
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta3"
                        value="b"
                    >
                    Comer
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta3"
                        value="c"
                    >
                    Videojuegos
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta3"
                        value="d"
                    >
                    Compras
                </label>

            </div>

        </div>


        <div class="question">

            <h3>
                4. ¿Qué lugar elegiría para pasar unas vacaciones?
            </h3>

            <div class="options">

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta4"
                        value="a"
                    >
                    La playa 🏖️
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta4"
                        value="b"
                    >
                    La montaña 🏔️
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta4"
                        value="c"
                    >
                    Una gran ciudad 🌆
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta4"
                        value="d"
                    >
                    Un pueblo tranquilo 🌳
                </label>

            </div>

        </div>


        <div class="question">

            <h3>
                5. ¿Qué prefiero?
            </h3>

            <div class="options">

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta5"
                        value="a"
                    >
                    Una película 🎬
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta5"
                        value="b"
                    >
                    Una serie 📺
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta5"
                        value="c"
                    >
                    Un concierto 🎵
                </label>

                <label class="option">
                    <input
                        type="radio"
                        name="pregunta5"
                        value="d"
                    >
                    Un videojuego 🎮
                </label>

            </div>

        </div>


        <button onclick="comprobarRespuestas()">
            🔐 Comprobar respuestas
        </button>


        <div id="resultado1"></div>


        <button
            id="continuar1"
            onclick="mostrarPrueba2()"
        >
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
                    👑 Coloca <strong>6 reinas</strong>.
                </li>

                <li>
                    Cada fila debe tener exactamente una reina.
                </li>

                <li>
                    Cada columna debe tener exactamente una reina.
                </li>

                <li>
                    Cada zona de color debe tener exactamente
                    una reina.
                </li>

                <li>
                    Las reinas no pueden tocarse, ni siquiera
                    en diagonal.
                </li>

                <li>
                    Haz clic una vez para ❌,
                    otra vez para 👑
                    y otra vez para limpiar.
                </li>

            </ul>

        </div>


        <div class="game-info">

            <span>
                👑 Reinas:
                <span id="contador">0</span>/6
            </span>

            <span>
                ❌ Casillas marcadas:
                <span id="marcadas">0</span>
            </span>

        </div>


        <div class="board-container">

            <div
                id="board"
                class="board"
            ></div>

        </div>


        <div id="mensajeJuego"></div>


        <button
            class="reset"
            onclick="reiniciarJuego()"
        >
            🔄 Reiniciar tablero
        </button>


        <div id="victoria">

            <h2>
                🎉 ¡PRUEBA SUPERADA! 🎉
            </h2>

            <p>
                Has conseguido colocar las 6 reinas.
            </p>

            <p>
                Pero todavía queda otra prueba...
                👀
            </p>

            <button
                id="continuar2"
                onclick="mostrarPrueba3()"
            >
                ✍️ Continuar
            </button>

        </div>

    </section>



    <!-- =====================================================
         PRUEBA 3
    ===================================================== -->

    <section id="prueba3">

        <div class="header">

            <h1>✍️ PRUEBA 3 ✍️</h1>

            <p>
                Ahora no tendrás ninguna respuesta entre
                la que elegir...
            </p>

            <p>
                <strong>
                    Esta vez tendrás que escribirlas tú.
                </strong>
                👀
            </p>

        </div>


        <div class="answer-question">

            <h3>
                1. ¿En qué ciudad nos conocimos?
            </h3>

            <input
                type="text"
                id="respuesta1"
                class="answer-input"
                placeholder="Escribe tu respuesta..."
                autocomplete="off"
            >

        </div>


        <div class="answer-question">

            <h3>
                2. ¿Cuál fue nuestra primera película juntos?
            </h3>

            <input
                type="text"
                id="respuesta2"
                class="answer-input"
                placeholder="Escribe tu respuesta..."
                autocomplete="off"
            >

        </div>


        <div class="answer-question">

            <h3>
                3. ¿Cuál es mi color favorito?
            </h3>

            <input
                type="text"
                id="respuesta3"
                class="answer-input"
                placeholder="Escribe tu respuesta..."
                autocomplete="off"
            >

        </div>


        <div class="answer-question">

            <h3>
                4. ¿Cuál es nuestro lugar favorito?
            </h3>

            <input
                type="text"
                id="respuesta4"
                class="answer-input"
                placeholder="Escribe tu respuesta..."
                autocomplete="off"
            >

        </div>


        <button onclick="comprobarRespuestas3()">
            🔐 Comprobar respuestas
        </button>


        <div id="resultado3"></div>


        <button
            id="continuar3"
            onclick="mostrarPrueba4()"
        >
            📸 Siguiente prueba
        </button>

    </section>



    <!-- =====================================================
         PRUEBA 4
    ===================================================== -->

    <section id="prueba4">

        <div class="header">

            <h1>📸 PRUEBA 4 📸</h1>

            <p>
                Ya queda muy poco...
            </p>

            <p>
                <strong>
                    Ahora tendrás que ordenar estos recuerdos
                    cronológicamente.
                </strong>
            </p>

        </div>


        <div class="photo-instructions">

            <strong>¿Cómo se juega?</strong>

            <ul>

                <li>
                    📸 Ordena las 6 fotos de la más antigua
                    a la más reciente.
                </li>

                <li>
                    🖱️ Puedes arrastrar las fotos para cambiar
                    su posición.
                </li>

                <li>
                    ⬆️⬇️ También puedes utilizar las flechas
                    para moverlas.
                </li>

                <li>
                    ❤️ Cuando creas que están correctamente
                    ordenadas, pulsa "Comprobar".
                </li>

            </ul>

        </div>


        <div
            id="photoBoard"
            class="photo-board"
        ></div>


        <button onclick="comprobarOrden()">
            🔐 Comprobar orden
        </button>


        <div id="resultado4"></div>


        <button
            id="continuar4"
            onclick="regaloFinal()"
        >
            🎁 Descubrir el regalo
        </button>

    </section>

</div>



<script>

    /* =====================================================
       PRUEBA 1
    ===================================================== */

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
                respuesta.value ===
                respuestasCorrectas[pregunta]
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

        } else {

            resultado.className = "incorrecto";

            resultado.innerHTML = `
                <h2>❌ Todavía no...</h2>

                <p>
                    Has acertado
                    <strong>${aciertos}/5</strong>.
                </p>

                <p>
                    Necesitas acertarlas todas
                    para continuar ❤️
                </p>
            `;

            continuar.style.display = "none";
        }
    }



    /* =====================================================
       PASAR A PRUEBA 2
    ===================================================== */

    function mostrarPrueba2() {

        document.getElementById("prueba1").style.display = "none";

        document.getElementById("prueba2").style.display = "block";

        window.scrollTo({
            top: 0,
            behavior: "smooth"
        });

        crearTablero();
    }



    /* =====================================================
       PRUEBA 2 - QUEENS
    ===================================================== */

    const regiones = [

        [0, 0, 1, 1, 2, 2],

        [0, 0, 1, 2, 2, 2],

        [3, 3, 1, 1, 2, 2],

        [3, 3, 4, 4, 4, 5],

        [3, 4, 4, 4, 5, 5],

        [4, 4, 4, 5, 5, 5]

    ];


    let estado = [];



    /* =====================================================
       CREAR TABLERO
    ===================================================== */

    function crearTablero() {

        const board =
            document.getElementById("board");

        board.innerHTML = "";

        estado = [];


        for (let fila = 0; fila < 6; fila++) {

            estado[fila] = [];


            for (
                let columna = 0;
                columna < 6;
                columna++
            ) {

                estado[fila][columna] = 0;


                const celda =
                    document.createElement("div");


                celda.className =
                    "cell region" +
                    regiones[fila][columna];


                celda.addEventListener(
                    "click",
                    function () {

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



    /* =====================================================
       CAMBIAR CASILLA
    ===================================================== */

    function cambiarCasilla(
        fila,
        columna
    ) {

        estado[fila][columna]++;


        if (
            estado[fila][columna] > 2
        ) {

            estado[fila][columna] = 0;

        }


        actualizarTablero();

        comprobarTablero();
    }



    /* =====================================================
       ACTUALIZAR TABLERO
    ===================================================== */

    function actualizarTablero() {

        const celdas =
            document.querySelectorAll(".cell");


        let contadorReinas = 0;

        let contadorX = 0;


        celdas.forEach(
            function (celda, indice) {

                const fila =
                    Math.floor(indice / 6);

                const columna =
                    indice % 6;


                celda.innerHTML = "";

                celda.classList.remove(
                    "x",
                    "queen",
                    "conflict"
                );


                if (
                    estado[fila][columna] === 1
                ) {

                    celda.innerHTML = "×";

                    celda.classList.add("x");

                    contadorX++;
                }


                if (
                    estado[fila][columna] === 2
                ) {

                    celda.innerHTML = "👑";

                    celda.classList.add("queen");

                    contadorReinas++;
                }

            }
        );


        document.getElementById(
            "contador"
        ).textContent = contadorReinas;


        document.getElementById(
            "marcadas"
        ).textContent = contadorX;
    }



    /* =====================================================
       COMPROBAR TABLERO
    ===================================================== */

    function comprobarTablero() {

        const reinas = [];


        for (let fila = 0; fila < 6; fila++) {

            for (
                let columna = 0;
                columna < 6;
                columna++
            ) {

                if (
                    estado[fila][columna] === 2
                ) {

                    reinas.push({
                        fila: fila,
                        columna: columna
                    });
                }
            }
        }


        let hayConflicto = false;


        for (
            let i = 0;
            i < reinas.length;
            i++
        ) {

            for (
                let j = i + 1;
                j < reinas.length;
                j++
            ) {

                const a = reinas[i];

                const b = reinas[j];


                /*
                    MISMA FILA
                */

                if (
                    a.fila === b.fila
                ) {

                    hayConflicto = true;

                    marcarConflicto(a, b);
                }


                /*
                    MISMA COLUMNA
                */

                if (
                    a.columna === b.columna
                ) {

                    hayConflicto = true;

                    marcarConflicto(a, b);
                }


                /*
                    MISMA REGIÓN
                */

                if (
                    regiones[a.fila][a.columna] ===
                    regiones[b.fila][b.columna]
                ) {

                    hayConflicto = true;

                    marcarConflicto(a, b);
                }


                /*
                    LAS REINAS NO PUEDEN TOCARSE
                    EN DIAGONAL
                */

                if (
                    Math.abs(
                        a.fila - b.fila
                    ) === 1 &&

                    Math.abs(
                        a.columna - b.columna
                    ) === 1
                ) {

                    hayConflicto = true;

                    marcarConflicto(a, b);
                }


                /*
                    TAMPOCO PUEDEN TOCARSE
                    HORIZONTAL O VERTICALMENTE
                */

                if (
                    Math.abs(
                        a.fila - b.fila
                    ) <= 1 &&

                    Math.abs(
                        a.columna - b.columna
                    ) <= 1 &&

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
            document.getElementById(
                "mensajeJuego"
            );


        if (hayConflicto) {

            mensaje.textContent =
                "❌ Hay una o más reinas en conflicto.";

            mensaje.style.color = "#c62828";

            return;
        }


        if (reinas.length < 6) {

            mensaje.textContent =
                "🧠 Sigue pensando...";

            mensaje.style.color = "#666";

            return;
        }


        /*
            Comprobar filas,
            columnas y regiones.
        */

        const filasUsadas = new Set();

        const columnasUsadas = new Set();

        const regionesUsadas = new Set();


        reinas.forEach(
            function (reina) {

                filasUsadas.add(
                    reina.fila
                );

                columnasUsadas.add(
                    reina.columna
                );

                regionesUsadas.add(
                    regiones[
                        reina.fila
                    ][
                        reina.columna
                    ]
                );
            }
        );


        if (
            filasUsadas.size === 6 &&
            columnasUsadas.size === 6 &&
            regionesUsadas.size === 6
        ) {

            ganarJuego();
        }
    }



    /* =====================================================
       MARCAR CONFLICTO
    ===================================================== */

    function marcarConflicto(a, b) {

        const indiceA =
            a.fila * 6 +
            a.columna;


        const indiceB =
            b.fila * 6 +
            b.columna;


        const celdas =
            document.querySelectorAll(
                ".cell"
            );


        celdas[indiceA]
            .classList.add("conflict");


        celdas[indiceB]
            .classList.add("conflict");
    }



    /* =====================================================
       GANAR PRUEBA 2
    ===================================================== */

    function ganarJuego() {

        const mensaje =
            document.getElementById(
                "mensajeJuego"
            );


        mensaje.textContent =
            "🎉 ¡TABLERO COMPLETADO! 🎉";


        mensaje.style.color =
            "#218838";


        document.getElementById(
            "victoria"
        ).style.display = "block";


        document.getElementById(
            "continuar2"
        ).style.display = "block";


        const celdas =
            document.querySelectorAll(
                ".cell"
            );


        celdas.forEach(
            function (celda) {

                celda.style.pointerEvents =
                    "none";
            }
        );
    }



    /* =====================================================
       REINICIAR TABLERO
    ===================================================== */

    function reiniciarJuego() {

        document.getElementById(
            "victoria"
        ).style.display = "none";


        document.getElementById(
            "mensajeJuego"
        ).textContent = "";


        crearTablero();
    }



    /* =====================================================
       PASAR A PRUEBA 3
    ===================================================== */

    function mostrarPrueba3() {

        document.getElementById(
            "prueba2"
        ).style.display = "none";


        document.getElementById(
            "prueba3"
        ).style.display = "block";


        window.scrollTo({
            top: 0,
            behavior: "smooth"
        });
    }



    /* =====================================================
       PRUEBA 3 - RESPUESTAS
    ===================================================== */

    /*
        CAMBIA ESTAS RESPUESTAS POR LAS TUYAS.
    */

    const respuestasPrueba3 = {

        respuesta1: "barcelona",

        respuesta2: "toy story",

        respuesta3: "azul",

        respuesta4: "paris"

    };


    function normalizarRespuesta(texto) {

        return texto
            .toLowerCase()
            .normalize("NFD")
            .replace(
                /[\u0300-\u036f]/g,
                ""
            )
            .trim();
    }



    function comprobarRespuestas3() {

        let aciertos = 0;


        for (
            let pregunta in
            respuestasPrueba3
        ) {

            const input =
                document.getElementById(
                    pregunta
                );


            const respuestaUsuario =
                normalizarRespuesta(
                    input.value
                );


            const respuestaCorrecta =
                normalizarRespuesta(
                    respuestasPrueba3[
                        pregunta
                    ]
                );


            if (
                respuestaUsuario ===
                respuestaCorrecta
            ) {

                aciertos++;
            }
        }


        const resultado =
            document.getElementById(
                "resultado3"
            );


        const continuar =
            document.getElementById(
                "continuar3"
            );


        resultado.style.display =
            "block";


        if (aciertos === 4) {

            resultado.className =
                "correcto";


            resultado.innerHTML = `

                <h2>🎉 ¡INCREÍBLE! 🎉</h2>

                <p>
                    Has acertado las
                    <strong>4 preguntas</strong>.
                </p>

                <p>
                    Ya estás muy cerca del final... 👀❤️
                </p>

            `;


            continuar.style.display =
                "block";

        } else {

            resultado.className =
                "incorrecto";


            resultado.innerHTML = `

                <h2>❌ Casi...</h2>

                <p>
                    Has acertado
                    <strong>${aciertos}/4</strong>.
                </p>

                <p>
                    Tienes que acertarlas todas
                    para continuar ❤️
                </p>

            `;


            continuar.style.display =
                "none";
        }
    }



   /* =====================================================
   PRUEBA 4 - FOTOS
===================================================== */

/*
    Las fotos están alojadas en GitHub.

    Repositorio:
    https://github.com/pfr-test/regalomunch

    Los archivos deben estar en la carpeta principal
    del repositorio:

    foto1.jpg
    foto2.jpg
    foto3.jpg
    foto4.jpg
    foto5.jpg
    foto6.jpg

    ORDEN CORRECTO:

    foto1 → foto2 → foto3 → foto4 → foto5 → foto6
*/


const fotos = [

    {
        id: 1,
        imagen: "https://raw.githubusercontent.com/pfr-test/regalomunch/main/foto1.jpg",
        titulo: "Recuerdo 1"
    },

    {
        id: 2,
        imagen: "https://raw.githubusercontent.com/pfr-test/regalomunch/main/foto2.jpg",
        titulo: "Recuerdo 2"
    },

    {
        id: 3,
        imagen: "https://raw.githubusercontent.com/pfr-test/regalomunch/main/foto3.jpg",
        titulo: "Recuerdo 3"
    },

    {
        id: 4,
        imagen: "https://raw.githubusercontent.com/pfr-test/regalomunch/main/foto4.jpg",
        titulo: "Recuerdo 4"
    },

    {
        id: 5,
        imagen: "https://raw.githubusercontent.com/pfr-test/regalomunch/main/foto5.jpg",
        titulo: "Recuerdo 5"
    },

    {
        id: 6,
        imagen: "https://raw.githubusercontent.com/pfr-test/regalomunch/main/foto6.jpg",
        titulo: "Recuerdo 6"
    }

];


/*
    Aquí se guarda el orden actual
    de las fotografías.
*/

let ordenFotos = [];


/*
    Fotografía que estamos arrastrando.
*/

let elementoArrastrado = null;



/* =====================================================
   PASAR A PRUEBA 4
===================================================== */

function mostrarPrueba4() {

    /*
        Ocultar Prueba 3.
    */

    document.getElementById(
        "prueba3"
    ).style.display = "none";


    /*
        Mostrar Prueba 4.
    */

    document.getElementById(
        "prueba4"
    ).style.display = "block";


    /*
        Subir al principio de la página.
    */

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });


    /*
        Crear un orden aleatorio
        de las fotografías.
    */

    crearFotos();

}



/* =====================================================
   CREAR FOTOS
===================================================== */

function crearFotos() {

    /*
        Hacemos una copia del array original.

        De esta manera "fotos" siempre mantiene
        el orden correcto 1-2-3-4-5-6.
    */

    ordenFotos = [...fotos];


    /*
        Mezcla aleatoria utilizando
        el algoritmo Fisher-Yates.
    */

    for (
        let i = ordenFotos.length - 1;
        i > 0;
        i--
    ) {

        const j =
            Math.floor(
                Math.random() * (i + 1)
            );


        const temporal =
            ordenFotos[i];


        ordenFotos[i] =
            ordenFotos[j];


        ordenFotos[j] =
            temporal;

    }


    /*
        Comprobamos que no haya salido
        casualmente el orden correcto.

        Si ha salido:

        1 → 2 → 3 → 4 → 5 → 6

        volvemos a mezclar.
    */

    const estaOrdenado =
        ordenFotos.every(
            function (foto, indice) {

                return foto.id === indice + 1;

            }
        );


    if (estaOrdenado) {

        crearFotos();

        return;

    }


    /*
        Mostrar las fotos.
    */

    renderizarFotos();

}



/* =====================================================
   RENDERIZAR FOTOS
===================================================== */

function renderizarFotos() {

    const photoBoard =
        document.getElementById(
            "photoBoard"
        );


    /*
        Limpiar el tablero.
    */

    photoBoard.innerHTML = "";


    /*
        Crear cada fotografía.
    */

    ordenFotos.forEach(
        function (foto, indice) {

            const tarjeta =
                document.createElement(
                    "div"
                );


            /*
                Clase principal.
            */

            tarjeta.className =
                "photo-card";


            /*
                Permitir arrastrar.
            */

            tarjeta.draggable =
                true;


            /*
                Guardar el ID de la foto.
            */

            tarjeta.dataset.id =
                foto.id;


            /*
                Contenido de la tarjeta.
            */

            tarjeta.innerHTML = `

                <div class="photo-number">
                    ${indice + 1}
                </div>

                <img
                    src="${foto.imagen}"
                    alt="${foto.titulo}"
                    draggable="false"
                >

                <div class="photo-title">
                    ${foto.titulo}
                </div>

                <div class="photo-buttons">

                    <button
                        type="button"
                        onclick="moverFoto(${indice}, -1)"
                    >
                        ▲
                    </button>

                    <button
                        type="button"
                        onclick="moverFoto(${indice}, 1)"
                    >
                        ▼
                    </button>

                </div>

            `;


            /*
                Cuando empieza a arrastrarse.
            */

            tarjeta.addEventListener(
                "dragstart",
                comenzarArrastre
            );


            /*
                Cuando termina el arrastre.
            */

            tarjeta.addEventListener(
                "dragend",
                terminarArrastre
            );


            /*
                Permitir soltar otra fotografía
                encima de esta.
            */

            tarjeta.addEventListener(
                "dragover",
                permitirSoltar
            );


            /*
                Cuando soltamos una fotografía.
            */

            tarjeta.addEventListener(
                "drop",
                soltarFoto
            );


            /*
                Añadir tarjeta al tablero.
            */

            photoBoard.appendChild(
                tarjeta
            );

        }
    );


    /*
        Actualizar números.
    */

    actualizarNumeros();

}



/* =====================================================
   COMENZAR ARRASTRE
===================================================== */

function comenzarArrastre(event) {

    elementoArrastrado =
        event.currentTarget;


    elementoArrastrado.classList.add(
        "dragging"
    );

}



/* =====================================================
   TERMINAR ARRASTRE
===================================================== */

function terminarArrastre(event) {

    event.currentTarget.classList.remove(
        "dragging"
    );


    elementoArrastrado = null;

}



/* =====================================================
   PERMITIR SOLTAR
===================================================== */

function permitirSoltar(event) {

    /*
        Necesario para permitir
        el evento "drop".
    */

    event.preventDefault();

}



/* =====================================================
   SOLTAR FOTO
===================================================== */

function soltarFoto(event) {

    event.preventDefault();


    /*
        Si no hay ninguna fotografía
        siendo arrastrada, no hacemos nada.
    */

    if (!elementoArrastrado) {

        return;

    }


    /*
        Fotografía sobre la que hemos soltado.
    */

    const destino =
        event.currentTarget;


    /*
        No hacemos nada si soltamos
        sobre la misma fotografía.
    */

    if (
        elementoArrastrado === destino
    ) {

        return;

    }


    /*
        Obtener todas las tarjetas.
    */

    const tarjetas =
        [
            ...document.querySelectorAll(
                ".photo-card"
            )
        ];


    /*
        Posición de origen.
    */

    const posicionOrigen =
        tarjetas.indexOf(
            elementoArrastrado
        );


    /*
        Posición de destino.
    */

    const posicionDestino =
        tarjetas.indexOf(
            destino
        );


    /*
        Intercambiar las fotografías
        dentro del array.
    */

    const temporal =
        ordenFotos[posicionOrigen];


    ordenFotos[posicionOrigen] =
        ordenFotos[posicionDestino];


    ordenFotos[posicionDestino] =
        temporal;


    /*
        Volvemos a dibujar el tablero.

        Esto hace que los números y las
        posiciones se actualicen correctamente.
    */

    renderizarFotos();


    /*
        Reiniciar elemento arrastrado.
    */

    elementoArrastrado = null;

}



/* =====================================================
   MOVER FOTO CON LAS FLECHAS
===================================================== */

function moverFoto(indice, direccion) {

    /*
        Calcular nueva posición.
    */

    const nuevaPosicion =
        indice + direccion;


    /*
        Si intentamos subir la primera foto
        o bajar la última, no hacemos nada.
    */

    if (
        nuevaPosicion < 0 ||
        nuevaPosicion >= ordenFotos.length
    ) {

        return;

    }


    /*
        Intercambiar las fotografías.
    */

    const temporal =
        ordenFotos[indice];


    ordenFotos[indice] =
        ordenFotos[nuevaPosicion];


    ordenFotos[nuevaPosicion] =
        temporal;


    /*
        Actualizar el tablero.
    */

    renderizarFotos();

}



/* =====================================================
   ACTUALIZAR NÚMEROS
===================================================== */

function actualizarNumeros() {

    const tarjetas =
        document.querySelectorAll(
            ".photo-card"
        );


    tarjetas.forEach(
        function (tarjeta, indice) {

            const numero =
                tarjeta.querySelector(
                    ".photo-number"
                );


            numero.textContent =
                indice + 1;

        }
    );

}



/* =====================================================
   COMPROBAR ORDEN
===================================================== */

function comprobarOrden() {

    let correcto = true;


    /*
        El orden correcto siempre es:

        FOTO 1
        FOTO 2
        FOTO 3
        FOTO 4
        FOTO 5
        FOTO 6
    */

    ordenFotos.forEach(
        function (foto, indice) {

            if (
                foto.id !== indice + 1
            ) {

                correcto = false;

            }

        }
    );


    /*
        Obtener elementos de resultado.
    */

    const resultado =
        document.getElementById(
            "resultado4"
        );


    const continuar =
        document.getElementById(
            "continuar4"
        );


    resultado.style.display =
        "block";


    /*
        ORDEN CORRECTO
    */

    if (correcto) {

        resultado.className =
            "correcto";


        resultado.innerHTML = `

            <h2>
                🎉 ¡LO HAS CONSEGUIDO! 🎉
            </h2>

            <p>
                Has colocado correctamente
                las 6 fotos.
            </p>

            <p>
                Has llegado al final... ❤️
            </p>

        `;


        /*
            Mostrar botón del regalo.
        */

        continuar.style.display =
            "block";


        /*
            Marcar todas las fotos
            como correctas.
        */

        document
            .querySelectorAll(
                ".photo-card"
            )
            .forEach(
                function (card) {

                    card.classList.add(
                        "correct-position"
                    );

                }
            );

    }


    /*
        ORDEN INCORRECTO
    */

    else {

        resultado.className =
            "incorrecto";


        resultado.innerHTML = `

            <h2>
                ❌ Todavía no...
            </h2>

            <p>
                Algunas fotos todavía
                no están en su sitio.
            </p>

            <p>
                ¡Inténtalo otra vez! ❤️
            </p>

        `;


        /*
            Ocultar botón del regalo.
        */

        continuar.style.display =
            "none";

    }

}



/* =====================================================
   REGALO FINAL
===================================================== */

function regaloFinal() {

    alert(
        "🎁 ¡HAS SUPERADO TODAS LAS PRUEBAS! ❤️"
    );

}

</script>


</body>

</html>
