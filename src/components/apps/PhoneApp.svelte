<style>
    :root {
        --phone-button: #333333;
        --phone-button-hover: #a6a6a6;
        --phone-call-button: #67cd67;
        --phone-call-button-hover: #479247;
    }
    .phone-grid {
        display: grid;
        align-items: center;
        align-content: center;
        justify-content: center;
        width: 100%;
        height: 100%;
        grid-template-columns: repeat(3, calc((var(--phone-width) / 3) - 1rem));
        grid-template-rows: minmax(80px, auto) repeat(5, calc(var(--phone-width) / 4));
    }
    .icon > svg {
        fill: white;
        width: .75em;
        height: .75em;
    }
    .phone-grid > button {
        width: 2em;
        height: 2em;
        margin: 0 auto;
        color: white;
        font-family: monospace;
        cursor: pointer;
        font-size: 2rem;
        outline: none;
        border: none;
        border-radius: 150%;
        background-color: var(--phone-button);
        transition: background-color 250ms ease-in-out;
    }
    .phone-grid > button:hover {
        background-color: var(--phone-button-hover);
    }
    .phone-grid > button:nth-child(14) {
        background-color: var(--phone-call-button);
    }
    .phone-grid > button:nth-child(14):hover {
        background-color: var(--phone-call-button-hover);
    }
    .phone-grid > button:last-child {
        background-color: transparent;
        fill: var(--phone-button);
    }
    .phone-grid > button:last-child > svg {
        transition: all 250ms ease-in-out;
        fill: var(--phone-button-hover);
    }
    .phone-grid > button:last-child > svg:hover {
        fill: white;
    }
    .hidden {
        display: none;
    }
    .middle {
        grid-column-start: 2;
    }
    .output {
        grid-column: 1 / -1;
        display: flex;
        align-items: center;
        justify-content: space-around;
        flex-direction: column;
        padding: 10px;
        word-wrap: break-word;
        word-break: break-all;
    }
    .output .current-number {
        color: var(--phone-button);
        font-size: 2.5rem;
    }
</style>

<script>
	import { onMount } from 'svelte';
    let number = false;

	onMount(() => {

        let buttons = document.querySelectorAll('[data-button]');
        let deleteButton = document.querySelector('[data-button-delete]');
        const current = document.querySelector('[data-current-number]');

        buttons.forEach(button => {
            button.addEventListener('click', () => {
                number = true;
                current.innerText = current.innerText + button.innerText;
            })
        })

        deleteButton.addEventListener('click', () => {
            current.innerText = current.innerText.toString().slice(0, -1);
            let currentValue = document.querySelector('[data-current-number]').innerText;
            if (currentValue.length < 1) number = false;
        })

	})

</script>

<div class="phone-grid">
    <div class="output">
        <div data-current-number class="current-number"></div>
    </div>
    <button data-button>1</button>
    <button data-button>2</button>
    <button data-button>3</button>
    <button data-button>4</button>
    <button data-button>5</button>
    <button data-button>6</button>
    <button data-button>7</button>
    <button data-button>8</button>
    <button data-button>9</button>
    <button data-button>*</button>
    <button data-button>0</button>
    <button data-button>#</button>
    <button data-button class="middle icon">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
            <path d="M511.2 387l-23.25 100.8c-3.266 14.25-15.79 24.22-30.46 24.22C205.2 512 0 306.8 0 54.5c0-14.66 9.969-27.2 24.22-30.45l100.8-23.25C139.7-2.602 154.7 5.018 160.8 18.92l46.52 108.5c5.438 12.78 1.77 27.67-8.98 36.45L144.5 207.1c33.98 69.22 90.26 125.5 159.5 159.5l44.08-53.8c8.688-10.78 23.69-14.51 36.47-8.975l108.5 46.51C506.1 357.2 514.6 372.4 511.2 387z"/>
        </svg>
    </button>
    <button data-button-delete class="delete-icon icon {number ? '' : 'hidden'}">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512">
            <path d="M576 384C576 419.3 547.3 448 512 448H205.3C188.3 448 172 441.3 160 429.3L9.372 278.6C3.371 272.6 0 264.5 0 256C0 247.5 3.372 239.4 9.372 233.4L160 82.75C172 70.74 188.3 64 205.3 64H512C547.3 64 576 92.65 576 128V384zM271 208.1L318.1 256L271 303C261.7 312.4 261.7 327.6 271 336.1C280.4 346.3 295.6 346.3 304.1 336.1L352 289.9L399 336.1C408.4 346.3 423.6 346.3 432.1 336.1C442.3 327.6 442.3 312.4 432.1 303L385.9 256L432.1 208.1C442.3 199.6 442.3 184.4 432.1 175C423.6 165.7 408.4 165.7 399 175L352 222.1L304.1 175C295.6 165.7 280.4 165.7 271 175C261.7 184.4 261.7 199.6 271 208.1V208.1z"/>
        </svg>
    </button>
</div>