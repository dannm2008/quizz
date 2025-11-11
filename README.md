<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <title>💖 TriviLocura 💖</title>
    <style>
        /* Reset */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif
        }

        /* Animated rainbow background */
        :root {
            --card-bg: rgba(255, 255, 255, 0.95);
        }

        body {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
            background: linear-gradient(120deg, #ff9a9e 0%, #fecfef 10%, #f6d365 20%, #fda085 30%, #a1c4fd 45%, #c2e9fb 55%, #d4fc79 70%, #96e6a1 85%, #fbc2eb 100%);
            background-size: 400% 400%;
            animation: rainbow 18s linear infinite;
        }

        @keyframes rainbow {
            0% {
                background-position: 0% 50%
            }

            50% {
                background-position: 100% 50%
            }

            100% {
                background-position: 0% 50%
            }
        }

        /* Container */
        .container {
            width: 100%;
            max-width: 980px;
            background: var(--card-bg);
            border-radius: 16px;
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.18);
            overflow: hidden;
            position: relative;
        }

        /* Header */
        .header {
            padding: 18px 22px;
            text-align: center;
            background: linear-gradient(90deg, rgba(255, 255, 255, 0.06), rgba(255, 255, 255, 0));
            border-bottom: 1px solid rgba(0, 0, 0, 0.06);
        }

        .title {
            font-size: 1.9rem;
            font-weight: 800;
            letter-spacing: 0.6px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
        }

        .title .heart {
            color: #ff5c9e;
            font-size: 1.3rem;
            transform: translateY(-2px);
        }

        .subtitle {
            color: #666;
            margin-top: 6px;
            font-size: 0.95rem;
            opacity: 0.95
        }

        /* Timer / progress */
        .timer-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 12px 20px;
            background: linear-gradient(to right, rgba(255, 255, 255, 0.6), rgba(255, 255, 255, 0.4));
            border-bottom: 1px solid rgba(0, 0, 0, 0.04);
        }

        .timer {
            font-weight: 700;
            color: #d6336c;
            background: #fff;
            padding: 6px 12px;
            border-radius: 20px;
            box-shadow: 0 2px 6px rgba(0, 0, 0, 0.06)
        }

        .progress {
            font-weight: 600;
            color: #333
        }

        /* Selection screen */
        .category-selection {
            padding: 26px;
            text-align: center
        }

        .category-title {
            font-size: 1.4rem;
            font-weight: 700;
            margin-bottom: 16px;
            color: #222
        }

        .categories-container {
            display: grid;
            gap: 12px;
            grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
            margin: 14px 0 22px
        }

        .category-card {
            background: linear-gradient(180deg, rgba(255, 255, 255, 0.7), rgba(255, 255, 255, 0.5));
            padding: 14px;
            border-radius: 12px;
            border: 2px solid rgba(0, 0, 0, 0.04);
            cursor: pointer;
            transition: transform .18s ease, box-shadow .18s ease;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            min-height: 84px;
            justify-content: center;
        }

        .category-card:hover {
            transform: translateY(-6px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08)
        }

        .category-card.selected {
            outline: 3px solid rgba(0, 0, 0, 0.06);
            transform: translateY(-2px);
        }

        .category-icon {
            font-size: 1.6rem
        }

        .category-name {
            font-weight: 700
        }

        /* Quiz screen */
        .quiz-container {
            padding: 22px 26px 30px
        }

        .question-container {
            margin-bottom: 18px
        }

        .question-number {
            color: #6c757d;
            margin-bottom: 6px
        }

        .question-text {
            font-size: 1.25rem;
            font-weight: 700;
            color: #222;
            line-height: 1.4;
            margin-bottom: 10px
        }

        .category-tag {
            display: inline-block;
            padding: 6px 10px;
            border-radius: 999px;
            font-weight: 700;
            color: #fff;
            margin-bottom: 10px
        }

        .options-container {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-top: 10px
        }

        .option {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 12px;
            border-radius: 10px;
            border: 2px solid rgba(0, 0, 0, 0.06);
            background: linear-gradient(180deg, #fff, #f8f9fb);
            cursor: pointer;
            transition: transform .12s ease, box-shadow .12s ease;
        }

        .option:hover {
            transform: translateY(-4px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.06)
        }

        .option.selected {
            background: linear-gradient(90deg, #6a11cb, #2575fc);
            color: #fff;
            border-color: transparent
        }

        .option-letter {
            width: 34px;
            height: 34px;
            border-radius: 50%;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            background: #eef2ff
        }

        .option.selected .option-letter {
            background: rgba(255, 255, 255, 0.25)
        }

        /* Navigation buttons */
        .navigation {
            display: flex;
            justify-content: space-between;
            gap: 8px;
            margin-top: 18px
        }

        .btn {
            padding: 12px 20px;
            border-radius: 10px;
            border: none;
            font-weight: 800;
            cursor: pointer;
            box-shadow: 0 6px 18px rgba(0, 0, 0, 0.06)
        }

        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
            transform: none;
            box-shadow: none
        }

        .btn-prev {
            background: #adb5bd;
            color: #fff
        }

        .btn-next {
            background: linear-gradient(90deg, #4a00e0, #8e2de2);
            color: #fff
        }

        .btn-start {
            background: linear-gradient(90deg, #ff7eb3, #ff758c);
            color: #fff;
            padding: 14px 28px;
            font-size: 1.05rem
        }

        /* Result screen */
        .results-container {
            padding: 22px
        }

        .results-title {
            font-size: 1.6rem;
            color: #6a11cb;
            font-weight: 800;
            text-align: center
        }

        .score {
            font-size: 2.4rem;
            font-weight: 900;
            color: #4a00e0;
            text-align: center;
            margin: 10px 0 6px
        }

        .results-summary {
            margin-top: 18px;
            background: #fff;
            padding: 16px;
            border-radius: 10px;
            max-height: 360px;
            overflow: auto;
            border: 1px solid rgba(0, 0, 0, 0.04)
        }

        .result-item {
            padding: 12px;
            border-bottom: 1px dashed rgba(0, 0, 0, 0.04)
        }

        .result-question {
            font-weight: 800;
            margin-bottom: 6px
        }

        .correct {
            color: #28a745;
            font-weight: 800
        }

        .incorrect {
            color: #dc3545;
            font-weight: 800
        }

        /* Feedback overlay */
        .feedback {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            top: 26%;
            z-index: 60;
            min-width: 260px;
            max-width: 80%;
            text-align: center;
            padding: 14px 18px;
            border-radius: 12px;
            display: none;
            align-items: center;
            gap: 10px;
            box-shadow: 0 14px 40px rgba(0, 0, 0, 0.18);
            font-weight: 900;
            font-size: 1.05rem;
        }

        .feedback.show {
            display: flex;
            animation: pop .32s ease both
        }

        @keyframes pop {
            from {
                transform: translateX(-50%) scale(0.8);
                opacity: 0
            }

            to {
                transform: translateX(-50%) scale(1);
                opacity: 1
            }
        }

        .feedback.correct {
            background: linear-gradient(90deg, #e9ffea, #d6ffe0);
            color: #1f7a3a
        }

        .feedback.incorrect {
            background: linear-gradient(90deg, #ffe7e7, #ffdcdc);
            color: #8a1f2b
        }

        /* Confetti canvas covers whole container */
        #confetti-canvas {
            position: absolute;
            inset: 0;
            pointer-events: none;
            z-index: 50
        }

        /* Shake animation for incorrect */
        .shake {
            animation: shake .45s ease both
        }

        @keyframes shake {

            10%,
            90% {
                transform: translateX(-1px)
            }

            20%,
            80% {
                transform: translateX(2px)
            }

            30%,
            50%,
            70% {
                transform: translateX(-4px)
            }

            40%,
            60% {
                transform: translateX(4px)
            }
        }

        /* Mobile tweaks */
        @media(max-width:640px) {
            .title {
                font-size: 1.4rem
            }

            .question-text {
                font-size: 1.05rem
            }

            .btn {
                padding: 10px 14px
            }
        }
    </style>
</head>

<body>
    <div class="container" id="app">
        <canvas id="confetti-canvas"></canvas>

        <div class="header">
            <div class="title">
                <span class="heart">💗</span>
                <span>TriviLocura</span>
                <span class="heart">💗</span>
            </div>
            <div class="subtitle">Elige una categoría y demuestra lo que sabes — ¡diviértete! 🎉</div>
        </div>

        <!-- Timer / progress -->
        <div class="timer-container">
            <div class="progress">Pregunta <span id="current-question">1</span> de 10</div>
            <div class="timer">Tiempo: <span id="time">02:00</span></div>
        </div>

        <!-- Category selection -->
        <div id="category-screen" class="category-selection">
            <h2 class="category-title">💖 Elige una categoría para estudiar</h2>
            <div class="categories-container" id="categories-container"></div>
            <button id="start-btn" class="btn btn-start" disabled>Comenzar Cuestionario</button>
        </div>

        <!-- Quiz screen -->
        <div id="quiz-screen" class="quiz-container hidden" style="display:none">
            <div class="question-container">
                <div class="question-number">Pregunta <span id="question-number">1</span></div>
                <div class="category-tag" id="question-category"></div>
                <div class="question-text" id="question-text"></div>
            </div>

            <div id="feedback" class="feedback" role="status" aria-live="polite"></div>

            <div class="options-container" id="options-container"></div>

            <div class="navigation">
                <button id="prev-btn" class="btn btn-prev" disabled>Anterior</button>
                <button id="next-btn" class="btn btn-next">Siguiente</button>
            </div>
        </div>

        <!-- Results screen -->
        <div id="results-screen" class="results-container hidden" style="display:none">
            <h2 class="results-title">Resultados del Cuestionario</h2>
            <div class="score" id="final-score">0/10</div>
            <p id="result-message" style="text-align:center"></p>
            <div class="results-summary" id="results-summary"></div>
            <div style="text-align:center; margin-top:14px;">
                <button id="restart-btn" class="btn btn-start">Volver a Seleccionar Categorías</button>
            </div>
        </div>
    </div>

    <script>
        /* -------------------------
           Datos de categorías y preguntas (sin imágenes)
           ------------------------- */
        const categories = [
            { id: 'matematicas', name: 'Matemáticas', color: '#FF6B6B', icon: '∑' },
            { id: 'ciencias', name: 'Ciencias', color: '#4ECDC4', icon: '🔬' },
            { id: 'historia', name: 'Historia', color: '#FFD166', icon: '📜' },
            { id: 'geografia', name: 'Geografía', color: '#06D6A0', icon: '🌎' },
            { id: 'literatura', name: 'Literatura', color: '#118AB2', icon: '📚' },
            { id: 'arte', name: 'Arte', color: '#073B4C', icon: '🎨' },
            { id: 'deportes', name: 'Deportes', color: '#EF476F', icon: '⚽' },
            { id: 'tecnologia', name: 'Tecnología', color: '#7209B7', icon: '💻' },
            { id: 'mixtas', name: 'Preguntas Mixtas', color: '#FF9E64', icon: '🎲' }
        ];

        function generateQuestions() {
            return [
                // MATEMÁTICAS (1-20 de 100)
                // MATEMÁTICAS (1-20 de 100)
                { id: 1, question: "¿Cuál es el resultado de 25 + 18?", options: ["41", "43", "45", "47"], correct: 1, explanation: "25 + 18 = 43", category: "matematicas" },
                { id: 2, question: "¿Cuánto es 7 × 9?", options: ["60", "63", "65", "67"], correct: 1, explanation: "7 × 9 = 63", category: "matematicas" },
                { id: 3, question: "¿Cuánto es 156 ÷ 12?", options: ["11", "12", "13", "14"], correct: 2, explanation: "156 ÷ 12 = 13", category: "matematicas" },
                { id: 4, question: "¿Cuánto es 45 - 27?", options: ["16", "17", "18", "19"], correct: 2, explanation: "45 - 27 = 18", category: "matematicas" },
                { id: 5, question: "¿Cuál es el cuadrado de 8?", options: ["60", "62", "64", "66"], correct: 2, explanation: "8² = 64", category: "matematicas" },
                { id: 6, question: "¿Cuál es la raíz cuadrada de 144?", options: ["10", "11", "12", "13"], correct: 2, explanation: "√144 = 12", category: "matematicas" },
                { id: 7, question: "¿Qué porcentaje es 40 de 200?", options: ["15%", "20%", "25%", "30%"], correct: 1, explanation: "40/200 = 20%", category: "matematicas" },
                { id: 8, question: "¿Cuánto es 5³?", options: ["115", "120", "125", "130"], correct: 2, explanation: "5³ = 125", category: "matematicas" },
                { id: 9, question: "¿Cuál es el perímetro de un cuadrado de lado 6 cm?", options: ["22 cm", "24 cm", "26 cm", "28 cm"], correct: 1, explanation: "Perímetro = 4 × 6 = 24 cm", category: "matematicas" },
                { id: 10, question: "¿Cuánto es 17 + 35?", options: ["50", "52", "54", "56"], correct: 1, explanation: "17 + 35 = 52", category: "matematicas" },
                { id: 11, question: "¿Cuál es el 30% de 150?", options: ["35", "40", "45", "50"], correct: 2, explanation: "30% de 150 = 45", category: "matematicas" },
                { id: 12, question: "¿Cuánto es 13 × 4?", options: ["49", "51", "52", "54"], correct: 2, explanation: "13 × 4 = 52", category: "matematicas" },
                { id: 13, question: "¿Cuál es el MCD de 24 y 36?", options: ["10", "12", "14", "16"], correct: 1, explanation: "MCD(24,36) = 12", category: "matematicas" },
                { id: 14, question: "¿Cuánto es 72 ÷ 8?", options: ["7", "8", "9", "10"], correct: 2, explanation: "72 ÷ 8 = 9", category: "matematicas" },
                { id: 15, question: "¿Qué fracción representa 0.25?", options: ["1/5", "1/4", "1/3", "1/2"], correct: 1, explanation: "0.25 = 1/4", category: "matematicas" },
                { id: 16, question: "¿Cuánto es 28 + 47?", options: ["73", "75", "77", "79"], correct: 1, explanation: "28 + 47 = 75", category: "matematicas" },
                { id: 17, question: "¿Cuál es el área de un rectángulo de 8 × 5?", options: ["35", "38", "40", "42"], correct: 2, explanation: "Área = 8 × 5 = 40", category: "matematicas" },
                { id: 18, question: "¿Cuánto es 96 - 38?", options: ["56", "58", "60", "62"], correct: 1, explanation: "96 - 38 = 58", category: "matematicas" },
                { id: 19, question: "¿Qué número es el 75% de 80?", options: ["55", "60", "65", "70"], correct: 1, explanation: "75% de 80 = 60", category: "matematicas" },
                { id: 20, question: "¿Cuánto es 6 × 7 + 8?", options: ["48", "50", "52", "54"], correct: 1, explanation: "6×7=42; 42+8=50", category: "matematicas" },
                { id: 21, question: "¿Cuál es el resultado de 36 + 29?", options: ["63", "65", "67", "69"], correct: 1, explanation: "36 + 29 = 65", category: "matematicas" },
                { id: 22, question: "¿Cuánto es 12 × 6?", options: ["68", "70", "72", "74"], correct: 2, explanation: "12 × 6 = 72", category: "matematicas" },
                { id: 23, question: "¿Cuál es el 40% de 200?", options: ["60", "70", "80", "90"], correct: 2, explanation: "40% de 200 = 80", category: "matematicas" },
                { id: 24, question: "¿Cuánto es 168 ÷ 14?", options: ["10", "11", "12", "13"], correct: 2, explanation: "168 ÷ 14 = 12", category: "matematicas" },
                { id: 25, question: "¿Cuál es el resultado de 52 - 27?", options: ["23", "24", "25", "26"], correct: 2, explanation: "52 - 27 = 25", category: "matematicas" },
                { id: 26, question: "¿Cuál es el perímetro de un triángulo equilátero de lado 8 cm?", options: ["22 cm", "24 cm", "26 cm", "28 cm"], correct: 1, explanation: "Perímetro = 3 × 8 = 24 cm", category: "matematicas" },
                { id: 27, question: "¿Cuánto es 15²?", options: ["215", "225", "235", "245"], correct: 1, explanation: "15² = 225", category: "matematicas" },
                { id: 28, question: "¿Qué fracción equivale a 0.5?", options: ["1/4", "1/3", "1/2", "2/3"], correct: 2, explanation: "0.5 = 1/2", category: "matematicas" },
                { id: 29, question: "¿Cuál es el MCM de 12 y 18?", options: ["32", "34", "36", "38"], correct: 2, explanation: "MCM(12,18) = 36", category: "matematicas" },
                { id: 30, question: "¿Cuánto es 23 + 48?", options: ["69", "71", "73", "75"], correct: 1, explanation: "23 + 48 = 71", category: "matematicas" },
                { id: 31, question: "¿Cuál es el resultado de 64 ÷ 8?", options: ["6", "7", "8", "9"], correct: 2, explanation: "64 ÷ 8 = 8", category: "matematicas" },
                { id: 32, question: "¿Cuánto es 11 × 7?", options: ["75", "77", "79", "81"], correct: 1, explanation: "11 × 7 = 77", category: "matematicas" },
                { id: 33, question: "¿Qué número es el 15% de 200?", options: ["25", "30", "35", "40"], correct: 1, explanation: "15% de 200 = 30", category: "matematicas" },
                { id: 34, question: "¿Cuál es el área de un triángulo de base 10 cm y altura 6 cm?", options: ["25 cm²", "30 cm²", "35 cm²", "40 cm²"], correct: 1, explanation: "Área = (10 × 6) ÷ 2 = 30 cm²", category: "matematicas" },
                { id: 35, question: "¿Cuánto es 84 - 36?", options: ["44", "46", "48", "50"], correct: 2, explanation: "84 - 36 = 48", category: "matematicas" },
                { id: 36, question: "¿Cuál es la raíz cuadrada de 225?", options: ["13", "14", "15", "16"], correct: 2, explanation: "√225 = 15", category: "matematicas" },
                { id: 37, question: "¿Cuánto es 19 + 26?", options: ["43", "45", "47", "49"], correct: 1, explanation: "19 + 26 = 45", category: "matematicas" },
                { id: 38, question: "¿Qué fracción representa 0.75?", options: ["2/4", "3/4", "4/4", "3/5"], correct: 1, explanation: "0.75 = 3/4", category: "matematicas" },
                { id: 39, question: "¿Cuánto es 13 × 8?", options: ["101", "104", "107", "110"], correct: 1, explanation: "13 × 8 = 104", category: "matematicas" },
                { id: 40, question: "¿Cuál es el 60% de 150?", options: ["85", "90", "95", "100"], correct: 1, explanation: "60% de 150 = 90", category: "matematicas" },
                { id: 41, question: "¿Cuánto es 56 + 39?", options: ["93", "95", "97", "99"], correct: 1, explanation: "56 + 39 = 95", category: "matematicas" },
                { id: 42, question: "¿Cuál es el resultado de 17 × 6?", options: ["99", "102", "105", "108"], correct: 0, explanation: "17 × 6 = 102", category: "matematicas" },
                { id: 43, question: "¿Cuánto es 225 ÷ 15?", options: ["12", "13", "14", "15"], correct: 3, explanation: "225 ÷ 15 = 15", category: "matematicas" },
                { id: 44, question: "¿Cuál es el 55% de 200?", options: ["100", "110", "120", "130"], correct: 1, explanation: "55% de 200 = 110", category: "matematicas" },
                { id: 45, question: "¿Cuánto es 78 - 45?", options: ["31", "33", "35", "37"], correct: 1, explanation: "78 - 45 = 33", category: "matematicas" },
                { id: 46, question: "¿Cuál es la raíz cuadrada de 196?", options: ["12", "13", "14", "15"], correct: 2, explanation: "√196 = 14", category: "matematicas" },
                { id: 47, question: "¿Cuánto es 7³?", options: ["331", "341", "343", "353"], correct: 2, explanation: "7³ = 343", category: "matematicas" },
                { id: 48, question: "¿Qué fracción representa 0.4?", options: ["2/5", "3/5", "4/5", "3/4"], correct: 0, explanation: "0.4 = 2/5", category: "matematicas" },
                { id: 49, question: "¿Cuál es el área de un cuadrado de lado 9 cm?", options: ["77 cm²", "81 cm²", "85 cm²", "89 cm²"], correct: 1, explanation: "Área = 9 × 9 = 81 cm²", category: "matematicas" },
                { id: 50, question: "¿Cuánto es 14 × 9?", options: ["122", "124", "126", "128"], correct: 2, explanation: "14 × 9 = 126", category: "matematicas" },
                { id: 51, question: "¿Cuál es el MCD de 36 y 48?", options: ["10", "12", "14", "16"], correct: 1, explanation: "MCD(36,48) = 12", category: "matematicas" },
                { id: 52, question: "¿Cuánto es 91 - 37?", options: ["52", "54", "56", "58"], correct: 1, explanation: "91 - 37 = 54", category: "matematicas" },
                { id: 53, question: "¿Qué número es el 70% de 90?", options: ["61", "63", "65", "67"], correct: 1, explanation: "70% de 90 = 63", category: "matematicas" },
                { id: 54, question: "¿Cuál es el perímetro de un rectángulo de 7 × 4 cm?", options: ["20 cm", "22 cm", "24 cm", "26 cm"], correct: 1, explanation: "Perímetro = 2(7 + 4) = 22 cm", category: "matematicas" },
                { id: 55, question: "¿Cuánto es 144 ÷ 16?", options: ["7", "8", "9", "10"], correct: 2, explanation: "144 ÷ 16 = 9", category: "matematicas" },
                { id: 56, question: "¿Cuál es el cuadrado de 11?", options: ["119", "121", "123", "125"], correct: 1, explanation: "11² = 121", category: "matematicas" },
                { id: 57, question: "¿Cuánto es 67 + 45?", options: ["110", "112", "114", "116"], correct: 1, explanation: "67 + 45 = 112", category: "matematicas" },
                { id: 58, question: "¿Qué fracción es equivalente a 0.9?", options: ["7/10", "8/10", "9/10", "10/10"], correct: 2, explanation: "0.9 = 9/10", category: "matematicas" },
                { id: 59, question: "¿Cuánto es 18 × 5?", options: ["86", "88", "90", "92"], correct: 2, explanation: "18 × 5 = 90", category: "matematicas" },
                { id: 60, question: "¿Cuál es el 25% de 320?", options: ["75", "80", "85", "90"], correct: 1, explanation: "25% de 320 = 80", category: "matematicas" },
                { id: 61, question: "¿Cuánto es 56 + 89?", options: ["143", "145", "147", "149"], correct: 1, explanation: "56 + 89 = 145", category: "matematicas" },
                { id: 62, question: "¿Cuál es el resultado de 18 × 5?", options: ["86", "88", "90", "92"], correct: 2, explanation: "18 × 5 = 90", category: "matematicas" },
                { id: 63, question: "¿Cuánto es 196 ÷ 14?", options: ["12", "13", "14", "15"], correct: 2, explanation: "196 ÷ 14 = 14", category: "matematicas" },
                { id: 64, question: "¿Qué número es el 80% de 150?", options: ["115", "120", "125", "130"], correct: 1, explanation: "80% de 150 = 120", category: "matematicas" },
                { id: 65, question: "¿Cuál es el área de un cuadrado de lado 12 cm?", options: ["140 cm²", "144 cm²", "148 cm²", "152 cm²"], correct: 1, explanation: "Área = 12 × 12 = 144 cm²", category: "matematicas" },
                { id: 66, question: "¿Cuánto es 95 - 47?", options: ["46", "48", "50", "52"], correct: 1, explanation: "95 - 47 = 48", category: "matematicas" },
                { id: 67, question: "¿Qué fracción representa 0.2?", options: ["1/5", "2/5", "3/5", "4/5"], correct: 0, explanation: "0.2 = 1/5", category: "matematicas" },
                { id: 68, question: "¿Cuál es la raíz cuadrada de 256?", options: ["14", "15", "16", "17"], correct: 2, explanation: "√256 = 16", category: "matematicas" },
                { id: 69, question: "¿Cuánto es 14 × 12?", options: ["164", "168", "172", "176"], correct: 1, explanation: "14 × 12 = 168", category: "matematicas" },
                { id: 70, question: "¿Cuál es el 70% de 200?", options: ["135", "140", "145", "150"], correct: 1, explanation: "70% de 200 = 140", category: "matematicas" },
                { id: 71, question: "¿Cuánto es 8³?", options: ["496", "504", "512", "520"], correct: 2, explanation: "8³ = 512", category: "matematicas" },
                { id: 72, question: "¿Cuál es el MCD de 48 y 72?", options: ["20", "24", "28", "32"], correct: 1, explanation: "MCD(48,72) = 24", category: "matematicas" },
                { id: 73, question: "¿Cuánto es 132 ÷ 11?", options: ["10", "11", "12", "13"], correct: 2, explanation: "132 ÷ 11 = 12", category: "matematicas" },
                { id: 74, question: "¿Qué fracción es equivalente a 0.3?", options: ["3/10", "3/9", "3/8", "3/7"], correct: 0, explanation: "0.3 = 3/10", category: "matematicas" },
                { id: 75, question: "¿Cuánto es 63 + 78?", options: ["139", "141", "143", "145"], correct: 1, explanation: "63 + 78 = 141", category: "matematicas" },
                { id: 76, question: "¿Cuál es el perímetro de un triángulo de lados 5, 6 y 7 cm?", options: ["16 cm", "18 cm", "20 cm", "22 cm"], correct: 1, explanation: "Perímetro = 5 + 6 + 7 = 18 cm", category: "matematicas" },
                { id: 77, question: "¿Cuánto es 17 × 9?", options: ["151", "153", "155", "157"], correct: 1, explanation: "17 × 9 = 153", category: "matematicas" },
                { id: 78, question: "¿Qué número es el 55% de 160?", options: ["86", "88", "90", "92"], correct: 1, explanation: "55% de 160 = 88", category: "matematicas" },
                { id: 79, question: "¿Cuál es el resultado de 108 - 59?", options: ["47", "49", "51", "53"], correct: 1, explanation: "108 - 59 = 49", category: "matematicas" },
                { id: 80, question: "¿Cuánto es 13²?", options: ["165", "169", "173", "177"], correct: 1, explanation: "13² = 169", category: "matematicas" },
                { id: 81, question: "¿Cuál es el MCM de 15 y 20?", options: ["55", "60", "65", "70"], correct: 1, explanation: "MCM(15,20) = 60", category: "matematicas" },
                { id: 82, question: "¿Cuánto es 123 + 89?", options: ["210", "212", "214", "216"], correct: 1, explanation: "123 + 89 = 212", category: "matematicas" },
                { id: 83, question: "¿Qué fracción representa 0.35?", options: ["7/20", "6/20", "8/20", "9/20"], correct: 0, explanation: "0.35 = 7/20", category: "matematicas" },
                { id: 84, question: "¿Cuál es la raíz cuadrada de 289?", options: ["15", "17", "19", "21"], correct: 1, explanation: "√289 = 17", category: "matematicas" },
                { id: 85, question: "¿Cuánto es 216 ÷ 18?", options: ["10", "12", "14", "16"], correct: 1, explanation: "216 ÷ 18 = 12", category: "matematicas" },
                { id: 86, question: "¿Qué número es el 90% de 250?", options: ["215", "225", "235", "245"], correct: 1, explanation: "90% de 250 = 225", category: "matematicas" },
                { id: 87, question: "¿Cuánto es 19 × 8?", options: ["148", "152", "156", "160"], correct: 1, explanation: "19 × 8 = 152", category: "matematicas" },
                { id: 88, question: "¿Cuál es el área de un rectángulo de 15 × 6 cm?", options: ["85 cm²", "90 cm²", "95 cm²", "100 cm²"], correct: 1, explanation: "Área = 15 × 6 = 90 cm²", category: "matematicas" },
                { id: 89, question: "¿Cuánto es 167 - 89?", options: ["76", "78", "80", "82"], correct: 1, explanation: "167 - 89 = 78", category: "matematicas" },
                { id: 90, question: "¿Qué fracción es equivalente a 0.45?", options: ["7/20", "8/20", "9/20", "10/20"], correct: 2, explanation: "0.45 = 9/20", category: "matematicas" },
                { id: 91, question: "¿Cuál es el perímetro de un cuadrado de lado 15 cm?", options: ["55 cm", "60 cm", "65 cm", "70 cm"], correct: 1, explanation: "Perímetro = 4 × 15 = 60 cm", category: "matematicas" },
                { id: 92, question: "¿Cuánto es 14³?", options: ["2644", "2744", "2844", "2744"], correct: 1, explanation: "14³ = 2744", category: "matematicas" },
                { id: 93, question: "¿Qué número es el 75% de 240?", options: ["175", "180", "185", "190"], correct: 1, explanation: "75% de 240 = 180", category: "matematicas" },
                { id: 94, question: "¿Cuánto es 23 × 7?", options: ["159", "161", "163", "165"], correct: 1, explanation: "23 × 7 = 161", category: "matematicas" },
                { id: 95, question: "¿Cuál es el MCD de 64 y 96?", options: ["30", "32", "34", "36"], correct: 1, explanation: "MCD(64,96) = 32", category: "matematicas" },
                { id: 96, question: "¿Cuánto es 144 ÷ 9?", options: ["14", "16", "18", "20"], correct: 1, explanation: "144 ÷ 9 = 16", category: "matematicas" },
                { id: 97, question: "¿Qué fracción representa 0.15?", options: ["3/20", "4/20", "5/20", "6/20"], correct: 0, explanation: "0.15 = 3/20", category: "matematicas" },
                { id: 98, question: "¿Cuál es el área de un triángulo de base 12 cm y altura 8 cm?", options: ["46 cm²", "48 cm²", "50 cm²", "52 cm²"], correct: 1, explanation: "Área = (12 × 8) ÷ 2 = 48 cm²", category: "matematicas" },
                { id: 99, question: "¿Cuánto es 185 - 97?", options: ["86", "88", "90", "92"], correct: 1, explanation: "185 - 97 = 88", category: "matematicas" },
                { id: 100, question: "¿Qué número es el 40% de 350?", options: ["135", "140", "145", "150"], correct: 1, explanation: "40% de 350 = 140", category: "matematicas" },
                // CIENCIAS (101-200)
                { id: 101, question: "¿Cuál es el símbolo químico del Oxígeno?", options: ["O", "Ox", "Og", "Om"], correct: 0, explanation: "El símbolo químico del Oxígeno es O", category: "ciencias" },
                { id: 102, question: "¿Qué planeta es conocido como el planeta rojo?", options: ["Venus", "Marte", "Júpiter", "Saturno"], correct: 1, explanation: "Marte es conocido como el planeta rojo", category: "ciencias" },
                { id: 103, question: "¿Cuál es el hueso más largo del cuerpo humano?", options: ["Húmero", "Fémur", "Tibia", "Radio"], correct: 1, explanation: "El fémur es el hueso más largo del cuerpo humano", category: "ciencias" },
                { id: 104, question: "¿Qué gas es el más abundante en la atmósfera terrestre?", options: ["Oxígeno", "Nitrógeno", "Dióxido de carbono", "Hidrógeno"], correct: 1, explanation: "El Nitrógeno constituye aproximadamente el 78% de la atmósfera", category: "ciencias" },
                { id: 105, question: "¿Cuál es la unidad básica de la vida?", options: ["Átomo", "Célula", "Molécula", "Tejido"], correct: 1, explanation: "La célula es la unidad básica de la vida", category: "ciencias" },
                { id: 106, question: "¿Cuántos planetas hay en el Sistema Solar?", options: ["7", "8", "9", "10"], correct: 1, explanation: "Hay 8 planetas en el Sistema Solar", category: "ciencias" },
                { id: 107, question: "¿Qué vitamina se produce en la piel gracias al sol?", options: ["Vitamina A", "Vitamina B", "Vitamina C", "Vitamina D"], correct: 3, explanation: "La vitamina D se produce en la piel por exposición al sol", category: "ciencias" },
                { id: 108, question: "¿Cuál es el elemento más abundante en el universo?", options: ["Oxígeno", "Carbono", "Hidrógeno", "Helio"], correct: 2, explanation: "El Hidrógeno es el elemento más abundante en el universo", category: "ciencias" },
                { id: 109, question: "¿Qué órgano del cuerpo humano produce la insulina?", options: ["Hígado", "Páncreas", "Riñón", "Bazo"], correct: 1, explanation: "El páncreas produce la insulina", category: "ciencias" },
                { id: 110, question: "¿Cuál es la velocidad de la luz?", options: ["299,792 km/s", "199,792 km/s", "399,792 km/s", "499,792 km/s"], correct: 0, explanation: "La velocidad de la luz es 299,792 kilómetros por segundo", category: "ciencias" },
                { id: 111, question: "¿Qué tipo de células son los glóbulos rojos?", options: ["Neuronas", "Leucocitos", "Eritrocitos", "Plaquetas"], correct: 2, explanation: "Los glóbulos rojos son eritrocitos", category: "ciencias" },
                { id: 112, question: "¿Cuál es el metal más abundante en la corteza terrestre?", options: ["Hierro", "Cobre", "Aluminio", "Zinc"], correct: 2, explanation: "El Aluminio es el metal más abundante en la corteza terrestre", category: "ciencias" },
                { id: 113, question: "¿Qué gas necesitan las plantas para realizar la fotosíntesis?", options: ["Oxígeno", "Nitrógeno", "Dióxido de carbono", "Hidrógeno"], correct: 2, explanation: "Las plantas necesitan CO2 para la fotosíntesis", category: "ciencias" },
                { id: 114, question: "¿Cuál es el órgano más grande del cuerpo humano?", options: ["Hígado", "Piel", "Intestino", "Pulmones"], correct: 1, explanation: "La piel es el órgano más grande del cuerpo humano", category: "ciencias" },
                { id: 115, question: "¿Qué elemento químico tiene el símbolo Fe?", options: ["Fósforo", "Flúor", "Hierro", "Flerovio"], correct: 2, explanation: "Fe es el símbolo químico del Hierro", category: "ciencias" },
                { id: 116, question: "¿Cuál es la principal función de los glóbulos blancos?", options: ["Transportar oxígeno", "Defender el organismo", "Coagular la sangre", "Producir hormonas"], correct: 1, explanation: "Los glóbulos blancos defienden al organismo contra infecciones", category: "ciencias" },
                { id: 117, question: "¿Qué planeta es el más grande del Sistema Solar?", options: ["Saturno", "Júpiter", "Urano", "Neptuno"], correct: 1, explanation: "Júpiter es el planeta más grande del Sistema Solar", category: "ciencias" },
                { id: 118, question: "¿Cuál es el proceso por el cual las plantas fabrican su alimento?", options: ["Digestión", "Respiración", "Fotosíntesis", "Fermentación"], correct: 2, explanation: "Las plantas fabrican su alimento mediante la fotosíntesis", category: "ciencias" },
                { id: 119, question: "¿Qué parte del cerebro controla el equilibrio?", options: ["Cerebelo", "Hipotálamo", "Tálamo", "Médula"], correct: 0, explanation: "El cerebelo controla el equilibrio", category: "ciencias" },
                { id: 120, question: "¿Cuál es el hueso más duro del cuerpo humano?", options: ["Fémur", "Cráneo", "Mandíbula", "Tibia"], correct: 1, explanation: "El cráneo es el hueso más duro del cuerpo humano", category: "ciencias" },
                { id: 121, question: "¿Qué elemento químico tiene el número atómico 1?", options: ["Helio", "Hidrógeno", "Litio", "Berilio"], correct: 1, explanation: "El Hidrógeno tiene el número atómico 1", category: "ciencias" },
                { id: 122, question: "¿Cuál es la capa más externa de la Tierra?", options: ["Núcleo", "Manto", "Corteza", "Astenosfera"], correct: 2, explanation: "La corteza es la capa más externa de la Tierra", category: "ciencias" },
                { id: 123, question: "¿Qué gas exhalan las plantas durante la noche?", options: ["Oxígeno", "Dióxido de carbono", "Nitrógeno", "Hidrógeno"], correct: 1, explanation: "Las plantas exhalan CO2 durante la noche", category: "ciencias" },
                { id: 124, question: "¿Cuál es el planeta más cercano al Sol?", options: ["Venus", "Marte", "Mercurio", "Tierra"], correct: 2, explanation: "Mercurio es el planeta más cercano al Sol", category: "ciencias" },
                { id: 125, question: "¿Qué tipo de energía es la eólica?", options: ["Solar", "Nuclear", "Eléctrica", "Renovable"], correct: 3, explanation: "La energía eólica es un tipo de energía renovable", category: "ciencias" },
                { id: 126, question: "¿Cuál es la función principal del sistema digestivo?", options: ["Respirar", "Digerir alimentos", "Bombear sangre", "Filtrar toxinas"], correct: 1, explanation: "El sistema digestivo se encarga de digerir los alimentos", category: "ciencias" },
                { id: 127, question: "¿Qué es un átomo?", options: ["Una célula", "La unidad básica de la materia", "Una molécula", "Un compuesto"], correct: 1, explanation: "El átomo es la unidad básica de la materia", category: "ciencias" },
                { id: 128, question: "¿Cuál es el metal más pesado?", options: ["Oro", "Plomo", "Osmio", "Platino"], correct: 2, explanation: "El Osmio es el metal más pesado", category: "ciencias" },
                { id: 129, question: "¿Qué es la mitosis?", options: ["Reproducción sexual", "División celular", "Fotosíntesis", "Respiración"], correct: 1, explanation: "La mitosis es un tipo de división celular", category: "ciencias" },
                { id: 130, question: "¿Cuál es el órgano que produce la bilis?", options: ["Páncreas", "Hígado", "Vesícula", "Estómago"], correct: 1, explanation: "El hígado produce la bilis", category: "ciencias" },
                { id: 131, question: "¿Qué es un protón?", options: ["Partícula sin carga", "Partícula negativa", "Partícula positiva", "Partícula neutra"], correct: 2, explanation: "Un protón es una partícula con carga positiva", category: "ciencias" },
                { id: 132, question: "¿Cuál es la principal función de los riñones?", options: ["Digestión", "Filtración", "Respiración", "Circulación"], correct: 1, explanation: "Los riñones filtran la sangre", category: "ciencias" },
                { id: 133, question: "¿Qué es un eclipse solar?", options: ["Luna cubre Sol", "Sol cubre Luna", "Luna nueva", "Luna llena"], correct: 0, explanation: "Un eclipse solar ocurre cuando la Luna cubre el Sol", category: "ciencias" },
                { id: 134, question: "¿Cuál es el gas noble más abundante?", options: ["Helio", "Neón", "Argón", "Xenón"], correct: 2, explanation: "El Argón es el gas noble más abundante en la atmósfera", category: "ciencias" },
                { id: 135, question: "¿Qué es la meiosis?", options: ["División celular", "Reproducción asexual", "División sexual", "Fotosíntesis"], correct: 2, explanation: "La meiosis es división celular para reproducción sexual", category: "ciencias" },
                { id: 136, question: "¿Cuál es el hueso más pequeño del cuerpo?", options: ["Estribo", "Yunque", "Martillo", "Cóclea"], correct: 0, explanation: "El estribo es el hueso más pequeño del cuerpo humano", category: "ciencias" },
                { id: 137, question: "¿Qué es la clorofila?", options: ["Hormona", "Pigmento verde", "Proteína", "Vitamina"], correct: 1, explanation: "La clorofila es el pigmento verde de las plantas", category: "ciencias" },
                { id: 138, question: "¿Cuál es el elemento más electronegativos?", options: ["Oxígeno", "Flúor", "Cloro", "Nitrógeno"], correct: 1, explanation: "El Flúor es el elemento más electronegativo", category: "ciencias" },
                { id: 139, question: "¿Qué es un neutrón?", options: ["Partícula positiva", "Partícula negativa", "Partícula neutra", "Electrón"], correct: 2, explanation: "Un neutrón es una partícula sin carga eléctrica", category: "ciencias" },
                { id: 140, question: "¿Cuál es la función principal del sistema respiratorio?", options: ["Oxigenar sangre", "Digerir", "Filtrar", "Circular"], correct: 0, explanation: "El sistema respiratorio oxigena la sangre", category: "ciencias" },
                { id: 141, question: "¿Qué es el ADN?", options: ["Proteína", "Ácido nucleico", "Carbohidrato", "Lípido"], correct: 1, explanation: "El ADN es un ácido nucleico", category: "ciencias" },
                { id: 142, question: "¿Cuál es la unidad básica del sonido?", options: ["Vatio", "Decibelio", "Hertz", "Lumen"], correct: 2, explanation: "El Hertz es la unidad básica del sonido", category: "ciencias" },
                { id: 143, question: "¿Qué es un electrón?", options: ["Partícula positiva", "Partícula negativa", "Partícula neutra", "Protón"], correct: 1, explanation: "Un electrón es una partícula con carga negativa", category: "ciencias" },
                { id: 144, question: "¿Cuál es el planeta más frío del Sistema Solar?", options: ["Neptuno", "Urano", "Saturno", "Plutón"], correct: 1, explanation: "Urano es el planeta más frío del Sistema Solar", category: "ciencias" },
                { id: 145, question: "¿Qué es la fotosíntesis?", options: ["Respiración", "Producción de alimento", "Digestión", "Circulación"], correct: 1, explanation: "La fotosíntesis es el proceso de producción de alimento en plantas", category: "ciencias" },
                { id: 146, question: "¿Cuál es la principal función del sistema circulatorio?", options: ["Respirar", "Digerir", "Transportar sangre", "Filtrar"], correct: 2, explanation: "El sistema circulatorio transporta sangre", category: "ciencias" },
                { id: 147, question: "¿Qué es un isótopo?", options: ["Mismo número atómico", "Mismo número másico", "Mismo número de neutrones", "Mismo peso"], correct: 0, explanation: "Los isótopos tienen el mismo número atómico", category: "ciencias" },
                { id: 148, question: "¿Cuál es la unidad básica de la corriente eléctrica?", options: ["Voltio", "Amperio", "Vatio", "Ohmio"], correct: 1, explanation: "El Amperio es la unidad de corriente eléctrica", category: "ciencias" },
                { id: 149, question: "¿Qué es la gravedad?", options: ["Fuerza de atracción", "Energía", "Velocidad", "Aceleración"], correct: 0, explanation: "La gravedad es una fuerza de atracción entre masas", category: "ciencias" },
                { id: 150, question: "¿Cuál es el planeta más caliente del Sistema Solar?", options: ["Mercurio", "Venus", "Marte", "Júpiter"], correct: 1, explanation: "Venus es el planeta más caliente debido a su efecto invernadero", category: "ciencias" },
                { id: 151, question: "¿Qué es un ácido?", options: ["pH mayor a 7", "pH menor a 7", "pH igual a 7", "Sin pH"], correct: 1, explanation: "Un ácido tiene pH menor a 7", category: "ciencias" },
                { id: 152, question: "¿Cuál es la función principal de los pulmones?", options: ["Bombear sangre", "Intercambiar gases", "Filtrar sangre", "Digerir"], correct: 1, explanation: "Los pulmones realizan el intercambio de gases", category: "ciencias" }, { id: 153, question: "¿Qué es una base?", options: ["pH menor a 7", "pH mayor a 7", "pH igual a 7", "Sin pH"], correct: 1, explanation: "Una base tiene pH mayor a 7", category: "ciencias" },
                { id: 154, question: "¿Cuál es el metal más conductivo?", options: ["Oro", "Cobre", "Plata", "Aluminio"], correct: 2, explanation: "La Plata es el metal más conductivo", category: "ciencias" },
                { id: 155, question: "¿Qué es la presión atmosférica?", options: ["Peso del aire", "Temperatura del aire", "Humedad del aire", "Densidad del aire"], correct: 0, explanation: "La presión atmosférica es el peso del aire sobre la Tierra", category: "ciencias" },
                { id: 156, question: "¿Cuál es la unidad básica de la temperatura?", options: ["Celsius", "Fahrenheit", "Kelvin", "Rankine"], correct: 2, explanation: "El Kelvin es la unidad básica de temperatura", category: "ciencias" },
                { id: 157, question: "¿Qué es un compuesto químico?", options: ["Un elemento", "Varios elementos unidos", "Un átomo", "Una molécula simple"], correct: 1, explanation: "Un compuesto químico está formado por varios elementos unidos", category: "ciencias" },
                { id: 158, question: "¿Cuál es la principal función del sistema nervioso?", options: ["Coordinar", "Digerir", "Respirar", "Circular"], correct: 0, explanation: "El sistema nervioso coordina las funciones del cuerpo", category: "ciencias" },
                { id: 159, question: "¿Qué es la energía cinética?", options: ["Energía potencial", "Energía del movimiento", "Energía térmica", "Energía química"], correct: 1, explanation: "La energía cinética es la energía del movimiento", category: "ciencias" },
                { id: 160, question: "¿Cuál es el elemento más abundante en la corteza terrestre?", options: ["Silicio", "Oxígeno", "Aluminio", "Hierro"], correct: 1, explanation: "El Oxígeno es el elemento más abundante en la corteza terrestre", category: "ciencias" },
                { id: 161, question: "¿Qué es la energía potencial?", options: ["Energía del movimiento", "Energía almacenada", "Energía térmica", "Energía química"], correct: 1, explanation: "La energía potencial es energía almacenada", category: "ciencias" },
                { id: 162, question: "¿Cuál es la velocidad del sonido en el aire?", options: ["343 m/s", "443 m/s", "543 m/s", "643 m/s"], correct: 0, explanation: "La velocidad del sonido en el aire es 343 m/s", category: "ciencias" },
                { id: 163, question: "¿Qué es un catalizador?", options: ["Acelera reacción", "Detiene reacción", "Cambia reacción", "Inhibe reacción"], correct: 0, explanation: "Un catalizador acelera una reacción química", category: "ciencias" },
                { id: 164, question: "¿Cuál es la función principal del hígado?", options: ["Digestión", "Detoxificación", "Respiración", "Circulación"], correct: 1, explanation: "El hígado detoxifica el cuerpo", category: "ciencias" },
                { id: 165, question: "¿Qué es la masa?", options: ["Peso", "Cantidad de materia", "Volumen", "Densidad"], correct: 1, explanation: "La masa es la cantidad de materia", category: "ciencias" },
                { id: 166, question: "¿Cuál es el principal componente del aire?", options: ["Oxígeno", "Nitrógeno", "Dióxido de carbono", "Argón"], correct: 1, explanation: "El Nitrógeno es el principal componente del aire", category: "ciencias" },
                { id: 167, question: "¿Qué es la tensión superficial?", options: ["Presión", "Fuerza en superficie", "Densidad", "Viscosidad"], correct: 1, explanation: "La tensión superficial es una fuerza en la superficie de líquidos", category: "ciencias" },
                { id: 168, question: "¿Cuál es la unidad básica de la fuerza?", options: ["Pascal", "Newton", "Julio", "Vatio"], correct: 1, explanation: "El Newton es la unidad básica de fuerza", category: "ciencias" },
                { id: 169, question: "¿Qué es la osmosis?", options: ["Difusión de agua", "Difusión de aire", "Difusión de calor", "Difusión de luz"], correct: 0, explanation: "La osmosis es la difusión de agua a través de una membrana", category: "ciencias" },
                { id: 170, question: "¿Cuál es el metal menos reactivo?", options: ["Oro", "Plata", "Platino", "Paladio"], correct: 0, explanation: "El Oro es el metal menos reactivo", category: "ciencias" },
                { id: 171, question: "¿Qué es la inercia?", options: ["Velocidad", "Resistencia al cambio", "Aceleración", "Momento"], correct: 1, explanation: "La inercia es la resistencia al cambio de movimiento", category: "ciencias" },
                { id: 172, question: "¿Cuál es la unidad básica de la energía?", options: ["Vatio", "Newton", "Julio", "Pascal"], correct: 2, explanation: "El Julio es la unidad básica de energía", category: "ciencias" },
                { id: 173, question: "¿Qué es la difusión?", options: ["Movimiento de partículas", "Presión", "Temperatura", "Densidad"], correct: 0, explanation: "La difusión es el movimiento de partículas de mayor a menor concentración", category: "ciencias" },
                { id: 174, question: "¿Cuál es el ácido del estómago?", options: ["Sulfúrico", "Nítrico", "Clorhídrico", "Acético"], correct: 2, explanation: "El ácido clorhídrico es el ácido del estómago", category: "ciencias" },
                { id: 175, question: "¿Qué es la sublimación?", options: ["Sólido a gas", "Líquido a gas", "Sólido a líquido", "Gas a líquido"], correct: 0, explanation: "La sublimación es el cambio de sólido a gas", category: "ciencias" },
                { id: 176, question: "¿Cuál es la capa más caliente de la Tierra?", options: ["Corteza", "Manto", "Núcleo externo", "Núcleo interno"], correct: 3, explanation: "El núcleo interno es la capa más caliente de la Tierra", category: "ciencias" },
                { id: 177, question: "¿Qué es la condensación?", options: ["Gas a sólido", "Gas a líquido", "Líquido a gas", "Sólido a gas"], correct: 1, explanation: "La condensación es el cambio de gas a líquido", category: "ciencias" },
                { id: 178, question: "¿Cuál es la unidad básica de potencia?", options: ["Julio", "Newton", "Vatio", "Pascal"], correct: 2, explanation: "El Vatio es la unidad básica de potencia", category: "ciencias" },
                { id: 179, question: "¿Qué es la fusión?", options: ["Gas a líquido", "Líquido a gas", "Sólido a líquido", "Gas a sólido"], correct: 2, explanation: "La fusión es el cambio de sólido a líquido", category: "ciencias" },
                { id: 180, question: "¿Cuál es el metal más ligero?", options: ["Sodio", "Litio", "Potasio", "Berilio"], correct: 1, explanation: "El Litio es el metal más ligero", category: "ciencias" },
                { id: 181, question: "¿Qué es la evaporación?", options: ["Sólido a gas", "Líquido a gas", "Gas a líquido", "Sólido a líquido"], correct: 1, explanation: "La evaporación es el cambio de líquido a gas", category: "ciencias" },
                { id: 182, question: "¿Cuál es la unidad básica de presión?", options: ["Newton", "Pascal", "Julio", "Bar"], correct: 1, explanation: "El Pascal es la unidad básica de presión", category: "ciencias" },
                { id: 183, question: "¿Qué es la densidad?", options: ["Masa/Volumen", "Masa/Peso", "Peso/Volumen", "Volumen/Masa"], correct: 0, explanation: "La densidad es masa por unidad de volumen", category: "ciencias" },
                { id: 184, question: "¿Cuál es el gas más ligero?", options: ["Helio", "Hidrógeno", "Neón", "Oxígeno"], correct: 1, explanation: "El Hidrógeno es el gas más ligero", category: "ciencias" },
                { id: 185, question: "¿Qué es la frecuencia?", options: ["Longitud de onda", "Ciclos por segundo", "Amplitud", "Velocidad"], correct: 1, explanation: "La frecuencia es el número de ciclos por segundo", category: "ciencias" },
                { id: 186, question: "¿Cuál es la función principal del páncreas?", options: ["Digestión", "Hormonas", "Ambas", "Ninguna"], correct: 2, explanation: "El páncreas tiene funciones digestivas y hormonales", category: "ciencias" },
                { id: 187, question: "¿Qué es un enlace covalente?", options: ["Compartir electrones", "Transferir electrones", "Sin electrones", "Ganar electrones"], correct: 0, explanation: "Un enlace covalente implica compartir electrones", category: "ciencias" },
                { id: 188, question: "¿Cuál es la unidad básica de intensidad luminosa?", options: ["Lumen", "Candela", "Lux", "Vatio"], correct: 1, explanation: "La Candela es la unidad de intensidad luminosa", category: "ciencias" },
                { id: 189, question: "¿Qué es la refracción?", options: ["Reflexión de luz", "Cambio de dirección", "Absorción de luz", "Emisión de luz"], correct: 1, explanation: "La refracción es el cambio de dirección de la luz", category: "ciencias" },
                { id: 190, question: "¿Cuál es el gas noble más pesado?", options: ["Xenón", "Radón", "Kriptón", "Neón"], correct: 1, explanation: "El Radón es el gas noble más pesado", category: "ciencias" },
                { id: 191, question: "¿Qué es la radiación?", options: ["Conducción", "Convección", "Emisión de energía", "Absorción"], correct: 2, explanation: "La radiación es la emisión de energía", category: "ciencias" },
                { id: 192, question: "¿Cuál es la principal función del sistema inmune?", options: ["Digestión", "Defensa", "Respiración", "Circulación"], correct: 1, explanation: "El sistema inmune defiende al organismo", category: "ciencias" },
                { id: 193, question: "¿Qué es un enlace iónico?", options: ["Compartir electrones", "Transferir electrones", "Sin electrones", "Ganar protones"], correct: 1, explanation: "Un enlace iónico implica transferencia de electrones", category: "ciencias" },
                { id: 194, question: "¿Cuál es la unidad básica de cantidad de sustancia?", options: ["Gramo", "Mol", "Kilogramo", "Litro"], correct: 1, explanation: "El Mol es la unidad de cantidad de sustancia", category: "ciencias" },
                { id: 195, question: "¿Qué es la conductividad?", options: ["Resistencia", "Capacidad de conducir", "Aislamiento", "Impedancia"], correct: 1, explanation: "La conductividad es la capacidad de conducir electricidad o calor", category: "ciencias" },
                { id: 196, question: "¿Cuál es el punto de ebullición del agua?", options: ["90°C", "95°C", "100°C", "105°C"], correct: 2, explanation: "El agua hierve a 100°C a nivel del mar", category: "ciencias" },
                { id: 197, question: "¿Qué es la polaridad?", options: ["Distribución de carga", "Neutralidad", "Conductividad", "Resistencia"], correct: 0, explanation: "La polaridad es la distribución desigual de carga", category: "ciencias" },
                { id: 198, question: "¿Cuál es el punto de fusión del agua?", options: ["0°C", "-5°C", "5°C", "10°C"], correct: 0, explanation: "El agua se congela a 0°C", category: "ciencias" },
                { id: 199, question: "¿Qué es la viscosidad?", options: ["Densidad", "Resistencia al flujo", "Presión", "Temperatura"], correct: 1, explanation: "La viscosidad es la resistencia de un fluido a fluir", category: "ciencias" },
                { id: 200, question: "¿Cuál es la unidad básica de masa?", options: ["Gramo", "Kilogramo", "Libra", "Onza"], correct: 1, explanation: "El Kilogramo es la unidad básica de masa", category: "ciencias" },
                // HISTORIA (201-300)
                { id: 201, question: "¿En qué año comenzó la Primera Guerra Mundial?", options: ["1912", "1913", "1914", "1915"], correct: 2, explanation: "La Primera Guerra Mundial comenzó en 1914", category: "historia" },
                { id: 202, question: "¿Quién fue el primer emperador romano?", options: ["Julio César", "Augusto", "Nerón", "Calígula"], correct: 1, explanation: "Augusto fue el primer emperador romano", category: "historia" },
                { id: 203, question: "¿En qué año se descubrió América?", options: ["1490", "1491", "1492", "1493"], correct: 2, explanation: "América fue descubierta en 1492", category: "historia" },
                { id: 204, question: "¿Quién pintó la Mona Lisa?", options: ["Miguel Ángel", "Leonardo da Vinci", "Rafael", "Donatello"], correct: 1, explanation: "Leonardo da Vinci pintó la Mona Lisa", category: "historia" },
                { id: 205, question: "¿En qué año terminó la Segunda Guerra Mundial?", options: ["1944", "1945", "1946", "1947"], correct: 1, explanation: "La Segunda Guerra Mundial terminó en 1945", category: "historia" },
                { id: 206, question: "¿Cuál fue la primera civilización de la historia?", options: ["Egipcia", "Sumeria", "Griega", "China"], correct: 1, explanation: "La civilización Sumeria fue la primera", category: "historia" },
                { id: 207, question: "¿En qué año cayó el Muro de Berlín?", options: ["1987", "1988", "1989", "1990"], correct: 2, explanation: "El Muro de Berlín cayó en 1989", category: "historia" },
                { id: 208, question: "¿Quién fue el primer presidente de Estados Unidos?", options: ["John Adams", "Thomas Jefferson", "George Washington", "Benjamin Franklin"], correct: 2, explanation: "George Washington fue el primer presidente", category: "historia" },
                { id: 209, question: "¿En qué año comenzó la Revolución Francesa?", options: ["1787", "1788", "1789", "1790"], correct: 2, explanation: "La Revolución Francesa comenzó en 1789", category: "historia" },
                { id: 210, question: "¿Quién fue Cleopatra?", options: ["Reina de Grecia", "Reina de Egipto", "Reina de Roma", "Reina de Persia"], correct: 1, explanation: "Cleopatra fue la última reina del Antiguo Egipto", category: "historia" },
                { id: 211, question: "¿En qué año se independizó México?", options: ["1810", "1821", "1830", "1835"], correct: 1, explanation: "México se independizó en 1821", category: "historia" },
                { id: 212, question: "¿Quién fue Napoleón Bonaparte?", options: ["General italiano", "Emperador francés", "Rey español", "General inglés"], correct: 1, explanation: "Napoleón fue emperador de Francia", category: "historia" },
                { id: 213, question: "¿En qué año comenzó la Revolución Industrial?", options: ["1750", "1760", "1770", "1780"], correct: 1, explanation: "La Revolución Industrial comenzó alrededor de 1760", category: "historia" },
                { id: 214, question: "¿Quién fue William Shakespeare?", options: ["Músico", "Dramaturgo", "Pintor", "Científico"], correct: 1, explanation: "Shakespeare fue un famoso dramaturgo inglés", category: "historia" },
                { id: 215, question: "¿En qué año se fundó la ONU?", options: ["1943", "1944", "1945", "1946"], correct: 2, explanation: "La ONU se fundó en 1945", category: "historia" },
                { id: 216, question: "¿Quién fue Martin Luther King Jr.?", options: ["Político", "Activista civil", "Músico", "Deportista"], correct: 1, explanation: "Fue un líder del movimiento por los derechos civiles", category: "historia" },
                { id: 217, question: "¿En qué año llegó el hombre a la Luna?", options: ["1967", "1968", "1969", "1970"], correct: 2, explanation: "El primer alunizaje fue en 1969", category: "historia" },
                { id: 218, question: "¿Quién fue Alexander Graham Bell?", options: ["Inventor del teléfono", "Inventor de la radio", "Inventor del avión", "Inventor del auto"], correct: 0, explanation: "Bell inventó el teléfono", category: "historia" },
                { id: 219, question: "¿En qué año terminó la Guerra Fría?", options: ["1989", "1990", "1991", "1992"], correct: 2, explanation: "La Guerra Fría terminó en 1991", category: "historia" },
                { id: 220, question: "¿Quién fue Nelson Mandela?", options: ["Músico africano", "Presidente sudafricano", "Deportista", "Escritor"], correct: 1, explanation: "Mandela fue presidente de Sudáfrica", category: "historia" },
                { id: 221, question: "¿En qué año comenzó la Guerra Civil Española?", options: ["1935", "1936", "1937", "1938"], correct: 1, explanation: "La Guerra Civil Española comenzó en 1936", category: "historia" },
                { id: 222, question: "¿Quién fue Marie Curie?", options: ["Escritora", "Científica", "Pintora", "Política"], correct: 1, explanation: "Marie Curie fue una científica pionera", category: "historia" },
                { id: 223, question: "¿En qué año se creó la Unión Europea?", options: ["1991", "1992", "1993", "1994"], correct: 2, explanation: "La UE se creó en 1993", category: "historia" },
                { id: 224, question: "¿Quién fue Albert Einstein?", options: ["Músico", "Físico", "Pintor", "Escritor"], correct: 1, explanation: "Einstein fue un físico teórico", category: "historia" },
                { id: 225, question: "¿En qué año terminó la Guerra de Vietnam?", options: ["1973", "1974", "1975", "1976"], correct: 2, explanation: "La Guerra de Vietnam terminó en 1975", category: "historia" },
                { id: 226, question: "¿Quién fue Mahatma Gandhi?", options: ["Líder pacifista", "Rey indio", "Militar", "Empresario"], correct: 0, explanation: "Gandhi fue un líder pacifista indio", category: "historia" },
                { id: 227, question: "¿En qué año se fundó la UNESCO?", options: ["1944", "1945", "1946", "1947"], correct: 1, explanation: "La UNESCO se fundó en 1945", category: "historia" },
                { id: 228, question: "¿Quién fue Ludwig van Beethoven?", options: ["Pintor", "Escritor", "Compositor", "Científico"], correct: 2, explanation: "Beethoven fue un compositor alemán", category: "historia" },
                { id: 229, question: "¿En qué año comenzó la Guerra de los Cien Años?", options: ["1337", "1347", "1357", "1367"], correct: 0, explanation: "La Guerra de los Cien Años comenzó en 1337", category: "historia" },
                { id: 230, question: "¿Quién fue Isaac Newton?", options: ["Músico", "Físico", "Pintor", "Poeta"], correct: 1, explanation: "Newton fue un físico y matemático", category: "historia" },
                { id: 231, question: "¿En qué año se firmó la Declaración de Independencia de EE.UU.?", options: ["1774", "1775", "1776", "1777"], correct: 2, explanation: "La Declaración se firmó en 1776", category: "historia" },
                { id: 232, question: "¿Quién fue Leonardo da Vinci?", options: ["Músico", "Artista polímata", "Escritor", "Rey"], correct: 1, explanation: "Da Vinci fue un artista y científico polímata", category: "historia" },
                { id: 233, question: "¿En qué año comenzó la Revolución Rusa?", options: ["1915", "1916", "1917", "1918"], correct: 2, explanation: "La Revolución Rusa comenzó en 1917", category: "historia" },
                { id: 234, question: "¿Quién fue Charles Darwin?", options: ["Físico", "Naturalista", "Químico", "Matemático"], correct: 1, explanation: "Darwin fue un naturalista británico", category: "historia" },
                { id: 235, question: "¿En qué año se inventó la imprenta?", options: ["1440", "1450", "1460", "1470"], correct: 0, explanation: "Gutenberg inventó la imprenta moderna hacia 1440", category: "historia" },
                { id: 236, question: "¿Quién fue Winston Churchill?", options: ["Primer Ministro británico", "General francés", "Presidente americano", "Rey inglés"], correct: 0, explanation: "Churchill fue Primer Ministro británico", category: "historia" },
                { id: 237, question: "¿En qué año comenzó la Guerra Civil Americana?", options: ["1859", "1860", "1861", "1862"], correct: 2, explanation: "La Guerra Civil Americana comenzó en 1861", category: "historia" },
                { id: 238, question: "¿Quién fue Pablo Picasso?", options: ["Músico", "Pintor", "Escritor", "Científico"], correct: 1, explanation: "Picasso fue un pintor español", category: "historia" },
                { id: 239, question: "¿En qué año se fundó la Cruz Roja?", options: ["1861", "1863", "1865", "1867"], correct: 1, explanation: "La Cruz Roja se fundó en 1863", category: "historia" },
                { id: 240, question: "¿Quién fue Thomas Edison?", options: ["Inventor", "Político", "Escritor", "Médico"], correct: 0, explanation: "Edison fue un prolífico inventor", category: "historia" },
                { id: 241, question: "¿En qué año comenzó la Revolución Mexicana?", options: ["1908", "1909", "1910", "1911"], correct: 2, explanation: "La Revolución Mexicana comenzó en 1910", category: "historia" },
                { id: 242, question: "¿Quién fue Aristóteles?", options: ["Matemático", "Filósofo", "General", "Poeta"], correct: 1, explanation: "Aristóteles fue un filósofo griego", category: "historia" },
                { id: 243, question: "¿En qué año se fundó la FIFA?", options: ["1902", "1904", "1906", "1908"], correct: 1, explanation: "La FIFA se fundó en 1904", category: "historia" },
                { id: 244, question: "¿Quién fue Vincent van Gogh?", options: ["Escritor", "Pintor", "Músico", "Científico"], correct: 1, explanation: "Van Gogh fue un pintor post-impresionista", category: "historia" },
                { id: 245, question: "¿En qué año se inventó la televisión?", options: ["1925", "1927", "1929", "1931"], correct: 1, explanation: "La televisión fue inventada en 1927", category: "historia" },
                { id: 246, question: "¿Quién fue Sigmund Freud?", options: ["Psicólogo", "Físico", "Químico", "Pintor"], correct: 0, explanation: "Freud fue el padre del psicoanálisis", category: "historia" },
                { id: 247, question: "¿En qué año se fundó Microsoft?", options: ["1973", "1974", "1975", "1976"], correct: 2, explanation: "Microsoft fue fundada en 1975", category: "historia" },
                { id: 248, question: "¿Quién fue Wolfgang Amadeus Mozart?", options: ["Pintor", "Escritor", "Compositor", "Científico"], correct: 2, explanation: "Mozart fue un compositor austriaco", category: "historia" },
                { id: 249, question: "¿En qué año se fundó la OMS?", options: ["1946", "1947", "1948", "1949"], correct: 2, explanation: "La OMS se fundó en 1948", category: "historia" },
                { id: 250, question: "¿Quién fue Marco Polo?", options: ["Explorador", "Rey", "Científico", "Pintor"], correct: 0, explanation: "Marco Polo fue un explorador veneciano", category: "historia" },
                { id: 251, question: "¿En qué año se inventó Internet?", options: ["1967", "1969", "1971", "1973"], correct: 1, explanation: "Internet fue inventado en 1969 (ARPANET)", category: "historia" },
                { id: 252, question: "¿Quién fue Miguel de Cervantes?", options: ["Pintor", "Escritor", "Músico", "Científico"], correct: 1, explanation: "Cervantes fue un escritor español", category: "historia" },
                { id: 253, question: "¿En qué año comenzó la Guerra de Corea?", options: ["1948", "1949", "1950", "1951"], correct: 2, explanation: "La Guerra de Corea comenzó en 1950", category: "historia" },
                { id: 254, question: "¿Quién fue Galileo Galilei?", options: ["Pintor", "Músico", "Científico", "Poeta"], correct: 2, explanation: "Galileo fue un científico italiano", category: "historia" },
                { id: 255, question: "¿En qué año se fundó Apple?", options: ["1974", "1975", "1976", "1977"], correct: 2, explanation: "Apple fue fundada en 1976", category: "historia" },
                { id: 256, question: "¿Quién fue Louis Pasteur?", options: ["Químico", "Físico", "Biólogo", "Matemático"], correct: 0, explanation: "Pasteur fue un químico y microbiólogo", category: "historia" },
                { id: 257, question: "¿En qué año se firmó el Tratado de Versalles?", options: ["1917", "1918", "1919", "1920"], correct: 2, explanation: "El Tratado de Versalles se firmó en 1919", category: "historia" },
                { id: 258, question: "¿Quién fue Friedrich Nietzsche?", options: ["Científico", "Filósofo", "Músico", "Pintor"], correct: 1, explanation: "Nietzsche fue un filósofo alemán", category: "historia" },
                { id: 259, question: "¿En qué año se creó la OTAN?", options: ["1947", "1948", "1949", "1950"], correct: 2, explanation: "La OTAN se creó en 1949", category: "historia" },
                { id: 260, question: "¿Quién fue Johannes Gutenberg?", options: ["Inventor", "Pintor", "Músico", "Escritor"], correct: 0, explanation: "Gutenberg inventó la imprenta moderna", category: "historia" },
                { id: 261, question: "¿En qué año comenzó la Guerra Fría?", options: ["1945", "1946", "1947", "1948"], correct: 2, explanation: "La Guerra Fría comenzó en 1947", category: "historia" },
                { id: 262, question: "¿Quién fue Franz Kafka?", options: ["Músico", "Escritor", "Pintor", "Científico"], correct: 1, explanation: "Kafka fue un escritor en lengua alemana", category: "historia" },
                { id: 263, question: "¿En qué año se construyó el Muro de Berlín?", options: ["1959", "1960", "1961", "1962"], correct: 2, explanation: "El Muro de Berlín se construyó en 1961", category: "historia" },
                { id: 264, question: "¿Quién fue Mary Curie?", options: ["Física", "Pintora", "Escritora", "Música"], correct: 0, explanation: "Marie Curie fue una física y química", category: "historia" },
                { id: 265, question: "¿En qué año se produjo la Revolución Cubana?", options: ["1957", "1958", "1959", "1960"], correct: 2, explanation: "La Revolución Cubana triunfó en 1959", category: "historia" },
                { id: 266, question: "¿Quién fue Charlie Chaplin?", options: ["Músico", "Actor", "Pintor", "Escritor"], correct: 1, explanation: "Chaplin fue un actor y director de cine", category: "historia" },
                { id: 267, question: "¿En qué año se fundó Google?", options: ["1996", "1997", "1998", "1999"], correct: 2, explanation: "Google fue fundada en 1998", category: "historia" },
                { id: 268, question: "¿Quién fue Karl Marx?", options: ["Científico", "Filósofo", "Músico", "Pintor"], correct: 1, explanation: "Marx fue un filósofo y economista", category: "historia" },
                { id: 269, question: "¿En qué año se fundó Twitter?", options: ["2004", "2005", "2006", "2007"], correct: 2, explanation: "Twitter fue fundada en 2006", category: "historia" },
                { id: 270, question: "¿Quién fue Walt Disney?", options: ["Empresario", "Científico", "Político", "Deportista"], correct: 0, explanation: "Disney fue un empresario y animador", category: "historia" },
                { id: 271, question: "¿En qué año se fundó Facebook?", options: ["2002", "2003", "2004", "2005"], correct: 2, explanation: "Facebook fue fundada en 2004", category: "historia" },
                { id: 272, question: "¿Quién fue Alfred Nobel?", options: ["Químico", "Físico", "Matemático", "Biólogo"], correct: 0, explanation: "Nobel fue un químico e inventor", category: "historia" },
                { id: 273, question: "¿En qué año se inventó el teléfono?", options: ["1874", "1875", "1876", "1877"], correct: 2, explanation: "Bell patentó el teléfono en 1876", category: "historia" },
                { id: 274, question: "¿Quién fue Virginia Woolf?", options: ["Pintora", "Escritora", "Música", "Científica"], correct: 1, explanation: "Woolf fue una escritora británica", category: "historia" },
                { id: 275, question: "¿En qué año se inventó la radio?", options: ["1893", "1895", "1897", "1899"], correct: 1, explanation: "Marconi inventó la radio en 1895", category: "historia" },
                { id: 276, question: "¿Quién fue Steve Jobs?", options: ["Empresario", "Científico", "Político", "Artista"], correct: 0, explanation: "Jobs fue cofundador de Apple", category: "historia" },
                { id: 277, question: "¿En qué año se inventó el automóvil?", options: ["1884", "1885", "1886", "1887"], correct: 2, explanation: "Benz patentó el primer automóvil en 1886", category: "historia" },
                { id: 278, question: "¿Quién fue Ernest Hemingway?", options: ["Pintor", "Escritor", "Músico", "Científico"], correct: 1, explanation: "Hemingway fue un escritor estadounidense", category: "historia" },
                { id: 279, question: "¿En qué año se inventó la bombilla?", options: ["1877", "1878", "1879", "1880"], correct: 2, explanation: "Edison patentó la bombilla en 1879", category: "historia" },
                { id: 280, question: "¿Quién fue Salvador Dalí?", options: ["Músico", "Pintor", "Escritor", "Científico"], correct: 1, explanation: "Dalí fue un pintor surrealista", category: "historia" },
                { id: 281, question: "¿En qué año comenzó la Guerra del Golfo?", options: ["1989", "1990", "1991", "1992"], correct: 1, explanation: "La Guerra del Golfo comenzó en 1990", category: "historia" },
                { id: 282, question: "¿Quién fue Florence Nightingale?", options: ["Enfermera", "Pintora", "Escritora", "Científica"], correct: 0, explanation: "Nightingale fue pionera de la enfermería", category: "historia" },
                { id: 283, question: "¿En qué año se fundó la NASA?", options: ["1956", "1957", "1958", "1959"], correct: 2, explanation: "La NASA se fundó en 1958", category: "historia" },
                { id: 284, question: "¿Quién fue Frida Kahlo?", options: ["Escritora", "Pintora", "Música", "Científica"], correct: 1, explanation: "Kahlo fue una pintora mexicana", category: "historia" },
                { id: 285, question: "¿En qué año se inventó el avión?", options: ["1901", "1902", "1903", "1904"], correct: 2, explanation: "Los hermanos Wright volaron en 1903", category: "historia" },
                { id: 286, question: "¿Quién fue Johann Sebastian Bach?", options: ["Pintor", "Escritor", "Compositor", "Científico"], correct: 2, explanation: "Bach fue un compositor alemán", category: "historia" },
                { id: 287, question: "¿En qué año se creó la World Wide Web?", options: ["1989", "1990", "1991", "1992"], correct: 1, explanation: "La WWW fue creada en 1990", category: "historia" },
                { id: 288, question: "¿Quién fue Alan Turing?", options: ["Matemático", "Pintor", "Músico", "Escritor"], correct: 0, explanation: "Turing fue un matemático y científico", category: "historia" },
                { id: 289, question: "¿En qué año se fundó Amazon?", options: ["1992", "1993", "1994", "1995"], correct: 2, explanation: "Amazon fue fundada en 1994", category: "historia" },
                { id: 290, question: "¿Quién fue George Orwell?", options: ["Músico", "Escritor", "Pintor", "Científico"], correct: 1, explanation: "Orwell fue un escritor británico", category: "historia" },
                { id: 291, question: "¿En qué año se lanzó el primer iPhone?", options: ["2005", "2006", "2007", "2008"], correct: 2, explanation: "El primer iPhone se lanzó en 2007", category: "historia" },
                { id: 292, question: "¿Quién fue Antoine de Saint-Exupéry?", options: ["Pintor", "Escritor", "Músico", "Científico"], correct: 1, explanation: "Saint-Exupéry fue un escritor francés", category: "historia" },
                { id: 293, question: "¿En qué año se fundó Netflix?", options: ["1995", "1996", "1997", "1998"], correct: 2, explanation: "Netflix fue fundada en 1997", category: "historia" },
                { id: 294, question: "¿Quién fue Stephen Hawking?", options: ["Químico", "Físico", "Biólogo", "Matemático"], correct: 1, explanation: "Hawking fue un físico teórico", category: "historia" },
                { id: 295, question: "¿En qué año se fundó YouTube?", options: ["2003", "2004", "2005", "2006"], correct: 2, explanation: "YouTube fue fundado en 2005", category: "historia" },
                { id: 296, question: "¿Quién fue Andy Warhol?", options: ["Músico", "Artista", "Escritor", "Científico"], correct: 1, explanation: "Warhol fue un artista pop", category: "historia" },
                { id: 297, question: "¿En qué año se lanzó Android?", options: ["2006", "2007", "2008", "2009"], correct: 2, explanation: "Android se lanzó en 2008", category: "historia" },
                { id: 298, question: "¿Quién fue Grace Hopper?", options: ["Científica", "Pintora", "Escritora", "Música"], correct: 0, explanation: "Hopper fue una científica computacional", category: "historia" },
                { id: 299, question: "¿En qué año se fundó Instagram?", options: ["2008", "2009", "2010", "2011"], correct: 2, explanation: "Instagram fue fundado en 2010", category: "historia" },
                { id: 300, question: "¿Quién fue Bill Gates?", options: ["Empresario", "Científico", "Artista", "Político"], correct: 0, explanation: "Gates es cofundador de Microsoft", category: "historia" },
                // GEOGRAFÍA (301-400)
                { id: 301, question: "¿Cuál es la capital de Francia?", options: ["Londres", "París", "Madrid", "Roma"], correct: 1, explanation: "La capital de Francia es París", category: "geografia" },
                { id: 302, question: "¿Cuál es el río más largo del mundo?", options: ["Nilo", "Amazonas", "Misisipi", "Yangtsé"], correct: 1, explanation: "El río Amazonas es el más largo del mundo", category: "geografia" },
                { id: 303, question: "¿En qué continente está Egipto?", options: ["Asia", "Europa", "África", "América"], correct: 2, explanation: "Egipto está en África", category: "geografia" },
                { id: 304, question: "¿Cuál es el océano más grande?", options: ["Atlántico", "Índico", "Pacífico", "Ártico"], correct: 2, explanation: "El océano Pacífico es el más grande", category: "geografia" },
                { id: 305, question: "¿Cuál es el país más poblado del mundo?", options: ["India", "China", "EE.UU.", "Indonesia"], correct: 0, explanation: "India es el país más poblado del mundo", category: "geografia" },
                { id: 306, question: "¿Dónde está la Selva Negra?", options: ["Francia", "Alemania", "Suiza", "Austria"], correct: 1, explanation: "La Selva Negra está en Alemania", category: "geografia" },
                { id: 307, question: "¿Cuál es la capital de Japón?", options: ["Seúl", "Pekín", "Tokio", "Bangkok"], correct: 2, explanation: "La capital de Japón es Tokio", category: "geografia" },
                { id: 308, question: "¿En qué país está el Taj Mahal?", options: ["India", "Pakistán", "Nepal", "Bangladesh"], correct: 0, explanation: "El Taj Mahal está en India", category: "geografia" },
                { id: 309, question: "¿Cuál es el desierto más grande del mundo?", options: ["Gobi", "Sahara", "Atacama", "Antártida"], correct: 1, explanation: "El Sahara es el desierto más grande", category: "geografia" },
                { id: 310, question: "¿En qué continente está Australia?", options: ["Asia", "Europa", "Oceanía", "América"], correct: 2, explanation: "Australia está en Oceanía", category: "geografia" },
                { id: 311, question: "¿Cuál es la capital de España?", options: ["Barcelona", "Madrid", "Valencia", "Sevilla"], correct: 1, explanation: "La capital de España es Madrid", category: "geografia" },
                { id: 312, question: "¿Qué país tiene forma de bota?", options: ["Francia", "España", "Italia", "Grecia"], correct: 2, explanation: "Italia tiene forma de bota", category: "geografia" },
                { id: 313, question: "¿Dónde está la Torre Eiffel?", options: ["Londres", "París", "Berlín", "Roma"], correct: 1, explanation: "La Torre Eiffel está en París", category: "geografia" },
                { id: 314, question: "¿Cuál es la capital de China?", options: ["Shanghái", "Hong Kong", "Pekín", "Cantón"], correct: 2, explanation: "La capital de China es Pekín", category: "geografia" },
                { id: 315, question: "¿En qué continente está México?", options: ["América del Norte", "América del Sur", "América Central", "Europa"], correct: 0, explanation: "México está en América del Norte", category: "geografia" },
                { id: 316, question: "¿Cuál es la montaña más alta del mundo?", options: ["K2", "Everest", "Aconcagua", "Mont Blanc"], correct: 1, explanation: "El Monte Everest es la montaña más alta", category: "geografia" },
                { id: 317, question: "¿Dónde están las pirámides de Giza?", options: ["Sudán", "Egipto", "Libia", "Marruecos"], correct: 1, explanation: "Las pirámides están en Egipto", category: "geografia" },
                { id: 318, question: "¿Cuál es la capital de Brasil?", options: ["Río de Janeiro", "São Paulo", "Brasilia", "Salvador"], correct: 2, explanation: "La capital de Brasil es Brasilia", category: "geografia" },
                { id: 319, question: "¿En qué país está el Big Ben?", options: ["Francia", "Alemania", "Reino Unido", "Italia"], correct: 2, explanation: "El Big Ben está en Reino Unido", category: "geografia" },
                { id: 320, question: "¿Cuál es el país más grande del mundo?", options: ["China", "EE.UU.", "Canadá", "Rusia"], correct: 3, explanation: "Rusia es el país más grande del mundo", category: "geografia" },
                { id: 321, question: "¿Dónde está la Gran Muralla China?", options: ["Japón", "China", "Mongolia", "Corea"], correct: 1, explanation: "La Gran Muralla está en China", category: "geografia" },
                { id: 322, question: "¿Cuál es la capital de Argentina?", options: ["Buenos Aires", "Santiago", "Montevideo", "Lima"], correct: 0, explanation: "La capital de Argentina es Buenos Aires", category: "geografia" },
                { id: 323, question: "¿En qué océano está Hawaii?", options: ["Atlántico", "Índico", "Pacífico", "Ártico"], correct: 2, explanation: "Hawaii está en el océano Pacífico", category: "geografia" },
                { id: 324, question: "¿Cuál es la capital de Rusia?", options: ["Kiev", "Minsk", "Moscú", "San Petersburgo"], correct: 2, explanation: "La capital de Rusia es Moscú", category: "geografia" },
                { id: 325, question: "¿En qué país está el Coliseo Romano?", options: ["Grecia", "España", "Francia", "Italia"], correct: 3, explanation: "El Coliseo está en Italia", category: "geografia" },
                { id: 326, question: "¿Cuál es el lago más profundo del mundo?", options: ["Baikal", "Victoria", "Superior", "Tanganica"], correct: 0, explanation: "El lago Baikal es el más profundo", category: "geografia" },
                { id: 327, question: "¿Dónde está Machu Picchu?", options: ["Colombia", "Perú", "Bolivia", "Ecuador"], correct: 1, explanation: "Machu Picchu está en Perú", category: "geografia" },
                { id: 328, question: "¿Cuál es la capital de Canadá?", options: ["Toronto", "Montreal", "Ottawa", "Vancouver"], correct: 2, explanation: "La capital de Canadá es Ottawa", category: "geografia" },
                { id: 329, question: "¿En qué continente está India?", options: ["Asia", "África", "Europa", "Oceanía"], correct: 0, explanation: "India está en Asia", category: "geografia" },
                { id: 330, question: "¿Cuál es el país más pequeño del mundo?", options: ["Mónaco", "San Marino", "Vaticano", "Liechtenstein"], correct: 2, explanation: "El Vaticano es el país más pequeño", category: "geografia" },
                { id: 331, question: "¿Dónde está la Estatua de la Libertad?", options: ["Washington", "Nueva York", "Boston", "Chicago"], correct: 1, explanation: "La Estatua está en Nueva York", category: "geografia" },
                { id: 332, question: "¿Cuál es la capital de Portugal?", options: ["Oporto", "Lisboa", "Faro", "Coímbra"], correct: 1, explanation: "La capital de Portugal es Lisboa", category: "geografia" },
                { id: 333, question: "¿En qué país está el Monte Fuji?", options: ["China", "Corea", "Japón", "Tailandia"], correct: 2, explanation: "El Monte Fuji está en Japón", category: "geografia" },
                { id: 334, question: "¿Cuál es la capital de México?", options: ["Guadalajara", "Monterrey", "Ciudad de México", "Cancún"], correct: 2, explanation: "La capital es Ciudad de México", category: "geografia" },
                { id: 335, question: "¿En qué continente está Sudáfrica?", options: ["Asia", "Europa", "África", "Oceanía"], correct: 2, explanation: "Sudáfrica está en África", category: "geografia" },
                { id: 336, question: "¿Dónde está el Canal de Suez?", options: ["Egipto", "Panamá", "Turquía", "Grecia"], correct: 0, explanation: "El Canal de Suez está en Egipto", category: "geografia" },
                { id: 337, question: "¿Cuál es la capital de Australia?", options: ["Sídney", "Melbourne", "Canberra", "Brisbane"], correct: 2, explanation: "La capital de Australia es Canberra", category: "geografia" },
                { id: 338, question: "¿En qué país está Ámsterdam?", options: ["Bélgica", "Alemania", "Países Bajos", "Dinamarca"], correct: 2, explanation: "Ámsterdam está en los Países Bajos", category: "geografia" },
                { id: 339, question: "¿Cuál es el río más largo de Europa?", options: ["Danubio", "Volga", "Rin", "Támesis"], correct: 1, explanation: "El Volga es el río más largo de Europa", category: "geografia" },
                { id: 340, question: "¿En qué país está el Kremlin?", options: ["Polonia", "Ucrania", "Rusia", "Bielorrusia"], correct: 2, explanation: "El Kremlin está en Rusia", category: "geografia" },
                { id: 341, question: "¿Cuál es la capital de Egipto?", options: ["El Cairo", "Alejandría", "Luxor", "Guiza"], correct: 0, explanation: "La capital de Egipto es El Cairo", category: "geografia" },
                { id: 342, question: "¿Dónde están las Cataratas del Niágara?", options: ["EE.UU./Canadá", "Brasil/Argentina", "Venezuela", "México"], correct: 0, explanation: "Las Cataratas están entre EE.UU. y Canadá", category: "geografia" },
                { id: 343, question: "¿Cuál es la capital de Suecia?", options: ["Oslo", "Copenhague", "Estocolmo", "Helsinki"], correct: 2, explanation: "La capital de Suecia es Estocolmo", category: "geografia" },
                { id: 344, question: "¿En qué país está el Partenón?", options: ["Italia", "Grecia", "Turquía", "Egipto"], correct: 1, explanation: "El Partenón está en Grecia", category: "geografia" },
                { id: 345, question: "¿Cuál es el estrecho entre España y África?", options: ["Bósforo", "Gibraltar", "Dardanelos", "Mesina"], correct: 1, explanation: "Es el Estrecho de Gibraltar", category: "geografia" },
                { id: 346, question: "¿Dónde está la ciudad de Petra?", options: ["Siria", "Jordania", "Líbano", "Israel"], correct: 1, explanation: "Petra está en Jordania", category: "geografia" },
                { id: 347, question: "¿Cuál es la capital de Sudáfrica?", options: ["Pretoria", "Ciudad del Cabo", "Johannesburgo", "Todas"], correct: 0, explanation: "Pretoria es la capital administrativa", category: "geografia" },
                { id: 348, question: "¿En qué país está el Kilimanjaro?", options: ["Kenia", "Tanzania", "Uganda", "Etiopía"], correct: 1, explanation: "El Kilimanjaro está en Tanzania", category: "geografia" },
                { id: 349, question: "¿Cuál es la cordillera más larga del mundo?", options: ["Himalaya", "Andes", "Montañas Rocosas", "Alpes"], correct: 1, explanation: "Los Andes son la cordillera más larga", category: "geografia" },
                { id: 350, question: "¿En qué país está Angkor Wat?", options: ["Tailandia", "Vietnam", "Camboya", "Laos"], correct: 2, explanation: "Angkor Wat está en Camboya", category: "geografia" },
                { id: 351, question: "¿Cuál es la capital de Turquía?", options: ["Estambul", "Ankara", "Esmirna", "Bursa"], correct: 1, explanation: "La capital de Turquía es Ankara", category: "geografia" },
                { id: 352, question: "¿Dónde está el Mar Muerto?", options: ["Israel/Jordania", "Egipto", "Siria", "Líbano"], correct: 0, explanation: "El Mar Muerto está entre Israel y Jordania", category: "geografia" },
                { id: 353, question: "¿Cuál es la capital de Vietnam?", options: ["Ho Chi Minh", "Hanói", "Da Nang", "Hue"], correct: 1, explanation: "La capital de Vietnam es Hanói", category: "geografia" },
                { id: 354, question: "¿En qué océano están las Maldivas?", options: ["Pacífico", "Atlántico", "Índico", "Ártico"], correct: 2, explanation: "Las Maldivas están en el Océano Índico", category: "geografia" },
                { id: 355, question: "¿Cuál es el lago más grande de América?", options: ["Superior", "Michigan", "Huron", "Ontario"], correct: 0, explanation: "El Lago Superior es el más grande", category: "geografia" },
                { id: 356, question: "¿Dónde está la Acrópolis?", options: ["Roma", "Atenas", "Esparta", "Tebas"], correct: 1, explanation: "La Acrópolis está en Atenas", category: "geografia" },
                { id: 357, question: "¿Cuál es la capital de Marruecos?", options: ["Casablanca", "Rabat", "Marrakech", "Tánger"], correct: 1, explanation: "La capital de Marruecos es Rabat", category: "geografia" },
                { id: 358, question: "¿En qué país está la ciudad de Petra?", options: ["Egipto", "Jordania", "Siria", "Irak"], correct: 1, explanation: "Petra está en Jordania", category: "geografia" },
                { id: 359, question: "¿Cuál es el punto más bajo de la Tierra?", options: ["Mar Muerto", "Valle de la Muerte", "Depresión del Danakil", "Mar Caspio"], correct: 0, explanation: "El Mar Muerto es el punto más bajo", category: "geografia" },
                { id: 360, question: "¿En qué país está el Monte Olimpo?", options: ["Italia", "Grecia", "Turquía", "Chipre"], correct: 1, explanation: "El Monte Olimpo está en Grecia", category: "geografia" },
                { id: 361, question: "¿Cuál es la capital de Colombia?", options: ["Medellín", "Bogotá", "Cali", "Cartagena"], correct: 1, explanation: "La capital de Colombia es Bogotá", category: "geografia" },
                { id: 362, question: "¿Dónde está el Lago Titicaca?", options: ["Perú/Bolivia", "Chile/Argentina", "Ecuador/Colombia", "Brasil/Paraguay"], correct: 0, explanation: "El Titicaca está entre Perú y Bolivia", category: "geografia" },
                { id: 363, question: "¿Cuál es la capital de Irlanda?", options: ["Belfast", "Cork", "Dublín", "Galway"], correct: 2, explanation: "La capital de Irlanda es Dublín", category: "geografia" },
                { id: 364, question: "¿En qué continente está Madagascar?", options: ["Asia", "África", "Oceanía", "Europa"], correct: 1, explanation: "Madagascar está en África", category: "geografia" },
                { id: 365, question: "¿Cuál es el río más largo de España?", options: ["Ebro", "Tajo", "Duero", "Guadiana"], correct: 1, explanation: "El Tajo es el río más largo de España", category: "geografia" },
                { id: 366, question: "¿Dónde está la Plaza Roja?", options: ["San Petersburgo", "Kiev", "Moscú", "Varsovia"], correct: 2, explanation: "La Plaza Roja está en Moscú", category: "geografia" },
                { id: 367, question: "¿Cuál es la capital de Nueva Zelanda?", options: ["Auckland", "Wellington", "Christchurch", "Hamilton"], correct: 1, explanation: "La capital es Wellington", category: "geografia" },
                { id: 368, question: "¿En qué país está el Monte Aconcagua?", options: ["Chile", "Argentina", "Perú", "Bolivia"], correct: 1, explanation: "El Aconcagua está en Argentina", category: "geografia" },
                { id: 369, question: "¿Cuál es la capital de Grecia?", options: ["Salónica", "Atenas", "Patras", "Heraklion"], correct: 1, explanation: "La capital de Grecia es Atenas", category: "geografia" },
                { id: 370, question: "¿Dónde está la Gran Barrera de Coral?", options: ["Indonesia", "Filipinas", "Australia", "Maldivas"], correct: 2, explanation: "La Gran Barrera está en Australia", category: "geografia" },
                { id: 371, question: "¿Cuál es la capital de Cuba?", options: ["Santiago", "La Habana", "Varadero", "Cienfuegos"], correct: 1, explanation: "La capital de Cuba es La Habana", category: "geografia" },
                { id: 372, question: "¿En qué país está el Valle de los Reyes?", options: ["Jordania", "Israel", "Egipto", "Irak"], correct: 2, explanation: "El Valle de los Reyes está en Egipto", category: "geografia" },
                { id: 373, question: "¿Cuál es la capital de Noruega?", options: ["Bergen", "Oslo", "Trondheim", "Stavanger"], correct: 1, explanation: "La capital de Noruega es Oslo", category: "geografia" },
                { id: 374, question: "¿En qué mar está Chipre?", options: ["Negro", "Mediterráneo", "Rojo", "Egeo"], correct: 1, explanation: "Chipre está en el Mar Mediterráneo", category: "geografia" },
                { id: 375, question: "¿Cuál es el volcán más alto de Europa?", options: ["Vesubio", "Etna", "Stromboli", "Vulcano"], correct: 1, explanation: "El Etna es el volcán más alto de Europa", category: "geografia" },
                { id: 376, question: "¿Dónde está el Palacio de Versalles?", options: ["París", "Lyon", "Marsella", "Niza"], correct: 0, explanation: "El Palacio está cerca de París", category: "geografia" },
                { id: 377, question: "¿Cuál es la capital de Chile?", options: ["Valparaíso", "Santiago", "Concepción", "Viña del Mar"], correct: 1, explanation: "La capital de Chile es Santiago", category: "geografia" },
                { id: 378, question: "¿En qué país está el río Danubio?", options: ["Varios", "Alemania", "Austria", "Hungría"], correct: 0, explanation: "El Danubio atraviesa varios países europeos", category: "geografia" },
                { id: 379, question: "¿Cuál es la capital de Dinamarca?", options: ["Oslo", "Estocolmo", "Copenhague", "Helsinki"], correct: 2, explanation: "La capital de Dinamarca es Copenhague", category: "geografia" },
                { id: 380, question: "¿Dónde está el Cabo de Buena Esperanza?", options: ["Namibia", "Mozambique", "Sudáfrica", "Angola"], correct: 2, explanation: "El Cabo está en Sudáfrica", category: "geografia" },
                { id: 381, question: "¿Cuál es la capital de Perú?", options: ["Cusco", "Lima", "Arequipa", "Trujillo"], correct: 1, explanation: "La capital de Perú es Lima", category: "geografia" },
                { id: 382, question: "¿En qué país está Casablanca?", options: ["Egipto", "Túnez", "Marruecos", "Argelia"], correct: 2, explanation: "Casablanca está en Marruecos", category: "geografia" },
                { id: 383, question: "¿Cuál es el punto más alto de África?", options: ["Kilimanjaro", "Monte Kenia", "Atlas", "Ras Dashen"], correct: 0, explanation: "El Kilimanjaro es el punto más alto", category: "geografia" },
                { id: 384, question: "¿Dónde está el Museo del Louvre?", options: ["Londres", "París", "Roma", "Madrid"], correct: 1, explanation: "El Louvre está en París", category: "geografia" },
                { id: 385, question: "¿Cuál es la capital de Bolivia?", options: ["La Paz", "Sucre", "Santa Cruz", "Ambas A y B"], correct: 3, explanation: "Bolivia tiene dos capitales: Sucre y La Paz", category: "geografia" },
                { id: 386, question: "¿En qué país está el lago Ness?", options: ["Irlanda", "Gales", "Escocia", "Inglaterra"], correct: 2, explanation: "El lago Ness está en Escocia", category: "geografia" },
                { id: 387, question: "¿Cuál es la capital de Finlandia?", options: ["Oslo", "Estocolmo", "Helsinki", "Copenhague"], correct: 2, explanation: "La capital de Finlandia es Helsinki", category: "geografia" },
                { id: 388, question: "¿Dónde está la Capilla Sixtina?", options: ["España", "Francia", "Italia", "Grecia"], correct: 2, explanation: "La Capilla Sixtina está en el Vaticano, Italia", category: "geografia" },
                { id: 389, question: "¿Cuál es la capital de Ecuador?", options: ["Guayaquil", "Quito", "Cuenca", "Manta"], correct: 1, explanation: "La capital de Ecuador es Quito", category: "geografia" },
                { id: 390, question: "¿En qué país está Dubái?", options: ["Qatar", "EAU", "Omán", "Bahréin"], correct: 1, explanation: "Dubái está en los Emiratos Árabes Unidos", category: "geografia" },
                { id: 391, question: "¿Cuál es la montaña más alta de América?", options: ["McKinley", "Aconcagua", "Ojos del Salado", "Huascarán"], correct: 1, explanation: "El Aconcagua es la montaña más alta de América", category: "geografia" },
                { id: 392, question: "¿Dónde está la ciudad de Petra?", options: ["Egipto", "Jordania", "Israel", "Líbano"], correct: 1, explanation: "Petra está en Jordania", category: "geografia" },
                { id: 393, question: "¿Cuál es la capital de Venezuela?", options: ["Maracaibo", "Caracas", "Valencia", "Barquisimeto"], correct: 1, explanation: "La capital de Venezuela es Caracas", category: "geografia" },
                { id: 394, question: "¿En qué país está el Monte Cervino?", options: ["Francia", "Suiza/Italia", "Austria", "Alemania"], correct: 1, explanation: "El Cervino está entre Suiza e Italia", category: "geografia" },
                { id: 395, question: "¿Cuál es la capital de Bélgica?", options: ["Amberes", "Brujas", "Bruselas", "Gante"], correct: 2, explanation: "La capital de Bélgica es Bruselas", category: "geografia" },
                { id: 396, question: "¿Dónde están las Islas Galápagos?", options: ["Colombia", "Ecuador", "Perú", "Chile"], correct: 1, explanation: "Las Galápagos pertenecen a Ecuador", category: "geografia" },
                { id: 397, question: "¿Cuál es la capital de Polonia?", options: ["Cracovia", "Varsovia", "Gdansk", "Poznan"], correct: 1, explanation: "La capital de Polonia es Varsovia", category: "geografia" },
                { id: 398, question: "¿En qué mar está Creta?", options: ["Adriático", "Jónico", "Egeo", "Mediterráneo"], correct: 2, explanation: "Creta está en el Mar Egeo", category: "geografia" },
                { id: 399, question: "¿Cuál es el río más largo de Asia?", options: ["Yangtsé", "Ganges", "Mekong", "Amarillo"], correct: 0, explanation: "El Yangtsé es el río más largo de Asia", category: "geografia" },
                { id: 400, question: "¿Dónde está el Monte Sinaí?", options: ["Israel", "Jordania", "Egipto", "Arabia Saudita"], correct: 2, explanation: "El Monte Sinaí está en Egipto", category: "geografia" },
                // LITERATURA (401-500)
                { id: 401, question: "¿Quién escribió 'Don Quijote de la Mancha'?", options: ["Lope de Vega", "Miguel de Cervantes", "Francisco de Quevedo", "Luis de Góngora"], correct: 1, explanation: "Miguel de Cervantes escribió Don Quijote", category: "literatura" },
                { id: 402, question: "¿Quién escribió '1984'?", options: ["George Orwell", "Aldous Huxley", "Ray Bradbury", "H.G. Wells"], correct: 0, explanation: "George Orwell escribió 1984", category: "literatura" },
                { id: 403, question: "¿De qué nacionalidad era William Shakespeare?", options: ["Estadounidense", "Irlandés", "Inglés", "Escocés"], correct: 2, explanation: "Shakespeare era inglés", category: "literatura" },
                { id: 404, question: "¿Quién escribió 'Cien años de soledad'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Julio Cortázar", "Pablo Neruda"], correct: 1, explanation: "García Márquez escribió Cien años de soledad", category: "literatura" },
                { id: 405, question: "¿Cuál es la obra más famosa de Franz Kafka?", options: ["La Metamorfosis", "El Proceso", "El Castillo", "América"], correct: 0, explanation: "La Metamorfosis es su obra más conocida", category: "literatura" },
                { id: 406, question: "¿Quién escribió 'Romeo y Julieta'?", options: ["Christopher Marlowe", "William Shakespeare", "Ben Jonson", "John Webster"], correct: 1, explanation: "Shakespeare escribió Romeo y Julieta", category: "literatura" },
                { id: 407, question: "¿Qué autor escribió 'El Principito'?", options: ["Jules Verne", "Victor Hugo", "Antoine de Saint-Exupéry", "Albert Camus"], correct: 2, explanation: "Saint-Exupéry escribió El Principito", category: "literatura" },
                { id: 408, question: "¿Quién es el autor de 'La Divina Comedia'?", options: ["Dante Alighieri", "Petrarca", "Boccaccio", "Maquiavelo"], correct: 0, explanation: "Dante Alighieri escribió La Divina Comedia", category: "literatura" },
                { id: 409, question: "¿Quién escribió 'El viejo y el mar'?", options: ["William Faulkner", "Ernest Hemingway", "John Steinbeck", "F. Scott Fitzgerald"], correct: 1, explanation: "Hemingway escribió El viejo y el mar", category: "literatura" },
                { id: 410, question: "¿Qué autor escribió 'Madame Bovary'?", options: ["Victor Hugo", "Gustave Flaubert", "Émile Zola", "Honoré de Balzac"], correct: 1, explanation: "Flaubert escribió Madame Bovary", category: "literatura" },
                { id: 411, question: "¿Quién escribió 'La Odisea'?", options: ["Homero", "Sófocles", "Eurípides", "Hesíodo"], correct: 0, explanation: "Homero escribió La Odisea", category: "literatura" },
                { id: 412, question: "¿Quién es el autor de 'Crimen y castigo'?", options: ["León Tolstói", "Fiódor Dostoievski", "Antón Chéjov", "Iván Turguénev"], correct: 1, explanation: "Dostoievski escribió Crimen y castigo", category: "literatura" },
                { id: 413, question: "¿Qué escritor creó al personaje Sherlock Holmes?", options: ["Edgar Allan Poe", "Arthur Conan Doyle", "Agatha Christie", "Jules Verne"], correct: 1, explanation: "Conan Doyle creó a Sherlock Holmes", category: "literatura" },
                { id: 414, question: "¿Quién escribió 'El retrato de Dorian Gray'?", options: ["Oscar Wilde", "Charles Dickens", "Emily Brontë", "Jane Austen"], correct: 0, explanation: "Oscar Wilde escribió El retrato de Dorian Gray", category: "literatura" },
                { id: 415, question: "¿Qué autor escribió 'Moby Dick'?", options: ["Mark Twain", "Herman Melville", "Walt Whitman", "Edgar Allan Poe"], correct: 1, explanation: "Herman Melville escribió Moby Dick", category: "literatura" },
                { id: 416, question: "¿Quién escribió 'Las aventuras de Tom Sawyer'?", options: ["Mark Twain", "Jack London", "Herman Melville", "Henry James"], correct: 0, explanation: "Mark Twain escribió Tom Sawyer", category: "literatura" },
                { id: 417, question: "¿Quién es el autor de 'El Alquimista'?", options: ["Gabriel García Márquez", "Isabel Allende", "Paulo Coelho", "Mario Vargas Llosa"], correct: 2, explanation: "Paulo Coelho escribió El Alquimista", category: "literatura" },
                { id: 418, question: "¿Qué escritor creó 'Los tres mosqueteros'?", options: ["Victor Hugo", "Alexandre Dumas", "Gustave Flaubert", "Émile Zola"], correct: 1, explanation: "Alexandre Dumas escribió Los tres mosqueteros", category: "literatura" },
                { id: 419, question: "¿Quién escribió 'Orgullo y prejuicio'?", options: ["Emily Brontë", "Jane Austen", "Charlotte Brontë", "Mary Shelley"], correct: 1, explanation: "Jane Austen escribió Orgullo y prejuicio", category: "literatura" },
                { id: 420, question: "¿Qué autor escribió 'El Señor de los Anillos'?", options: ["C.S. Lewis", "J.R.R. Tolkien", "George R.R. Martin", "Terry Pratchett"], correct: 1, explanation: "Tolkien escribió El Señor de los Anillos", category: "literatura" },
                { id: 421, question: "¿Quién escribió 'La metamorfosis'?", options: ["Thomas Mann", "Franz Kafka", "Hermann Hesse", "Bertolt Brecht"], correct: 1, explanation: "Franz Kafka escribió La metamorfosis", category: "literatura" },
                { id: 422, question: "¿Qué autor escribió 'Rayuela'?", options: ["Jorge Luis Borges", "Julio Cortázar", "Mario Vargas Llosa", "Gabriel García Márquez"], correct: 1, explanation: "Julio Cortázar escribió Rayuela", category: "literatura" },
                { id: 423, question: "¿Quién escribió 'La Ilíada'?", options: ["Homero", "Virgilio", "Sófocles", "Eurípides"], correct: 0, explanation: "Homero escribió La Ilíada", category: "literatura" },
                { id: 424, question: "¿Qué autor escribió 'Los miserables'?", options: ["Honoré de Balzac", "Émile Zola", "Victor Hugo", "Alexandre Dumas"], correct: 2, explanation: "Victor Hugo escribió Los miserables", category: "literatura" },
                { id: 425, question: "¿Quién escribió 'El nombre de la rosa'?", options: ["Italo Calvino", "Umberto Eco", "Alberto Moravia", "Luigi Pirandello"], correct: 1, explanation: "Umberto Eco escribió El nombre de la rosa", category: "literatura" },
                { id: 426, question: "¿Qué autor escribió 'Frankenstein'?", options: ["Mary Shelley", "Jane Austen", "Emily Brontë", "Virginia Woolf"], correct: 0, explanation: "Mary Shelley escribió Frankenstein", category: "literatura" },
                { id: 427, question: "¿Quién escribió 'El guardián entre el centeno'?", options: ["F. Scott Fitzgerald", "J.D. Salinger", "Ernest Hemingway", "William Faulkner"], correct: 1, explanation: "J.D. Salinger escribió El guardián entre el centeno", category: "literatura" },
                { id: 428, question: "¿Qué autor escribió 'La casa de los espíritus'?", options: ["Gabriel García Márquez", "Isabel Allende", "Mario Vargas Llosa", "Julio Cortázar"], correct: 1, explanation: "Isabel Allende escribió La casa de los espíritus", category: "literatura" },
                { id: 429, question: "¿Quién escribió 'El lobo estepario'?", options: ["Thomas Mann", "Hermann Hesse", "Franz Kafka", "Bertolt Brecht"], correct: 1, explanation: "Hermann Hesse escribió El lobo estepario", category: "literatura" },
                { id: 430, question: "¿Qué autor escribió 'La naranja mecánica'?", options: ["George Orwell", "Aldous Huxley", "Anthony Burgess", "Ray Bradbury"], correct: 2, explanation: "Anthony Burgess escribió La naranja mecánica", category: "literatura" },
                { id: 431, question: "¿Quién escribió 'Pedro Páramo'?", options: ["Octavio Paz", "Juan Rulfo", "Carlos Fuentes", "Elena Garro"], correct: 1, explanation: "Juan Rulfo escribió Pedro Páramo", category: "literatura" },
                { id: 432, question: "¿Qué autor escribió 'El gran Gatsby'?", options: ["Ernest Hemingway", "F. Scott Fitzgerald", "William Faulkner", "John Steinbeck"], correct: 1, explanation: "F. Scott Fitzgerald escribió El gran Gatsby", category: "literatura" },
                { id: 433, question: "¿Quién escribió 'Las venas abiertas de América Latina'?", options: ["Gabriel García Márquez", "Eduardo Galeano", "Mario Vargas Llosa", "Julio Cortázar"], correct: 1, explanation: "Eduardo Galeano escribió Las venas abiertas de América Latina", category: "literatura" },
                { id: 434, question: "¿Qué autor escribió 'El perfume'?", options: ["Milan Kundera", "Patrick Süskind", "Günter Grass", "Heinrich Böll"], correct: 1, explanation: "Patrick Süskind escribió El perfume", category: "literatura" },
                { id: 435, question: "¿Quién escribió 'La peste'?", options: ["Jean-Paul Sartre", "Albert Camus", "Simone de Beauvoir", "André Malraux"], correct: 1, explanation: "Albert Camus escribió La peste", category: "literatura" },
                { id: 436, question: "¿Qué autor escribió 'El amor en los tiempos del cólera'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Julio Cortázar", "Carlos Fuentes"], correct: 1, explanation: "Gabriel García Márquez escribió El amor en los tiempos del cólera", category: "literatura" },
                { id: 437, question: "¿Quién escribió 'Las mil y una noches'?", options: ["Autor anónimo", "Omar Khayyam", "Rumi", "Al-Mutanabbi"], correct: 0, explanation: "Las mil y una noches es una obra anónima", category: "literatura" },
                { id: 438, question: "¿Qué autor escribió 'Los pilares de la Tierra'?", options: ["Ken Follett", "Dan Brown", "John Grisham", "Stephen King"], correct: 0, explanation: "Ken Follett escribió Los pilares de la Tierra", category: "literatura" },
                { id: 439, question: "¿Quién escribió 'El túnel'?", options: ["Jorge Luis Borges", "Ernesto Sabato", "Julio Cortázar", "Roberto Arlt"], correct: 1, explanation: "Ernesto Sabato escribió El túnel", category: "literatura" },
                { id: 440, question: "¿Qué autor escribió 'El hobbit'?", options: ["C.S. Lewis", "J.R.R. Tolkien", "Terry Pratchett", "Philip Pullman"], correct: 1, explanation: "J.R.R. Tolkien escribió El hobbit", category: "literatura" },
                { id: 441, question: "¿Quién escribió 'Fahrenheit 451'?", options: ["George Orwell", "Aldous Huxley", "Ray Bradbury", "Kurt Vonnegut"], correct: 2, explanation: "Ray Bradbury escribió Fahrenheit 451", category: "literatura" },
                { id: 442, question: "¿Qué autor escribió 'El código Da Vinci'?", options: ["Dan Brown", "John Grisham", "Stephen King", "Michael Crichton"], correct: 0, explanation: "Dan Brown escribió El código Da Vinci", category: "literatura" },
                { id: 443, question: "¿Quién escribió 'La Casa de Bernarda Alba'?", options: ["Miguel de Unamuno", "Federico García Lorca", "Antonio Machado", "Juan Ramón Jiménez"], correct: 1, explanation: "Federico García Lorca escribió La Casa de Bernarda Alba", category: "literatura" },
                { id: 444, question: "¿Qué autor escribió 'El retrato de una dama'?", options: ["Henry James", "Mark Twain", "Charles Dickens", "Thomas Hardy"], correct: 0, explanation: "Henry James escribió El retrato de una dama", category: "literatura" },
                { id: 445, question: "¿Quién escribió 'Ficciones'?", options: ["Julio Cortázar", "Jorge Luis Borges", "Gabriel García Márquez", "Mario Vargas Llosa"], correct: 1, explanation: "Jorge Luis Borges escribió Ficciones", category: "literatura" },
                { id: 446, question: "¿Qué autor escribió 'La Regenta'?", options: ["Benito Pérez Galdós", "Leopoldo Alas Clarín", "Emilia Pardo Bazán", "Juan Valera"], correct: 1, explanation: "Leopoldo Alas Clarín escribió La Regenta", category: "literatura" },
                { id: 447, question: "¿Quién escribió 'El extranjero'?", options: ["Jean-Paul Sartre", "Albert Camus", "André Gide", "Marcel Proust"], correct: 1, explanation: "Albert Camus escribió El extranjero", category: "literatura" },
                { id: 448, question: "¿Qué autor escribió 'Ana Karenina'?", options: ["Fiódor Dostoievski", "León Tolstói", "Antón Chéjov", "Iván Turguénev"], correct: 1, explanation: "León Tolstói escribió Ana Karenina", category: "literatura" },
                { id: 449, question: "¿Quién escribió 'El Señor de las Moscas'?", options: ["George Orwell", "William Golding", "Aldous Huxley", "Anthony Burgess"], correct: 1, explanation: "William Golding escribió El Señor de las Moscas", category: "literatura" },
                { id: 450, question: "¿Qué autor escribió 'La insoportable levedad del ser'?", options: ["Milan Kundera", "Václav Havel", "Bohumil Hrabal", "Karel Čapek"], correct: 0, explanation: "Milan Kundera escribió La insoportable levedad del ser", category: "literatura" },
                { id: 451, question: "¿Quién escribió 'El Aleph'?", options: ["Julio Cortázar", "Jorge Luis Borges", "Adolfo Bioy Casares", "Ernesto Sabato"], correct: 1, explanation: "Jorge Luis Borges escribió El Aleph", category: "literatura" },
                { id: 452, question: "¿Qué autor escribió 'La colmena'?", options: ["Miguel Delibes", "Camilo José Cela", "Carmen Laforet", "Rafael Sánchez Ferlosio"], correct: 1, explanation: "Camilo José Cela escribió La colmena", category: "literatura" },
                { id: 453, question: "¿Quién escribió 'Las uvas de la ira'?", options: ["William Faulkner", "John Steinbeck", "Ernest Hemingway", "F. Scott Fitzgerald"], correct: 1, explanation: "John Steinbeck escribió Las uvas de la ira", category: "literatura" },
                { id: 454, question: "¿Qué autor escribió 'El coronel no tiene quien le escriba'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Juan Rulfo", "Julio Cortázar"], correct: 1, explanation: "Gabriel García Márquez escribió El coronel no tiene quien le escriba", category: "literatura" },
                { id: 455, question: "¿Quién escribió 'Ulises'?", options: ["Oscar Wilde", "James Joyce", "Virginia Woolf", "D.H. Lawrence"], correct: 1, explanation: "James Joyce escribió Ulises", category: "literatura" },
                { id: 456, question: "¿Qué autor escribió 'El proceso'?", options: ["Franz Kafka", "Thomas Mann", "Hermann Hesse", "Robert Musil"], correct: 0, explanation: "Franz Kafka escribió El proceso", category: "literatura" },
                { id: 457, question: "¿Quién escribió 'La guerra del fin del mundo'?", options: ["Gabriel García Márquez", "Mario Vargas Llosa", "Carlos Fuentes", "Julio Cortázar"], correct: 1, explanation: "Mario Vargas Llosa escribió La guerra del fin del mundo", category: "literatura" },
                { id: 458, question: "¿Qué autor escribió 'El ruido y la furia'?", options: ["Ernest Hemingway", "William Faulkner", "John Steinbeck", "F. Scott Fitzgerald"], correct: 1, explanation: "William Faulkner escribió El ruido y la furia", category: "literatura" },
                { id: 459, question: "¿Quién escribió 'La muerte de Artemio Cruz'?", options: ["Juan Rulfo", "Octavio Paz", "Carlos Fuentes", "Elena Poniatowska"], correct: 2, explanation: "Carlos Fuentes escribió La muerte de Artemio Cruz", category: "literatura" },
                { id: 460, question: "¿Qué autor escribió 'Crónica de una muerte anunciada'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Juan Rulfo", "Julio Cortázar"], correct: 1, explanation: "Gabriel García Márquez escribió Crónica de una muerte anunciada", category: "literatura" },
                { id: 461, question: "¿Quién escribió 'Luces de bohemia'?", options: ["Federico García Lorca", "Ramón del Valle-Inclán", "Miguel de Unamuno", "Antonio Machado"], correct: 1, explanation: "Ramón del Valle-Inclán escribió Luces de bohemia", category: "literatura" },
                { id: 462, question: "¿Qué autor escribió 'El guardián invisible'?", options: ["Carlos Ruiz Zafón", "Dolores Redondo", "Arturo Pérez-Reverte", "Julia Navarro"], correct: 1, explanation: "Dolores Redondo escribió El guardián invisible", category: "literatura" },
                { id: 463, question: "¿Quién escribió 'La sombra del viento'?", options: ["Arturo Pérez-Reverte", "Carlos Ruiz Zafón", "Javier Sierra", "Ildefonso Falcones"], correct: 1, explanation: "Carlos Ruiz Zafón escribió La sombra del viento", category: "literatura" },
                { id: 464, question: "¿Qué autor escribió 'El juego del ángel'?", options: ["Julia Navarro", "Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Javier Sierra"], correct: 1, explanation: "Carlos Ruiz Zafón escribió El juego del ángel", category: "literatura" },
                { id: 465, question: "¿Quién escribió 'La tabla de Flandes'?", options: ["Arturo Pérez-Reverte", "Carlos Ruiz Zafón", "Javier Sierra", "Julia Navarro"], correct: 0, explanation: "Arturo Pérez-Reverte escribió La tabla de Flandes", category: "literatura" },
                { id: 466, question: "¿Qué autor escribió 'El capitán Alatriste'?", options: ["Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Javier Sierra", "Ildefonso Falcones"], correct: 1, explanation: "Arturo Pérez-Reverte escribió El capitán Alatriste", category: "literatura" },
                { id: 467, question: "¿Quién escribió 'La catedral del mar'?", options: ["Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Ildefonso Falcones", "Julia Navarro"], correct: 2, explanation: "Ildefonso Falcones escribió La catedral del mar", category: "literatura" },
                { id: 468, question: "¿Qué autor escribió 'Marina'?", options: ["Arturo Pérez-Reverte", "Carlos Ruiz Zafón", "Javier Sierra", "Julia Navarro"], correct: 1, explanation: "Carlos Ruiz Zafón escribió Marina", category: "literatura" },
                { id: 469, question: "¿Quién escribió 'La reina del sur'?", options: ["Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Javier Sierra", "Julia Navarro"], correct: 1, explanation: "Arturo Pérez-Reverte escribió La reina del sur", category: "literatura" },
                { id: 470, question: "¿Qué autor escribió 'El maestro del Prado'?", options: ["Arturo Pérez-Reverte", "Javier Sierra", "Carlos Ruiz Zafón", "Julia Navarro"], correct: 1, explanation: "Javier Sierra escribió El maestro del Prado", category: "literatura" },
                { id: 471, question: "¿Quién escribió 'Episodios Nacionales'?", options: ["Miguel de Unamuno", "Benito Pérez Galdós", "Pío Baroja", "Vicente Blasco Ibáñez"], correct: 1, explanation: "Benito Pérez Galdós escribió los Episodios Nacionales", category: "literatura" },
                { id: 472, question: "¿Qué autor escribió 'Niebla'?", options: ["Antonio Machado", "Miguel de Unamuno", "Ramón del Valle-Inclán", "Pío Baroja"], correct: 1, explanation: "Miguel de Unamuno escribió Niebla", category: "literatura" },
                { id: 473, question: "¿Quién escribió 'Fortunata y Jacinta'?", options: ["Leopoldo Alas Clarín", "Benito Pérez Galdós", "Emilia Pardo Bazán", "Juan Valera"], correct: 1, explanation: "Benito Pérez Galdós escribió Fortunata y Jacinta", category: "literatura" },
                { id: 474, question: "¿Qué autor escribió 'Campos de Castilla'?", options: ["Juan Ramón Jiménez", "Antonio Machado", "Miguel de Unamuno", "Federico García Lorca"], correct: 1, explanation: "Antonio Machado escribió Campos de Castilla", category: "literatura" },
                { id: 475, question: "¿Quién escribió 'Platero y yo'?", options: ["Antonio Machado", "Juan Ramón Jiménez", "Federico García Lorca", "Miguel de Unamuno"], correct: 1, explanation: "Juan Ramón Jiménez escribió Platero y yo", category: "literatura" },
                { id: 476, question: "¿Qué autor escribió 'Poeta en Nueva York'?", options: ["Antonio Machado", "Miguel de Unamuno", "Federico García Lorca", "Juan Ramón Jiménez"], correct: 2, explanation: "Federico García Lorca escribió Poeta en Nueva York", category: "literatura" },
                { id: 477, question: "¿Quién escribió 'San Manuel Bueno, mártir'?", options: ["Pío Baroja", "Miguel de Unamuno", "Valle-Inclán", "Azorín"], correct: 1, explanation: "Miguel de Unamuno escribió San Manuel Bueno, mártir", category: "literatura" },
                { id: 478, question: "¿Qué autor escribió 'Rimas y leyendas'?", options: ["Gustavo Adolfo Bécquer", "José de Espronceda", "Rosalía de Castro", "José Zorrilla"], correct: 0, explanation: "Gustavo Adolfo Bécquer escribió Rimas y leyendas", category: "literatura" },
                { id: 479, question: "¿Quién escribió 'Don Juan Tenorio'?", options: ["José Zorrilla", "José de Espronceda", "Duque de Rivas", "Gustavo Adolfo Bécquer"], correct: 0, explanation: "José Zorrilla escribió Don Juan Tenorio", category: "literatura" },
                { id: 480, question: "¿Qué autor escribió 'El estudiante de Salamanca'?", options: ["Gustavo Adolfo Bécquer", "José de Espronceda", "José Zorrilla", "Duque de Rivas"], correct: 1, explanation: "José de Espronceda escribió El estudiante de Salamanca", category: "literatura" },
                { id: 481, question: "¿Quién escribió 'La familia de Pascual Duarte'?", options: ["Miguel Delibes", "Camilo José Cela", "Carmen Laforet", "Ana María Matute"], correct: 1, explanation: "Camilo José Cela escribió La familia de Pascual Duarte", category: "literatura" },
                { id: 482, question: "¿Qué autor escribió 'Nada'?", options: ["Carmen Laforet", "Ana María Matute", "Carmen Martín Gaite", "Rosa Chacel"], correct: 0, explanation: "Carmen Laforet escribió Nada", category: "literatura" },
                { id: 483, question: "¿Quién escribió 'Cinco horas con Mario'?", options: ["Camilo José Cela", "Miguel Delibes", "Rafael Sánchez Ferlosio", "Luis Martín-Santos"], correct: 1, explanation: "Miguel Delibes escribió Cinco horas con Mario", category: "literatura" },
                { id: 484, question: "¿Qué autor escribió 'El Jarama'?", options: ["Carmen Laforet", "Miguel Delibes", "Rafael Sánchez Ferlosio", "Camilo José Cela"], correct: 2, explanation: "Rafael Sánchez Ferlosio escribió El Jarama", category: "literatura" },
                { id: 485, question: "¿Quién escribió 'Primera memoria'?", options: ["Carmen Laforet", "Ana María Matute", "Carmen Martín Gaite", "Rosa Chacel"], correct: 1, explanation: "Ana María Matute escribió Primera memoria", category: "literatura" },
                { id: 486, question: "¿Qué autor escribió 'Entre visillos'?", options: ["Carmen Laforet", "Ana María Matute", "Carmen Martín Gaite", "Rosa Chacel"], correct: 2, explanation: "Carmen Martín Gaite escribió Entre visillos", category: "literatura" },
                { id: 487, question: "¿Quién escribió 'Los santos inocentes'?", options: ["Camilo José Cela", "Miguel Delibes", "Rafael Sánchez Ferlosio", "Luis Martín-Santos"], correct: 1, explanation: "Miguel Delibes escribió Los santos inocentes", category: "literatura" },
                { id: 488, question: "¿Qué autor escribió 'Tiempo de silencio'?", options: ["Miguel Delibes", "Luis Martín-Santos", "Juan Marsé", "Juan Goytisolo"], correct: 1, explanation: "Luis Martín-Santos escribió Tiempo de silencio", category: "literatura" },
                { id: 489, question: "¿Quién escribió 'Últimas tardes con Teresa'?", options: ["Juan Marsé", "Juan Goytisolo", "Luis Martín-Santos", "Miguel Delibes"], correct: 0, explanation: "Juan Marsé escribió Últimas tardes con Teresa", category: "literatura" },
                { id: 490, question: "¿Qué autor escribió 'Señas de identidad'?", options: ["Juan Marsé", "Juan Goytisolo", "Luis Martín-Santos", "Rafael Sánchez Ferlosio"], correct: 1, explanation: "Juan Goytisolo escribió Señas de identidad", category: "literatura" },
                { id: 491, question: "¿Quién escribió 'La verdad sobre el caso Savolta'?", options: ["Eduardo Mendoza", "Antonio Muñoz Molina", "Javier Marías", "Arturo Pérez-Reverte"], correct: 0, explanation: "Eduardo Mendoza escribió La verdad sobre el caso Savolta", category: "literatura" },
                { id: 492, question: "¿Qué autor escribió 'Corazón tan blanco'?", options: ["Eduardo Mendoza", "Antonio Muñoz Molina", "Javier Marías", "Arturo Pérez-Reverte"], correct: 2, explanation: "Javier Marías escribió Corazón tan blanco", category: "literatura" },                // Agregar después de las preguntas de matemáticas, ciencias, historia y geografía:

                // LITERATURA (401-500)
                { id: 401, question: "¿Quién escribió 'Don Quijote de la Mancha'?", options: ["Lope de Vega", "Miguel de Cervantes", "Francisco de Quevedo", "Luis de Góngora"], correct: 1, explanation: "Miguel de Cervantes escribió Don Quijote", category: "literatura" },
                { id: 402, question: "¿Quién escribió '1984'?", options: ["George Orwell", "Aldous Huxley", "Ray Bradbury", "H.G. Wells"], correct: 0, explanation: "George Orwell escribió 1984", category: "literatura" },
                { id: 403, question: "¿De qué nacionalidad era William Shakespeare?", options: ["Estadounidense", "Irlandés", "Inglés", "Escocés"], correct: 2, explanation: "Shakespeare era inglés", category: "literatura" },
                { id: 404, question: "¿Quién escribió 'Cien años de soledad'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Julio Cortázar", "Pablo Neruda"], correct: 1, explanation: "García Márquez escribió Cien años de soledad", category: "literatura" },
                { id: 405, question: "¿Cuál es la obra más famosa de Franz Kafka?", options: ["La Metamorfosis", "El Proceso", "El Castillo", "América"], correct: 0, explanation: "La Metamorfosis es su obra más conocida", category: "literatura" },
                { id: 406, question: "¿Quién escribió 'Romeo y Julieta'?", options: ["Christopher Marlowe", "William Shakespeare", "Ben Jonson", "John Webster"], correct: 1, explanation: "Shakespeare escribió Romeo y Julieta", category: "literatura" },
                { id: 407, question: "¿Qué autor escribió 'El Principito'?", options: ["Jules Verne", "Victor Hugo", "Antoine de Saint-Exupéry", "Albert Camus"], correct: 2, explanation: "Saint-Exupéry escribió El Principito", category: "literatura" },
                { id: 408, question: "¿Quién es el autor de 'La Divina Comedia'?", options: ["Dante Alighieri", "Petrarca", "Boccaccio", "Maquiavelo"], correct: 0, explanation: "Dante Alighieri escribió La Divina Comedia", category: "literatura" },
                { id: 409, question: "¿Quién escribió 'El viejo y el mar'?", options: ["William Faulkner", "Ernest Hemingway", "John Steinbeck", "F. Scott Fitzgerald"], correct: 1, explanation: "Hemingway escribió El viejo y el mar", category: "literatura" },
                { id: 410, question: "¿Qué autor escribió 'Madame Bovary'?", options: ["Victor Hugo", "Gustave Flaubert", "Émile Zola", "Honoré de Balzac"], correct: 1, explanation: "Flaubert escribió Madame Bovary", category: "literatura" },
                { id: 411, question: "¿Quién escribió 'La Odisea'?", options: ["Homero", "Sófocles", "Eurípides", "Hesíodo"], correct: 0, explanation: "Homero escribió La Odisea", category: "literatura" },
                { id: 412, question: "¿Quién es el autor de 'Crimen y castigo'?", options: ["León Tolstói", "Fiódor Dostoievski", "Antón Chéjov", "Iván Turguénev"], correct: 1, explanation: "Dostoievski escribió Crimen y castigo", category: "literatura" },
                { id: 413, question: "¿Qué escritor creó al personaje Sherlock Holmes?", options: ["Edgar Allan Poe", "Arthur Conan Doyle", "Agatha Christie", "Jules Verne"], correct: 1, explanation: "Conan Doyle creó a Sherlock Holmes", category: "literatura" },
                { id: 414, question: "¿Quién escribió 'El retrato de Dorian Gray'?", options: ["Oscar Wilde", "Charles Dickens", "Emily Brontë", "Jane Austen"], correct: 0, explanation: "Oscar Wilde escribió El retrato de Dorian Gray", category: "literatura" },
                { id: 415, question: "¿Qué autor escribió 'Moby Dick'?", options: ["Mark Twain", "Herman Melville", "Walt Whitman", "Edgar Allan Poe"], correct: 1, explanation: "Herman Melville escribió Moby Dick", category: "literatura" },
                { id: 416, question: "¿Quién escribió 'Las aventuras de Tom Sawyer'?", options: ["Mark Twain", "Jack London", "Herman Melville", "Henry James"], correct: 0, explanation: "Mark Twain escribió Tom Sawyer", category: "literatura" },
                { id: 417, question: "¿Quién es el autor de 'El Alquimista'?", options: ["Gabriel García Márquez", "Isabel Allende", "Paulo Coelho", "Mario Vargas Llosa"], correct: 2, explanation: "Paulo Coelho escribió El Alquimista", category: "literatura" },
                { id: 418, question: "¿Qué escritor creó 'Los tres mosqueteros'?", options: ["Victor Hugo", "Alexandre Dumas", "Gustave Flaubert", "Émile Zola"], correct: 1, explanation: "Alexandre Dumas escribió Los tres mosqueteros", category: "literatura" },
                { id: 419, question: "¿Quién escribió 'Orgullo y prejuicio'?", options: ["Emily Brontë", "Jane Austen", "Charlotte Brontë", "Mary Shelley"], correct: 1, explanation: "Jane Austen escribió Orgullo y prejuicio", category: "literatura" },
                { id: 420, question: "¿Qué autor escribió 'El Señor de los Anillos'?", options: ["C.S. Lewis", "J.R.R. Tolkien", "George R.R. Martin", "Terry Pratchett"], correct: 1, explanation: "Tolkien escribió El Señor de los Anillos", category: "literatura" },
                { id: 421, question: "¿Quién escribió 'La metamorfosis'?", options: ["Thomas Mann", "Franz Kafka", "Hermann Hesse", "Bertolt Brecht"], correct: 1, explanation: "Franz Kafka escribió La metamorfosis", category: "literatura" },
                { id: 422, question: "¿Qué autor escribió 'Rayuela'?", options: ["Jorge Luis Borges", "Julio Cortázar", "Mario Vargas Llosa", "Gabriel García Márquez"], correct: 1, explanation: "Julio Cortázar escribió Rayuela", category: "literatura" },
                { id: 423, question: "¿Quién escribió 'La Ilíada'?", options: ["Homero", "Virgilio", "Sófocles", "Eurípides"], correct: 0, explanation: "Homero escribió La Ilíada", category: "literatura" },
                { id: 424, question: "¿Qué autor escribió 'Los miserables'?", options: ["Honoré de Balzac", "Émile Zola", "Victor Hugo", "Alexandre Dumas"], correct: 2, explanation: "Victor Hugo escribió Los miserables", category: "literatura" },
                { id: 425, question: "¿Quién escribió 'El nombre de la rosa'?", options: ["Italo Calvino", "Umberto Eco", "Alberto Moravia", "Luigi Pirandello"], correct: 1, explanation: "Umberto Eco escribió El nombre de la rosa", category: "literatura" },
                { id: 426, question: "¿Qué autor escribió 'Frankenstein'?", options: ["Mary Shelley", "Jane Austen", "Emily Brontë", "Virginia Woolf"], correct: 0, explanation: "Mary Shelley escribió Frankenstein", category: "literatura" },
                { id: 427, question: "¿Quién escribió 'El guardián entre el centeno'?", options: ["F. Scott Fitzgerald", "J.D. Salinger", "Ernest Hemingway", "William Faulkner"], correct: 1, explanation: "J.D. Salinger escribió El guardián entre el centeno", category: "literatura" },
                { id: 428, question: "¿Qué autor escribió 'La casa de los espíritus'?", options: ["Gabriel García Márquez", "Isabel Allende", "Mario Vargas Llosa", "Julio Cortázar"], correct: 1, explanation: "Isabel Allende escribió La casa de los espíritus", category: "literatura" },
                { id: 429, question: "¿Quién escribió 'El lobo estepario'?", options: ["Thomas Mann", "Hermann Hesse", "Franz Kafka", "Bertolt Brecht"], correct: 1, explanation: "Hermann Hesse escribió El lobo estepario", category: "literatura" },
                { id: 430, question: "¿Qué autor escribió 'La naranja mecánica'?", options: ["George Orwell", "Aldous Huxley", "Anthony Burgess", "Ray Bradbury"], correct: 2, explanation: "Anthony Burgess escribió La naranja mecánica", category: "literatura" },
                { id: 431, question: "¿Quién escribió 'Pedro Páramo'?", options: ["Octavio Paz", "Juan Rulfo", "Carlos Fuentes", "Elena Garro"], correct: 1, explanation: "Juan Rulfo escribió Pedro Páramo", category: "literatura" },
                { id: 432, question: "¿Qué autor escribió 'El gran Gatsby'?", options: ["Ernest Hemingway", "F. Scott Fitzgerald", "William Faulkner", "John Steinbeck"], correct: 1, explanation: "F. Scott Fitzgerald escribió El gran Gatsby", category: "literatura" },
                { id: 433, question: "¿Quién escribió 'Las venas abiertas de América Latina'?", options: ["Gabriel García Márquez", "Eduardo Galeano", "Mario Vargas Llosa", "Julio Cortázar"], correct: 1, explanation: "Eduardo Galeano escribió Las venas abiertas de América Latina", category: "literatura" },
                { id: 434, question: "¿Qué autor escribió 'El perfume'?", options: ["Milan Kundera", "Patrick Süskind", "Günter Grass", "Heinrich Böll"], correct: 1, explanation: "Patrick Süskind escribió El perfume", category: "literatura" },
                { id: 435, question: "¿Quién escribió 'La peste'?", options: ["Jean-Paul Sartre", "Albert Camus", "Simone de Beauvoir", "André Malraux"], correct: 1, explanation: "Albert Camus escribió La peste", category: "literatura" },
                { id: 436, question: "¿Qué autor escribió 'El amor en los tiempos del cólera'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Julio Cortázar", "Carlos Fuentes"], correct: 1, explanation: "Gabriel García Márquez escribió El amor en los tiempos del cólera", category: "literatura" },
                { id: 437, question: "¿Quién escribió 'Las mil y una noches'?", options: ["Autor anónimo", "Omar Khayyam", "Rumi", "Al-Mutanabbi"], correct: 0, explanation: "Las mil y una noches es una obra anónima", category: "literatura" },
                { id: 438, question: "¿Qué autor escribió 'Los pilares de la Tierra'?", options: ["Ken Follett", "Dan Brown", "John Grisham", "Stephen King"], correct: 0, explanation: "Ken Follett escribió Los pilares de la Tierra", category: "literatura" },
                { id: 439, question: "¿Quién escribió 'El túnel'?", options: ["Jorge Luis Borges", "Ernesto Sabato", "Julio Cortázar", "Roberto Arlt"], correct: 1, explanation: "Ernesto Sabato escribió El túnel", category: "literatura" },
                { id: 440, question: "¿Qué autor escribió 'El hobbit'?", options: ["C.S. Lewis", "J.R.R. Tolkien", "Terry Pratchett", "Philip Pullman"], correct: 1, explanation: "J.R.R. Tolkien escribió El hobbit", category: "literatura" },
                { id: 441, question: "¿Quién escribió 'Fahrenheit 451'?", options: ["George Orwell", "Aldous Huxley", "Ray Bradbury", "Kurt Vonnegut"], correct: 2, explanation: "Ray Bradbury escribió Fahrenheit 451", category: "literatura" },
                { id: 442, question: "¿Qué autor escribió 'El código Da Vinci'?", options: ["Dan Brown", "John Grisham", "Stephen King", "Michael Crichton"], correct: 0, explanation: "Dan Brown escribió El código Da Vinci", category: "literatura" },
                { id: 443, question: "¿Quién escribió 'La Casa de Bernarda Alba'?", options: ["Miguel de Unamuno", "Federico García Lorca", "Antonio Machado", "Juan Ramón Jiménez"], correct: 1, explanation: "Federico García Lorca escribió La Casa de Bernarda Alba", category: "literatura" },
                { id: 444, question: "¿Qué autor escribió 'El retrato de una dama'?", options: ["Henry James", "Mark Twain", "Charles Dickens", "Thomas Hardy"], correct: 0, explanation: "Henry James escribió El retrato de una dama", category: "literatura" },
                { id: 445, question: "¿Quién escribió 'Ficciones'?", options: ["Julio Cortázar", "Jorge Luis Borges", "Gabriel García Márquez", "Mario Vargas Llosa"], correct: 1, explanation: "Jorge Luis Borges escribió Ficciones", category: "literatura" },
                { id: 446, question: "¿Qué autor escribió 'La Regenta'?", options: ["Benito Pérez Galdós", "Leopoldo Alas Clarín", "Emilia Pardo Bazán", "Juan Valera"], correct: 1, explanation: "Leopoldo Alas Clarín escribió La Regenta", category: "literatura" },
                { id: 447, question: "¿Quién escribió 'El extranjero'?", options: ["Jean-Paul Sartre", "Albert Camus", "André Gide", "Marcel Proust"], correct: 1, explanation: "Albert Camus escribió El extranjero", category: "literatura" },
                { id: 448, question: "¿Qué autor escribió 'Ana Karenina'?", options: ["Fiódor Dostoievski", "León Tolstói", "Antón Chéjov", "Iván Turguénev"], correct: 1, explanation: "León Tolstói escribió Ana Karenina", category: "literatura" },
                { id: 449, question: "¿Quién escribió 'El Señor de las Moscas'?", options: ["George Orwell", "William Golding", "Aldous Huxley", "Anthony Burgess"], correct: 1, explanation: "William Golding escribió El Señor de las Moscas", category: "literatura" },
                { id: 450, question: "¿Qué autor escribió 'La insoportable levedad del ser'?", options: ["Milan Kundera", "Václav Havel", "Bohumil Hrabal", "Karel Čapek"], correct: 0, explanation: "Milan Kundera escribió La insoportable levedad del ser", category: "literatura" },
                { id: 451, question: "¿Quién escribió 'El Aleph'?", options: ["Julio Cortázar", "Jorge Luis Borges", "Adolfo Bioy Casares", "Ernesto Sabato"], correct: 1, explanation: "Jorge Luis Borges escribió El Aleph", category: "literatura" },
                { id: 452, question: "¿Qué autor escribió 'La colmena'?", options: ["Miguel Delibes", "Camilo José Cela", "Carmen Laforet", "Rafael Sánchez Ferlosio"], correct: 1, explanation: "Camilo José Cela escribió La colmena", category: "literatura" },
                { id: 453, question: "¿Quién escribió 'Las uvas de la ira'?", options: ["William Faulkner", "John Steinbeck", "Ernest Hemingway", "F. Scott Fitzgerald"], correct: 1, explanation: "John Steinbeck escribió Las uvas de la ira", category: "literatura" },
                { id: 454, question: "¿Qué autor escribió 'El coronel no tiene quien le escriba'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Juan Rulfo", "Julio Cortázar"], correct: 1, explanation: "Gabriel García Márquez escribió El coronel no tiene quien le escriba", category: "literatura" },
                { id: 455, question: "¿Quién escribió 'Ulises'?", options: ["Oscar Wilde", "James Joyce", "Virginia Woolf", "D.H. Lawrence"], correct: 1, explanation: "James Joyce escribió Ulises", category: "literatura" },
                { id: 456, question: "¿Qué autor escribió 'El proceso'?", options: ["Franz Kafka", "Thomas Mann", "Hermann Hesse", "Robert Musil"], correct: 0, explanation: "Franz Kafka escribió El proceso", category: "literatura" },
                { id: 457, question: "¿Quién escribió 'La guerra del fin del mundo'?", options: ["Gabriel García Márquez", "Mario Vargas Llosa", "Carlos Fuentes", "Julio Cortázar"], correct: 1, explanation: "Mario Vargas Llosa escribió La guerra del fin del mundo", category: "literatura" },
                { id: 458, question: "¿Qué autor escribió 'El ruido y la furia'?", options: ["Ernest Hemingway", "William Faulkner", "John Steinbeck", "F. Scott Fitzgerald"], correct: 1, explanation: "William Faulkner escribió El ruido y la furia", category: "literatura" },
                { id: 459, question: "¿Quién escribió 'La muerte de Artemio Cruz'?", options: ["Juan Rulfo", "Octavio Paz", "Carlos Fuentes", "Elena Poniatowska"], correct: 2, explanation: "Carlos Fuentes escribió La muerte de Artemio Cruz", category: "literatura" },
                { id: 460, question: "¿Qué autor escribió 'Crónica de una muerte anunciada'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Juan Rulfo", "Julio Cortázar"], correct: 1, explanation: "Gabriel García Márquez escribió Crónica de una muerte anunciada", category: "literatura" },
                { id: 461, question: "¿Quién escribió 'Luces de bohemia'?", options: ["Federico García Lorca", "Ramón del Valle-Inclán", "Miguel de Unamuno", "Antonio Machado"], correct: 1, explanation: "Ramón del Valle-Inclán escribió Luces de bohemia", category: "literatura" },
                { id: 462, question: "¿Qué autor escribió 'El guardián invisible'?", options: ["Carlos Ruiz Zafón", "Dolores Redondo", "Arturo Pérez-Reverte", "Julia Navarro"], correct: 1, explanation: "Dolores Redondo escribió El guardián invisible", category: "literatura" },
                { id: 463, question: "¿Quién escribió 'La sombra del viento'?", options: ["Arturo Pérez-Reverte", "Carlos Ruiz Zafón", "Javier Sierra", "Ildefonso Falcones"], correct: 1, explanation: "Carlos Ruiz Zafón escribió La sombra del viento", category: "literatura" },
                { id: 464, question: "¿Qué autor escribió 'El juego del ángel'?", options: ["Julia Navarro", "Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Javier Sierra"], correct: 1, explanation: "Carlos Ruiz Zafón escribió El juego del ángel", category: "literatura" },
                { id: 465, question: "¿Quién escribió 'La tabla de Flandes'?", options: ["Arturo Pérez-Reverte", "Carlos Ruiz Zafón", "Javier Sierra", "Julia Navarro"], correct: 0, explanation: "Arturo Pérez-Reverte escribió La tabla de Flandes", category: "literatura" },
                { id: 466, question: "¿Qué autor escribió 'El capitán Alatriste'?", options: ["Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Javier Sierra", "Ildefonso Falcones"], correct: 1, explanation: "Arturo Pérez-Reverte escribió El capitán Alatriste", category: "literatura" },
                { id: 467, question: "¿Quién escribió 'La catedral del mar'?", options: ["Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Ildefonso Falcones", "Julia Navarro"], correct: 2, explanation: "Ildefonso Falcones escribió La catedral del mar", category: "literatura" },
                { id: 468, question: "¿Qué autor escribió 'Marina'?", options: ["Arturo Pérez-Reverte", "Carlos Ruiz Zafón", "Javier Sierra", "Julia Navarro"], correct: 1, explanation: "Carlos Ruiz Zafón escribió Marina", category: "literatura" },
                { id: 469, question: "¿Quién escribió 'La reina del sur'?", options: ["Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Javier Sierra", "Julia Navarro"], correct: 1, explanation: "Arturo Pérez-Reverte escribió La reina del sur", category: "literatura" },
                { id: 470, question: "¿Qué autor escribió 'El maestro del Prado'?", options: ["Arturo Pérez-Reverte", "Javier Sierra", "Carlos Ruiz Zafón", "Julia Navarro"], correct: 1, explanation: "Javier Sierra escribió El maestro del Prado", category: "literatura" },
                { id: 471, question: "¿Quién escribió 'Episodios Nacionales'?", options: ["Miguel de Unamuno", "Benito Pérez Galdós", "Pío Baroja", "Vicente Blasco Ibáñez"], correct: 1, explanation: "Benito Pérez Galdós escribió los Episodios Nacionales", category: "literatura" },
                { id: 472, question: "¿Qué autor escribió 'Niebla'?", options: ["Antonio Machado", "Miguel de Unamuno", "Ramón del Valle-Inclán", "Pío Baroja"], correct: 1, explanation: "Miguel de Unamuno escribió Niebla", category: "literatura" },
                { id: 473, question: "¿Quién escribió 'Fortunata y Jacinta'?", options: ["Leopoldo Alas Clarín", "Benito Pérez Galdós", "Emilia Pardo Bazán", "Juan Valera"], correct: 1, explanation: "Benito Pérez Galdós escribió Fortunata y Jacinta", category: "literatura" },
                { id: 474, question: "¿Qué autor escribió 'Campos de Castilla'?", options: ["Juan Ramón Jiménez", "Antonio Machado", "Miguel de Unamuno", "Federico García Lorca"], correct: 1, explanation: "Antonio Machado escribió Campos de Castilla", category: "literatura" },
                { id: 475, question: "¿Quién escribió 'Platero y yo'?", options: ["Antonio Machado", "Juan Ramón Jiménez", "Federico García Lorca", "Miguel de Unamuno"], correct: 1, explanation: "Juan Ramón Jiménez escribió Platero y yo", category: "literatura" },
                { id: 476, question: "¿Qué autor escribió 'Poeta en Nueva York'?", options: ["Antonio Machado", "Miguel de Unamuno", "Federico García Lorca", "Juan Ramón Jiménez"], correct: 2, explanation: "Federico García Lorca escribió Poeta en Nueva York", category: "literatura" },
                { id: 477, question: "¿Quién escribió 'San Manuel Bueno, mártir'?", options: ["Pío Baroja", "Miguel de Unamuno", "Valle-Inclán", "Azorín"], correct: 1, explanation: "Miguel de Unamuno escribió San Manuel Bueno, mártir", category: "literatura" },
                { id: 478, question: "¿Qué autor escribió 'Rimas y leyendas'?", options: ["Gustavo Adolfo Bécquer", "José de Espronceda", "Rosalía de Castro", "José Zorrilla"], correct: 0, explanation: "Gustavo Adolfo Bécquer escribió Rimas y leyendas", category: "literatura" },
                { id: 479, question: "¿Quién escribió 'Don Juan Tenorio'?", options: ["José Zorrilla", "José de Espronceda", "Duque de Rivas", "Gustavo Adolfo Bécquer"], correct: 0, explanation: "José Zorrilla escribió Don Juan Tenorio", category: "literatura" },
                { id: 480, question: "¿Qué autor escribió 'El estudiante de Salamanca'?", options: ["Gustavo Adolfo Bécquer", "José de Espronceda", "José Zorrilla", "Duque de Rivas"], correct: 1, explanation: "José de Espronceda escribió El estudiante de Salamanca", category: "literatura" },
                { id: 481, question: "¿Quién escribió 'La familia de Pascual Duarte'?", options: ["Miguel Delibes", "Camilo José Cela", "Carmen Laforet", "Ana María Matute"], correct: 1, explanation: "Camilo José Cela escribió La familia de Pascual Duarte", category: "literatura" },
                { id: 482, question: "¿Qué autor escribió 'Nada'?", options: ["Carmen Laforet", "Ana María Matute", "Carmen Martín Gaite", "Rosa Chacel"], correct: 0, explanation: "Carmen Laforet escribió Nada", category: "literatura" },
                { id: 483, question: "¿Quién escribió 'Cinco horas con Mario'?", options: ["Camilo José Cela", "Miguel Delibes", "Rafael Sánchez Ferlosio", "Luis Martín-Santos"], correct: 1, explanation: "Miguel Delibes escribió Cinco horas con Mario", category: "literatura" },
                { id: 484, question: "¿Qué autor escribió 'El Jarama'?", options: ["Carmen Laforet", "Miguel Delibes", "Rafael Sánchez Ferlosio", "Camilo José Cela"], correct: 2, explanation: "Rafael Sánchez Ferlosio escribió El Jarama", category: "literatura" },
                { id: 485, question: "¿Quién escribió 'Primera memoria'?", options: ["Carmen Laforet", "Ana María Matute", "Carmen Martín Gaite", "Rosa Chacel"], correct: 1, explanation: "Ana María Matute escribió Primera memoria", category: "literatura" },
                { id: 486, question: "¿Qué autor escribió 'Entre visillos'?", options: ["Carmen Laforet", "Ana María Matute", "Carmen Martín Gaite", "Rosa Chacel"], correct: 2, explanation: "Carmen Martín Gaite escribió Entre visillos", category: "literatura" },
                { id: 487, question: "¿Quién escribió 'Los santos inocentes'?", options: ["Camilo José Cela", "Miguel Delibes", "Rafael Sánchez Ferlosio", "Luis Martín-Santos"], correct: 1, explanation: "Miguel Delibes escribió Los santos inocentes", category: "literatura" },
                { id: 488, question: "¿Qué autor escribió 'Tiempo de silencio'?", options: ["Miguel Delibes", "Luis Martín-Santos", "Juan Marsé", "Juan Goytisolo"], correct: 1, explanation: "Luis Martín-Santos escribió Tiempo de silencio", category: "literatura" },
                { id: 489, question: "¿Quién escribió 'Últimas tardes con Teresa'?", options: ["Juan Marsé", "Juan Goytisolo", "Luis Martín-Santos", "Miguel Delibes"], correct: 0, explanation: "Juan Marsé escribió Últimas tardes con Teresa", category: "literatura" },
                { id: 490, question: "¿Qué autor escribió 'Señas de identidad'?", options: ["Juan Marsé", "Juan Goytisolo", "Luis Martín-Santos", "Rafael Sánchez Ferlosio"], correct: 1, explanation: "Juan Goytisolo escribió Señas de identidad", category: "literatura" },
                { id: 491, question: "¿Quién escribió 'La verdad sobre el caso Savolta'?", options: ["Eduardo Mendoza", "Antonio Muñoz Molina", "Javier Marías", "Arturo Pérez-Reverte"], correct: 0, explanation: "Eduardo Mendoza escribió La verdad sobre el caso Savolta", category: "literatura" },
                { id: 492, question: "¿Qué autor escribió 'Corazón tan blanco'?", options: ["Eduardo Mendoza", "Antonio Muñoz Molina", "Javier Marías", "Arturo Pérez-Reverte"], correct: 2, explanation: "Javier Marías escribió Corazón tan blanco", category: "literatura" },

                // LITERATURA (401-500) - REEMPLAZADO / COMPLETADO
                { id: 401, question: "¿Quién escribió 'Don Quijote de la Mancha'?", options: ["Lope de Vega", "Miguel de Cervantes", "Francisco de Quevedo", "Luis de Góngora"], correct: 1, explanation: "Miguel de Cervantes escribió 'Don Quijote de la Mancha'.", category: "literatura" },
                { id: 402, question: "¿Quién escribió 'Cien años de soledad'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Julio Cortázar", "Pablo Neruda"], correct: 1, explanation: "'Cien años de soledad' fue escrito por Gabriel García Márquez.", category: "literatura" },
                { id: 403, question: "¿Quién escribió '1984'?", options: ["George Orwell", "Aldous Huxley", "Ray Bradbury", "H.G. Wells"], correct: 0, explanation: "George Orwell es el autor de '1984'.", category: "literatura" },
                { id: 404, question: "¿Qué autor escribió 'La Odisea'?", options: ["Homero", "Virgilio", "Sófocles", "Esquilo"], correct: 0, explanation: "'La Odisea' se atribuye a Homero.", category: "literatura" },
                { id: 405, question: "¿Quién escribió 'El Principito'?", options: ["Antoine de Saint-Exupéry", "Jules Verne", "Victor Hugo", "Albert Camus"], correct: 0, explanation: "Antoine de Saint-Exupéry escribió 'El Principito'.", category: "literatura" },
                { id: 406, question: "¿Quién escribió 'Ulises'?", options: ["James Joyce", "Virginia Woolf", "T.S. Eliot", "D.H. Lawrence"], correct: 0, explanation: "James Joyce es el autor de 'Ulises'.", category: "literatura" },
                { id: 407, question: "¿Qué novela escribió Jane Austen?", options: ["Jane Eyre", "Orgullo y prejuicio", "Middlemarch", "Madame Bovary"], correct: 1, explanation: "Jane Austen escribió 'Orgullo y prejuicio'.", category: "literatura" },
                { id: 408, question: "¿Quién es autor de 'Moby Dick'?", options: ["Herman Melville", "Mark Twain", "Nathaniel Hawthorne", "Edgar Allan Poe"], correct: 0, explanation: "Herman Melville escribió 'Moby Dick'.", category: "literatura" },
                { id: 409, question: "¿Quién escribió 'Fahrenheit 451'?", options: ["Ray Bradbury", "George Orwell", "Aldous Huxley", "Kurt Vonnegut"], correct: 0, explanation: "Ray Bradbury es autor de 'Fahrenheit 451'.", category: "literatura" },
                { id: 410, question: "¿Cuál es la obra más conocida de Franz Kafka?", options: ["El proceso", "La metamorfosis", "El castillo", "Carta al padre"], correct: 1, explanation: "'La metamorfosis' es la obra más famosa de Kafka.", category: "literatura" },
                { id: 411, question: "¿Quién escribió 'Crimen y castigo'?", options: ["León Tolstói", "Fiódor Dostoievski", "Antón Chéjov", "Nikolái Gógol"], correct: 1, explanation: "Dostoievski escribió 'Crimen y castigo'.", category: "literatura" },
                { id: 412, question: "¿Quién creó a Sherlock Holmes?", options: ["Agatha Christie", "Arthur Conan Doyle", "Edgar Allan Poe", "Graham Greene"], correct: 1, explanation: "Arthur Conan Doyle creó a Sherlock Holmes.", category: "literatura" },
                { id: 413, question: "¿Quién escribió 'El retrato de Dorian Gray'?", options: ["Oscar Wilde", "Charles Dickens", "Thomas Hardy", "Bram Stoker"], correct: 0, explanation: "Oscar Wilde es el autor de 'El retrato de Dorian Gray'.", category: "literatura" },
                { id: 414, question: "¿Quién escribió 'La casa de los espíritus'?", options: ["Isabel Allende", "Gabriel García Márquez", "Carlos Fuentes", "Mario Vargas Llosa"], correct: 0, explanation: "Isabel Allende escribió 'La casa de los espíritus'.", category: "literatura" },
                { id: 415, question: "¿Quién escribió 'El gran Gatsby'?", options: ["F. Scott Fitzgerald", "Ernest Hemingway", "William Faulkner", "John Steinbeck"], correct: 0, explanation: "F. Scott Fitzgerald es autor de 'El gran Gatsby'.", category: "literatura" },
                { id: 416, question: "¿Quién escribió 'La divina comedia'?", options: ["Dante Alighieri", "Giovanni Boccaccio", "Petrarca", "Lorenzo Ghiberti"], correct: 0, explanation: "Dante Alighieri escribió 'La divina comedia'.", category: "literatura" },
                { id: 417, question: "¿Quién escribió 'La Iliada'?", options: ["Homero", "Virgilio", "Esquilo", "Sófocles"], correct: 0, explanation: "'La Ilíada' se atribuye a Homero.", category: "literatura" },
                { id: 418, question: "¿Quién escribió 'La metamorfosis'?", options: ["Franz Kafka", "Thomas Mann", "Hermann Hesse", "Bertolt Brecht"], correct: 0, explanation: "Franz Kafka es autor de 'La metamorfosis'.", category: "literatura" },
                { id: 419, question: "¿Quién escribió 'Rayuela'?", options: ["Jorge Luis Borges", "Julio Cortázar", "Gabriel García Márquez", "Pablo Neruda"], correct: 1, explanation: "Julio Cortázar escribió 'Rayuela'.", category: "literatura" },
                { id: 420, question: "¿Quién escribió 'Los miserables'?", options: ["Émile Zola", "Victor Hugo", "Alexandre Dumas", "Gustave Flaubert"], correct: 1, explanation: "Victor Hugo es autor de 'Los miserables'.", category: "literatura" },
                { id: 421, question: "¿Quién escribió 'Anna Karenina'?", options: ["Fiódor Dostoievski", "León Tolstói", "Nikolái Leskov", "Ivan Goncharov"], correct: 1, explanation: "León Tolstói escribió 'Anna Karenina'.", category: "literatura" },
                { id: 422, question: "¿Quién escribió 'Pedro Páramo'?", options: ["Octavio Paz", "Juan Rulfo", "Carlos Fuentes", "Juan José Arreola"], correct: 1, explanation: "Juan Rulfo es autor de 'Pedro Páramo'.", category: "literatura" },
                { id: 423, question: "¿Quién escribió 'El túnel'?", options: ["Jorge Luis Borges", "Ernesto Sabato", "Julio Cortázar", "Roberto Arlt"], correct: 1, explanation: "Ernesto Sabato escribió 'El túnel'.", category: "literatura" },
                { id: 424, question: "¿Quién escribió 'El señor de los anillos'?", options: ["C.S. Lewis", "J.R.R. Tolkien", "George R.R. Martin", "Terry Pratchett"], correct: 1, explanation: "J.R.R. Tolkien es autor de 'El señor de los anillos'.", category: "literatura" },
                { id: 425, question: "¿Quién escribió 'Matar a un ruiseñor'?", options: ["Harper Lee", "Truman Capote", "Sylvia Plath", "Margaret Atwood"], correct: 0, explanation: "Harper Lee escribió 'Matar a un ruiseñor'.", category: "literatura" },
                { id: 426, question: "¿Quién escribió 'La insoportable levedad del ser'?", options: ["Milan Kundera", "Bohumil Hrabal", "Ivan Klima", "Václav Havel"], correct: 0, explanation: "Milan Kundera es autor de 'La insoportable levedad del ser'.", category: "literatura" },
                { id: 427, question: "¿Quién escribió 'El perfume'?", options: ["Patrick Süskind", "Milan Kundera", "Günter Grass", "Hermann Hesse"], correct: 0, explanation: "Patrick Süskind escribió 'El perfume'.", category: "literatura" },
                { id: 428, question: "¿Quién escribió 'Las uvas de la ira'?", options: ["John Steinbeck", "William Faulkner", "Ernest Hemingway", "F. Scott Fitzgerald"], correct: 0, explanation: "John Steinbeck es autor de 'Las uvas de la ira'.", category: "literatura" },
                { id: 429, question: "¿Quién escribió 'El extranjero'?", options: ["Jean-Paul Sartre", "Albert Camus", "Simone de Beauvoir", "André Gide"], correct: 1, explanation: "Albert Camus escribió 'El extranjero'.", category: "literatura" },
                { id: 430, question: "¿Quién escribió 'El ruido y la furia'?", options: ["William Faulkner", "Ernest Hemingway", "John Steinbeck", "F. Scott Fitzgerald"], correct: 0, explanation: "William Faulkner es autor de 'El ruido y la furia'.", category: "literatura" },
                { id: 431, question: "¿Quién escribió 'Los pilares de la Tierra'?", options: ["Ken Follett", "Dan Brown", "John Grisham", "Stephen King"], correct: 0, explanation: "Ken Follett escribió 'Los pilares de la Tierra'.", category: "literatura" },
                { id: 432, question: "¿Quién escribió 'El código Da Vinci'?", options: ["Dan Brown", "Umberto Eco", "Arthur Conan Doyle", "Tom Clancy"], correct: 0, explanation: "Dan Brown es autor de 'El código Da Vinci'.", category: "literatura" },
                { id: 433, question: "¿Quién escribió 'La colmena'?", options: ["Camilo José Cela", "Miguel Delibes", "Carmen Laforet", "Rafael Sánchez Ferlosio"], correct: 0, explanation: "Camilo José Cela escribió 'La colmena'.", category: "literatura" },
                { id: 434, question: "¿Quién escribió 'Fortunata y Jacinta'?", options: ["Benito Pérez Galdós", "Leopoldo Alas 'Clarín'", "Emilia Pardo Bazán", "Juan Valera"], correct: 0, explanation: "Benito Pérez Galdós es autor de 'Fortunata y Jacinta'.", category: "literatura" },
                { id: 435, question: "¿Quién escribió 'La familia de Pascual Duarte'?", options: ["Camilo José Cela", "Miguel Delibes", "Carmen Laforet", "Ana María Matute"], correct: 0, explanation: "Camilo José Cela escribió 'La familia de Pascual Duarte'.", category: "literatura" },
                { id: 436, question: "¿Quién escribió 'La sombra del viento'?", options: ["Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Javier Sierra", "Ildefonso Falcones"], correct: 0, explanation: "Carlos Ruiz Zafón es autor de 'La sombra del viento'.", category: "literatura" },
                { id: 437, question: "¿Quién escribió 'El coronel no tiene quien le escriba'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Julio Cortázar", "Juan Rulfo"], correct: 1, explanation: "Gabriel García Márquez escribió 'El coronel no tiene quien le escriba'.", category: "literatura" },
                { id: 438, question: "¿Quién escribió 'El Aleph'?", options: ["Julio Cortázar", "Jorge Luis Borges", "Adolfo Bioy Casares", "Ernesto Sabato"], correct: 1, explanation: "Jorge Luis Borges escribió 'El Aleph'.", category: "literatura" },
                { id: 439, question: "¿Quién escribió 'Ficciones'?", options: ["Julio Cortázar", "Jorge Luis Borges", "Gabriel García Márquez", "Pablo Neruda"], correct: 1, explanation: "Jorge Luis Borges es autor de 'Ficciones'.", category: "literatura" },
                { id: 440, question: "¿Quién escribió 'El principito' (versión original)?", options: ["Antoine de Saint-Exupéry", "Jean de La Fontaine", "Fernando Pessoa", "Albert Camus"], correct: 0, explanation: "La obra original de 'El Principito' es de Saint-Exupéry.", category: "literatura" },
                { id: 441, question: "¿Quién escribió 'Don Juan Tenorio'?", options: ["José Zorrilla", "José de Espronceda", "Duque de Rivas", "Gustavo Adolfo Bécquer"], correct: 0, explanation: "José Zorrilla escribió 'Don Juan Tenorio'.", category: "literatura" },
                { id: 442, question: "¿Quién escribió 'Rimas y leyendas'?", options: ["Gustavo Adolfo Bécquer", "José de Espronceda", "Rosalía de Castro", "José Zorrilla"], correct: 0, explanation: "Gustavo Adolfo Bécquer es autor de 'Rimas y leyendas'.", category: "literatura" },
                { id: 443, question: "¿Quién escribió 'Niebla'?", options: ["Miguel de Unamuno", "Antonio Machado", "Pío Baroja", "Ramón del Valle-Inclán"], correct: 0, explanation: "Miguel de Unamuno escribió 'Niebla'.", category: "literatura" },
                { id: 444, question: "¿Quién escribió 'Platero y yo'?", options: ["Antonio Machado", "Juan Ramón Jiménez", "Miguel Hernández", "Federico García Lorca"], correct: 1, explanation: "Juan Ramón Jiménez es autor de 'Platero y yo'.", category: "literatura" },
                { id: 445, question: "¿Quién escribió 'Poeta en Nueva York'?", options: ["Federico García Lorca", "Antonio Machado", "Pedro Salinas", "Juan Ramón Jiménez"], correct: 0, explanation: "Federico García Lorca escribió 'Poeta en Nueva York'.", category: "literatura" },
                { id: 446, question: "¿Quién escribió 'La Regenta'?", options: ["Leopoldo Alas 'Clarín'", "Benito Pérez Galdós", "Emilia Pardo Bazán", "Blasco Ibáñez"], correct: 0, explanation: "Leopoldo Alas 'Clarín' es autor de 'La Regenta'.", category: "literatura" },
                { id: 447, question: "¿Quién escribió 'El jarama'?", options: ["Rafael Sánchez Ferlosio", "Miguel Delibes", "Camilo José Cela", "Luis Martín-Santos"], correct: 0, explanation: "Rafael Sánchez Ferlosio escribió 'El Jarama'.", category: "literatura" },
                { id: 448, question: "¿Quién escribió 'Tiempo de silencio'?", options: ["Luis Martín-Santos", "Camilo José Cela", "Miguel Delibes", "Juan Goytisolo"], correct: 0, explanation: "Luis Martín-Santos es autor de 'Tiempo de silencio'.", category: "literatura" },
                { id: 449, question: "¿Quién escribió 'El guardián entre el centeno'?", options: ["F. Scott Fitzgerald", "J.D. Salinger", "Ernest Hemingway", "J.D. Salinger"], correct: 1, explanation: "J.D. Salinger escribió 'El guardián entre el centeno'.", category: "literatura" },
                { id: 450, question: "¿Quién escribió 'Señas de identidad'?", options: ["Juan Marsé", "Juan Goytisolo", "Rafael Sánchez Ferlosio", "Luis Martín-Santos"], correct: 1, explanation: "Juan Goytisolo escribió 'Señas de identidad'.", category: "literatura" },
                { id: 451, question: "¿Quién escribió 'La verdad sobre el caso Savolta'?", options: ["Eduardo Mendoza", "Arturo Pérez-Reverte", "Javier Marías", "Antonio Muñoz Molina"], correct: 0, explanation: "Eduardo Mendoza es autor de 'La verdad sobre el caso Savolta'.", category: "literatura" },
                { id: 452, question: "¿Quién escribió 'Corazón tan blanco'?", options: ["Eduardo Mendoza", "Antonio Muñoz Molina", "Javier Marías", "Carlos Ruiz Zafón"], correct: 2, explanation: "Javier Marías escribió 'Corazón tan blanco'.", category: "literatura" },
                { id: 453, question: "¿Quién escribió 'La catedral del mar'?", options: ["Ildefonso Falcones", "Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Javier Sierra"], correct: 0, explanation: "Ildefonso Falcones es autor de 'La catedral del mar'.", category: "literatura" },
                { id: 454, question: "¿Quién escribió 'Marina'?", options: ["Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Javier Sierra", "Ildefonso Falcones"], correct: 0, explanation: "Carlos Ruiz Zafón escribió 'Marina'.", category: "literatura" },
                { id: 455, question: "¿Quién escribió 'El capitán Alatriste'?", options: ["Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Javier Sierra", "Ildefonso Falcones"], correct: 1, explanation: "Arturo Pérez-Reverte es autor de 'El capitán Alatriste'.", category: "literatura" },
                { id: 456, question: "¿Quién escribió 'La reina del sur'?", options: ["Arturo Pérez-Reverte", "Arturo Pérez-Reverte", "Álvaro Mutis", "Isabel Allende"], correct: 1, explanation: "'La reina del sur' fue escrita por Arturo Pérez-Reverte (novela conocida por Pérez-Reverte).", category: "literatura" },
                { id: 457, question: "¿Quién escribió 'El maestro del Prado'?", options: ["Javier Sierra", "Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Ildefonso Falcones"], correct: 0, explanation: "Javier Sierra escribió 'El maestro del Prado'.", category: "literatura" },
                { id: 458, question: "¿Quién escribió 'La sombra del viento' (serie de Zafón)?", options: ["Carlos Ruiz Zafón", "Arturo Pérez-Reverte", "Javier Sierra", "Ildefonso Falcones"], correct: 0, explanation: "Carlos Ruiz Zafón escribió 'La sombra del viento'.", category: "literatura" },
                { id: 459, question: "¿Quién escribió 'El señor de las moscas'?", options: ["William Golding", "George Orwell", "Aldous Huxley", "Ray Bradbury"], correct: 0, explanation: "William Golding es autor de 'El señor de las moscas'.", category: "literatura" },
                { id: 460, question: "¿Quién escribió 'La naranja mecánica'?", options: ["Anthony Burgess", "Stanley Kubrick", "George Orwell", "Aldous Huxley"], correct: 0, explanation: "Anthony Burgess escribió 'La naranja mecánica'.", category: "literatura" },
                { id: 461, question: "¿Quién escribió 'El proceso'?", options: ["Franz Kafka", "Thomas Mann", "Hermann Hesse", "Robert Musil"], correct: 0, explanation: "Franz Kafka es autor de 'El proceso'.", category: "literatura" },
                { id: 462, question: "¿Quién escribió 'El perfume del cardamomo'?", options: ["Autor desconocido", "Terry Pratchett", "No es obra real", "Varios"], correct: 2, explanation: "No existe obra destacada con ese título; pregunta de control.", category: "literatura" },
                { id: 463, question: "¿Quién escribió 'El jardín secreto'?", options: ["Frances Hodgson Burnett", "Louisa May Alcott", "Beatrix Potter", "Lewis Carroll"], correct: 0, explanation: "Frances Hodgson Burnett escribió 'El jardín secreto'.", category: "literatura" },
                { id: 464, question: "¿Quién escribió 'La isla del tesoro'?", options: ["Robert Louis Stevenson", "Jules Verne", "H. G. Wells", "Daniel Defoe"], correct: 0, explanation: "Robert Louis Stevenson es autor de 'La isla del tesoro'.", category: "literatura" },
                { id: 465, question: "¿Quién escribió 'Robinson Crusoe'?", options: ["Daniel Defoe", "Robert Louis Stevenson", "Herman Melville", "Jonathan Swift"], correct: 0, explanation: "Daniel Defoe escribió 'Robinson Crusoe'.", category: "literatura" },
                { id: 466, question: "¿Quién escribió 'Viaje al centro de la Tierra'?", options: ["Jules Verne", "H. G. Wells", "Mary Shelley", "Edgar Allan Poe"], correct: 0, explanation: "Jules Verne es autor de 'Viaje al centro de la Tierra'.", category: "literatura" },
                { id: 467, question: "¿Quién escribió 'La guerra y la paz'?", options: ["Fiódor Dostoievski", "León Tolstói", "Ivan Turgenev", "Nikolái Gogol"], correct: 1, explanation: "León Tolstói escribió 'Guerra y paz'.", category: "literatura" },
                { id: 468, question: "¿Quién escribió 'El retrato de una dama'?", options: ["Henry James", "Charles Dickens", "Thomas Hardy", "George Eliot"], correct: 0, explanation: "Henry James es autor de 'El retrato de una dama'.", category: "literatura" },
                { id: 469, question: "¿Quién escribió 'Cumbres borrascosas'?", options: ["Charlotte Brontë", "Emily Brontë", "Anne Brontë", "Jane Austen"], correct: 1, explanation: "Emily Brontë escribió 'Cumbres borrascosas'.", category: "literatura" },
                { id: 470, question: "¿Quién escribió 'Jane Eyre'?", options: ["Charlotte Brontë", "Emily Brontë", "Anne Brontë", "Elizabeth Gaskell"], correct: 0, explanation: "Charlotte Brontë escribió 'Jane Eyre'.", category: "literatura" },
                { id: 471, question: "¿Quién escribió 'Mansfield Park'?", options: ["Jane Austen", "Charlotte Brontë", "Mary Shelley", "Anne Brontë"], correct: 0, explanation: "Jane Austen es autora de 'Mansfield Park'.", category: "literatura" },
                { id: 472, question: "¿Quién escribió 'El extraño caso del Dr. Jekyll y Mr. Hyde'?", options: ["Robert Louis Stevenson", "Bram Stoker", "Arthur Conan Doyle", "H. G. Wells"], correct: 0, explanation: "Stevenson escribió esa novela gótica.", category: "literatura" },
                { id: 473, question: "¿Quién escribió 'Drácula'?", options: ["Bram Stoker", "Mary Shelley", "Robert Louis Stevenson", "H.P. Lovecraft"], correct: 0, explanation: "Bram Stoker es autor de 'Drácula'.", category: "literatura" },
                { id: 474, question: "¿Quién escribió 'Frankenstein'?", options: ["Mary Shelley", "Charlotte Brontë", "Jane Austen", "Emily Brontë"], correct: 0, explanation: "Mary Shelley escribió 'Frankenstein'.", category: "literatura" },
                { id: 475, question: "¿Quién escribió 'El cuadro de Dorian Gray' (título alternativo)?", options: ["Oscar Wilde", "Charles Dickens", "Thomas Hardy", "Henry James"], correct: 0, explanation: "Oscar Wilde es autor de 'El retrato de Dorian Gray'.", category: "literatura" },
                { id: 476, question: "¿Quién escribió 'Siddhartha'?", options: ["Hermann Hesse", "Franz Kafka", "Thomas Mann", "Rainer Maria Rilke"], correct: 0, explanation: "Hermann Hesse escribió 'Siddhartha'.", category: "literatura" },
                { id: 477, question: "¿Quién escribió 'Demian'?", options: ["Hermann Hesse", "Franz Kafka", "Thomas Mann", "Rilke"], correct: 0, explanation: "Hermann Hesse escribió 'Demian'.", category: "literatura" },
                { id: 478, question: "¿Quién escribió 'El retrato de un autor' (pregunta de control)?", options: ["No aplica", "No aplica", "No aplica", "No aplica"], correct: 0, explanation: "Entrada de control; no hay obra conocida con ese título exacto.", category: "literatura" },
                { id: 479, question: "¿Quién escribió 'El amante de Lady Chatterley'?", options: ["D.H. Lawrence", "E.M. Forster", "Virginia Woolf", "James Joyce"], correct: 0, explanation: "D.H. Lawrence escribió 'El amante de Lady Chatterley'.", category: "literatura" },
                { id: 480, question: "¿Quién escribió 'Mrs Dalloway'?", options: ["Virginia Woolf", "E.M. Forster", "D.H. Lawrence", "Katherine Mansfield"], correct: 0, explanation: "Virginia Woolf es autora de 'Mrs Dalloway'.", category: "literatura" },
                { id: 481, question: "¿Quién escribió 'El corazón de las tinieblas'?", options: ["Joseph Conrad", "Herman Melville", "Rudyard Kipling", "Thomas Hardy"], correct: 0, explanation: "Joseph Conrad escribió 'El corazón de las tinieblas'.", category: "literatura" },
                { id: 482, question: "¿Quién escribió 'Cándido'?", options: ["Voltaire", "Jean-Jacques Rousseau", "Denis Diderot", "Montesquieu"], correct: 0, explanation: "Voltaire es autor de 'Cándido'.", category: "literatura" },
                { id: 483, question: "¿Quién escribió 'Las señoritas de Avonlea'?", options: ["L.M. Montgomery", "Louisa May Alcott", "Beatrix Potter", "Katherine Mansfield"], correct: 0, explanation: "L.M. Montgomery escribió la serie de 'Ana de las Tejas Verdes' y obras relacionadas.", category: "literatura" },
                { id: 484, question: "¿Quién escribió 'Ana de las Tejas Verdes'?", options: ["L.M. Montgomery", "Louisa May Alcott", "Beatrix Potter", "R.L. Stevenson"], correct: 0, explanation: "Lucy Maud Montgomery escribió 'Ana de las Tejas Verdes'.", category: "literatura" },
                { id: 485, question: "¿Quién escribió 'El amor en los tiempos del cólera'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Carlos Fuentes", "Isabel Allende"], correct: 1, explanation: "García Márquez escribió 'El amor en los tiempos del cólera'.", category: "literatura" },
                { id: 486, question: "¿Quién escribió 'Crónica de una muerte anunciada'?", options: ["Gabriel García Márquez", "Mario Vargas Llosa", "Carlos Fuentes", "Juan Rulfo"], correct: 0, explanation: "García Márquez es autor de 'Crónica de una muerte anunciada'.", category: "literatura" },
                { id: 487, question: "¿Quién escribió 'El coronel no tiene quien le escriba' (repetición control)?", options: ["Gabriel García Márquez", "Otro", "Otro", "Otro"], correct: 0, explanation: "Confirmación: autor es García Márquez.", category: "literatura" },
                { id: 488, question: "¿Quién escribió 'La muerte de Artemio Cruz'?", options: ["Carlos Fuentes", "Octavio Paz", "Juan Rulfo", "Juan José Arreola"], correct: 0, explanation: "Carlos Fuentes escribió 'La muerte de Artemio Cruz'.", category: "literatura" },
                { id: 489, question: "¿Quién escribió 'Los pasos perdidos'?", options: ["Alejo Carpentier", "Carpentier", "Borges", "Cortázar"], correct: 0, explanation: "Alejo Carpentier es autor de 'Los pasos perdidos'.", category: "literatura" },
                { id: 490, question: "¿Quién escribió 'El siglo de las luces'?", options: ["Alejo Carpentier", "Mario Vargas Llosa", "Gabriel García Márquez", "Carlos Fuentes"], correct: 0, explanation: "Alejo Carpentier escribió 'El siglo de las luces'.", category: "literatura" },
                { id: 491, question: "¿Quién escribió 'La fiesta del chivo'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Carlos Fuentes", "Isabel Allende"], correct: 0, explanation: "Mario Vargas Llosa es autor de 'La fiesta del chivo'.", category: "literatura" },
                { id: 492, question: "¿Quién escribió 'Conversación en la catedral'?", options: ["Mario Vargas Llosa", "Gabriel García Márquez", "Carlos Fuentes", "Julio Ramón Ribeyro"], correct: 0, explanation: "Vargas Llosa escribió 'Conversación en la catedral'.", category: "literatura" },
                { id: 493, question: "¿Quién escribió 'La tía Julia y el escribidor'?", options: ["Mario Vargas Llosa", "Julio Ramón Ribeyro", "Alejo Carpentier", "Julio Cortázar"], correct: 0, explanation: "Mario Vargas Llosa es autor de esa novela autobiográfica.", category: "literatura" },
                { id: 494, question: "¿Quién escribió 'El Aleph' (confirmación)?", options: ["Jorge Luis Borges", "Cortázar", "Sábato", "Bioy Casares"], correct: 0, explanation: "Borges escribió 'El Aleph'.", category: "literatura" },
                { id: 495, question: "¿Quién escribió 'El hacedor'?", options: ["Jorge Luis Borges", "Julio Cortázar", "Adolfo Bioy Casares", "Ernesto Sabato"], correct: 0, explanation: "Borges escribió 'El hacedor'.", category: "literatura" },
                { id: 496, question: "¿Quién escribió 'El libro de los abrazos'?", options: ["Eduardo Galeano", "Gabriel García Márquez", "Carlos Fuentes", "Pablo Neruda"], correct: 0, explanation: "Eduardo Galeano es autor de 'El libro de los abrazos'.", category: "literatura" },
                { id: 497, question: "¿Quién escribió 'Memorias de Adriano'?", options: ["Marguerite Yourcenar", "Simone de Beauvoir", "Colette", "George Sand"], correct: 0, explanation: "Marguerite Yourcenar escribió 'Memorias de Adriano'.", category: "literatura" },
                { id: 498, question: "¿Quién escribió 'El tercer hombre' (guion literario)?", options: ["Graham Greene", "Orson Welles", "Carol Reed", "No aplica"], correct: 0, explanation: "Graham Greene escribió el guion de 'El tercer hombre'.", category: "literatura" },
                { id: 499, question: "¿Quién escribió 'El llano en llamas'?", options: ["Juan Rulfo", "Octavio Paz", "Carlos Fuentes", "Alejo Carpentier"], correct: 0, explanation: "Juan Rulfo es autor de 'El llano en llamas'.", category: "literatura" },
                { id: 500, question: "¿Quién escribió 'Pedro Páramo' (confirmación)?", options: ["Juan Rulfo", "Carlos Fuentes", "Juan José Arreola", "Gabriel García Márquez"], correct: 0, explanation: "Confirmación: 'Pedro Páramo' fue escrito por Juan Rulfo.", category: "literatura" },
                // ARTE (601-700
                { id: 601, question: "¿Quién pintó la Mona Lisa?", options: ["Miguel Ángel", "Leonardo da Vinci", "Rafael", "Botticelli"], correct: 1, explanation: "Leonardo da Vinci pintó la Mona Lisa", category: "arte" },
                { id: 602, question: "¿En qué siglo se desarrolló el Renacimiento?", options: ["XIV", "XV", "XVI", "XVII"], correct: 1, explanation: "El Renacimiento se desarrolló principalmente en el siglo XV", category: "arte" },
                { id: 603, question: "¿Quién pintó 'La noche estrellada'?", options: ["Claude Monet", "Vincent van Gogh", "Pablo Picasso", "Salvador Dalí"], correct: 1, explanation: "Vincent van Gogh pintó La noche estrellada", category: "arte" },
                { id: 604, question: "¿Qué artista es conocido por sus relojes derretidos?", options: ["Pablo Picasso", "Salvador Dalí", "Joan Miró", "René Magritte"], correct: 1, explanation: "Salvador Dalí es famoso por sus relojes derretidos", category: "arte" },
                { id: 605, question: "¿Quién pintó el techo de la Capilla Sixtina?", options: ["Leonardo da Vinci", "Rafael", "Miguel Ángel", "Botticelli"], correct: 2, explanation: "Miguel Ángel pintó el techo de la Capilla Sixtina", category: "arte" },
                { id: 606, question: "¿En qué ciudad está el Museo del Louvre?", options: ["Roma", "Madrid", "París", "Londres"], correct: 2, explanation: "El Museo del Louvre está en París", category: "arte" },
                { id: 607, question: "¿Quién pintó 'El grito'?", options: ["Edvard Munch", "Gustav Klimt", "Vincent van Gogh", "Claude Monet"], correct: 0, explanation: "Edvard Munch pintó El grito", category: "arte" },
                { id: 608, question: "¿A qué movimiento artístico pertenecía Pablo Picasso?", options: ["Impresionismo", "Cubismo", "Surrealismo", "Expresionismo"], correct: 1, explanation: "Picasso fue uno de los creadores del Cubismo", category: "arte" },
                { id: 609, question: "¿Quién pintó 'Las meninas'?", options: ["El Greco", "Francisco de Goya", "Diego Velázquez", "Bartolomé Murillo"], correct: 2, explanation: "Diego Velázquez pintó Las meninas", category: "arte" },
                { id: 610, question: "¿Qué famoso pintor se cortó una oreja?", options: ["Pablo Picasso", "Vincent van Gogh", "Claude Monet", "Paul Gauguin"], correct: 1, explanation: "Vincent van Gogh se cortó parte de su oreja", category: "arte" },
                { id: 611, question: "¿Quién esculpió el David?", options: ["Leonardo da Vinci", "Miguel Ángel", "Donatello", "Rafael"], correct: 1, explanation: "Miguel Ángel esculpió el David", category: "arte" },
                { id: 612, question: "¿Qué pintor es conocido por sus nenúfares?", options: ["Vincent van Gogh", "Claude Monet", "Pierre-Auguste Renoir", "Edgar Degas"], correct: 1, explanation: "Claude Monet es famoso por sus pinturas de nenúfares", category: "arte" },
                { id: 613, question: "¿En qué museo se encuentra 'La Gioconda'?", options: ["Museo del Prado", "Museo del Louvre", "Galería Uffizi", "Museo Británico"], correct: 1, explanation: "La Gioconda está en el Museo del Louvre", category: "arte" },
                { id: 614, question: "¿Quién pintó 'La última cena'?", options: ["Miguel Ángel", "Leonardo da Vinci", "Rafael", "Botticelli"], correct: 1, explanation: "Leonardo da Vinci pintó La última cena", category: "arte" },
                { id: 615, question: "¿A qué movimiento pertenece 'La persistencia de la memoria'?", options: ["Cubismo", "Impresionismo", "Surrealismo", "Expresionismo"], correct: 2, explanation: "La persistencia de la memoria es una obra surrealista", category: "arte" },
                { id: 616, question: "¿Quién pintó 'El nacimiento de Venus'?", options: ["Leonardo da Vinci", "Miguel Ángel", "Botticelli", "Rafael"], correct: 2, explanation: "Botticelli pintó El nacimiento de Venus", category: "arte" },
                { id: 617, question: "¿En qué ciudad está la Galería Uffizi?", options: ["Roma", "Florencia", "Venecia", "Milán"], correct: 1, explanation: "La Galería Uffizi está en Florencia", category: "arte" },
                { id: 618, question: "¿Quién pintó 'Guernica'?", options: ["Salvador Dalí", "Joan Miró", "Pablo Picasso", "Francisco de Goya"], correct: 2, explanation: "Pablo Picasso pintó el Guernica", category: "arte" },
                { id: 619, question: "¿Qué artista es conocido por sus latas de sopa Campbell?", options: ["Roy Lichtenstein", "Andy Warhol", "Keith Haring", "Jackson Pollock"], correct: 1, explanation: "Andy Warhol pintó las latas de sopa Campbell", category: "arte" },
                { id: 620, question: "¿Quién pintó 'Los girasoles'?", options: ["Claude Monet", "Vincent van Gogh", "Paul Gauguin", "Paul Cézanne"], correct: 1, explanation: "Vincent van Gogh pintó Los girasoles", category: "arte" },
                { id: 621, question: "¿En qué siglo se desarrolló el Barroco?", options: ["XVI", "XVII", "XVIII", "XIX"], correct: 1, explanation: "El Barroco se desarrolló principalmente en el siglo XVII", category: "arte" },
                { id: 622, question: "¿Quién pintó 'La joven de la perla'?", options: ["Rembrandt", "Johannes Vermeer", "Frans Hals", "Jan van Eyck"], correct: 1, explanation: "Johannes Vermeer pintó La joven de la perla", category: "arte" },
                { id: 623, question: "¿A qué movimiento pertenecía Claude Monet?", options: ["Cubismo", "Impresionismo", "Surrealismo", "Expresionismo"], correct: 1, explanation: "Claude Monet fue un pintor impresionista", category: "arte" },
                { id: 624, question: "¿Quién diseñó la Sagrada Familia de Barcelona?", options: ["Le Corbusier", "Antoni Gaudí", "Frank Lloyd Wright", "Oscar Niemeyer"], correct: 1, explanation: "Antoni Gaudí diseñó la Sagrada Familia", category: "arte" },
                { id: 625, question: "¿En qué museo está 'La ronda de noche'?", options: ["Rijksmuseum", "Louvre", "Museo del Prado", "National Gallery"], correct: 0, explanation: "La ronda de noche está en el Rijksmuseum de Ámsterdam", category: "arte" },
                { id: 626, question: "¿Quién es el artista de 'La persistencia de la memoria'?", options: ["Pablo Picasso", "Salvador Dalí", "Joan Miró", "René Magritte"], correct: 1, explanation: "Salvador Dalí pintó los relojes derretidos", category: "arte" },
                { id: 627, question: "¿Qué artista es conocido por sus latas de sopa Campbell?", options: ["Roy Lichtenstein", "Andy Warhol", "Keith Haring", "Jean-Michel Basquiat"], correct: 1, explanation: "Andy Warhol es el artista pop de las latas Campbell", category: "arte" },
                { id: 628, question: "¿Quién pintó 'El grito'?", options: ["Vincent van Gogh", "Edvard Munch", "Gustav Klimt", "Wassily Kandinsky"], correct: 1, explanation: "Edvard Munch pintó El grito", category: "arte" },
                { id: 629, question: "¿Qué movimiento artístico fundó Jackson Pollock?", options: ["Expresionismo abstracto", "Pop Art", "Minimalismo", "Arte conceptual"], correct: 0, explanation: "Pollock fue pionero del expresionismo abstracto", category: "arte" },
                { id: 630, question: "¿Qué artista es famoso por cortar su propia oreja?", options: ["Paul Gauguin", "Vincent van Gogh", "Claude Monet", "Paul Cézanne"], correct: 1, explanation: "Van Gogh se cortó parte de su oreja", category: "arte" },
                { id: 631, question: "¿Quién es el artista de las 'Latas de Brillo'?", options: ["Andy Warhol", "Roy Lichtenstein", "Claes Oldenburg", "Robert Rauschenberg"], correct: 0, explanation: "Warhol creó las famosas cajas de Brillo", category: "arte" },
                { id: 632, question: "¿Qué artista es conocido por sus 'drippings'?", options: ["Willem de Kooning", "Jackson Pollock", "Mark Rothko", "Franz Kline"], correct: 1, explanation: "Pollock desarrolló la técnica del dripping", category: "arte" },
                { id: 633, question: "¿Quién creó la obra 'Fountain' (un urinario)?", options: ["Marcel Duchamp", "Man Ray", "Salvador Dalí", "Pablo Picasso"], correct: 0, explanation: "Duchamp creó esta obra de arte conceptual", category: "arte" },
                { id: 634, question: "¿Qué artista es famoso por sus puntos?", options: ["Roy Lichtenstein", "Yayoi Kusama", "Keith Haring", "Jean Dubuffet"], correct: 1, explanation: "Kusama es conocida por sus instalaciones de puntos", category: "arte" },
                { id: 635, question: "¿Quién pintó 'Las señoritas de Avignon'?", options: ["Henri Matisse", "Pablo Picasso", "Georges Braque", "Paul Cézanne"], correct: 1, explanation: "Picasso pintó esta obra cubista", category: "arte" },
                { id: 626, question: "¿En qué década surgió el Pop Art?", options: ["1940s", "1950s", "1960s", "1970s"], correct: 1, explanation: "El Pop Art surgió en los años 50", category: "arte" },
                { id: 627, question: "¿Qué movimiento artístico fundó Jackson Pollock?", options: ["Expresionismo abstracto", "Pop Art", "Minimalismo", "Arte conceptual"], correct: 0, explanation: "Pollock fue pionero del expresionismo abstracto", category: "arte" },
                { id: 628, question: "¿Cuál fue la primera instalación artística?", options: ["Fountain de Duchamp", "Merzbau de Schwitters", "4'33'' de Cage", "Le Vide de Klein"], correct: 1, explanation: "El Merzbau de Kurt Schwitters es considerada la primera instalación", category: "arte" }, { id: 629, question: "¿En qué año se realizó la primera Performance Art?", options: ["1952", "1960", "1967", "1970"], correct: 0, explanation: "La primera performance reconocida fue en 1952", category: "arte" },
                { id: 630, question: "¿Quién es considerado el padre del arte conceptual?", options: ["Andy Warhol", "Marcel Duchamp", "Joseph Beuys", "Yves Klein"], correct: 1, explanation: "Duchamp es considerado el padre del arte conceptual", category: "arte" },
                { id: 631, question: "¿Cuándo surgió el arte digital?", options: ["1950s", "1960s", "1970s", "1980s"], correct: 1, explanation: "El arte digital surgió en los años 60", category: "arte" },
                { id: 632, question: "¿Quién realizó la primera videocreación?", options: ["Nam June Paik", "Bill Viola", "Andy Warhol", "Wolf Vostell"], correct: 0, explanation: "Nam June Paik creó la primera obra de videoarte", category: "arte" },
                { id: 633, question: "¿Cuál fue el primer museo de arte contemporáneo?", options: ["MoMA", "Tate Modern", "Centre Pompidou", "Guggenheim"], correct: 0, explanation: "El MoMA fue el primer museo dedicado al arte contemporáneo", category: "arte" },
                { id: 634, question: "¿Quién popularizó el arte urbano?", options: ["Keith Haring", "Jean-Michel Basquiat", "Banksy", "Shepard Fairey"], correct: 0, explanation: "Keith Haring fue pionero en llevar el arte urbano a las galerías", category: "arte" },
                { id: 635, question: "¿Cuándo se realizó la primera Bienal de Venecia de arte contemporáneo?", options: ["1895", "1907", "1920", "1948"], correct: 0, explanation: "La primera Bienal de Venecia fue en 1895", category: "arte" },
                { id: 636, question: "¿Quién fundó la Factory en Nueva York?", options: ["Andy Warhol", "Roy Lichtenstein", "Robert Rauschenberg", "Jasper Johns"], correct: 0, explanation: "Andy Warhol fundó la Factory en los años 60", category: "arte" },
                { id: 637, question: "¿Qué artista creó las 'Marilyn' en serigrafía?", options: ["Keith Haring", "Andy Warhol", "Roy Lichtenstein", "Robert Indiana"], correct: 1, explanation: "Warhol creó las famosas serigrafías de Marilyn Monroe", category: "arte" },
                { id: 638, question: "¿Quién es el artista del 'LOVE'?", options: ["Keith Haring", "Robert Indiana", "Roy Lichtenstein", "Claes Oldenburg"], correct: 1, explanation: "Robert Indiana creó la icónica escultura LOVE", category: "arte" },
                { id: 639, question: "¿Qué artista es conocido por sus figuras bailando?", options: ["Keith Haring", "Jean-Michel Basquiat", "Kenny Scharf", "Roy Lichtenstein"], correct: 0, explanation: "Keith Haring es famoso por sus figuras bailando", category: "arte" },
                { id: 640, question: "¿Quién es conocido por sus instalaciones de espejos?", options: ["Yayoi Kusama", "Marina Abramović", "Yoko Ono", "Nam June Paik"], correct: 0, explanation: "Yayoi Kusama es famosa por sus instalaciones de espejos", category: "arte" },
                { id: 641, question: "¿Qué artista creó la obra '4'33\"'?", options: ["John Cage", "Nam June Paik", "Yoko Ono", "Joseph Beuys"], correct: 0, explanation: "John Cage compuso la pieza silenciosa 4'33\"", category: "arte" },
                { id: 642, question: "¿Quién es pionero del videoarte?", options: ["Bill Viola", "Nam June Paik", "Marina Abramović", "Vito Acconci"], correct: 1, explanation: "Nam June Paik es considerado el padre del videoarte", category: "arte" },
                { id: 643, question: "¿Qué artista es famosa por sus performances?", options: ["Yoko Ono", "Marina Abramović", "Yayoi Kusama", "Louise Bourgeois"], correct: 1, explanation: "Marina Abramović es conocida como la 'abuela de la performance'", category: "arte" },
                { id: 644, question: "¿Quién creó la obra 'The Weather Project'?", options: ["Olafur Eliasson", "Anish Kapoor", "James Turrell", "Dan Flavin"], correct: 0, explanation: "Olafur Eliasson creó esta instalación en la Tate Modern", category: "arte" },
                { id: 645, question: "¿Qué artista es conocido por sus 'Balloon Dogs'?", options: ["Jeff Koons", "Damien Hirst", "Takashi Murakami", "Anish Kapoor"], correct: 0, explanation: "Jeff Koons es famoso por sus perros globo", category: "arte" },
                { id: 646, question: "¿Qué movimiento artístico se centra en la idea o concepto de la obra sobre el objeto material?", options: ["Arte Povera", "Minimalismo", "Arte Conceptual", "Land Art"], correct: 2, explanation: "El Arte Conceptual prioriza la idea sobre la estética o el material", category: "arte" },
                { id: 647, question: "¿Quién pintó la serie de cuadros 'La Danza'?", options: ["Paul Cézanne", "Henri Matisse", "Georges Braque", "Wassily Kandinsky"], correct: 1, explanation: "Henri Matisse pintó varias versiones de 'La Danza'", category: "arte" },
                { id: 648, question: "¿Quién es el arquitecto del Museo Guggenheim de Bilbao?", options: ["Norman Foster", "Santiago Calatrava", "Frank Gehry", "Renzo Piano"], correct: 2, explanation: "Frank Gehry diseñó el famoso edificio del Guggenheim en Bilbao", category: "arte" },
                { id: 649, question: "¿Quién esculpió 'El Pensador'?", options: ["Constantin Brâncuși", "Auguste Rodin", "Alberto Giacometti", "Henry Moore"], correct: 1, explanation: "Auguste Rodin es el autor de 'El Pensador'", category: "arte" },
                { id: 650, question: "¿Qué artista es conocido por la pintura 'Arreglo en gris y negro n.º 1' (El retrato de la madre del artista)?", options: ["James McNeill Whistler", "John Singer Sargent", "Grant Wood", "Winslow Homer"], correct: 0, explanation: "James McNeill Whistler pintó 'El retrato de la madre del artista' (Whistler's Mother)", category: "arte" },
                { id: 651, question: "¿Qué técnica de pintura se realiza sobre una pared o techo con revoque de cal húmeda?", options: ["Temple", "Óleo", "Fresco", "Acrílico"], correct: 2, explanation: "La pintura al fresco se aplica sobre una capa de argamasa fresca", category: "arte" },
                { id: 652, question: "¿Quién pintó 'Composición II en Rojo, Azul y Amarillo', caracterizada por líneas negras y bloques de color?", options: ["Kazimir Malévich", "Piet Mondrian", "Jackson Pollock", "Mark Rothko"], correct: 1, explanation: "Piet Mondrian es el autor de esta icónica obra de De Stijl", category: "arte" },
                { id: 653, question: "¿Qué estilo artístico es una evolución del Barroco, caracterizado por la gracia, la ligereza y la ornamentación excesiva, especialmente en Francia?", options: ["Neoclasicismo", "Rococó", "Manierismo", "Impresionismo"], correct: 1, explanation: "El Rococó sucedió al Barroco y es conocido por su decoración elegante y recargada", category: "arte" },
                { id: 654, question: "¿Quién pintó el tríptico 'El jardín de las delicias'?", options: ["Pieter Brueghel el Viejo", "El Bosco", "Jan van Eyck", "Roger van der Weyden"], correct: 1, explanation: "El Bosco (Hieronymus Bosch) es el pintor de 'El jardín de las delicias'", category: "arte" },
                { id: 655, question: "¿Qué pintor, considerado uno de los pioneros del arte abstracto, escribió el tratado 'De lo espiritual en el arte'?", options: ["Paul Klee", "Wassily Kandinsky", "Franz Marc", "Gustav Klimt"], correct: 1, explanation: "Wassily Kandinsky fue una figura clave en el desarrollo del arte abstracto", category: "arte" },
                { id: 656, question: "¿Qué artista pop es famoso por sus pinturas a gran escala que imitan el estilo de los cómics y la impresión de puntos Benday?", options: ["Andy Warhol", "Roy Lichtenstein", "Richard Hamilton", "Jasper Johns"], correct: 1, explanation: "Roy Lichtenstein es conocido por su uso de puntos Benday y temas de cómic", category: "arte" },
                { id: 657, question: "¿Qué famoso cuadro de Jan van Eyck muestra a una pareja en un interior con un espejo convexo?", options: ["La Anunciación", "El retrato de Giovanni Arnolfini y su esposa", "El Descendimiento", "La Virgen del Canciller Rolin"], correct: 1, explanation: "Jan van Eyck pintó 'El retrato de Giovanni Arnolfini y su esposa' (también conocido como el Matrimonio Arnolfini)", category: "arte" },
                { id: 658, question: "¿En qué ciudad se encuentra el Partenón, un templo dedicado a la diosa Atenea?", options: ["Roma", "Estambul", "Alejandría", "Atenas"], correct: 3, explanation: "El Partenón se encuentra en la Acrópolis de Atenas, Grecia", category: "arte" },
                { id: 659, question: "¿Cuál es el movimiento artístico que busca expresar el funcionamiento real del pensamiento, mediante la eliminación de todo control ejercido por la razón?", options: ["Dadaísmo", "Expresionismo", "Surrealismo", "Fauvismo"], correct: 2, explanation: "El Surrealismo, fundado por André Breton, se centra en el subconsciente y el sueño", category: "arte" },
                { id: 660, question: "¿Quién creó la escultura de mármol 'La Piedad' (Pietà), que se encuentra en la Basílica de San Pedro en el Vaticano?", options: ["Donatello", "Leonardo da Vinci", "Miguel Ángel", "Rafael"], correct: 2, explanation: "Miguel Ángel Buonarroti es el autor de la 'Piedad' del Vaticano", category: "arte" },
                { id: 661, question: "¿En qué siglo se desarrolló predominantemente el movimiento artístico conocido como Romanticismo?", options: ["Siglo XVIII", "Siglo XIX", "Siglo XVII", "Siglo XX"], correct: 1, explanation: "El Romanticismo se desarrolló principalmente a lo largo del siglo XIX", category: "arte" },
                { id: 662, question: "¿Cuál es otra famosa escultura de Auguste Rodin, además de 'El Pensador'?", options: ["La Venus de Milo", "El Beso", "El David", "La Puerta del Infierno"], correct: 1, explanation: "'El Beso' (Le Baiser) es otra de las esculturas más famosas de Rodin", category: "arte" },
                { id: 663, question: "¿Cuál es el nombre de la máscara funeraria de oro y lapislázuli de un faraón del Imperio Nuevo de Egipto?", options: ["Máscara de Ramsés II", "Máscara de Akenatón", "Máscara de Tutankamón", "Máscara de Nefertiti"], correct: 2, explanation: "La máscara de Tutankamón es una de las obras de arte más icónicas del antiguo Egipto", category: "arte" },
                { id: 664, question: "¿Quién pintó 'Impresión, sol naciente', obra que dio nombre al movimiento Impresionista?", options: ["Pierre-Auguste Renoir", "Edgar Degas", "Alfred Sisley", "Claude Monet"], correct: 3, explanation: "Claude Monet pintó 'Impression, soleil levant' en 1872", category: "arte" },
                { id: 665, question: "¿En qué ciudad española se encuentra el Museo Nacional Centro de Arte Reina Sofía, donde se exhibe el 'Guernica' de Picasso?", options: ["Barcelona", "Madrid", "Sevilla", "Valencia"], correct: 1, explanation: "El Museo Reina Sofía, hogar del 'Guernica', está en Madrid", category: "arte" },
                { id: 666, question: "¿Qué técnica artística consiste en componer una obra pegando diversos materiales, como recortes de papel o fotografías, sobre un soporte?", options: ["Grabado", "Collage", "Mosaico", "Ensamblaje"], correct: 1, explanation: "El collage es la técnica de pegar diferentes elementos sobre una superficie", category: "arte" },
                { id: 667, question: "¿Quién fue el ingeniero civil que diseñó la Torre Eiffel para la Exposición Universal de 1889 en París?", options: ["Barón Haussmann", "Eugène Viollet-le-Duc", "Gustave Eiffel", "Charles Garnier"], correct: 2, explanation: "La torre fue diseñada por Gustave Eiffel y sus colaboradores", category: "arte" },
                { id: 668, question: "¿Qué movimiento artístico, surgido a principios del siglo XX, se caracteriza por la intensidad emocional y la distorsión de la realidad?", options: ["Cubismo", "Fauvismo", "Expresionismo", "Dadaísmo"], correct: 2, explanation: "El Expresionismo busca la expresión de los sentimientos y emociones del artista", category: "arte" },
                { id: 669, question: "¿Qué famoso pintor pasó por un 'Período Azul' y un 'Período Rosa' a principios del siglo XX?", options: ["Paul Gauguin", "Pablo Picasso", "Henri Matisse", "Amedeo Modigliani"], correct: 1, explanation: "Pablo Picasso tuvo sus famosos Períodos Azul y Rosa antes de desarrollar el Cubismo", category: "arte" },
                { id: 670, question: "¿Cómo se llama la escultura que se adhiere a un fondo, proyectándose en diferentes grados?", options: ["Estatua", "Móvil", "Relieve", "Talla"], correct: 2, explanation: "Un relieve es una escultura que no está totalmente exenta y tiene un fondo", category: "arte" },
                { id: 671, question: "¿Qué artista postimpresionista es conocido por el uso de la técnica del *impasto*, aplicando la pintura en capas gruesas y visibles?", options: ["Paul Cézanne", "Vincent van Gogh", "Paul Gauguin", "Georges Seurat"], correct: 1, explanation: "Vincent van Gogh es famoso por su uso expresivo del impasto en obras como 'La noche estrellada'", category: "arte" },
                { id: 672, question: "¿Qué antigua civilización es responsable de la construcción del Coliseo de Roma?", options: ["Griegos", "Etruscos", "Romanos", "Egipcios"], correct: 2, explanation: "El Coliseo (Anfiteatro Flavio) fue construido por la Antigua Roma", category: "arte" },
                { id: 673, question: "¿Quién pintó 'El juramento de los Horacios', una obra maestra del Neoclasicismo?", options: ["Eugène Delacroix", "Francisco de Goya", "Jacques-Louis David", "Jean-Auguste-Dominique Ingres"], correct: 2, explanation: "Jacques-Louis David es el pintor neoclásico de 'El juramento de los Horacios'", category: "arte" },
                { id: 674, question: "¿Cuál es el término italiano para el fuerte contraste de luces y sombras utilizado por Caravaggio y otros artistas barrocos?", options: ["Sfumato", "Impasto", "Chiaroscuro", "Tenebrismo"], correct: 2, explanation: "El *chiaroscuro* (claroscuro) es el uso de contrastes fuertes de luz y sombra", category: "arte" },
                { id: 675, question: "¿Qué famosa escultura de la Antigua Grecia, descubierta en 1820, es conocida por tener los brazos mutilados?", options: ["Victoria de Samotracia", "Laocoonte y sus hijos", "Venus de Milo", "Discóbolo"], correct: 2, explanation: "La Venus de Milo (Afrodita de Melos) es famosa por su estado fragmentario", category: "arte" },
                { id: 676, question: "¿Quién pintó 'Olympia', un cuadro que causó escándalo en 1865 por su desnudo franco y moderno?", options: ["Claude Monet", "Gustave Courbet", "Édouard Manet", "James McNeill Whistler"], correct: 2, explanation: "Édouard Manet pintó 'Olympia' y 'El almuerzo sobre la hierba', obras que marcaron la transición al Impresionismo", category: "arte" },
                { id: 677, question: "¿Qué movimiento artístico italiano, de principios del siglo XX, glorificaba la velocidad, la tecnología y la guerra?", options: ["Dadaísmo", "Futurismo", "Vorticismo", "Suprematismo"], correct: 1, explanation: "El Futurismo, fundado por Marinetti, rechazaba el pasado y abrazaba la modernidad dinámica", category: "arte" },
                { id: 678, question: "¿Quién pintó el famoso panel 'La creación de Adán' en el techo de la Capilla Sixtina?", options: ["Rafael", "Leonardo da Vinci", "Miguel Ángel", "Botticelli"], correct: 2, explanation: "Miguel Ángel pintó la 'Creación de Adán' como parte del fresco del techo de la Capilla Sixtina", category: "arte" },
                { id: 679, question: "¿Qué artista es conocido por sus composiciones abstractas de formas geométricas rectangulares y primarias en el movimiento De Stijl?", options: ["Kasimir Malévich", "Piet Mondrian", "Theo van Doesburg", "Gerrit Rietveld"], correct: 1, explanation: "Piet Mondrian llevó la abstracción geométrica al máximo en De Stijl", category: "arte" },
                { id: 680, question: "¿Quién es considerada la pintora mexicana más famosa, conocida por sus autorretratos y el uso del simbolismo?", options: ["Remedios Varo", "Leonora Carrington", "María Izquierdo", "Frida Kahlo"], correct: 3, explanation: "Frida Kahlo es mundialmente famosa por sus autorretratos introspectivos", category: "arte" },
                { id: 681, question: "¿Qué término se usa para describir una obra de arte, como una pintura o un relieve, dividida en dos paneles o partes?", options: ["Tríptico", "Políptico", "Díptico", "Ensamblaje"], correct: 2, explanation: "Un díptico es una obra compuesta por dos paneles articulados o yuxtapuestos", category: "arte" },
                { id: 682, question: "¿Quién pintó 'El Tres de Mayo' (Los fusilamientos del 3 de mayo), en conmemoración de la resistencia española contra Napoleón?", options: ["El Greco", "Diego Velázquez", "Francisco de Goya", "Joaquín Sorolla"], correct: 2, explanation: "Francisco de Goya pintó esta icónica obra sobre la Guerra de la Independencia", category: "arte" },
                { id: 683, question: "¿Qué estilo de arte post-Segunda Guerra Mundial se caracteriza por la extrema sencillez de la forma, utilizando a menudo formas geométricas primarias?", options: ["Pop Art", "Expresionismo Abstracto", "Arte Conceptual", "Minimalismo"], correct: 3, explanation: "El Minimalismo ('Arte Mínimo') se distingue por la reducción a lo esencial", category: "arte" },
                { id: 684, question: "¿Cuál es el nombre de la pirámide más antigua y grande de las tres de la necrópolis de Guiza?", options: ["Pirámide de Kefrén", "Pirámide de Micerino", "Pirámide de Zoser", "Gran Pirámide de Keops"], correct: 3, explanation: "La Gran Pirámide de Guiza es la de Keops (Jufu)", category: "arte" },
                { id: 685, question: "¿Quién es la autora del autorretrato 'Autorretrato con collar de espinas y colibrí'?", options: ["Tamara de Lempicka", "Frida Kahlo", "Georgia O'Keeffe", "Louise Bourgeois"], correct: 1, explanation: "Frida Kahlo es la autora de este y muchos otros autorretratos con alto contenido simbólico", category: "arte" },
                { id: 686, question: "¿Qué expresión artística francesa significa 'engañar al ojo', creando una ilusión óptica de realidad?", options: ["Faux Pas", "Trompe-l'oeil", "Coup de Grâce", "Je Ne Sais Quoi"], correct: 1, explanation: "El *trompe-l'oeil* es una técnica pictórica que busca crear una ilusión tridimensional", category: "arte" },
                { id: 687, question: "¿Quién fue el principal arquitecto renacentista que inició la construcción de la Basílica de San Pedro en Roma?", options: ["Filippo Brunelleschi", "Donato Bramante", "León Battista Alberti", "Andrea Palladio"], correct: 1, explanation: "Donato Bramante fue el primer arquitecto de la nueva Basílica de San Pedro en 1506", category: "arte" },
                { id: 688, question: "¿Cómo se llama la técnica artística que utiliza pequeñas piezas de material (teselas) para crear una imagen en una superficie?", options: ["Frescoes", "Mosaico", "Intarsia", "Taracea"], correct: 1, explanation: "El mosaico se realiza con teselas de piedra, vidrio o cerámica", category: "arte" },
                { id: 689, question: "¿Qué artista impresionista y post-impresionista es famoso por sus pinturas de bailarinas de ballet y carreras de caballos?", options: ["Camille Pissarro", "Edgar Degas", "Alfred Sisley", "Berthe Morisot"], correct: 1, explanation: "Edgar Degas es conocido por capturar escenas de la vida moderna, especialmente el ballet", category: "arte" },
                { id: 690, question: "¿Qué término se usa para describir una obra de arte compuesta por tres paneles, a menudo unida por bisagras?", options: ["Díptico", "Tetráptico", "Políptico", "Tríptico"], correct: 3, explanation: "Un tríptico es una obra de arte con tres secciones", category: "arte" },
                { id: 691, question: "¿Cuál es la principal característica del Pointillism (Puntillismo)?", options: ["Uso de líneas gruesas", "Aplicación de grandes manchas de color", "Uso de pequeños puntos de color puro", "Pintura sobre tela de saco"], correct: 2, explanation: "El Puntillismo, desarrollado por Seurat, aplica pequeños puntos de color que se mezclan ópticamente", category: "arte" },
                { id: 692, question: "¿Qué artista pop es famoso por sus serigrafías de celebridades y figuras políticas como Mao?", options: ["Keith Haring", "Andy Warhol", "Roy Lichtenstein", "Robert Indiana"], correct: 1, explanation: "Andy Warhol produjo la serie de retratos de Mao en la década de 1970", category: "arte" },
                { id: 693, question: "¿Quién pintó 'Los Embajadores', un retrato doble con una calavera anamórfica oculta?", options: ["Albrecht Dürer", "Hans Holbein el Joven", "Lucas Cranach el Viejo", "El Greco"], correct: 1, explanation: "Hans Holbein el Joven pintó 'Los Embajadores' en el Renacimiento nórdico", category: "arte" },
                { id: 694, question: "¿En qué ciudad se encuentra el Museo Nacional del Prado, que alberga obras maestras de Velázquez, Goya y El Greco?", options: ["Barcelona", "Madrid", "Sevilla", "Lisboa"], correct: 1, explanation: "El Museo del Prado está ubicado en Madrid", category: "arte" },
                { id: 695, question: "¿Cómo se llama la técnica de dibujo que utiliza líneas paralelas o entrecruzadas para crear la ilusión de sombra y volumen?", options: ["Esbozo", "Sombreado", "Hachurado (Achurado)", "Esgrafiado"], correct: 2, explanation: "El hachurado o achurado es la técnica de sombreado con líneas para crear valor y textura", category: "arte" },
                { id: 696, question: "¿Qué famoso pintor veneciano del Renacimiento es conocido por su dominio del color y el retrato, como 'La Asunción de la Virgen'?", options: ["Giorgione", "Tiziano", "Veronés", "Tintoretto"], correct: 1, explanation: "Tiziano (Tiziano Vecellio) es uno de los máximos exponentes de la pintura veneciana", category: "arte" },
                { id: 697, question: "¿Cuál es el nombre de la cueva prehistórica en Francia, famosa por sus magníficas pinturas rupestres de animales del Paleolítico Superior?", options: ["Cueva de Altamira", "Cueva de Chauvet", "Cueva de Lascaux", "Cueva de El Castillo"], correct: 2, explanation: "La Cueva de Lascaux en Dordoña es famosa por su Salón de los Toros", category: "arte" },
                { id: 698, question: "¿Qué artista pop es el autor de las icónicas obras que representan latas de sopa Campbell?", options: ["Roy Lichtenstein", "Richard Hamilton", "Robert Rauschenberg", "Andy Warhol"], correct: 3, explanation: "Andy Warhol popularizó las latas de sopa Campbell como tema artístico", category: "arte" },
                { id: 699, question: "¿Cuál es el término italiano, popularizado por Leonardo da Vinci, para la técnica de difuminar los contornos para crear una transición suave de color y luz?", options: ["Chiaroscuro", "Sfumato", "Cangiante", "Unione"], correct: 1, explanation: "El *sfumato* (ahumado) crea una atmósfera brumosa y contornos indefinidos, como en la Mona Lisa", category: "arte" },
                { id: 700, question: "¿Quién es el escultor griego clásico que creó la estatua del 'Discóbolo' (lanzador de disco)?", options: ["Fidias", "Praxíteles", "Mirón", "Policleto"], correct: 2, explanation: "Mirón es el autor del 'Discóbolo', una obra que representa el ideal de la belleza atlética griega", category: "arte" },
