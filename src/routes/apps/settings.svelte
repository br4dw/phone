<style>

	*, *::before, *::after {
		box-sizing: border-box;
	}

	:root {
		--phone-width: 20em; /* dont go below 20 or above 60 xd */
		--border-size: .2em;
		--app-size: calc((var(--phone-width) / 8) + .5em);
		--phone-height: calc(var(--phone-width) * 2);
		--border-radius: 35px;
		--border-color: white;
		--notch-height: calc(var(--phone-width) / 10 / 2);
		--app-bg: #FFFA;
		--bottom-bg: rgba(0, 0, 0, 0.3);
		--top-bg: rgba(0, 0, 0, 0.8);
		--app-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
	}

	.phone {
		display: grid;
		grid-template-columns: repeat(1, 1fr);
		grid-template-rows: repeat(15, 1fr);
		width: var(--phone-width);
		height: var(--phone-height);
		min-width: 20em;
		min-height: 40em;
		border: var(--border-size) solid var(--border-color);
		background-color: transparent;
		background-image: url("https://source.unsplash.com/kMxlbbzbFhQ");
		background-position: center;
		background-repeat: no-repeat;
		background-size: var(--phone-width) var(--phone-height);
		border-radius: var(--border-radius);
		margin: 0 auto;
	}
	.phone:last-child {
		grid-row-start: 7;
	}

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
	.bottom-icons button {
		background: none;
		border: none;
		color: inherit;
		padding: 0;
		margin-right: .91em;
		margin-left: .96em;
		margin-top: .95em;
		margin-bottom: .83em;
		cursor: pointer;

		height: 1.15em;
		width: 1.15em;
		font-size: calc(var(--phone-width) / 25);
		fill: white;
	}
	.bottom-icons-container {
		display: grid;
		margin: 0 auto;
		padding: 15px;
	}
	.bottom-icons {
		display: grid;
		gap: 4.5%;
		justify-content: center;
		grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
		font-size: calc((var(--phone-width) / 90) + .9em);
	}
    .app-container {
        grid-row: span 16;
        background-color: white;
        display: flex;
        width: auto;
        padding: 10px;
    }
</style>

<script>
	import moment from 'moment';
	import { onMount } from 'svelte';
	let time = "00:00";

	onMount(() => {
		time = generateTime();
		setInterval(() => {
			time = generateTime();
		}, 100);
		document.querySelector('.time').textContent = time;
	})

	function generateTime() {
		return moment(new Date()).format('hh:mm');
	}
</script>

<svelte:head>
	<title>Phone</title>
</svelte:head>


<div class="phone">
	<div class="top-icons">
		<div class="time-container noselect">
			<div class="time">{time}</div>
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
    <div class="app-container noselect">
        <h1>Settings</h1>
    </div>
	<div class="bottom-icons-container">
		<div class="bottom-icons">
			<button class="bell">
				<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
					<path d="M256 32V51.2C329 66.03 384 130.6 384 208V226.8C384 273.9 401.3 319.2 432.5 354.4L439.9 362.7C448.3 372.2 450.4 385.6 445.2 397.1C440 408.6 428.6 416 416 416H32C19.4 416 7.971 408.6 2.809 397.1C-2.353 385.6-.2883 372.2 8.084 362.7L15.5 354.4C46.74 319.2 64 273.9 64 226.8V208C64 130.6 118.1 66.03 192 51.2V32C192 14.33 206.3 0 224 0C241.7 0 256 14.33 256 32H256zM224 512C207 512 190.7 505.3 178.7 493.3C166.7 481.3 160 464.1 160 448H288C288 464.1 281.3 481.3 269.3 493.3C257.3 505.3 240.1 512 224 512z"/>
				</svg>
			</button>
			<button class="camera">
				<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
					<path d="M194.6 32H317.4C338.1 32 356.4 45.22 362.9 64.82L373.3 96H448C483.3 96 512 124.7 512 160V416C512 451.3 483.3 480 448 480H64C28.65 480 0 451.3 0 416V160C0 124.7 28.65 96 64 96H138.7L149.1 64.82C155.6 45.22 173.9 32 194.6 32H194.6zM256 384C309 384 352 341 352 288C352 234.1 309 192 256 192C202.1 192 160 234.1 160 288C160 341 202.1 384 256 384z"/>
				</svg>
			</button>
			<a href="/">
				<button class="home">
					<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
						<path d="M222.7 32.15C227.7 49.08 218.1 66.9 201.1 71.94C121.8 95.55 64 169.1 64 255.1C64 362 149.1 447.1 256 447.1C362 447.1 448 362 448 255.1C448 169.1 390.2 95.55 310.9 71.94C293.9 66.9 284.3 49.08 289.3 32.15C294.4 15.21 312.2 5.562 329.1 10.6C434.9 42.07 512 139.1 512 255.1C512 397.4 397.4 511.1 256 511.1C114.6 511.1 0 397.4 0 255.1C0 139.1 77.15 42.07 182.9 10.6C199.8 5.562 217.6 15.21 222.7 32.15V32.15z"/>
					</svg>
				</button>
			</a>
			<button class="refresh">
				<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
					<path d="M464 16c-17.67 0-32 14.31-32 32v74.09C392.1 66.52 327.4 32 256 32C161.5 32 78.59 92.34 49.58 182.2c-5.438 16.81 3.797 34.88 20.61 40.28c16.89 5.5 34.88-3.812 40.3-20.59C130.9 138.5 189.4 96 256 96c50.5 0 96.26 24.55 124.4 64H336c-17.67 0-32 14.31-32 32s14.33 32 32 32h128c17.67 0 32-14.31 32-32V48C496 30.31 481.7 16 464 16zM441.8 289.6c-16.92-5.438-34.88 3.812-40.3 20.59C381.1 373.5 322.6 416 256 416c-50.5 0-96.25-24.55-124.4-64H176c17.67 0 32-14.31 32-32s-14.33-32-32-32h-128c-17.67 0-32 14.31-32 32v144c0 17.69 14.33 32 32 32s32-14.31 32-32v-74.09C119.9 445.5 184.6 480 255.1 480c94.45 0 177.4-60.34 206.4-150.2C467.9 313 458.6 294.1 441.8 289.6z"/>
				</svg>
			</button>
			<button class="google">
				<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 488 512">
					<path d="M488 261.8C488 403.3 391.1 504 248 504 110.8 504 0 393.2 0 256S110.8 8 248 8c66.8 0 123 24.5 166.3 64.9l-67.5 64.9C258.5 52.6 94.3 116.6 94.3 256c0 86.5 69.1 156.6 153.7 156.6 98.2 0 135-70.4 140.8-106.9H248v-85.3h236.1c2.3 12.7 3.9 24.9 3.9 41.4z"/>
				</svg>
			</button>
		</div>
	</div>
</div>