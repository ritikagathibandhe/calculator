# calculator
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Basic Calculator</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
            margin: 0;
        }

        .calculator {
            border: 1px solid #ccc;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            background-color: #f0f0f0; /* Light gray background */
        }

        .display {
            font-size: 2em;
            margin-bottom: 10px;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background-color: #eee;
            text-align: right;
            min-height: 50px;
            color: #333; /* Dark text color */
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            grid-gap: 10px;
        }

        .btn {
            font-size: 1.5em;
            padding: 20px;
            border: none;
            border-radius: 5px;
            background-color: #e0e0e0; 
            cursor: pointer;
            transition: background-color 0.3s;
            color: #444; 
        }

        .btn:hover {
            background-color: #ccc; 
        }

        .btn:active {
            transform: translateY(1px); 
        }

        .span-two {
            grid-column: span 2;
        }

        
        .btn.operator {
            background-color: #ff9800; 
            color: white; 
        }

       
        .btn.equals {
            background-color: #4caf50; 
            color: white; 
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div id="display" class="display">0</div>
        <div class="buttons">
            <button class="btn" onclick="clearDisplay()">C</button>
            <button class="btn" onclick="deleteLast()">DEL</button>
            <button class="btn operator" onclick="appendCharacter('/')">/</button>
            <button class="btn operator" onclick="appendCharacter('*')">*</button>
            <button class="btn" onclick="appendCharacter('7')">7</button>
            <button class="btn" onclick="appendCharacter('8')">8</button>
            <button class="btn" onclick="appendCharacter('9')">9</button>
            <button class="btn operator" onclick="appendCharacter('-')">-</button>
            <button class="btn" onclick="appendCharacter('4')">4</button>
            <button class="btn" onclick="appendCharacter('5')">5</button>
            <button class="btn" onclick="appendCharacter('6')">6</button>
            <button class="btn operator" onclick="appendCharacter('+')">+</button>
            <button class="btn" onclick="appendCharacter('1')">1</button>
            <button class="btn" onclick="appendCharacter('2')">2</button>
            <button class="btn" onclick="appendCharacter('3')">3</button>
            <button class="btn equals span-two" onclick="calculateResult()">=</button>
            <button class="btn" onclick="appendCharacter('0')">0</button>
            <button class="btn" onclick="appendCharacter('.')">.</button>
        </div>
    </div>
    <script>
        let display = document.getElementById('display');

        function clearDisplay() {
            display.innerText = '0';
        }

        function deleteLast() {
            if (display.innerText.length > 1) {
                display.innerText = display.innerText.slice(0, -1);
            } else {
                display.innerText = '0';
            }
        }

        function appendCharacter(char) {
            if (display.innerText === '0' && char !== '.') {
                display.innerText = char;
            } else {
                display.innerText += char;
            }
        }

        function calculateResult() {
            try {
                display.innerText = eval(display.innerText);
            } catch (error) {
                display.innerText = 'Error';
            }
        }
    </script>
</body>
</html>