//deportes 701 - 800
                { id: 701, question: "¿Cuántos jugadores por equipo están en el campo al inicio de un partido de fútbol?", options: ["10", "11", "9", "12"], correct: 1, explanation: "Un equipo de fútbol comienza con 11 jugadores en el campo.", category: "deportes" },
                { id: 702, question: "¿Qué país ganó la primera Copa Mundial de la FIFA en 1930?", options: ["Brasil", "Italia", "Uruguay", "Argentina"], correct: 2, explanation: "Uruguay ganó el primer Mundial de la historia, celebrado en Montevideo.", category: "deportes" },
                { id: 703, question: "¿En qué deporte se utiliza el término 'birdie'?", options: ["Tenis", "Bádminton", "Golf", "Críquet"], correct: 2, explanation: "En golf, un 'birdie' significa terminar un hoyo con un golpe bajo el par.", category: "deportes" },
                { id: 704, question: "¿Quién es el atleta con más medallas de oro en la historia de los Juegos Olímpicos?", options: ["Usain Bolt", "Paavo Nurmi", "Michael Phelps", "Carl Lewis"], correct: 2, explanation: "El nadador Michael Phelps tiene el récord con 23 medallas de oro.", category: "deportes" },
                { id: 705, question: "¿Cuántos puntos vale un triple en baloncesto?", options: ["1", "2", "3", "4"], correct: 2, explanation: "Un lanzamiento anotado desde fuera de la línea curva vale 3 puntos.", category: "deportes" },
                { id: 706, question: "¿En qué ciudad se celebraron los Juegos Olímpicos de 1992?", options: ["Atlanta", "Seúl", "Barcelona", "Sídney"], correct: 2, explanation: "Los Juegos Olímpicos de Verano de 1992 se llevaron a cabo en Barcelona, España.", category: "deportes" },
                { id: 707, question: "¿Cuál es el nombre del trofeo que se otorga al campeón de la UEFA Champions League?", options: ["La Copa del Mundo", "El Balón de Oro", "La Orejona", "La Copa América"], correct: 2, explanation: "La UEFA Champions League es conocida popularmente como 'La Orejona' por la forma de sus asas.", category: "deportes" },
                { id: 708, question: "¿Qué deporte se juega en el torneo de Wimbledon?", options: ["Fútbol", "Golf", "Tenis", "Rugby"], correct: 2, explanation: "Wimbledon es uno de los cuatro torneos de Grand Slam de tenis.", category: "deportes" },
                { id: 709, question: "¿Qué famoso boxeador era conocido como 'The Greatest'?", options: ["Mike Tyson", "Rocky Marciano", "Sugar Ray Robinson", "Muhammad Ali"], correct: 3, explanation: "Muhammad Ali (anteriormente Cassius Clay) se autoproclamó 'The Greatest'.", category: "deportes" },
                { id: 710, question: "¿Cuántas grandes vueltas ciclistas existen anualmente?", options: ["2", "3", "4", "5"], correct: 1, explanation: "Son tres: el Tour de Francia, el Giro de Italia y la Vuelta a España.", category: "deportes" },
                { id: 711, question: "¿Qué país tiene más títulos de Copas Mundiales de la FIFA masculinas?", options: ["Alemania", "Italia", "Argentina", "Brasil"], correct: 3, explanation: "Brasil tiene cinco títulos mundiales (Pentacampeón).", category: "deportes" },
                { id: 712, question: "¿Cuál es la distancia oficial de una maratón en kilómetros?", options: ["40.195 km", "42.195 km", "45.000 km", "42.000 km"], correct: 1, explanation: "La distancia oficial es 42.195 kilómetros (26 millas y 385 yardas).", category: "deportes" },
                { id: 713, question: "¿Quién es el máximo ganador de títulos individuales de Grand Slam masculinos en tenis?", options: ["Roger Federer", "Rafael Nadal", "Novak Djokovic", "Pete Sampras"], correct: 2, explanation: "Novak Djokovic posee el récord de títulos de Grand Slam individuales masculinos.", category: "deportes" },
                { id: 714, question: "¿Qué objeto se utiliza para golpear la pelota en el bádminton?", options: ["Una raqueta", "Un bate", "Un *shuttlecock* o volante", "Una maza"], correct: 0, explanation: "En bádminton se golpea el volante o pluma con una raqueta.", category: "deportes" },
                { id: 715, question: "¿Qué país es la cuna del judo?", options: ["China", "Corea", "Japón", "Brasil"], correct: 2, explanation: "El judo es un arte marcial y deporte de combate de origen japonés.", category: "deportes" },
                { id: 716, question: "¿A qué altura reglamentaria está la canasta en baloncesto?", options: ["3.05 metros", "2.80 metros", "3.20 metros", "3.50 metros"], correct: 0, explanation: "La canasta de baloncesto se sitúa a 3.05 metros (10 pies) de altura.", category: "deportes" },
                { id: 717, question: "¿Cómo se llama el arte marcial coreano caracterizado por sus patadas altas y técnicas de salto?", options: ["Karate", "Judo", "Taekwondo", "Kárate-do"], correct: 2, explanation: "El Taekwondo es el arte marcial nacional de Corea.", category: "deportes" },
                { id: 718, question: "¿En qué deporte se puede realizar un 'hole-in-one'?", options: ["Béisbol", "Golf", "Billar", "Hockey sobre hielo"], correct: 1, explanation: "En golf, un 'hole-in-one' es cuando la pelota entra en el hoyo con el primer golpe.", category: "deportes" },
                { id: 719, question: "¿Qué equipo de la NBA ha ganado más campeonatos de la historia junto a los Boston Celtics?", options: ["Chicago Bulls", "Los Angeles Lakers", "San Antonio Spurs", "Golden State Warriors"], correct: 1, explanation: "Los **Los Angeles Lakers** y los **Boston Celtics** son los equipos más laureados de la NBA.", category: "deportes" },
                { id: 720, question: "¿Cuál es el deporte nacional de Japón?", options: ["Kárate", "Judo", "Béisbol", "Sumo"], correct: 3, explanation: "El Sumo es considerado el deporte nacional de Japón.", category: "deportes" },
                { id: 721, question: "¿Qué tipo de natación no está permitida en los Juegos Olímpicos?", options: ["Espalda", "Crol", "Mariposa", "Ninguna de las anteriores"], correct: 3, explanation: "Los cuatro estilos (Libre/Crol, Espalda, Braza, Mariposa) están permitidos.", category: "deportes" },
                { id: 722, question: "¿Qué país lidera la tabla histórica de medallas de oro en los Juegos Olímpicos de Invierno?", options: ["Rusia", "Noruega", "Estados Unidos", "Alemania"], correct: 1, explanation: "Noruega es la nación con más medallas de oro y más medallas totales en los Juegos de Invierno.", category: "deportes" },
                { id: 723, question: "¿Qué famosa gimnasta rumana fue la primera en conseguir una puntuación perfecta de 10.0 en unos Juegos Olímpicos?", options: ["Svetlana Khorkina", "Larisa Latynina", "Nadia Comăneci", "Olga Korbut"], correct: 2, explanation: "Nadia Comăneci lo logró en los Juegos de Montreal 1976.", category: "deportes" },
                { id: 724, question: "¿Cuántos jugadores hay en un equipo de voleibol en la cancha?", options: ["5", "6", "7", "8"], correct: 1, explanation: "Un equipo de voleibol tiene 6 jugadores en la cancha en un momento dado.", category: "deportes" },
                { id: 725, question: "¿Quién fue el piloto de Fórmula 1 apodado 'El Kaiser'?", options: ["Ayrton Senna", "Juan Manuel Fangio", "Michael Schumacher", "Lewis Hamilton"], correct: 2, explanation: "Michael Schumacher, el heptacampeón, fue apodado 'El Kaiser'.", category: "deportes" },
                { id: 726, question: "¿En qué deporte se utiliza la 'chistera' o 'sombrero' como regate?", options: ["Tenis", "Baloncesto", "Fútbol", "Boxeo"], correct: 2, explanation: "En fútbol, la 'chistera' (sombrero) es levantar el balón por encima del rival.", category: "deportes" },
                { id: 727, question: "¿Cuántos anillos componen el símbolo olímpico?", options: ["4", "5", "6", "7"], correct: 1, explanation: "Los 5 anillos representan los 5 continentes poblados que participan.", category: "deportes" },
                { id: 728, question: "¿Cuál es el color de la camiseta que identifica al líder de la clasificación general del Tour de Francia?", options: ["Amarillo", "Verde", "Rojo", "Blanco"], correct: 0, explanation: "El 'maillot jaune' (maillot amarillo) lo viste el líder de la carrera.", category: "deportes" },
                { id: 729, question: "¿Qué deporte se conoce popularmente como 'el ballet acuático'?", options: ["Waterpolo", "Natación de larga distancia", "Natación sincronizada", "Saltos ornamentales"], correct: 2, explanation: "La Natación Artística, antes Natación Sincronizada, se conoce por su gracia.", category: "deportes" },
                { id: 730, question: "¿Qué país ha ganado más veces la Copa Davis de tenis?", options: ["Australia", "España", "Estados Unidos", "Francia"], correct: 2, explanation: "Estados Unidos tiene el récord de títulos en la Copa Davis.", category: "deportes" },
                { id: 731, question: "¿Qué es un 'touchdown' en el fútbol americano?", options: ["Una patada a palos", "Un placaje", "Una anotación de 6 puntos", "Un pase largo"], correct: 2, explanation: "Un 'touchdown' es la anotación de mayor valor (6 puntos) en este deporte.", category: "deportes" },
                { id: 732, question: "¿Qué deporte se juega en el estadio Old Trafford?", options: ["Fútbol", "Rugby", "Críquet", "Béisbol"], correct: 0, explanation: "Old Trafford es el estadio del Manchester United F.C.", category: "deportes" },
                { id: 733, question: "¿Cuál es el nombre del trofeo de la Ryder Cup?", options: ["Ryder Cup", "Seve Trophy", "PGA Championship", "Ninguno de los anteriores"], correct: 0, explanation: "El trofeo que se disputa en el torneo bienal de golf es la Ryder Cup.", category: "deportes" },
                { id: 734, question: "¿Cuál es el nombre del campo de juego en el béisbol?", options: ["Pista", "Cancha", "Diamante", "Ring"], correct: 2, explanation: "El campo de béisbol, con sus cuatro bases, tiene forma de diamante.", category: "deportes" },
                { id: 735, question: "¿Qué deporte combina natación, ciclismo y carrera a pie?", options: ["Decatlón", "Pentatlón moderno", "Triatlón", "Duatlón"], correct: 2, explanation: "El Triatlón se compone de los tres deportes en ese orden.", category: "deportes" },
                { id: 736, question: "¿En qué deporte es famoso el 'Smash' o 'Remate'?", options: ["Tenis", "Voleibol", "Bádminton", "Todos los anteriores"], correct: 3, explanation: "Es un golpe fuerte de arriba a abajo usado en varios deportes de red.", category: "deportes" },
                { id: 737, question: "¿En qué país se originó el Rugby?", options: ["Gales", "Australia", "Inglaterra", "Francia"], correct: 2, explanation: "El Rugby se originó en la escuela de Rugby, Inglaterra.", category: "deportes" },
                { id: 738, question: "¿Cuál es el deporte en el que destaca la española Carolina Marín?", options: ["Tenis", "Bádminton", "Squash", "Tenis de Mesa"], correct: 1, explanation: "Carolina Marín es una campeona olímpica y mundial de bádminton.", category: "deportes" },
                { id: 739, question: "¿Cuántas penalizaciones (strikes) pueden tener los jugadores de críquet antes de ser eliminados (out)?", options: ["1", "2", "3", "Ninguna"], correct: 3, explanation: "El concepto de 'strike' es más propio del béisbol, no del críquet.", category: "deportes" },
                { id: 740, question: "¿Qué equipo de fútbol es conocido como 'Los Diablos Rojos'?", options: ["AC Milan", "Bayern Múnich", "Manchester United", "Liverpool FC"], correct: 2, explanation: "El apodo 'The Red Devils' es emblemático del Manchester United.", category: "deportes" },
                { id: 741, question: "¿En qué deporte se utiliza una 'escoba' para afectar la trayectoria de una piedra?", options: ["Curling", "Hockey sobre hielo", "Bobsleigh", "Patinaje artístico"], correct: 0, explanation: "En el Curling, el *sweeping* (barrido) con escobas ayuda a que la piedra se deslice más lejos o menos curvada.", category: "deportes" },
                { id: 742, question: "¿Cuántas medallas de oro olímpicas tiene el nadador Mark Spitz?", options: ["7", "8", "9", "10"], correct: 2, explanation: "Mark Spitz ganó 7 medallas en 1972 y 2 en 1968, sumando 9 oros.", category: "deportes" },
                { id: 743, question: "¿Qué deporte se juega en el Madison Square Garden de Nueva York?", options: ["Fútbol americano", "Béisbol", "Baloncesto y Hockey sobre Hielo", "Automovilismo"], correct: 2, explanation: "Es la sede de los New York Knicks (NBA) y los New York Rangers (NHL).", category: "deportes" },
                { id: 744, question: "¿Cuál es el nombre del campeonato de fútbol americano más importante?", options: ["World Series", "Super Bowl", "Stanley Cup", "NBA Finals"], correct: 1, explanation: "La Super Bowl es el partido final del campeonato de la NFL.", category: "deportes" },
                { id: 745, question: "¿Qué posición en el fútbol americano es el líder del ataque y el que lanza la pelota?", options: ["Running Back", "Wide Receiver", "Quarterback", "Linebacker"], correct: 2, explanation: "El *Quarterback* (QB) es el director de juego ofensivo.", category: "deportes" },
                { id: 746, question: "¿En qué deporte se celebra la Copa del Mundo Webb Ellis?", options: ["Fútbol", "Rugby", "Críquet", "Hockey"], correct: 1, explanation: "La Copa Webb Ellis es el trofeo que se da al ganador del Mundial de Rugby.", category: "deportes" },
                { id: 747, question: "¿Quién es el máximo goleador histórico de los mundiales de fútbol?", options: ["Pelé", "Ronaldo Nazário", "Miroslav Klose", "Lionel Messi"], correct: 2, explanation: "Miroslav Klose (Alemania) tiene 16 goles en Copas del Mundo.", category: "deportes" },
                { id: 748, question: "¿Qué deporte acuático se considera el más antiguo jamás registrado?", options: ["Natación", "Buceo", "Waterpolo", "Remo"], correct: 1, explanation: "El Buceo y actividades de apnea son actividades humanas muy antiguas.", category: "deportes" },
                { id: 749, question: "¿A qué tenista se le conoce con el apodo de 'El Expreso Suizo'?", options: ["Stan Wawrinka", "Roger Federer", "Rafael Nadal", "Andre Agassi"], correct: 1, explanation: "Roger Federer recibió el apodo por su velocidad y elegancia en la pista.", category: "deportes" },
                { id: 750, question: "¿En qué deporte se puede dar un 'jaque mate'?", options: ["Damas", "Póker", "Ajedrez", "Go"], correct: 2, explanation: "El 'jaque mate' es la jugada que pone fin a una partida de Ajedrez.", category: "deportes" },
                { id: 751, question: "¿Cuál es el nombre completo de 'O Rei', la leyenda brasileña del fútbol?", options: ["Garrincha", "Zico", "Pelé", "Rivelino"], correct: 2, explanation: "El nombre completo de Pelé es Edson Arantes do Nascimento.", category: "deportes" },
                { id: 752, question: "¿Qué se premia con el Balón de Oro?", options: ["Al mejor equipo de la temporada", "Al mejor gol del año", "Al mejor jugador del año", "Al máximo goleador de una liga"], correct: 2, explanation: "El Balón de Oro (Ballon d'Or) premia al mejor futbolista del año.", category: "deportes" },
                { id: 753, question: "¿Cuál es la última prueba del decatlón en atletismo?", options: ["1500 metros", "Salto con pértiga", "Jabalina", "400 metros"], correct: 0, explanation: "El Decatlón (10 pruebas) finaliza con la carrera de 1500 metros.", category: "deportes" },
                { id: 754, question: "¿Qué deporte utiliza un 'Volante' o 'Pluma' como proyectil?", options: ["Tenis", "Squash", "Bádminton", "Tenis de Mesa"], correct: 2, explanation: "El *shuttlecock* o volante es característico del bádminton.", category: "deportes" },
                { id: 755, question: "¿En qué país se originó el Béisbol moderno?", options: ["Canadá", "Japón", "Estados Unidos", "Cuba"], correct: 2, explanation: "El béisbol se desarrolló y popularizó en Estados Unidos en el siglo XIX.", category: "deportes" },
                { id: 756, question: "¿En qué deporte se puede conseguir un 'strike'?", options: ["Bolos", "Béisbol", "Sóftbol", "Todos los anteriores"], correct: 3, explanation: "El término 'strike' se usa en béisbol, sóftbol y bolos con diferentes significados.", category: "deportes" },
                { id: 757, question: "¿Cuántos *Grand Slams* componen el circuito profesional de tenis?", options: ["3", "4", "5", "6"], correct: 1, explanation: "Son 4: Australia, Roland Garros, Wimbledon y US Open.", category: "deportes" },
                { id: 758, question: "¿En qué deporte es famoso el equipo 'All Blacks'?", options: ["Fútbol", "Baloncesto", "Rugby", "Grillo"], correct: 2, explanation: "Los All Blacks son el equipo nacional de Rugby de Nueva Zelanda.", category: "deportes" },
                { id: 759, question: "¿Quién fue el primer campeón olímpico de maratón de la era moderna?", options: ["Spiridon Louis", "Emil Zátopek", "Abebe Bikila", "Lasse Virén"], correct: 0, explanation: "Spiridon Louis, un griego, ganó la maratón en Atenas 1896.", category: "deportes" },
                { id: 760, question: "¿Qué atleta ostenta los récords mundiales de 100 y 200 metros planos?", options: ["Jesse Owens", "Carl Lewis", "Tyson Gay", "Usain Bolt"], correct: 3, explanation: "Usain Bolt (Jamaica) es el actual poseedor de ambos récords mundiales.", category: "deportes" },
                { id: 761, question: "¿Qué deporte se juega en la 'Copa Stanley'?", options: ["Hockey sobre hielo", "Béisbol", "Fútbol", "Baloncesto"], correct: 0, explanation: "La Stanley Cup es el trofeo que se disputa en la NHL de Hockey sobre Hielo.", category: "deportes" },
                { id: 762, question: "¿Cuál es el país con más medallas de oro en los Juegos Olímpicos de verano en la historia?", options: ["China", "Unión Soviética/Rusia", "Alemania", "Estados Unidos"], correct: 3, explanation: "Estados Unidos es el país que más medallas de oro ha ganado.", category: "deportes" },
                { id: 763, question: "¿En qué arte marcial se utiliza el término 'Kata' para referirse a una secuencia de movimientos preestablecidos?", options: ["Judo", "Karate", "Taekwondo", "Kendo"], correct: 1, explanation: "El 'Kata' es una práctica fundamental en el Karate-do.", category: "deportes" },
                { id: 764, question: "¿Qué jugador de baloncesto popularizó el 'Dream Shake'?", options: ["Kareem Abdul-Jabbar", "Hakeem Olajuwon", "Michael Jordan", "Shaquille O'Neal"], correct: 1, explanation: "Hakeem 'The Dream' Olajuwon es conocido por su elegante movimiento 'Dream Shake'.", category: "deportes" },
                { id: 765, question: "¿Qué famoso golfista es conocido por su sobrenombre 'Tiger'?", options: ["Rory McIlroy", "Jack Nicklaus", "Phil Mickelson", "Eldrick Woods"], correct: 3, explanation: "Tiger Woods es el sobrenombre de Eldrick Woods.", category: "deportes" },
                { id: 766, question: "¿Cuántos periodos se juegan en un partido de Hockey sobre Hielo?", options: ["2", "3", "4", "5"], correct: 1, explanation: "Un partido reglamentario de hockey sobre hielo se divide en 3 periodos.", category: "deportes" },
                { id: 767, question: "¿Qué deporte tiene su sede mundial en la 'Maison du Sport International' en Lausana, Suiza?", options: ["Fútbol", "Bádminton", "Natación", "Todos los anteriores"], correct: 3, explanation: "La mayoría de las federaciones deportivas internacionales tienen su sede allí (COI, FIBA, FINA, etc.).", category: "deportes" },
                { id: 768, question: "¿Cuál es el único deporte que se ha jugado en todos los Juegos Olímpicos de verano de la era moderna?", options: ["Fútbol", "Atletismo", "Natación", "Esgrima"], correct: 3, explanation: "La Esgrima se ha disputado ininterrumpidamente desde 1896.", category: "deportes" },
                { id: 769, question: "¿Qué famoso equipo de fútbol juega en el Camp Nou?", options: ["Real Madrid", "Atlético de Madrid", "FC Barcelona", "Valencia CF"], correct: 2, explanation: "El Camp Nou es el estadio del Fútbol Club Barcelona.", category: "deportes" },
                { id: 770, question: "¿Qué tenista ganó el 'Golden Slam' (los 4 Grand Slam y el Oro Olímpico en un mismo año) en 1988?", options: ["Steffi Graf", "Serena Williams", "Martina Navratilova", "Margaret Court"], correct: 0, explanation: "Steffi Graf es la única persona en la historia en lograr el Golden Slam.", category: "deportes" },
                { id: 771, question: "¿En qué deporte se utiliza la 'Pértiga'?", options: ["Gimnasia", "Atletismo", "Natación", "Béisbol"], correct: 1, explanation: "La Pértiga se utiliza en la prueba de Salto con Pértiga en el atletismo.", category: "deportes" },
                { id: 772, question: "¿Qué jugador de fútbol fue apodado 'El Pibe de Oro'?", options: ["Alfredo Di Stéfano", "Gabriel Batistuta", "Diego Maradona", "Lionel Messi"], correct: 2, explanation: "Diego Armando Maradona es conocido con este apodo.", category: "deportes" },
                { id: 773, question: "¿Cuál es el tiempo reglamentario de un partido de baloncesto de la NBA?", options: ["32 minutos", "40 minutos", "48 minutos", "60 minutos"], correct: 2, explanation: "Un partido de la NBA se divide en 4 cuartos de 12 minutos cada uno.", category: "deportes" },
                { id: 774, question: "¿Qué deporte se juega en el Campeonato Seis Naciones?", options: ["Fútbol", "Baloncesto", "Rugby", "Hockey"], correct: 2, explanation: "El Seis Naciones es el principal torneo internacional de Rugby en Europa.", category: "deportes" },
                { id: 775, question: "¿En qué año se celebraron los primeros Juegos Olímpicos de la era moderna?", options: ["1892", "1896", "1900", "1904"], correct: 1, explanation: "Los primeros Juegos Modernos se celebraron en Atenas en 1896.", category: "deportes" },
                { id: 776, question: "¿Qué significa el 'Par' en el golf?", options: ["El número máximo de golpes permitidos", "El número promedio de golpes necesarios", "El número de golpes que el jugador hizo", "El número mínimo de golpes permitidos"], correct: 1, explanation: "El Par es el número de golpes que un golfista experto debería necesitar para completar el hoyo.", category: "deportes" },
                { id: 777, question: "¿Qué famoso jugador de béisbol fue conocido como 'The Sultan of Swat'?", options: ["Babe Ruth", "Ty Cobb", "Hank Aaron", "Jackie Robinson"], correct: 0, explanation: "Babe Ruth es considerado uno de los mejores jugadores de béisbol de la historia.", category: "deportes" },
                { id: 778, question: "¿Cómo se llama la posición que protege la portería en el Hockey sobre hielo?", options: ["Defensa", "Delantero", "Pívot", "Portero (Goaltender)"], correct: 3, explanation: "El Goaltender o Portero es la última línea de defensa.", category: "deportes" },
                { id: 779, question: "¿Qué deporte se juega en el torneo 'Masters de Augusta'?", options: ["Tenis", "Golf", "Billar", "Snooker"], correct: 1, explanation: "El Masters de Augusta es uno de los 4 *Majors* del golf masculino.", category: "deportes" },
                { id: 780, question: "¿Cuál es el nombre de la mascota de los Juegos Olímpicos de Barcelona 1992?", options: ["Hodori", "Izzy", "Cobi", "Misha"], correct: 2, explanation: "Cobi fue la mascota diseñada por Javier Mariscal.", category: "deportes" },
                { id: 781, question: "¿Qué deporte se practica en la 'Vuelta a España'?", options: ["Carrera a pie", "Motociclismo", "Ciclismo", "Automovilismo"], correct: 2, explanation: "La Vuelta a España es la tercera de las grandes vueltas ciclistas.", category: "deportes" },
                { id: 782, question: "¿Qué país ha ganado más Mundiales de Rugby?", options: ["Australia", "Nueva Zelanda", "Sudáfrica", "Todos los anteriores"], correct: 3, explanation: "Nueva Zelanda y Sudáfrica comparten el récord de Mundiales ganados.", category: "deportes" },
                { id: 783, question: "¿Cuál es la distancia de la prueba de natación más larga en los Juegos Olímpicos?", options: ["800 metros", "1500 metros", "5 kilómetros", "10 kilómetros"], correct: 3, explanation: "Los 10 km de aguas abiertas son la prueba más larga.", category: "deportes" },
                { id: 784, question: "¿Quién fue el primer jugador de la historia del fútbol en ganar 6 Balones de Oro?", options: ["Cristiano Ronaldo", "Johan Cruyff", "Alfredo Di Stéfano", "Lionel Messi"], correct: 3, explanation: "Lionel Messi fue el primero en alcanzar esa cifra.", category: "deportes" },
                { id: 785, question: "¿Qué deportista es la máxima medallista olímpica femenina en la historia?", options: ["Larisa Latynina", "Birgit Fischer", "Jenny Thompson", "Allyson Felix"], correct: 0, explanation: "La gimnasta soviética Larisa Latynina (18 medallas totales).", category: "deportes" },
                { id: 786, question: "¿Cómo se llama la posición en el fútbol americano que recibe los pases del Quarterback?", options: ["Tackle", "Tight End", "Wide Receiver", "Safety"], correct: 2, explanation: "El *Wide Receiver* se especializa en correr rutas y atrapar pases.", category: "deportes" },
                { id: 787, question: "¿Qué deporte se conoce como 'el deporte rey'?", options: ["Baloncesto", "Fútbol", "Atletismo", "Tenis"], correct: 1, explanation: "El fútbol es el deporte más popular y con más seguidores a nivel global.", category: "deportes" },
                { id: 788, question: "¿Cuál es el nombre del estadio donde se celebra anualmente la final de la FA Cup inglesa?", options: ["Old Trafford", "Anfield", "Wembley Stadium", "Emirates Stadium"], correct: 2, explanation: "Wembley es la sede de las finales de las principales competiciones de copa de Inglaterra.", category: "deportes" },
                { id: 789, question: "¿Qué atleta es conocido por el 'Salto del Siglo' en los Juegos Olímpicos de 1968?", options: ["Jesse Owens", "Bob Beamon", "Carl Lewis", "Mike Powell"], correct: 1, explanation: "Bob Beamon estableció un increíble récord mundial de Salto de Longitud en México 1968.", category: "deportes" },
                { id: 790, question: "¿En qué deporte se utiliza una 'Manguera' o 'Pala' en lugar de una raqueta con cuerdas?", options: ["Tenis de Mesa", "Squash", "Bádminton", "Pádel"], correct: 3, explanation: "El Pádel utiliza una pala sólida sin cuerdas o un cordaje de red.", category: "deportes" },
                { id: 791, question: "¿Qué jugador de hockey sobre hielo es considerado el mejor de todos los tiempos y conocido como 'The Great One'?", options: ["Bobby Orr", "Mario Lemieux", "Wayne Gretzky", "Sidney Crosby"], correct: 2, explanation: "Wayne Gretzky ostenta casi todos los récords ofensivos de la NHL.", category: "deportes" },
                { id: 792, question: "¿Cuántos caballos son necesarios para un partido de polo?", options: ["4", "8", "6", "Depende del jugador"], correct: 0, explanation: "Cada equipo de polo tiene 4 jugadores a caballo en la cancha.", category: "deportes" },
                { id: 793, question: "¿Cuál es el deporte nacional de Canadá?", options: ["Hockey sobre hielo y Lacrosse", "Fútbol", "Béisbol", "Bobsleigh"], correct: 0, explanation: "El Hockey sobre Hielo (invierno) y el Lacrosse (verano) son los deportes nacionales.", category: "deportes" },
                { id: 794, question: "¿Qué carrera de caballos se conoce como 'la carrera de los dos minutos más grandes en el deporte'?", options: ["Kentucky Derby", "Grand National", "Preakness Stakes", "Belmont Stakes"], correct: 0, explanation: "El Kentucky Derby es famoso por su corta e intensa duración.", category: "deportes" },
                { id: 795, question: "¿Cómo se llama el arte marcial brasileño que combina danza y acrobacias?", options: ["Jiu-Jitsu", "Capoeira", "Samba", "Muay Thai"], correct: 1, explanation: "La Capoeira es una forma de arte marcial afrobrasileña.", category: "deportes" },
                { id: 796, question: "¿Cuántos *strikes* consecutivos se necesitan para un 'perfect game' en el béisbol?", options: ["18", "21", "24", "27"], correct: 3, explanation: "Un 'juego perfecto' es cuando el lanzador retira a los 27 bateadores sin que ninguno alcance base.", category: "deportes" },
                { id: 797, question: "¿Qué significa FIFA?", options: ["Federación Internacional de Fútbol Americano", "Federación Internacional de Fútbol Asociación", "Fondo Internacional de Fútbol Amateur", "Federación Internacional de Filantropía Atlética"], correct: 1, explanation: "FIFA significa *Fédération Internationale de Football Association*.", category: "deportes" },
                { id: 798, question: "¿Quién fue el ciclista más joven en ganar el Tour de Francia?", options: ["Egan Bernal", "Tadej Pogačar", "Eddy Merckx", "Henri Cornet"], correct: 3, explanation: "Henri Cornet ganó el Tour de 1904 con menos de 20 años.", category: "deportes" },
                { id: 799, question: "¿En qué deporte se utiliza una 'Red de Mano' para atrapar la pelota?", options: ["Fútbol", "Lacrosse", "Waterpolo", "Hockey"], correct: 1, explanation: "El Lacrosse utiliza un palo con una red de malla para llevar y lanzar la pelota.", category: "deportes" },
                { id: 800, question: "¿Cuál es el deporte en el que el atleta lanza una jabalina?", options: ["Pentatlón", "Decatlón", "Atletismo", "Bobsleigh"], correct: 2, explanation: "El lanzamiento de jabalina es una de las pruebas de lanzamiento del Atletismo.", category: "deportes" },
