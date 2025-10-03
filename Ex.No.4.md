# Ex04 Simple Calculator - React Project
## Date:3.10.25

## AIM
To  develop a Simple Calculator using React.js with clean and responsive design, ensuring a smooth user experience across different screen sizes.

## ALGORITHM
### STEP 1
Create a React App.

### STEP 2
Open a terminal and run:
  <ul><li>npx create-react-app simple-calculator</li>
  <li>cd simple-calculator</li>
  <li>npm start</li></ul>

### STEP 3
Inside the src/ folder, create a new file Calculator.js and define the basic structure.

### STEP 4
Plan the UI: Display screen, number buttons (0-9), operators (+, -, *, /), clear (C), and equal (=).

### STEP 5
Create a new file Calculator.css in src/ and add the styling.

### STEP 6
Open src/App.js and modify it.

### STEP 7
Start the development server.
  npm start

### STEP 8
Open http://localhost:3000/ in the browser.

### STEP 9
Test the calculator by entering numbers and operations.

### STEP 10
Fix styling issues and refine content placement.

### STEP 11
Deploy the website.

### STEP 12
Upload to GitHub Pages for free hosting.

## PROGRAM
app.jsx
```
import React, { useState } from 'react';
import './App.css';

const Calculator = () => {
  const [input, setInput] = useState('');

  const handleClick = (value) => {
    setInput(input + value);
  };

  const handleClear = () => {
    setInput('');
  };

  const handleBackspace = () => {
    setInput(input.slice(0, -1));
  };

  const handleEqual = () => {
    try {
      const result = evaluateExpression(input);
      setInput(result.toString());
    } catch (error) {
      setInput('Error');
    }
  };

  const evaluateExpression = (expr) => {
    const operators = ['+', '-', '*', '/'];
    let numbers = [];
    let currentNum = '';

    for (let i = 0; i < expr.length; i++) {
      const char = expr[i];

      if (operators.includes(char)) {
        if (currentNum !== '') {
          numbers.push(parseFloat(currentNum));
        }
        numbers.push(char); 
        currentNum = ''; 
      } else {
        currentNum += char; 
      }
    }

    if (currentNum !== '') {
      numbers.push(parseFloat(currentNum));
    }

  
    for (let i = 1; i < numbers.length - 1; i++) {
      if (numbers[i] === '*' || numbers[i] === '/') {
        const left = numbers[i - 1];
        const right = numbers[i + 1];
        const result = numbers[i] === '*' ? left * right : left / right;
        numbers.splice(i - 1, 3, result); 
        i--; 
      }
    }

    let result = numbers[0];
    for (let i = 1; i < numbers.length; i += 2) {
      const operator = numbers[i];
      const value = numbers[i + 1];
      if (operator === '+') {
        result += value;
      } else if (operator === '-') {
        result -= value;
      }
    }

    return result;
  };

  return (
    <div className="calculator">
      <div className="display">{input || '0'}</div>
      <div className="buttons">
        <button onClick={handleClear} className="clear">C</button>
        <button onClick={handleBackspace} className="backspace">⌫</button> {/* Remove button */}
        <button onClick={() => handleClick('/')}>/</button>
        <button onClick={() => handleClick('*')}>*</button>
        
        <button onClick={() => handleClick('7')}>7</button>
        <button onClick={() => handleClick('8')}>8</button>
        <button onClick={() => handleClick('9')}>9</button>
        <button onClick={() => handleClick('+')}>+</button>
        <button onClick={() => handleClick('4')}>4</button>
        <button onClick={() => handleClick('5')}>5</button>
        <button onClick={() => handleClick('6')}>6</button>

        <button onClick={() => handleClick('-')}>-</button>
        <button onClick={() => handleClick('2')}>2</button>
        <button onClick={() => handleClick('3')}>3</button>
        <button onClick={() => handleClick('1')}>1</button>
        <button onClick={handleEqual} className="equal">=</button>
        <button onClick={() => handleClick('00')} className="zero-zero">00</button>
        <button onClick={() => handleClick('0')} className="zero">0</button>
        <button onClick={() => handleClick('.')}>.</button>
      </div>
      <footer className="footer">
        <p>&copy; 2025 Simple Calculator </p>
          <p>MAGATHI (212223040108)</p>
      </footer>
    </div>
  );
};

export default Calculator;
```

app.css
```
.calculator {
    width: 100%;
    max-width: 350px;
    margin: 40px auto;
    padding: 25px;
    border-radius: 12px;
    background: hsl(300, 64%, 65%);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  }
  
  .display {
    font-size: 32px;
    padding: 20px;
    text-align: right;
    background: oklab(80.503% -0.13574 -0.02566);
    margin-bottom: 20px;
    border-radius: 8px;
    border: 1px solid #ccc;
  }
  
  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
  }
  
  button {
    padding: 20px;
    font-size: 18px;
    background-color: hsl(195, 93%, 51%);
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background 0.2s;
  }
  
  button:hover {
    background-color: hsl(187, 81%, 51%);
  }
  
  .clear {
    background-color: #ef5350;
    color: hsl(210, 17%, 98%);
  }
  
  .clear:hover {
    background-color: #e53935;
  }
  
  .equal {
    background-color: #4caf50;
    color: hsl(317, 20%, 93%);
    grid-column: span 1;
  }
  
  .equal:hover {
    background-color: #388e3c;
  }
  
  .zero {
    grid-column: span 2;
  }
```

## OUTPUT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f0e21b65-044a-40eb-8f26-574b0f0b96f7" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/76a7d961-0280-4047-a4e4-282f98b9a55b" />

## RESULT
The program for developing a simple calculator in React.js is executed successfully.
