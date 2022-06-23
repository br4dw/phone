<style>
    .apps {
		grid-row: span 15;
		display: grid;
		flex-direction: row;
		flex-wrap: wrap;
    	align-content: flex-start;
		justify-items: center;
		grid-template-columns: 1fr 1fr 1fr 1fr;
		gap: 1em;
		margin: 1rem 1rem 1rem 1rem;
		overflow-y: scroll;
		-ms-overflow-style: none;
  		scrollbar-width: none;
	}
	.app {
		width: calc(var(--app-size) + .5em);
		height: calc(var(--app-size) + .5em);
		background-color: var(--app-bg);
		border-radius: 15px;
		cursor: pointer;
		box-shadow: var(--app-shadow);
	}
	.apps::-webkit-scrollbar {
		display: none;
	}
	.app-icon {
		width: 100%;
		border-radius: 15px;
	}
</style>

<div class="apps noselect">
    <div class="app">
        <img src="img/apps/info.png" alt="" class="app-icon" draggable="false">
    </div>
    <div class="app">
        <a href="/apps/settings">
            <img src="img/apps/settings.png" alt="" class="app-icon" draggable="false">
        </a>
    </div>
    <div class="app">
        <a href="/apps/phone">
            <img src="img/apps/phone.png" alt="" class="app-icon" draggable="false">
        </a>
    </div>
    <div class="app">
        <img src="img/apps/messages.png" alt="" class="app-icon" draggable="false">
    </div>
    <div class="app">
        <img src="img/apps/location.png" alt="" class="app-icon" draggable="false">
    </div>
    <div class="app">
        <img src="img/apps/mail.png" alt="" class="app-icon" draggable="false">
    </div>
    <div class="app">
        <img src="img/apps/advertisements.png" alt="" class="app-icon" draggable="false">
    </div>
    <div class="app">
        <a href="/apps/calculator">
            <img src="img/apps/calculator.png" alt="" class="app-icon" draggable="false">
        </a>
    </div>
</div>