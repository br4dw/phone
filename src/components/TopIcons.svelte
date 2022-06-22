<script>
    import { onMount } from 'svelte';
    import moment from 'moment';

    onMount(() => {
		document.querySelector('.time').textContent = generateTime();
		setInterval(() => {
			document.querySelector('.time').textContent = generateTime();
		}, 1000);
	})

    function generateTime() {
		return moment(new Date()).format('hh:mm');
	}
</script>

<style>
    .top-icons {
		display: flex;
		gap: .5em;
		align-items: flex-start;
		color: white;
		padding: .75em;
		border-radius: calc(var(--border-radius) - .5rem) calc(var(--border-radius) - .5rem) 0 0;
	}

	.top-icons button {
		background: none;
		border: none;
		color: inherit;
		padding: 0;
		height: 1em;
		width: 1em;
		font-size: calc((var(--phone-width) / 30) + .5em);
		fill: white;
	}
	.time-container {
		display: flex;
		align-items: center;
		gap: .25rem;
		flex-grow: 1;
	}
	.time {
		font-size: calc((var(--phone-width) / 30) + .5em);
	}
</style>

<div class="top-icons">
    <div class="time-container noselect">
        <div class="time"></div>
    </div>
    <button class="wifi">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512">
            <path d="M319.1 351.1c-35.35 0-64 28.66-64 64.01s28.66 64.01 64 64.01c35.34 0 64-28.66 64-64.01S355.3 351.1 319.1 351.1zM320 191.1c-70.25 0-137.9 25.6-190.5 72.03C116.3 275.7 115 295.9 126.7 309.2C138.5 322.4 158.7 323.7 171.9 312C212.8 275.9 265.4 256 320 256s107.3 19.88 148.1 56C474.2 317.4 481.8 320 489.3 320c8.844 0 17.66-3.656 24-10.81C525 295.9 523.8 275.7 510.5 264C457.9 217.6 390.3 191.1 320 191.1zM630.2 156.7C546.3 76.28 436.2 32 320 32S93.69 76.28 9.844 156.7c-12.75 12.25-13.16 32.5-.9375 45.25c12.22 12.78 32.47 13.12 45.25 .9375C125.1 133.1 220.4 96 320 96s193.1 37.97 265.8 106.9C592.1 208.8 600 211.8 608 211.8c8.406 0 16.81-3.281 23.09-9.844C643.3 189.2 642.9 168.1 630.2 156.7z"/>
        </svg>
    </button>
    <button class="battery">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512">
            <path d="M352 320H96V192H352V320zM0 176C0 131.8 35.82 96 80 96H464C508.2 96 544 131.8 544 176V192C561.7 192 576 206.3 576 224V288C576 305.7 561.7 320 544 320V336C544 380.2 508.2 416 464 416H80C35.82 416 0 380.2 0 336V176zM80 160C71.16 160 64 167.2 64 176V336C64 344.8 71.16 352 80 352H464C472.8 352 480 344.8 480 336V176C480 167.2 472.8 160 464 160H80z"/>
        </svg>
    </button>
</div>