//tecnologia 801-900

                { id: 801, question: "¿Cuál es el acrónimo de World Wide Web?", options: ["WWW", "W3", "WEB", "WWC"], correct: 0, explanation: "WWW son las siglas de World Wide Web.", category: "tecnología" },
                { id: 802, question: "¿Qué unidad de medida se usa para la velocidad de procesamiento de un CPU?", options: ["Byte", "Hertz (Hz)", "Volt", "Watt"], correct: 1, explanation: "La velocidad se mide en GigaHertz (GHz) o MegaHertz (MHz).", category: "tecnología" },
                { id: 803, question: "¿Qué lenguaje de programación es conocido por ser usado para el desarrollo web *frontend*?", options: ["Python", "Java", "JavaScript", "C++"], correct: 2, explanation: "JavaScript es esencial para la interactividad del lado del cliente.", category: "tecnología" },
                { id: 804, question: "¿Cuál es el acrónimo de Random Access Memory?", options: ["ROM", "RAM", "CPU", "GPU"], correct: 1, explanation: "RAM significa Memoria de Acceso Aleatorio.", category: "tecnología" },
                { id: 805, question: "¿Qué empresa desarrolló el sistema operativo Android?", options: ["Apple", "Microsoft", "Google", "Samsung"], correct: 2, explanation: "Android fue desarrollado originalmente por Android Inc., comprada por Google.", category: "tecnología" },
                { id: 806, question: "¿Qué se mide en 'bits por segundo' (bps)?", options: ["Capacidad de almacenamiento", "Velocidad de descarga de datos", "Frecuencia de la señal", "Tamaño de pantalla"], correct: 1, explanation: "Los bits por segundo miden la velocidad de transferencia de datos.", category: "tecnología" },
                { id: 807, question: "¿Cuál fue la primera computadora electrónica digital de propósito general?", options: ["UNIVAC", "EDSAC", "ENIAC", "Mark I"], correct: 2, explanation: "La ENIAC (Electronic Numerical Integrator and Computer) se completó en 1945.", category: "tecnología" },
                { id: 808, question: "¿Qué tecnología permite transmitir voz a través de una conexión a Internet?", options: ["ADSL", "VoIP", "VPN", "LTE"], correct: 1, explanation: "VoIP (Voice over Internet Protocol) es la tecnología utilizada.", category: "tecnología" },
                { id: 809, question: "¿Qué empresa lanzó la primera computadora personal con interfaz gráfica de usuario (GUI) comercialmente exitosa?", options: ["IBM", "Microsoft", "Apple", "Xerox"], correct: 2, explanation: "El Macintosh de Apple (1984) popularizó la GUI y el ratón.", category: "tecnología" },
                { id: 810, question: "¿Qué tipo de software es Linux?", options: ["Software propietario", "Sistema operativo de código cerrado", "Sistema operativo de código abierto", "Aplicación de ofimática"], correct: 2, explanation: "Linux es conocido por ser un sistema operativo de código abierto y gratuito.", category: "tecnología" },
                { id: 811, question: "¿Qué se utiliza para convertir una dirección IP en un nombre de dominio legible (ej. google.com)?", options: ["DHCP", "Firewall", "Router", "DNS"], correct: 3, explanation: "DNS (Domain Name System) traduce nombres a direcciones IP.", category: "tecnología" },
                { id: 812, question: "¿Cuál es el nombre del primer microprocesador de Intel?", options: ["Intel 8086", "Intel 4004", "Intel Pentium", "Intel Core i3"], correct: 1, explanation: "El Intel 4004, lanzado en 1971, fue el primer microprocesador comercial.", category: "tecnología" },
                { id: 813, question: "¿Qué tipo de cable se utiliza a menudo para las conexiones Ethernet de red por cable?", options: ["Fibra óptica", "Coaxial", "Par trenzado (UTP)", "HDMI"], correct: 2, explanation: "El cable de Par Trenzado (como el Cat 5e o Cat 6) es el más común en Ethernet.", category: "tecnología" },
                { id: 814, question: "¿Cuál es la función principal de una tarjeta gráfica (GPU)?", options: ["Almacenar datos a largo plazo", "Realizar cálculos matemáticos de la CPU", "Procesar y renderizar imágenes y videos", "Proporcionar memoria temporal"], correct: 2, explanation: "La GPU (Graphics Processing Unit) se especializa en la manipulación de gráficos.", category: "tecnología" },
                { id: 815, question: "¿Qué término describe una red que conecta dispositivos en un área pequeña, como una casa u oficina?", options: ["WAN", "LAN", "MAN", "GAN"], correct: 1, explanation: "LAN (Local Area Network) es una red de área local.", category: "tecnología" },
                { id: 816, question: "¿Qué protocolo se utiliza para el envío de correos electrónicos?", options: ["HTTP", "FTP", "SMTP", "POP3"], correct: 2, explanation: "SMTP (Simple Mail Transfer Protocol) es el protocolo para enviar correos.", category: "tecnología" },
                { id: 817, question: "¿Qué tipo de almacenamiento no pierde los datos al apagar la computadora?", options: ["Volátil", "Cache", "No volátil", "DRAM"], correct: 2, explanation: "El almacenamiento no volátil (como el disco duro o SSD) retiene los datos sin energía.", category: "tecnología" },
                { id: 818, question: "¿Cuál es el lenguaje de marcado estándar para crear páginas web?", options: ["CSS", "XML", "HTML", "PHP"], correct: 2, explanation: "HTML (HyperText Markup Language) estructura el contenido de la web.", category: "tecnología" },
                { id: 819, question: "¿Qué invento de los laboratorios Bell en 1947 revolucionó la electrónica?", options: ["El Circuito Integrado", "El Transistor", "La Computadora Personal", "El Láser"], correct: 1, explanation: "El transistor permitió la miniaturización de la electrónica.", category: "tecnología" },
                { id: 820, question: "¿Qué significa el acrónimo URL?", options: ["Universal Resource Locator", "Uniform Remote Link", "Unified Resource Locator", "Uniform Resource Locator"], correct: 3, explanation: "URL significa Localizador Uniforme de Recursos.", category: "tecnología" },
                { id: 821, question: "¿Qué componente de hardware se considera el 'cerebro' de la computadora?", options: ["RAM", "Disco duro", "Placa base", "CPU"], correct: 3, explanation: "El CPU (Central Processing Unit) ejecuta las instrucciones del software.", category: "tecnología" },
                { id: 822, question: "¿Cómo se llama el proceso de encender una computadora?", options: ["Shutdown", "Sleep", "Reboot", "Booting (Arrancar)"], correct: 3, explanation: "El *booting* o arranque es el proceso inicial de carga del sistema operativo.", category: "tecnología" },
                { id: 823, question: "¿Qué compañía fundó Bill Gates y Paul Allen?", options: ["Apple", "Google", "Microsoft", "Oracle"], correct: 2, explanation: "Microsoft fue fundada por Gates y Allen en 1975.", category: "tecnología" },
                { id: 824, question: "¿Qué es un 'píxel' en términos de imágenes digitales?", options: ["Una línea de código", "La unidad más grande de una imagen", "El punto más pequeño de una imagen", "Una medida de velocidad"], correct: 2, explanation: "Un píxel (picture element) es el elemento unitario de color en una imagen.", category: "tecnología" },
                { id: 825, question: "¿Cuál es el nombre del protocolo estándar para transferir archivos entre computadoras a través de una red?", options: ["HTTP", "SMTP", "POP3", "FTP"], correct: 3, explanation: "FTP (File Transfer Protocol) se utiliza para subir y descargar archivos.", category: "tecnología" },
                { id: 826, question: "¿Qué significa el término 'Malware'?", options: ["Software de correo electrónico", "Software malicioso", "Software de gestión de base de datos", "Software de modelado 3D"], correct: 1, explanation: "Malware es la abreviatura de *Malicious Software*.", category: "tecnología" },
                { id: 827, question: "¿Qué lenguaje de programación se utiliza a menudo para el análisis de datos y la inteligencia artificial?", options: ["C#", "Ruby", "Python", "PHP"], correct: 2, explanation: "Python es muy popular en el campo de Data Science y Machine Learning.", category: "tecnología" },
                { id: 828, question: "¿Qué tecnología inalámbrica se utiliza para conectar periféricos a corta distancia (ratones, teclados, etc.)?", options: ["Wi-Fi", "NFC", "Bluetooth", "3G"], correct: 2, explanation: "Bluetooth es el estándar para la comunicación inalámbrica de corto alcance.", category: "tecnología" },
                { id: 829, question: "¿Qué significa el acrónimo SSD?", options: ["Super Speed Drive", "Solid State Drive", "System Security Device", "Standard Storage Disk"], correct: 1, explanation: "SSD (Solid State Drive) es un dispositivo de almacenamiento basado en memoria flash.", category: "tecnología" },
                { id: 830, question: "¿Qué es el *firmware*?", options: ["El software que se compra en una tienda", "Software integrado directamente en un hardware", "Un tipo de virus informático", "La parte más reciente de un sistema operativo"], correct: 1, explanation: "El *firmware* es software de bajo nivel que proporciona control para el hardware del dispositivo.", category: "tecnología" },
                { id: 831, question: "¿Cuál es el principal objetivo del *phishing*?", options: ["Mejorar la velocidad de la red", "Robar información confidencial del usuario", "Bloquear el acceso a sitios web", "Cifrar archivos para protegerlos"], correct: 1, explanation: "El *phishing* es un intento de adquirir información sensible haciéndose pasar por una entidad de confianza.", category: "tecnología" },
                { id: 832, question: "¿Qué protocolo de red se utiliza para la navegación web segura (con cifrado)?", options: ["HTTP", "HTTPS", "FTP", "SSH"], correct: 1, explanation: "HTTPS añade la capa de seguridad SSL/TLS al protocolo HTTP.", category: "tecnología" },
                { id: 833, question: "¿Qué compañía popularizó el uso de los microprocesadores x86 en las computadoras personales?", options: ["Apple", "Motorola", "AMD", "Intel"], correct: 3, explanation: "Intel, con sus chips como el 8086 y sus sucesores, se convirtió en el estándar.", category: "tecnología" },
                { id: 834, question: "¿Qué se mide en *dpi* (dots per inch) en una impresora o escáner?", options: ["Velocidad de impresión", "Resolución de imagen", "Tamaño del papel", "Consumo de tinta"], correct: 1, explanation: "Los DPI miden la resolución de imagen o impresión (puntos por pulgada).", category: "tecnología" },
                { id: 835, question: "¿Qué tipo de red permite a los usuarios acceder a una red privada sobre una red pública (Internet)?", options: ["VPN", "LAN", "WAN", "PAN"], correct: 0, explanation: "VPN (Virtual Private Network) crea una conexión segura sobre Internet.", category: "tecnología" },
                { id: 836, question: "¿Qué significa el acrónimo IoT?", options: ["Internet of Traffic", "Information on Time", "Internet of Things", "Integrated Operating Tools"], correct: 2, explanation: "IoT significa Internet de las Cosas.", category: "tecnología" },
                { id: 837, question: "¿Quién es considerado uno de los padres de Internet por su trabajo en el protocolo TCP/IP?", options: ["Tim Berners-Lee", "Vint Cerf", "Alan Turing", "Steve Wozniak"], correct: 1, explanation: "Vint Cerf, junto con Bob Kahn, es a menudo llamado 'el padre de Internet'.", category: "tecnología" },
                { id: 838, question: "¿Qué es un 'algoritmo' en informática?", options: ["Un tipo de virus", "Un lenguaje de programación", "Un conjunto de pasos para realizar una tarea", "Una pieza de hardware"], correct: 2, explanation: "Un algoritmo es una secuencia finita de instrucciones para resolver un problema.", category: "tecnología" },
                { id: 839, question: "¿Qué se utiliza en las pantallas OLED para emitir luz?", options: ["Cristales líquidos", "Diodos emisores de luz orgánicos", "Plasma de gas noble", "Lámparas fluorescentes"], correct: 1, explanation: "OLED significa *Organic Light-Emitting Diode*.", category: "tecnología" },
                { id: 840, question: "¿Qué tipo de ataque intenta saturar un servidor con tráfico masivo para dejarlo inaccesible?", options: ["Phishing", "Ransomware", "DDoS", "Keylogging"], correct: 2, explanation: "DDoS (Distributed Denial of Service) es un ataque de denegación de servicio distribuido.", category: "tecnología" },
                { id: 841, question: "¿Cuál es el nombre del lenguaje de programación creado por Guido van Rossum?", options: ["Java", "C++", "Python", "Ruby"], correct: 2, explanation: "Guido van Rossum creó Python, conocido por su sintaxis legible.", category: "tecnología" },
                { id: 842, question: "¿Qué término se usa para una imagen que no pierde calidad al cambiar su tamaño (basada en ecuaciones matemáticas)?", options: ["Rasterizada", "Bitmap", "Vectorial", "Pixelada"], correct: 2, explanation: "Las imágenes vectoriales (ej. SVG) son escalables sin pérdida de calidad.", category: "tecnología" },
                { id: 843, question: "¿Cuál es la función del *router* en una red?", options: ["Almacenar datos de la red", "Filtrar correo no deseado", "Dirigir el tráfico de datos entre diferentes redes", "Generar direcciones IP automáticamente"], correct: 2, explanation: "El *router* conecta redes (como tu LAN a Internet).", category: "tecnología" },
                { id: 844, question: "¿Qué significa el acrónimo GPS?", options: ["Global Positioning System", "General Power Source", "Geographic Program System", "Global Privacy Shield"], correct: 0, explanation: "GPS (Sistema de Posicionamiento Global) se basa en una red de satélites.", category: "tecnología" },
                { id: 845, question: "¿Qué sistema de codificación es el estándar moderno para representar texto en computadoras (incluyendo emojis)?", options: ["ASCII", "Unicode", "EBCDIC", "ISO-8859"], correct: 1, explanation: "Unicode es el estándar actual, con UTF-8 siendo la codificación más común.", category: "tecnología" },
                { id: 846, question: "¿Quién fue el inventor de la imprenta con tipos móviles, considerada la primera revolución tecnológica?", options: ["Leonardo da Vinci", "Johannes Gutenberg", "Galileo Galilei", "Thomas Edison"], correct: 1, explanation: "Johannes Gutenberg inventó la imprenta moderna alrededor de 1440.", category: "tecnología" },
                { id: 847, question: "¿Qué se entiende por 'Big Data'?", options: ["Una computadora grande", "El uso de discos duros de gran capacidad", "Conjuntos de datos extremadamente grandes y complejos", "Un programa de contabilidad"], correct: 2, explanation: "Big Data se refiere a datos con gran volumen, velocidad y variedad (*3 V's*).", category: "tecnología" },
                { id: 848, question: "¿Qué tipo de tecnología permite a un programa aprender de los datos sin ser programado explícitamente?", options: ["Inteligencia artificial débil", "Realidad aumentada", "Aprendizaje automático (Machine Learning)", "Computación cuántica"], correct: 2, explanation: "El *Machine Learning* es una rama de la IA enfocada en el aprendizaje a partir de datos.", category: "tecnología" },
                { id: 849, question: "¿Cuál es la abreviatura de la tecnología de conexión inalámbrica de corto alcance que usan las tarjetas de crédito *contactless*?", options: ["Wi-Fi", "Bluetooth", "NFC", "RFID"], correct: 2, explanation: "NFC (Near Field Communication) se utiliza para pagos y conexiones a muy corta distancia.", category: "tecnología" },
                { id: 850, question: "¿Cuál es la capa superior de un chip de silicio que conecta los transistores?", options: ["Diodo", "Sustrato", "Metal", "Capacitor"], correct: 2, explanation: "Las capas de **metal** (aluminio o cobre) se utilizan como interconexiones eléctricas en los chips.", category: "tecnología" },
                { id: 851, question: "¿Qué significa el acrónimo LED?", options: ["Light Emitting Display", "Liquid Energy Device", "Low Emission Diode", "Light Emitting Diode"], correct: 3, explanation: "LED significa Diodo Emisor de Luz.", category: "tecnología" },
                { id: 852, question: "¿Cuál es el principal estándar de hoja de estilo utilizado para dar formato a los documentos HTML?", options: ["JavaScript", "Python", "CSS", "SQL"], correct: 2, explanation: "CSS (Cascading Style Sheets) es fundamental para el diseño y la presentación web.", category: "tecnología" },
                { id: 853, question: "¿Qué tipo de impresora crea modelos tridimensionales a partir de un archivo digital?", options: ["Inyección de tinta", "Láser", "Matriz de puntos", "3D"], correct: 3, explanation: "Las impresoras 3D construyen objetos capa por capa.", category: "tecnología" },
                { id: 854, question: "¿Qué compañía desarrolló el sistema operativo MS-DOS?", options: ["Apple", "IBM", "Microsoft", "Intel"], correct: 2, explanation: "MS-DOS (*Microsoft Disk Operating System*) fue el sistema de Microsoft antes de Windows.", category: "tecnología" },
                { id: 855, question: "¿Qué tecnología permite que una cámara de seguridad se mueva automáticamente para seguir un objeto?", options: ["PTZ", "NVR", "DVR", "POE"], correct: 0, explanation: "PTZ (Pan-Tilt-Zoom) son las funciones de movimiento de la cámara.", category: "tecnología" },
                { id: 856, question: "¿Qué es un 'servidor proxy'?", options: ["Un tipo de base de datos", "Un servidor que actúa como intermediario entre un usuario y otro servidor", "Un tipo de cable de red", "Un software antivirus"], correct: 1, explanation: "Un servidor proxy filtra o reenvía solicitudes de clientes a otros servidores.", category: "tecnología" },
                { id: 857, question: "¿Qué se utiliza en las pantallas LCD para generar luz de fondo?", options: ["LED o CCFL", "Diodos orgánicos", "Filamentos incandescentes", "Plasma"], correct: 0, explanation: "Las pantallas LCD (cristal líquido) requieren una luz de fondo, típicamente LED o CCFL (*Cold Cathode Fluorescent Lamp*).", category: "tecnología" },
                { id: 858, question: "¿Cuál es la principal diferencia entre un *Data Lake* y un *Data Warehouse*?", options: ["El Data Lake es más pequeño", "El Data Lake almacena datos sin procesar (crudos)", "El Data Warehouse almacena datos no estructurados", "No hay diferencia real"], correct: 1, explanation: "El Data Lake almacena datos en su formato original, sin procesar ni estructurar.", category: "tecnología" },
                { id: 859, question: "¿Qué tecnología se utiliza para escanear y leer códigos de barras o QR?", options: ["GPS", "NFC", "Óptica", "Infrarrojos"], correct: 2, explanation: "Los lectores utilizan tecnología óptica (láser o cámara) para interpretar los patrones.", category: "tecnología" },
                { id: 860, question: "¿Cuál es el nombre de la placa principal que conecta todos los componentes de una computadora?", options: ["CPU", "GPU", "Placa base (Motherboard)", "Tarjeta de red"], correct: 2, explanation: "La placa base (Motherboard o Mainboard) es el circuito principal.", category: "tecnología" },
                { id: 861, question: "¿Qué protocolo de correo electrónico se utiliza para *recibir* correos y almacenarlos en el servidor?", options: ["SMTP", "POP3 y IMAP", "HTTP", "FTP"], correct: 1, explanation: "POP3 (descarga y elimina) e IMAP (sincronización) son los protocolos de recepción.", category: "tecnología" },
                { id: 862, question: "¿Qué se mide en 'Terabytes' (TB)?", options: ["Velocidad de Internet", "Capacidad de almacenamiento", "Frecuencia del procesador", "Velocidad de impresión"], correct: 1, explanation: "Un Terabyte es una unidad de capacidad de almacenamiento (1024 Gigabytes).", category: "tecnología" },
                { id: 863, question: "¿Qué tecnología de cableado es inmune a las interferencias electromagnéticas y se usa para largas distancias?", options: ["Coaxial", "Fibra óptica", "Par trenzado", "USB"], correct: 1, explanation: "La fibra óptica utiliza luz, no electricidad, lo que la hace inmune a EMI.", category: "tecnología" },
                { id: 864, question: "¿Qué se entiende por 'Cloud Computing'?", options: ["Programas que funcionan en clima nublado", "El almacenamiento de datos en la memoria RAM", "El uso de servicios informáticos a través de Internet", "La conexión por cable de red"], correct: 2, explanation: "La Computación en la Nube se refiere al acceso bajo demanda a recursos informáticos por Internet.", category: "tecnología" },
                { id: 865, question: "¿Qué tipo de software se utiliza para proteger la red de accesos no autorizados?", options: ["Antivirus", "Firewall", "Navegador web", "Sistema operativo"], correct: 1, explanation: "El Firewall (Cortafuegos) actúa como una barrera de seguridad.", category: "tecnología" },
                { id: 866, question: "¿Qué es la 'Latencia' en redes informáticas?", options: ["La velocidad máxima de descarga", "El tiempo de retardo en la transmisión de datos", "El número de dispositivos conectados", "El ancho de banda disponible"], correct: 1, explanation: "La latencia es el tiempo que tarda un paquete de datos en ir de un punto a otro.", category: "tecnología" },
                { id: 867, question: "¿Qué significa el acrónimo VR?", options: ["Voice Recognition", "Virtual Reality", "Video Recording", "Vector Raster"], correct: 1, explanation: "VR significa Realidad Virtual.", category: "tecnología" },
                { id: 868, question: "¿Cuál es el nombre del primer lenguaje de programación de alto nivel de amplio uso (creado en 1957)?", options: ["C", "FORTRAN", "COBOL", "BASIC"], correct: 1, explanation: "FORTRAN (Formula Translation) fue creado por IBM y es uno de los más antiguos.", category: "tecnología" },
                { id: 869, question: "¿Qué se utiliza para cifrar los datos en la tecnología *blockchain*?", options: ["Direcciones IP", "Protocolos HTTP", "Funciones *Hash*", "Sistemas de *Cache*"], correct: 2, explanation: "Las funciones *hash* criptográficas garantizan la integridad de los bloques de la cadena.", category: "tecnología" },
                { id: 870, question: "¿Qué significa el acrónimo SCM en el contexto de la gestión de proyectos de software (ej. Git)?", options: ["Software Code Management", "Source Code Metrics", "Software Configuration Management", "System Control Module"], correct: 2, explanation: "SCM (Software Configuration Management) se ocupa de gestionar los cambios en el código (ej. con Git).", category: "tecnología" },
                { id: 871, question: "¿Qué inventor es conocido por la bombilla incandescente y el fonógrafo?", options: ["Nikola Tesla", "Alexander Graham Bell", "Thomas Edison", "Guglielmo Marconi"], correct: 2, explanation: "Thomas Edison es famoso por sus inventos en la electricidad y grabación de sonido.", category: "tecnología" },
                { id: 872, question: "¿Qué se entiende por 'Realidad Aumentada' (AR)?", options: ["Una simulación totalmente inmersiva", "Imágenes y sonido generados por computadora en el mundo real", "Una simulación de un mundo inexistente", "El estudio de la física cuántica"], correct: 1, explanation: "La Realidad Aumentada superpone elementos virtuales sobre la visión real del usuario.", category: "tecnología" },
                { id: 873, question: "¿Cuál es el principal estándar de comunicación para la tecnología *Bluetooth*?", options: ["IEEE 802.11", "IEEE 802.15.1", "IEEE 802.3", "IEEE 802.16"], correct: 1, explanation: "IEEE 802.15.1 es el estándar original de Bluetooth.", category: "tecnología" },
                { id: 874, question: "¿Qué es un 'cookie' de Internet?", options: ["Un archivo multimedia", "Un pequeño archivo de texto almacenado en el navegador", "Un tipo de virus informático", "Un lenguaje de programación web"], correct: 1, explanation: "Las *cookies* almacenan información de estado para recordar al usuario en futuras visitas.", category: "tecnología" },
                { id: 875, question: "¿Cuál es el nombre del puerto de video digital que reemplazó a VGA y DVI y se usa comúnmente en pantallas modernas?", options: ["HDMI", "USB-C", "DisplayPort", "Thunderbolt"], correct: 0, explanation: "HDMI (High-Definition Multimedia Interface) es el estándar de conexión más común.", category: "tecnología" },
                { id: 876, question: "¿Qué se utiliza para crear copias de seguridad de una base de datos en un momento específico?", options: ["Claves primarias", "Instantáneas (*Snapshot*)", "Consultas SQL", "Triggers"], correct: 1, explanation: "Una *snapshot* o instantánea es una copia del estado de un sistema o base de datos en un momento dado.", category: "tecnología" },
                { id: 877, question: "¿Qué tipo de ataque utiliza programas que se disfrazan de software útil?", options: ["Gusano (*Worm*)", "Caballo de Troya (*Trojan*)", "Adware", "Spyware"], correct: 1, explanation: "Un *Caballo de Troya* se instala ocultando su propósito malicioso.", category: "tecnología" },
                { id: 878, question: "¿Qué significa el acrónimo API?", options: ["Application Programming Interface", "Advanced Personal Identifier", "Automated Process Integrator", "Application Privacy Indicator"], correct: 0, explanation: "API (Interfaz de Programación de Aplicaciones) permite que el software interactúe entre sí.", category: "tecnología" },
                { id: 879, question: "¿Quién es considerado el 'padre de la teoría de la computación' y la 'Inteligencia Artificial'?", options: ["Bill Gates", "Alan Turing", "John von Neumann", "Ada Lovelace"], correct: 1, explanation: "Alan Turing, con su concepto de la 'Máquina de Turing' y el 'Test de Turing'.", category: "tecnología" },
                { id: 880, question: "¿Qué componente se encarga de convertir la corriente alterna (AC) en corriente continua (DC) para la computadora?", options: ["Tarjeta de red", "Placa base", "Unidad de Fuente de Alimentación (PSU)", "Regulador de voltaje"], correct: 2, explanation: "La PSU (Power Supply Unit) realiza la conversión y regula el voltaje.", category: "tecnología" },
                { id: 881, question: "¿Qué lenguaje se utiliza para manipular y consultar bases de datos relacionales?", options: ["HTML", "C++", "SQL", "JavaScript"], correct: 2, explanation: "SQL (Structured Query Language) es el estándar para bases de datos relacionales.", category: "tecnología" },
                { id: 882, question: "¿Qué se utiliza en la tecnología de reconocimiento facial para mapear las características de la cara?", options: ["Píxeles 3D", "Puntos nodales", "Funciones *Hash*", "Vectores geométricos"], correct: 1, explanation: "Los sistemas de reconocimiento facial identifican y miden *puntos nodales* o puntos clave en el rostro.", category: "tecnología" },
                { id: 883, question: "¿Cuál es la principal desventaja de la tecnología LCD en comparación con OLED?", options: ["Mayor consumo de energía", "Baja resolución", "Menor vida útil", "Negros menos profundos (necesita retroiluminación)"], correct: 3, explanation: "LCD requiere una luz de fondo, lo que impide alcanzar el negro puro que logra OLED.", category: "tecnología" },
                { id: 884, question: "¿Qué se entiende por 'Realidad Mixta' (MR)?", options: ["Realidad aumentada y virtual en paralelo", "La fusión de mundos real y virtual para producir nuevos entornos", "Un tipo de juego de computadora", "Una técnica de compresión de datos"], correct: 1, explanation: "La Realidad Mixta (ej. Hololens) permite la interacción física y virtual.", category: "tecnología" },
                { id: 885, question: "¿Qué es un *bytecode*?", options: ["El código fuente de un programa", "Código ejecutable intermedio usado por máquinas virtuales (ej. Java)", "Un tipo de dato en C++", "La salida de un compilador de Python"], correct: 1, explanation: "El *bytecode* es un código de bajo nivel que se interpreta en una máquina virtual.", category: "tecnología" },
                { id: 886, question: "¿Cuál es el nombre de la prueba que se usa para determinar si una máquina puede exhibir un comportamiento inteligente indistinguible de un humano?", options: ["Test de Lógica", "Test de Turing", "Test de Computabilidad", "Test de Velocidad"], correct: 1, explanation: "El Test de Turing, propuesto por Alan Turing, es la prueba de inteligencia artificial.", category: "tecnología" },
                { id: 887, question: "¿Qué significa el acrónimo IaaS en *Cloud Computing*?", options: ["Internal Application as a Service", "Identity and Access as a Service", "Infrastructure as a Service", "Integration and Analysis as a Service"], correct: 2, explanation: "IaaS (Infraestructura como Servicio) proporciona recursos informáticos básicos por Internet.", category: "tecnología" },
                { id: 888, question: "¿Qué componente de hardware se conecta directamente al *Northbridge* o *Southbridge* (en arquitecturas antiguas)?", options: ["Teclado", "CPU y Memoria RAM", "Impresora", "Ratón"], correct: 1, explanation: "El *Northbridge* (o *Memory Controller Hub*) conectaba la CPU con la RAM y la tarjeta gráfica.", category: "tecnología" },
                { id: 889, question: "¿Qué lenguaje de programación es esencial para el desarrollo de aplicaciones nativas de iOS?", options: ["Java", "Kotlin", "Swift", "C#"], correct: 2, explanation: "Swift es el lenguaje moderno de Apple para el desarrollo de iOS/macOS.", category: "tecnología" },
                { id: 890, question: "¿Cuál es el nombre de la tecnología que permite a una computadora trabajar con más de un núcleo de procesamiento?", options: ["Overclocking", "Multitarea", "Multihilo (*Multithreading*)", "Multicore"], correct: 3, explanation: "La tecnología *Multicore* (múltiples núcleos) aumenta la capacidad de procesamiento paralelo.", category: "tecnología" },
                { id: 891, question: "¿Qué significa el acrónimo SaaS en *Cloud Computing*?", options: ["Software as a Service", "System Access and Storage", "Service and Application Security", "Scalable Application and System"], correct: 0, explanation: "SaaS (Software como Servicio) proporciona aplicaciones alojadas en la nube a los usuarios.", category: "tecnología" },
                { id: 892, question: "¿Qué se utiliza para crear un modelo digital de un objeto físico mediante la medición de su geometría?", options: ["Modelado CAD", "Renderizado", "Escaneo 3D", "Impresión 3D"], correct: 2, explanation: "El Escaneo 3D captura la forma y, a veces, el color de un objeto real.", category: "tecnología" },
                { id: 893, question: "¿Cuál es la función principal de la *Cache* de un CPU?", options: ["Almacenar datos a largo plazo", "Almacenar datos usados frecuentemente para un acceso rápido", "Suministrar energía a la CPU", "Controlar la temperatura de la CPU"], correct: 1, explanation: "La *Cache* es una memoria pequeña y muy rápida para acelerar el acceso a los datos.", category: "tecnología" },
                { id: 894, question: "¿Qué tipo de red inalámbrica se usa en las ciudades para proporcionar cobertura en un área metropolitana?", options: ["LAN", "WAN", "PAN", "MAN"], correct: 3, explanation: "MAN (Metropolitan Area Network) cubre un área geográfica de tamaño urbano.", category: "tecnología" },
                { id: 895, question: "¿Cuál es el nombre del estándar de compresión de audio más popular?", options: ["WAV", "FLAC", "MP3", "AAC"], correct: 2, explanation: "MP3 es el formato de audio comprimido más ampliamente adoptado.", category: "tecnología" },
                { id: 896, question: "¿Qué inventó el científico J.C.R. Licklider, que fue crucial para el desarrollo de Internet?", options: ["El ratón", "El módem", "La idea de la red galáctica (red global de computadoras)", "El microprocesador"], correct: 2, explanation: "Licklider fue uno de los pioneros de la informática y el concepto de red interconectada.", category: "tecnología" },
                { id: 897, question: "¿Qué significa el acrónimo RAID en el almacenamiento de datos?", options: ["Random Access Input Device", "Redundant Array of Independent Disks", "Rapid Application Interface Device", "Remote Access Installation Driver"], correct: 1, explanation: "RAID se utiliza para mejorar el rendimiento o la redundancia (copia de seguridad) de los datos.", category: "tecnología" },
                { id: 898, question: "¿Cuál es el principal estándar de comunicación inalámbrica utilizado en redes Wi-Fi?", options: ["IEEE 802.11", "IEEE 802.3", "IEEE 802.15", "IEEE 802.16"], correct: 0, explanation: "IEEE 802.11 es la familia de estándares para redes de área local inalámbricas (WLAN).", category: "tecnología" },
                { id: 899, question: "¿Qué tipo de software permite a los sistemas operativos emular el hardware de otra computadora?", options: ["Driver", "Antivirus", "Máquina Virtual", "Compilador"], correct: 2, explanation: "Una Máquina Virtual (VM) emula un sistema operativo y su hardware asociado dentro de otro sistema operativo.", category: "tecnología" },
                { id: 900, question: "¿Qué tecnología utiliza láser para leer datos almacenados en discos (CD, DVD, Blu-ray)?", options: ["Tecnología magnética", "Tecnología de estado sólido", "Tecnología óptica", "Tecnología de *Flash*"], correct: 2, explanation: "Los discos ópticos usan láser para leer y escribir datos.", category: "tecnología" }
                            ];
            return questions;
        }

        const allQuestions = generateQuestions();
        let currentQuestions = [];
        let currentQuestionIndex = 0;
        let userAnswers = [];
        let timer, timeLeft = 120; // Cambiado a 120 segundos (2 minutos)
        let selectedCategory = null;

        /* DOM */
        const categoryScreen = document.getElementById('category-screen');
        const quizScreen = document.getElementById('quiz-screen');
        const resultsScreen = document.getElementById('results-screen');
        const categoriesContainer = document.getElementById('categories-container');
        const startBtn = document.getElementById('start-btn');
        const questionText = document.getElementById('question-text');
        const questionCategory = document.getElementById('question-category');
        const optionsContainer = document.getElementById('options-container');
        const prevBtn = document.getElementById('prev-btn');
        const nextBtn = document.getElementById('next-btn');
        const questionNumber = document.getElementById('question-number');
        const currentQuestionSpan = document.getElementById('current-question');
        const timeDisplay = document.getElementById('time');
        const finalScore = document.getElementById('final-score');
        const resultMessage = document.getElementById('result-message');
        const resultsSummary = document.getElementById('results-summary');
        const restartBtn = document.getElementById('restart-btn');
        const feedbackDiv = document.getElementById('feedback');
        const confettiCanvas = document.getElementById('confetti-canvas');
        const app = document.getElementById('app');

        /* -------------------------
           Inicializar app
           ------------------------- */
        function initApp() {
            renderCategories();
            setupEventListeners();
        }
        window.onload = initApp;

        /* -------------------------
           Render categorías
           ------------------------- */
        function renderCategories() {
            categoriesContainer.innerHTML = '';
            categories.forEach(cat => {
                const card = document.createElement('div');
                card.className = 'category-card';
                card.dataset.id = cat.id;
                card.innerHTML = `<div class="category-icon">${cat.icon}</div><div class="category-name">${cat.name}</div>`;
                card.addEventListener('click', () => selectCategory(cat.id, card));
                categoriesContainer.appendChild(card);
            });
            setupEventListeners(); // Agregar esta línea
        }

        function selectCategory(categoryId, cardEl) {
            document.querySelectorAll('.category-card').forEach(c => c.classList.remove('selected'));
            cardEl.classList.add('selected');
            selectedCategory = categoryId;
            startBtn.disabled = false;
        }

        /* -------------------------
           Event listeners
           ------------------------- */
        function setupEventListeners() {
            startBtn.addEventListener('click', startQuiz);
            prevBtn.addEventListener('click', prevQuestion);
            nextBtn.addEventListener('click', nextQuestion);
            restartBtn.addEventListener('click', restartQuiz);

            // Agregar doble clic a las categorías
            document.querySelectorAll('.category-card').forEach(card => {
                card.addEventListener('dblclick', () => {
                    const categoryId = card.dataset.id;
                    selectCategory(categoryId, card);
                    startQuiz(); // Inicia el quiz inmediatamente
                });
            });
        }

        /* -------------------------
           Iniciar cuestionario
           ------------------------- */
        function startQuiz() {
            // Reiniciar el temporizador cada vez que se inicia un nuevo quiz
            clearInterval(timer);
            timeLeft = 120; // Reiniciar a 120 segundos

            if (selectedCategory === 'mixtas') {
                currentQuestions = getRandomQuestions(allQuestions, 10);
            } else {
                const pool = allQuestions.filter(q => q.category === selectedCategory);
                currentQuestions = getRandomQuestions(pool, 10);
            }
            currentQuestionIndex = 0;
            userAnswers = Array(10).fill(null);
            startTimer();
            showQuestion();
            categoryScreen.style.display = 'none';
            quizScreen.style.display = 'block';
            resultsScreen.style.display = 'none';
        }

        /* -------------------------
           Random questions
           ------------------------- */
        function getRandomQuestions(questions, count) {
            if (questions.length <= count) return [...questions];
            return [...questions].sort(() => 0.5 - Math.random()).slice(0, count);
        }

        /* -------------------------
           Mostrar pregunta
           ------------------------- */
        function showQuestion() {
            const q = currentQuestions[currentQuestionIndex];
            const catInfo = categories.find(c => c.id === q.category) || { name: '', color: '#888' };

            questionText.textContent = q.question;
            questionNumber.textContent = currentQuestionIndex + 1;
            currentQuestionSpan.textContent = currentQuestionIndex + 1;

            questionCategory.textContent = catInfo.name;
            questionCategory.style.backgroundColor = catInfo.color;
            questionCategory.style.color = '#fff';

            // Modificar la función getRandomQuestions
            function getRandomQuestions(questions, count) {
                // Crear una copia del array de preguntas para no modificar el original
                const shuffledQuestions = [...questions];

                // Algoritmo de Fisher-Yates para mezclar el array
                for (let i = shuffledQuestions.length - 1; i > 0; i--) {
                    const j = Math.floor(Math.random() * (i + 1));
                    [shuffledQuestions[i], shuffledQuestions[j]] = [shuffledQuestions[j], shuffledQuestions[i]];
                }

                // Retornar solo las primeras 'count' preguntas
                return shuffledQuestions.slice(0, count);
            }

            // Modificar la función startQuiz para usar la nueva función
            function startQuiz() {
                // Reiniciar el temporizador
                clearInterval(timer);
                timeLeft = 120;

                // Seleccionar preguntas según la categoría
                if (selectedCategory === 'mixtas') {
                    // Para preguntas mixtas, tomar de todas las categorías
                    currentQuestions = getRandomQuestions(allQuestions, 10);
                } else {
                    // Para una categoría específica, filtrar primero
                    const categoryQuestions = allQuestions.filter(q => q.category === selectedCategory);
                    currentQuestions = getRandomQuestions(categoryQuestions, 10);
                }

                // Reiniciar el estado del quiz
                currentQuestionIndex = 0;
                userAnswers = Array(10).fill(null);

                // Iniciar el temporizador y mostrar la primera pregunta
                startTimer();
                showQuestion();

                // Cambiar la visualización de las pantallas
                categoryScreen.style.display = 'none';
                quizScreen.style.display = 'block';
                resultsScreen.style.display = 'none';
            }

            function getRandomQuestions(questions, count) {
                // Crear una copia del array de preguntas para no modificar el original
                const shuffledQuestions = [...questions];

                // Algoritmo de Fisher-Yates para mezclar el array
                for (let i = shuffledQuestions.length - 1; i > 0; i--) {
                    const j = Math.floor(Math.random() * (i + 1));
                    [shuffledQuestions[i], shuffledQuestions[j]] = [shuffledQuestions[j], shuffledQuestions[i]];
                }

                // Retornar solo las primeras 'count' preguntas
                return shuffledQuestions.slice(0, count);
            }

            // Modificar la función startQuiz para usar la nueva función
            function startQuiz() {
                // Reiniciar el temporizador
                clearInterval(timer);
                timeLeft = 120;

                // Seleccionar preguntas según la categoría
                if (selectedCategory === 'mixtas') {
                    // Para preguntas mixtas, tomar de todas las categorías
                    currentQuestions = getRandomQuestions(allQuestions, 10);
                } else {
                    // Para una categoría específica, filtrar primero
                    const categoryQuestions = allQuestions.filter(q => q.category === selectedCategory);
                    currentQuestions = getRandomQuestions(categoryQuestions, 10);
                }

                // Reiniciar el estado del quiz
                currentQuestionIndex = 0;
                userAnswers = Array(10).fill(null);

                // Iniciar el temporizador y mostrar la primera pregunta
                startTimer();
                showQuestion();

                // Cambiar la visualización de las pantallas
                categoryScreen.style.display = 'none';
                quizScreen.style.display = 'block';
                resultsScreen.style.display = 'none';
            }
            // opciones
            optionsContainer.innerHTML = '';
            q.options.forEach((opt, idx) => {
                const el = document.createElement('div');
                el.className = 'option';
                if (userAnswers[currentQuestionIndex] === idx) el.classList.add('selected');

                const letter = document.createElement('div');
                letter.className = 'option-letter';
                letter.textContent = String.fromCharCode(65 + idx);

                const text = document.createElement('div');
                text.textContent = opt;

                el.appendChild(letter);
                el.appendChild(text);

                el.addEventListener('click', () => selectOption(idx));
                optionsContainer.appendChild(el);
            });

            prevBtn.disabled = currentQuestionIndex === 0;
            nextBtn.textContent = currentQuestionIndex === 9 ? 'Finalizar' : 'Siguiente';
        }

        /* -------------------------
           Seleccionar opción (feedback inmediato)
           ------------------------- */
        function selectOption(optionIndex) {
            const q = currentQuestions[currentQuestionIndex];

            // Guardar respuesta
            userAnswers[currentQuestionIndex] = optionIndex;

            // Marcar seleccionado visualmente
            // (re-render opciones)
            showQuestion();

            // Mostrar feedback inmediato
            if (optionIndex === q.correct) {
                showFeedbackCorrect();
            } else {
                showFeedbackIncorrect();
            }
        }

        /* -------------------------
           Feedback: Correcto (confeti + cohete)
           ------------------------- */
        function showFeedbackCorrect() {
            // texto
            feedbackDiv.className = 'feedback correct show';
            feedbackDiv.innerHTML = `✅ ¡Correcto! <span style="margin-left:8px">🎉🚀</span>`;

            // confetti por toda la pantalla
            confettiBurst(80);

            // ocultar después
            setTimeout(() => { feedbackDiv.classList.remove('show'); }, 1600);
        }

        /* -------------------------
           Feedback: Incorrecto (X roja + carita triste + vibración)
           ------------------------- */
        function showFeedbackIncorrect() {
            feedbackDiv.className = 'feedback incorrect show';
            feedbackDiv.innerHTML = `❌ Incorrecto <span style="margin-left:8px">😢</span>`;

            // efecto de temblor en contenedor de opciones
            optionsContainer.classList.add('shake');
            setTimeout(() => { optionsContainer.classList.remove('shake'); }, 480);

            // vibrar si el dispositivo lo permite
            if (window.navigator && navigator.vibrate) {
                navigator.vibrate([80, 40, 80]);
            }

            setTimeout(() => { feedbackDiv.classList.remove('show'); }, 1400);
        }

        /* -------------------------
           Navegación preguntas
           ------------------------- */
        function prevQuestion() { if (currentQuestionIndex > 0) { currentQuestionIndex--; showQuestion(); } }
        function nextQuestion() { if (currentQuestionIndex < 9) { currentQuestionIndex++; showQuestion(); } else { finishQuiz(); } }

        /* -------------------------
           Temporizador
           ------------------------- */
        function startTimer() {
            clearInterval(timer);
            timeLeft = 120; // Asegurar que empiece en 120 segundos
            updateTimerDisplay();
            timer = setInterval(() => {
                timeLeft--;
                updateTimerDisplay();
                if (timeLeft <= 0) {
                    clearInterval(timer);
                    finishQuiz();
                }
            }, 1000);
        }
        function updateTimerDisplay() {
            const m = Math.floor(timeLeft / 60);
            const s = timeLeft % 60;
            timeDisplay.textContent = `${String(m).padStart(2, '0')}:${String(s).padStart(2, '0')}`;
            if (timeLeft <= 10) { timeDisplay.style.color = '#dc3545'; } else { timeDisplay.style.color = ''; }
        }

        /* -------------------------
           Finalizar y mostrar resultados
           ------------------------- */
        function finishQuiz() {
            clearInterval(timer);
            let score = 0;
            currentQuestions.forEach((q, i) => { if (userAnswers[i] === q.correct) score++; });

            finalScore.textContent = `${score}/10`;
            if (score >= 9) resultMessage.textContent = "¡Excelente! Has demostrado un gran conocimiento.";
            else if (score >= 7) resultMessage.textContent = "¡Buen trabajo! Tienes un buen nivel de conocimiento.";
            else if (score >= 5) resultMessage.textContent = "Resultado aceptable. Sigue practicando para mejorar.";
            else resultMessage.textContent = "Necesitas repasar más. ¡No te rindas!";

            // Resumen
            resultsSummary.innerHTML = '';
            currentQuestions.forEach((q, i) => {
                const isCorrect = userAnswers[i] === q.correct;
                const userAnsText = userAnswers[i] !== null ? `${String.fromCharCode(65 + userAnswers[i])}. ${q.options[userAnswers[i]]}` : 'Sin responder';
                const correctText = `${String.fromCharCode(65 + q.correct)}. ${q.options[q.correct]}`;
                const catInfo = categories.find(c => c.id === q.category) || { color: '#999', name: q.category };

                const item = document.createElement('div');
                item.className = 'result-item';
                item.innerHTML = `
            <div style="display:flex;justify-content:space-between;align-items:center;gap:10px;">
                <div style="min-width:60%"><div class="result-question">${i + 1}. ${q.question}</div>
                <div style="margin-top:6px;"><span class="category-tag" style="background:${catInfo.color};color:#fff;padding:6px 10px;border-radius:999px;font-weight:700">${catInfo.name}</span></div></div>
                <div style="text-align:right;min-width:30%">
                    <div style="font-weight:900; font-size:1.05rem; ${isCorrect ? 'color:#28a745' : 'color:#dc3545'}">
                        ${isCorrect ? '✅ Correcto 😁' : '❌ Incorrecto 😞'}
                    </div>
                </div>
            </div>
            <div style="margin-top:8px; display:flex; justify-content:space-between; gap:10px; flex-wrap:wrap;">
                <div>Tu respuesta: <strong class="${isCorrect ? 'correct' : 'incorrect'}">${userAnsText}</strong></div>
                <div>Respuesta correcta: <strong class="correct">${correctText}</strong></div>
            </div>
            <div style="margin-top:8px;"><small>${q.explanation}</small></div>
        `;
                resultsSummary.appendChild(item);
            });

            // Cambiar pantallas
            quizScreen.style.display = 'none';
            resultsScreen.style.display = 'block';
        }

        /* -------------------------
           Reiniciar
           ------------------------- */
        function restartQuiz() {
            clearInterval(timer); // Limpiar el temporizador al reiniciar
            timeLeft = 120; // Reiniciar el tiempo
            selectedCategory = null;
            document.querySelectorAll('.category-card').forEach(c => c.classList.remove('selected'));
            startBtn.disabled = true;
            categoryScreen.style.display = 'block';
            quizScreen.style.display = 'none';
            resultsScreen.style.display = 'none';
            updateTimerDisplay(); // Actualizar la visualización del tiempo
        }

        /* -------------------------
           Confetti system (canvas particles)
           ------------------------- */
        (function setupConfetti() {
            const ctx = confettiCanvas.getContext('2d');
            let W = confettiCanvas.width = app.clientWidth;
            let H = confettiCanvas.height = app.clientHeight;
            const particles = [];
            let animating = false;

            // Resize canvas with container
            function resize() {
                W = confettiCanvas.width = app.clientWidth;
                H = confettiCanvas.height = app.clientHeight;
            }
            window.addEventListener('resize', resize);

            // Colors for confetti
            const COLORS = ['#ff5c9e', '#ffd166', '#4ecdc4', '#7209b7', '#ff9e64', '#4a00e0', '#2575fc', '#ffd6e0'];

            function random(min, max) { return Math.random() * (max - min) + min; }

            // Create burst
            window.confettiBurst = function (count = 60) {
                for (let i = 0; i < count; i++) {
                    particles.push({
                        x: random(0, W),
                        y: random(-20, H / 3),
                        w: random(6, 12),
                        h: random(8, 14),
                        vx: random(-3.5, 3.5),
                        vy: random(1, 5),
                        angle: random(0, Math.PI * 2),
                        angularVel: random(-0.15, 0.15),
                        color: COLORS[Math.floor(Math.random() * COLORS.length)],
                        ttl: random(80, 160),
                        gravity: random(0.02, 0.12),
                        drag: 0.995
                    });
                }
                if (!animating) { animating = true; requestAnimationFrame(update); }
            };

            // Animation loop
            function update() {
                ctx.clearRect(0, 0, W, H);
                for (let i = particles.length - 1; i >= 0; i--) {
                    const p = particles[i];
                    p.vy += p.gravity;
                    p.vx *= p.drag;
                    p.vy *= p.drag;
                    p.x += p.vx;
                    p.y += p.vy;
                    p.angle += p.angularVel;
                    p.ttl--;

                    ctx.save();
                    ctx.translate(p.x, p.y);
                    ctx.rotate(p.angle);
                    ctx.fillStyle = p.color;
                    ctx.fillRect(-p.w / 2, -p.h / 2, p.w, p.h);
                    ctx.restore();

                    if (p.y > H + 40 || p.ttl <= 0) particles.splice(i, 1);
                }

                if (particles.length > 0) { requestAnimationFrame(update); } else { animating = false; ctx.clearRect(0, 0, W, H); }
            }
        })();

    </script>
</body>

</html>
