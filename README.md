<!DOCTYPE html>
<html>
<head>
    <title>Колесо Русских Согласных</title>
    <style>
•	{
            Margin: 0;
            Padding: 0;
            Box-sizing: border-box;
        }

        Body {
            Font-family: ‘Times New Roman’, serif;
            Background: linear-gradient(135deg, #0c2461 0%, #1e3799 50%, #4a69bd 100%);
            Color: white;
            Min-height: 100vh;
            Padding: 20px;
            Position: relative;
            Overflow-x: hidden;
        }

        /* Плавающие буквы на фоне */
        .floating-letters {
            Position: fixed;
            Top: 0;
            Left: 0;
            Width: 100%;
            Height: 100%;
            Pointer-events: none;
            z-index: 0;
        }

        .floating-letter {
            Position: absolute;
            Font-size: 24px;
            Color: rgba(255, 255, 255, 0.1);
            Animation: float 20s infinite linear;
        }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); }
            100% { transform: translateY(-100px) rotate(360deg); }
        }

        .container {
            Max-width: 1200px;
            Margin: 0 auto;
            Position: relative;
            z-index: 1;
        }

        Header {
            Text-align: center;
            Padding: 30px 0 40px 0;
            Position: relative;
        }

        H1 {
            Font-family: ‘Times New Roman’, serif;
            Font-size: 4.2em;
            Margin-bottom: 10px;
            Background: linear-gradient(45deg, #FFD700, #FFA500, #FF8C00, #FFD700);
            Background-size: 400% 400%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            Animation: gradientShift 4s ease infinite, textGlow 2s ease-in-out infinite alternate;
            Font-weight: bold;
            Letter-spacing: 1px;
            Text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
            Padding: 10px 0;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes textGlow {
            From { 
                Text-shadow: 0 0 10px rgba(255, 215, 0, 0.7), 
                           0 0 20px rgba(255, 165, 0, 0.5),
                           2px 2px 4px rgba(0,0,0,0.5);
            }
            To { 
                Text-shadow: 0 0 20px rgba(255, 215, 0, 0.9), 
                           0 0 30px rgba(255, 165, 0, 0.7),
                           0 0 40px rgba(255, 140, 0, 0.5),
                           2px 2px 6px rgba(0,0,0,0.6);
            }
        }

        .subtitle {
            Font-family: ‘Times New Roman’, serif;
            Font-size: 1.8em;
            Margin-bottom: 30px;
            Color: #ffd700;
            Font-style: italic;
            Text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
        }

        /* Основной контент */
        .main-content {
            Display: flex;
            Flex-wrap: wrap;
            Gap: 60px;
            Justify-content: center;
            Align-items: flex-start;
            Margin-bottom: 40px;
        }

        /* Левая часть: Колесо с кнопкой в центре */
        .wheel-section {
            Flex: 1;
            Min-width: 600px;
            Position: relative;
            Text-align: center;
        }

        #wheelCanvas {
            Width: 100%;
            Height: 600px;
            Filter: drop-shadow(0 15px 35px rgba(0,0,0,0.4));
            Transition: transform 0.5s ease;
        }

        /* Кнопка КРУТИТЬ в центре колеса */
        .wheel-center-btn {
            Position: absolute;
            Top: 50%;
            Left: 50%;
            Transform: translate(-50%, -50%);
            Width: 160px;
            Height: 160px;
            Background: radial-gradient(circle, #ff3d00, #c62828);
            Color: white;
            Border: none;
            Border-radius: 50%;
            Font-family: ‘Times New Roman’, serif;
            Font-size: 1.8em;
            Font-weight: bold;
            Cursor: pointer;
            z-index: 10;
            box-shadow: 0 10px 30px rgba(198, 40, 40, 0.5);
            transition: all 0.3s;
            animation: buttonPulse 2s infinite;
            text-transform: uppercase;
            letter-spacing: 2px;
            border: 5px solid #ffd700;
        }

        @keyframes buttonPulse {
            0% { box-shadow: 0 0 0 0 rgba(255, 61, 0, 0.7); }
            70% { box-shadow: 0 0 0 30px rgba(255, 61, 0, 0); }
            100% { box-shadow: 0 0 0 0 rgba(255, 61, 0, 0); }
        }

        .wheel-center-btn:hover {
            Transform: translate(-50%, -50%) scale(1.1);
            Background: radial-gradient(circle, #ff5252, #ff3838);
        }

        .wheel-center-btn:active {
            Transform: translate(-50%, -50%) scale(0.95);
        }

        .wheel-center-btn:disabled {
            Background: #546e7a;
            Cursor: not-allowed;
            Animation: none;
            Box-shadow: none;
            Transform: translate(-50%, -50%);
            Border-color: #78909c;
        }

        /* Правая часть: Игровая панель */
        .game-section {
            Flex: 1;
            Min-width: 500px;
            Display: flex;
            Flex-direction: column;
            Align-items: center;
        }

        /* Игровая панель */
        .game-panel {
            Width: 100%;
            Background: rgba(255, 255, 255, 0.08);
            Backdrop-filter: blur(5px);
            Border-radius: 20px;
            Padding: 35px;
            Border: 2px solid rgba(255, 255, 255, 0.15);
            Box-shadow: 0 15px 30px rgba(0,0,0,0.2);
        }

        .game-panel h2 {
            Font-family: ‘Times New Roman’, serif;
            Font-size: 2.2em;
            Text-align: center;
            Margin-bottom: 25px;
            Color: #ffd700;
            Font-weight: bold;
            Text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
        }

        .instruction {
            Font-family: ‘Times New Roman’, serif;
            Font-size: 1.4em;
            Text-align: center;
            Margin-bottom: 30px;
            Color: #bbdefb;
            Line-height: 1.5;
            Padding: 15px;
            Background: rgba(0, 0, 0, 0.2);
            Border-radius: 10px;
            Border-left: 4px solid #ffd700;
        }

        .current-word-container {
            Background: rgba(0, 0, 0, 0.25);
            Border-radius: 15px;
            Padding: 20px;
            Margin: 25px 0;
            Border: 2px solid rgba(255, 215, 0, 0.3);
            Text-align: center;
        }

        .current-word-label {
            Font-family: ‘Times New Roman’, serif;
            Font-size: 1.4em;
            Color: #ffd700;
            Margin-bottom: 10px;
            Font-weight: bold;
        }

        .current-word {
            Font-family: ‘Times New Roman’, serif;
            Font-size: 3.5em;
            Font-weight: bold;
            Text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
            Color: white;
            Min-height: 80px;
            Display: flex;
            Align-items: center;
            Justify-content: center;
        }

        /* Кнопки ДА/НЕТ */
        .answer-buttons {
            Display: flex;
            Gap: 40px;
            Justify-content: center;
            Margin: 30px 0 40px 0;
        }

        .answer-btn {
            Padding: 25px 60px;
            Font-family: ‘Times New Roman’, serif;
            Font-size: 1.8em;
            Border: none;
            Border-radius: 12px;
            Cursor: pointer;
            Transition: all 0.3s ease;
            Font-weight: bold;
            Min-width: 180px;
            Box-shadow: 0 10px 20px rgba(0,0,0,0.3);
            Letter-spacing: 1px;
        }

        .answer-btn:disabled {
            Opacity: 0.5;
            Cursor: not-allowed;
            Transform: none !important;
            Box-shadow: 0 5px 10px rgba(0,0,0,0.2);
        }

        .answer-btn:hover:not(:disabled) {
            Transform: translateY(-5px);
            Box-shadow: 0 15px 25px rgba(0,0,0,0.4);
        }

        .yes-btn {
            Background: linear-gradient(145deg, #2e7d32, #1b5e20);
            Color: white;
            Border: 2px solid #4caf50;
        }

        .no-btn {
            Background: linear-gradient(145deg, #c62828, #b71c1c);
            Color: white;
            Border: 2px solid #f44336;
        }

        /* Статистика */
        .stats-container {
            Display: flex;
            Justify-content: center;
            Gap: 40px;
            Margin-top: 20px;
        }

        .stat-item {
            Text-align: center;
            Padding: 15px 25px;
            Background: rgba(255, 255, 255, 0.1);
            Border-radius: 12px;
            Min-width: 140px;
            Border: 1px solid rgba(255, 215, 0, 0.2);
        }

        .stat-label {
            Font-family: ‘Times New Roman’, serif;
            Font-size: 1.3em;
            Color: #bbdefb;
            Margin-bottom: 8px;
            Font-weight: bold;
        }

        .stat-value {
            Font-family: ‘Times New Roman’, serif;
            Font-size: 2.8em;
            Font-weight: bold;
            Color: #ffd700;
            Text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }

        /* Результат */
        .result-container {
            Background: rgba(255, 255, 255, 0.1);
            Border-radius: 15px;
            Padding: 20px;
            Margin-top: 25px;
            Border: 2px solid rgba(255, 215, 0, 0.2);
            Text-align: center;
            Min-height: 100px;
            Display: flex;
            Align-items: center;
            Justify-content: center;
        }

        .result-message {
            Font-family: ‘Times New Roman’, serif;
            Font-size: 1.4em;
            Line-height: 1.5;
            Color: white;
        }

        .correct {
            Color: #c8e6c9;
            Background: rgba(76, 175, 80, 0.15);
            Border-color: #4caf50;
        }

        .wrong {
            Color: #ffcdd2;
            Background: rgba(244, 67, 54, 0.15);
            Border-color: #f44336;
        }

        /* Правила */
        .rules {
            Background: rgba(255, 255, 255, 0.08);
            Padding: 30px;
            Border-radius: 20px;
            Margin-top: 40px;
            Border-left: 5px solid #ff6b6b;
        }

        .rules h3 {
            Font-family: ‘Times New Roman’, serif;
            Font-size: 1.8em;
            Color: #ffd700;
            Margin-bottom: 20px;
            Text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
        }

        .rules ul {
            List-style-position: inside;
            Line-height: 1.8;
            Font-size: 1.1em;
        }

        .rules li {
            Margin: 12px 0;
            Padding-left: 10px;
            Position: relative;
            Color: #e3f2fd;
        }

        .rules li:before {
            Content: “•”;
            Color: #ffd700;
            Font-size: 1.5em;
            Position: absolute;
            Left: -5px;
            Top: -2px;
        }

        /* Адаптивность */
        @media (max-width: 1200px) {
            .main-content {
                Flex-direction: column;
                Align-items: center;
            }
            
            .wheel-section, .game-section {
                Min-width: 90%;
            }
            
            #wheelCanvas {
                Height: 500px;
            }
            
            H1 {
                Font-size: 3.2em;
            }
            
            .wheel-center-btn {
                Width: 130px;
                Height: 130px;
                Font-size: 1.5em;
            }
        }

        @media (max-width: 768px) {
            #wheelCanvas {
                Height: 400px;
            }
            
            H1 {
                Font-size: 2.5em;
            }
            
            .subtitle {
                Font-size: 1.4em;
            }
            
            .current-word {
                Font-size: 2.5em;
            }
            
            .answer-buttons {
                Flex-direction: column;
                Gap: 20px;
            }
            
            .answer-btn {
                Min-width: auto;
                Padding: 20px 40px;
                Font-size: 1.5em;
            }
            
            .stats-container {
                Flex-direction: column;
                Gap: 15px;
                Align-items: center;
            }
            
            .wheel-center-btn {
                Width: 100px;
                Height: 100px;
                Font-size: 1.2em;
                Border-width: 3px;
            }
        }
    </style>
</head>
<body>
    <!—Плавающие буквы на фоне 
    <div class=”floating-letters” id=”floatingLetters”></div>

    <div class=”container”>
        <header>
            <h1>Колесо Русских Согласных</h1>
            <div class=”subtitle”>Проверь свои знания удвоенных согласных в русском языке!</div>
        </header>

        <div class=”main-content”>
            <!—Левая часть: Колесо с кнопкой в центре 
            <div class=”wheel-section”>
                <canvas id=”wheelCanvas” width=”600” height=”600”></canvas>
                <button class=”wheel-center-btn” id=”spinButton”>КРУТИТЬ</button>
            </div>

            <!—Правая часть: Игровая панель 
            <div class=”game-section”>
                <div class=”game-panel”>
                    <h2>Жми “Крутить”!</h2>
                    
                    <div class=”instruction” id=”instruction”>
                        Крутите колесо, чтобы начать игру
                    </div>
                    
                    <div class=”current-word-container”>
                        <div class=”current-word-label”>Выпавшее слово:</div>
                        <div class=”current-word” id=”currentWord”>—</div>
                    </div>
                    
                    <div class=”answer-buttons”>
                        <button class=”answer-btn yes-btn” id=”yesBtn”>ДА</button>
                        <button class=”answer-btn no-btn” id=”noBtn”>НЕТ</button>
                    </div>
                    
                    <div class=”result-container”>
                        <div class=”result-message” id=”resultMessage”>
                            Готовы начать игру?
                        </div>
                    </div>
                    
                    <div class=”stats-container”>
                        <div class=”stat-item”>
                            <div class=”stat-label”>Очки</div>
                            <div class=”stat-value” id=”score”>0</div>
                        </div>
                        <div class=”stat-item”>
                            <div class=”stat-label”>Правильно</div>
                            <div class=”stat-value” id=”correct”>0</div>
                        </div>
                        <div class=”stat-item”>
                            <div class=”stat-label”>Всего слов</div>
                            <div class=”stat-value” id=”total”>0</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!—Правила игры 
        <div class=”rules”>
            <h3>📚 Как играть:</h3>
            <ul>
                <li>Нажми “КРУТИТЬ” – колесо выберет случайное слово</li>
                <li>Определи, правильно ли оно написано с точки зрения удвоенных согласных</li>
                <li>Нажми ДА (правильно) или НЕТ (есть ошибка)</li>
                <li>+15 очков за правильный ответ, -10 за ошибку</li>
                <li>Обрати внимание, что здесь присутствуют слова, которые не имеют орфограмму удвоенной согласной и пишутся с одной буквой</li>
                <li>Если слово написано с ошибкой – увидишь правильный вариант и объяснение</li>
            </ul>
            <p style=”margin-top: 20px; color: #ffd700; font-size: 1.1em;”>
                💡 <strong>Совет:</strong> Запоминай правильное написание слов, где часто делают ошибки!
            </p>
        </div>
    </div>

    <!—Скрипты 
    <script src=https://cdn.jsdelivr.net/npm/canvas-confetti@1.5.1/dist/confetti.browser.min.js></script>
    <script>
        // === УМНЫЙ СПИСОК СЛОВ ===
        Const words = [
            // КАТЕГОРИЯ 1: Правильно написанные с удвоенной согласной
            { 
                Text: “АНТЕННА”, 
                Correct: true, 
                Explanation: “Правильно! Слово ‘антенна’ пишется с двумя НН” 
            },
            { 
                Text: “КОЛЛЕКЦИЯ”, 
                Correct: true, 
                Explanation: “Правильно! Слово ‘коллекция’ пишется с двумя ЛЛ” 
            },
            { 
                Text: “ПРОГРАММА”, 
                Correct: true, 
                Explanation: “Правильно! Слово ‘программа’ пишется с двумя ММ” 
            },
            { 
                Text: “АЛЛЕЯ”, 
                Correct: true, 
                Explanation: “Правильно! Слово ‘аллея’ пишется с двумя ЛЛ” 
            },
            { 
                Text: “СУММА”, 
                Correct: true, 
                Explanation: “Правильно! Слово ‘сумма’ пишется с двумя ММ” 
            },
            { 
                Text: “ГРАММАТИКА”, 
                Correct: true, 
                Explanation: “Правильно! Слово ‘грамматика’ пишется с двумя ММ” 
            },
            
            // КАТЕГОРИЯ 2: Правильно написанные БЕЗ удвоенной согласной
            { 
                Text: “АБАЖУР”, 
                Correct: true, 
                Explanation: “Правильно! В слове ‘абажур’ нет удвоенных согласных” 
            },
            { 
                Text: “БЕРЕЗА”, 
                Correct: true, 
                Explanation: “Правильно! В слове ‘береза’ нет удвоенных согласных” 
            },
            { 
                Text: “КОРИДОР”, 
                Correct: true, 
                Explanation: “Правильно! Слово ‘коридор’ пишется с одной Р, хотя произносится как бы с двумя” 
            },
            { 
                Text: “ГАЛЕРЕЯ”, 
                Correct: true, 
                Explanation: “Правильно! Слово ‘галерея’ пишется с одной Л, хотя может казаться, что их две” 
            },
            { 
                Text: “КАРИКАТУРА”, 
                Correct: true, 
                Explanation: “Правильно! Слово ‘карикатура’ пишется с одной Р, хотя звучит как две” 
            },
            
            // КАТЕГОРИЯ 3: Неправильно написанные
            { 
                Text: “КОРИИДОР”, 
                Correct: false,
                correctVersion: “КОРИДОР”,
                explanation: “Ошибка! Правильно пишется ‘коридор’ с одной Р”
            },
            { 
                Text: “ГАЛЛЕРЕЯ”, 
                Correct: false,
                correctVersion: “ГАЛЕРЕЯ”,
                explanation: “Ошибка! Правильно пишется ‘галерея’ с одной Л”
            },
            { 
                Text: “АЛЕЯ”, 
                Correct: false,
                correctVersion: “АЛЛЕЯ”,
                explanation: “Ошибка! Правильно пишется ‘аллея’ с двумя ЛЛ”
            },
            { 
                Text: “КОЛЕКЦИЯ”, 
                Correct: false,
                correctVersion: “КОЛЛЕКЦИЯ”,
                explanation: “Ошибка! Правильно пишется ‘коллекция’ с двумя ЛЛ”
            }
        ];

        // Переменные игры
        Let wheel;
        Let currentWordIndex = -1;
        Let score = 0;
        Let correctAnswers = 0;
        Let totalQuestions = 0;
        Let isSpinning = false;
        Let canAnswer = false;

        // Создаем плавающие буквы
        Function createFloatingLetters() {
            Const letters = “АБВГДЕЁЖЗИЙКЛМНОПРСТУФХЦЧШЩЪЫЬЭЮЯ”;
            Const container = document.getElementById(‘floatingLetters’);
            
            For(let i = 0; i < 60; i++) {
                Const letter = document.createElement(‘div’);
                Letter.className = ‘floating-letter’;
                Letter.textContent = letters[Math.floor(Math.random() * letters.length)];
                Letter.style.left = `${Math.random() * 100}%`;
                Letter.style.animationDuration = `${15 + Math.random() * 25}s`;
                Letter.style.animationDelay = `${Math.random() * 8}s`;
                Letter.style.fontSize = `${20 + Math.random() * 30}px`;
                Container.appendChild(letter);
            }
        }

        // Создаем монотонное колесо
        Function createWheel() {
            Const segments = words.map((word, index) => ({
                Text: word.text,
                fillStyle: ‘#4a69bd’,
                textFillStyle: ‘white’,
                textFontSize: 22,
                textFontFamily: ‘Times New Roman’,
                strokeStyle: ‘#ffd700’,
                lineWidth: 2
            }));

            Wheel = new Winwheel({
                canvasId: ‘wheelCanvas’,
                numSegments: words.length,
                segments: segments,
                outerRadius: 250,
                innerRadius: 60, // Увеличил внутренний радиус для кнопки
                centerX: 300,
                centerY: 300,
                textOrientation: ‘horizontal’,
                textAlignment: ‘center’,
                textFontSize: 20,
                textFontFamily: ‘Times New Roman’,
                strokeStyle: ‘#ffd700’,
                lineWidth: 2,
                animation: {
                    type: ‘spinToStop’,
                    duration: 5,
                    spins: 6,
                    callbackFinished: onWheelStop,
                    easing: ‘Cubic.easeOut’
                }
            });
        }

        // Запуск вращения
        Function spinWheel() {
            If (isSpinning) return;
            
            isSpinning = true;
            canAnswer = false;
            
            // Блокируем кнопки
            Document.getElementById(‘spinButton’).disabled = true;
            Document.getElementById(‘yesBtn’).disabled = true;
            Document.getElementById(‘noBtn’).disabled = true;
            
            // Обновляем интерфейс
            Document.getElementById(‘currentWord’).textContent = “Вращается…”;
            Document.getElementById(‘instruction’).textContent = “Колесо вращается…”;
            Document.getElementById(‘resultMessage’).textContent = “Ждите результат…”;
            Document.querySelector(‘.result-container’).className = “result-container”;
            
            // Выбираем случайное слово
            currentWordIndex = Math.floor(Math.random() * words.length);
            const currentWord = words[currentWordIndex];
            
            // Вычисляем угол остановки
            Const segmentAngle = 360 / words.length;
            Const stopAngle = currentWordIndex * segmentAngle + (Math.random() * segmentAngle);
            
            // Запускаем анимацию
            Wheel.animation.stopAngle = stopAngle;
            Wheel.startAnimation();
        }

        // Когда колесо остановилось
        Function onWheelStop() {
            isSpinning = false;
            canAnswer = true;
            
            const currentWord = words[currentWordIndex];
            
            // Обновляем интерфейс
            Document.getElementById(‘currentWord’).textContent = currentWord.text;
            Document.getElementById(‘instruction’).textContent = “Правильно ли написано это слово?”;
            Document.getElementById(‘resultMessage’).textContent = “Выберите ответ: ДА или НЕТ”;
            
            // Разблокируем кнопки
            Document.getElementById(‘spinButton’).disabled = false;
            Document.getElementById(‘yesBtn’).disabled = false;
            Document.getElementById(‘noBtn’).disabled = false;
            
            // Обновляем статистику
            updateStats();
        }

        // Проверка ответа
        Function checkAnswer(userAnswer) {
            If (!canAnswer || currentWordIndex === -1) return;
            
            Const currentWord = words[currentWordIndex];
            Const isCorrect = (userAnswer === currentWord.correct);
            
            totalQuestions++;
            
            // Блокируем кнопки
            canAnswer = false;
            document.getElementById(‘yesBtn’).disabled = true;
            document.getElementById(‘noBtn’).disabled = true;
            
            if (isCorrect) {
                score += 15;
                correctAnswers++;
                
                // Показываем положительный результат
                Document.getElementById(‘resultMessage’).innerHTML = 
                    `<strong>✅ ВЕРНО!</strong><br>${currentWord.explanation}`;
                Document.querySelector(‘.result-container’).className = “result-container correct”;
                
                // Запускаем конфетти
                showConfetti();
                
            } else {
                Score -= 10;
                If (score < 0) score = 0;
                
                // Показываем отрицательный результат
                Let message = `<strong>❌ НЕВЕРНО!</strong><br>${currentWord.explanation}`;
                
                // Если слово написано с ошибкой, показываем правильный вариант
                If (!currentWord.correct && currentWord.correctVersion) {
                    Message += `<br><br><strong>Правильно:</strong> ${currentWord.correctVersion}`;
                }
                
                Document.getElementById(‘resultMessage’).innerHTML = message;
                Document.querySelector(‘.result-container’).className = “result-container wrong”;
            }
            
            // Обновляем статистику
            updateStats();
            
            // Через 3 секунды готовим к следующему ходу
            setTimeout(() => {
                document.getElementById(‘resultMessage’).innerHTML = 
                    “Нажмите ‘Крутить’ для следующего слова!”;
                Document.querySelector(‘.result-container’).className = “result-container”;
                Document.getElementById(‘instruction’).textContent = “Крутите колесо снова!”;
                
                // Сбрасываем слово
                Document.getElementById(‘currentWord’).textContent = “—“;
                
                // Разблокируем только кнопку крутить
                Document.getElementById(‘spinButton’).disabled = false;
                Document.getElementById(‘yesBtn’).disabled = true;
                Document.getElementById(‘noBtn’).disabled = true;
                
            }, 3000);
        }

        // Обновление статистики
        Function updateStats() {
            Document.getElementById(‘score’).textContent = score;
            Document.getElementById(‘correct’).textContent = correctAnswers;
            Document.getElementById(‘total’).textContent = totalQuestions;
        }

        // Конфетти
        Function showConfetti() {
            Confetti({
                particleCount: 150,
                spread: 100,
                origin: { y: 0.6 }
            });
            
            setTimeout(() => {
                confetti({
                    particleCount: 100,
                    angle: 60,
                    spread: 80,
                    origin: { x: 0 }
                });
                Confetti({
                    particleCount: 100,
                    angle: 120,
                    spread: 80,
                    origin: { x: 1 }
                });
            }, 250);
        }

        // Инициализация
        Window.onload = function() {
            // Загружаем Winwheel.js
            Const script = document.createElement(‘script’);
            Script.src = ‘https://cdn.jsdelivr.net/npm/winwheel@1.1.1/dist/Winwheel.min.js’;
            Script.onload = function() {
                createFloatingLetters();
                createWheel();
                
                // Назначаем обработчики кнопок
                Document.getElementById(‘spinButton’).addEventListener(‘click’, spinWheel);
                Document.getElementById(‘yesBtn’).addEventListener(‘click’, () => checkAnswer(true));
                Document.getElementById(‘noBtn’).addEventListener(‘click’, () => checkAnswer(false));
                
                // Изначально кнопки ответа заблокированы
                Document.getElementById(‘yesBtn’).disabled = true;
                Document.getElementById(‘noBtn’).disabled = true;
                
                // Первоначальное обновление статистики
                updateStats();
            };
            Document.head.appendChild(script);
        };

        // Адаптация размера колеса
        Window.addEventListener(‘resize’, function() {
            If (wheel) {
                Wheel.clearCanvas();
                Wheel.draw();
            }
        });
    </script>
</body>
</html>
