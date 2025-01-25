<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>آلة حاسبة</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
        }
        .calculator {
            background: #fff;
            width: 20rem;
            margin: 2rem auto;
            padding: 1.5rem;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
        }
        .calculator input[type="text"] {
            width: 100%;
            height: 3rem;
            text-align: right;
            margin-bottom: 1rem;
            font-size: 1.2rem;
            border: 1px solid #ccc;
            border-radius: 5px;
            padding-right: 0.5rem;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 0.5rem;
        }
        .buttons button {
            height: 3rem;
            font-size: 1rem;
            border: none;
            background: #007bff;
            color: white;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        .buttons button:hover {
            background: #0056b3;
        }
        .buttons .clear {
            background: #f44336;
        }
        .buttons .clear:hover {
            background: #d32f2f;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" id="result" disabled>
        <div class="buttons">
            <button onclick="appendValue('1')">1</button>
            <button onclick="appendValue('2')">2</button>
            <button onclick="appendValue('3')">3</button>
            <button onclick="appendValue('+')">+</button>
            <button onclick="appendValue('4')">4</button>
            <button onclick="appendValue('5')">5</button>
            <button onclick="appendValue('6')">6</button>
            <button onclick="appendValue('-')">-</button>
            <button onclick="appendValue('7')">7</button>
            <button onclick="appendValue('8')">8</button>
            <button onclick="appendValue('9')">9</button>
            <button onclick="appendValue('*')">*</button>
            <button onclick="appendValue('0')">0</button>
            <button onclick="clearResult()" class="clear">C</button>
            <button onclick="calculateResult()">=</button>
            <button onclick="appendValue('/')">/</button>
        </div>
    </div>

    <script>
        const resultField = document.getElementById('result');

        function appendValue(value) {
            resultField.value += value;
        }

        function clearResult() {
            resultField.value = '';
        }

        function calculateResult() {
            try {
                const expression = resultField.value;
                if (isValidExpression(expression)) {
                    resultField.value = eval(expression); // استخدام eval بعد التحقق من صحة التعبير
                } else {
                    throw new Error('Invalid Expression');
                }
            } catch (error) {
                resultField.value = 'تعبير غير صحيح';
                setTimeout(() => clearResult(), 1500); // مسح النتيجة بعد 1.5 ثانية
            }
        }

        function isValidExpression(expression) {
            return /^[0-9+\-*/.() ]+$/.test(expression) && !/(\.\D|\d+\.+\D|\d+\.\.)/.test(expression);
        }
    </script>
</body>
</html>
