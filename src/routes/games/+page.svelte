<script>

    import {onMount} from "svelte";
    import {getCookie, setCookie} from "svelte-cookie";
    import {redirect} from "@sveltejs/kit";

    let username = '';
    let games = [];

    onMount(() => {
        username = getCookie('username');
        fetch('http://10.5.238.248:3000/games')
            .then(response => response.json())
            .then(data => {
                games = data;
            });
    });

    function registerPlayer() {
        if (username !== '') {
            location.href = '/games/login';
            console.log('redirecting to login')
        }

        fetch('http://10.5.238.248:3000/players', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({
                name: username
            })
        }).then(response => {
            if (response.status === 201) {
                setCookie('username', username, {expires: 1})
                location.href = '/games/wait-list';
            } else {
                console.log('error');
            }
        });
    }
</script>

<h4 class="fw-bold py-3 mb-4">Games</h4>
<div class="row mb-5">
    {#each games as game}
    <div class="col-md-6 col-lg-4 mb-3">
        <div class="card h-100">
            <a href="/games/wait-list" on:click={registerPlayer}>
                <img class="card-img-top" src={game.photo} alt={game.description}/>
                <div class="card-body">
                    <h5 class="card-title">{game.name}</h5>
                    <p class="card-text">
                        {game.description}
                    </p>
                </div>
            </a>
        </div>
    </div>
    {/each}
</div>
