<style>
    .app-container {
        grid-row: span 16;
        background-color: rgba(42, 44, 53, 0.7);
        display: flex;
        width: auto;
        color: white;
    }

    .calculator-grid {
        display: grid;
        justify-content: center;
        align-content: center;
        width: 100%;
        height: 100%;
        grid-template-columns: repeat(4, calc((var(--phone-width) / 4) - .1rem));
        grid-template-rows: minmax(120px, auto) repeat(5, calc(var(--phone-width) / 4));
    }
    .calculator-grid > button {
        font-family: monospace;
        cursor: pointer;
        font-size: 2rem;
        border: 1px solid white;
        outline: none;
        background-color: var(--button-bg);
        transition: background-color 100ms ease-in-out;
    }
    .calculator-grid > button:hover {
        background-color: var(--button-hover-bg);
    }
    .span-two {
        grid-column: span 2;
    }
    .output {
        grid-column: 1 / -1;
        background-color: var(--output-bg);
        display: flex;
        align-items: flex-end;
        justify-content: space-around;
        flex-direction: column;
        padding: 10px;
        word-wrap: break-word;
        word-break: break-all;
    }
    .output .previous-operand {
        color: var(--button-bg);
        font-size: 1.5rem;
    }
    .output .current-operand {
        color: white;
        font-size: 2.5rem;
    }
</style>

<script>
    import moment from 'moment';
	import { onMount } from 'svelte';

	onMount(() => {
        document.querySelector('.time').textContent = generateTime();
		setInterval(() => {
			document.querySelector('.time').textContent = generateTime();
		}, 1000);

        class Calculator {
            constructor(previousOperandTextElement, currentOperandTextElement) {
                this.previousOperandTextElement = previousOperandTextElement;
                this.currentOperandTextElement = currentOperandTextElement;
                this.clear();
            }

            clear() {
                this.currentOperand = '';
                this.previousOperand = '';
                this.operation = undefined;
            }

            delete() {
                this.currentOperand = this.currentOperand.toString().slice(0, -1);
            }

            appendNumber(number) {
                if (number === '.' && this.currentOperand.includes('.')) return;
                this.currentOperand = this.currentOperand.toString() + number.toString();
            }

            chooseOperation(operation) {
                if (this.currentOperand === '') return;
                if (this.previousOperand !== '') this.compute();
                this.operation = operation;
                this.previousOperand = this.currentOperand;
                this.currentOperand = '';
            }

            compute() {
                let computation;
                const prev = parseFloat(this.previousOperand);
                const current = parseFloat(this.currentOperand);
                if (isNaN(prev) || isNaN(current)) return;
                switch(this.operation) {
                    case '÷':
                        computation = prev / current;
                        break;
                    case '*':
                        computation = prev * current;
                        break;
                    case '+':
                        computation = prev + current;
                        break;
                    case '-':
                        computation = prev - current;
                        break;
                    default:
                        return;
                }
                this.currentOperand = computation;
                this.operation = undefined;
                this.previousOperand = '';
            }

            getDisplayNumber(number) {
                const stringNumber = number.toString();
                const integerDigits = parseFloat(stringNumber.split('.')[0])
                const decimalDigits = stringNumber.split('.')[1];
                let integerDisplay;
                if (isNaN(integerDigits)) {
                    integerDisplay = '';
                } else {
                    integerDisplay = integerDigits.toLocaleString('en', { maximumFractionDigits: 0 });
                }
                if (decimalDigits != null) {
                    return `${integerDisplay}.${decimalDigits}`
                } else {
                    return integerDisplay;
                }
            }

            updateDisplay() {
                this.currentOperandTextElement.innerText = this.getDisplayNumber(this.currentOperand);
                if (this.operation != null) {
                    this.previousOperandTextElement.innerText = `${this.getDisplayNumber(this.previousOperand)} ${this.operation}`;
                } else {
                    this.previousOperandTextElement.innerText = '';
                }
            }

        }

        const numberButtons = document.querySelectorAll('[data-number]');
        const operationButtons = document.querySelectorAll('[data-operation]');
        const equalsButton = document.querySelector('[data-equals]');
        const deleteButton = document.querySelector('[data-delete]');
        const allClearButton = document.querySelector('[data-all-clear]');
        const previousOperandTextElement = document.querySelector('[data-previous-operand]');
        const currentOperandTextElement = document.querySelector('[data-current-operand]');

        const calculator = new Calculator(previousOperandTextElement, currentOperandTextElement)

        numberButtons.forEach(button => {
            button.addEventListener('click', () => {
                calculator.appendNumber(button.innerText);
                calculator.updateDisplay();
            })
        })

        operationButtons.forEach(button => {
            button.addEventListener('click', () => {
                calculator.chooseOperation(button.innerText);
                calculator.updateDisplay();
            })
        })

        equalsButton.addEventListener('click', button => {
            calculator.compute();
            calculator.updateDisplay();
        })
        allClearButton.addEventListener('click', button => {
            calculator.clear();
            calculator.updateDisplay();
        })
        deleteButton.addEventListener('click', button => {
            calculator.delete();
            calculator.updateDisplay();
        })

	})

	function generateTime() {
		return moment(new Date()).format('hh:mm');
	}
</script>

<div class="calculator-grid">
    <div class="output">
        <div data-previous-operand class="previous-operand"></div>
        <div data-current-operand class="current-operand"></div>
    </div>
    <button class="span-two" data-all-clear>AC</button>
    <button data-delete>DEL</button>
    <button data-operation>÷</button>
    <button data-number>1</button>
    <button data-number>2</button>
    <button data-number>3</button>
    <button data-operation>*</button>
    <button data-number>4</button>
    <button data-number>5</button>
    <button data-number>6</button>
    <button data-operation>+</button>
    <button data-number>7</button>
    <button data-number>8</button>
    <button data-number>9</button>
    <button data-operation>-</button>
    <button data-number>0</button>
    <button data-number>.</button>
    <button class="span-two" data-equals>=</button>
</div>