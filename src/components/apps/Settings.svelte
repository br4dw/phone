<style>
    .settings-container {
        display: grid;
        width: 100%;
        height: 100%;
    }
    .title {
        display: flex;
        position: absolute;
        font-size: 2em;
        right: 46%;
        margin-bottom: .5em;
    }
    .setting-title {
        margin: .3em;
    }
    .setting {
        margin-top: 5em;
    }
    .setting-input,
    .setting-confirm {
        width: 100%;
        height: 2em;
        border: none;
        border-radius: 6px;
        font-size: 1em;
        padding: .2em;
        margin-bottom: .5em;
        transition: all 200ms ease-in-out;
    }
    .setting-input {
        background-color: var(--button-bg);
    }
    .disabled {
        pointer-events: none;
    }
    .setting-input:focus {
        outline: none !important;
        border: none;
    }
    .setting-confirm {
        background-color: var(--success);
        color: white;
        cursor: pointer;
    }
    .setting-confirm.disabled {
        background-color: var(--danger);
    }
    .setting-confirm:hover {
        background-color: var(--success-hover);
    }
    .setting-confirm.disabled:hover {
        background-color: var(--danger-hover);
    }
    
</style>

<script>
    async function changeWallpaper() {
        // let url = document.getElementById('wallpaper').value;
        // let wallpaper = localStorage.getItem('wallpaper');
        // if (url === wallpaper) return;
        // let validUrl = await validateImageUrl(url);
        // if (validUrl) {
        //     localStorage.setItem('wallpaper', url);
        //     document.querySelector('.phone').setAttribute('wallpaper', `url("${url}")`)
        // } else {
        //     document.querySelector('.phone').setAttribute('wallpaper', 'url("")')
        //     localStorage.setItem('wallpaper', false);
        //     return console.log('Not a valid image')
        // }
    }
    // function validateImageUrl(url) {
    //     return new Promise((resolve) => {
    //         const img = new Image();
    //         img.src = url;
    //         img.onload = () => resolve(true);
    //         img.onerror = () => resolve(false);
    //     })
    // }
</script>

<div class="settings-container">
    <div class="title">Settings</div>
    <div class="setting">
        <div class="setting-title">Wallpaper</div>
        <input class="setting-input disabled" type="text" name="wallpaper" id="wallpaper" placeholder="URL to image">
        <button class="setting-confirm disabled" on:click={changeWallpaper}>Confirm</button>
    </div>
</div>