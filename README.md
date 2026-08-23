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
            max-width: 700px;
            padding: 40px;
            border-radius: 25px;
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.15);
        }

        .header {
            text-align: center;
            margin-bottom: 35px;
        }

        .header h1 {
            color: #e75480;
            margin-bottom: 10px;
        }

        .header p {
            color: #666;
            font-size: 17px;
        }

        .question {
            margin-bottom: 30px;
        }

        .question h3 {
            margin-bottom: 15px;
            color: #333;
        }

        .options {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .option {
            border: 2px solid #eee;
            border-radius: 12px;
            padding: 12px 15px;
            cursor: pointer;
            transition: 0.2s;
        }

        .option:hover {
            border-color: #e75480;
            background: #fff5f7;
        }

        .option input {
            margin-right: 10px;
        }

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
            background: #d9436d;
            transform: translateY(-2px);
        }

        #resultado {
            display: none;
            text-align: center;
            margin-top: 25px;
            padding: 20px;
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

        #continuar {
            display: none;
            margin-top: 15px;
            background: #28a745;
        }

        #continuar:hover {
            background: #218838;
        }

        @media (max-width: 600px) {
            .container {
                padding: 25px;
            }
        }
    </style>
</head>

<body>

<div class="container">

    <div class="header">
        <h1>❤️ PRUEBA 1 ❤️</h1>
        <p>
            Si quieres descubrir tu sorpresa tendrás que superar
            esta primera prueba...
        </p>
        <p><strong>5 preguntas. 5 respuestas correctas.</strong></p>
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


    <div id="resultado"></div>

    <button id="continuar" onclick="siguientePrueba()">
        🎁 Continuar →
    </button>

</div>


<script>

    // CAMBIA ESTAS LETRAS POR LAS RESPUESTAS CORRECTAS
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

            const respuesta = document.querySelector(
                `input[name="${pregunta}"]:checked`
            );

            if (respuesta && respuesta.value === respuestasCorrectas[pregunta]) {
                aciertos++;
            }
        }


        const resultado = document.getElementById("resultado");
        const continuar = document.getElementById("continuar");

        resultado.style.display = "block";


        if (aciertos === 5) {

            resultado.className = "correcto";

            resultado.innerHTML = `
                <h2>🎉 ¡HAS SUPERADO LA PRUEBA! 🎉</h2>
                <p>
                    Parece que me conoces bastante bien...
                    Pero esto solo acaba de empezar 👀
                </p>
            `;

            continuar.style.display = "block";

        } else {

            resultado.className = "incorrecto";

            resultado.innerHTML = `
                <h2>❌ Casi...</h2>
                <p>
                    Has acertado <strong>${aciertos}/5</strong>.
                </p>
                <p>
                    Necesitas acertar las 5 para continuar.
                    ¡Vuelve a intentarlo! ❤️
                </p>
            `;

            continuar.style.display = "none";
        }
    }


    function siguientePrueba() {

        alert("¡Prueba 2 desbloqueada! 🚀");

        // Aquí pondremos posteriormente la segunda prueba.
        // Por ejemplo:
        // window.location.href = "prueba2.html";
    }

</script>

</body>
</html>
