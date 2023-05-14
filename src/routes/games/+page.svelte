<script>

    import {onMount} from "svelte";
    import {getCookie, setCookie} from "svelte-cookie";
    import {redirect} from "@sveltejs/kit";

    let username = '';

    onMount(() => {
        username = getCookie('username');
    });

    function registerPlayer() {
        if (username !== '') {
            location.href = '/games/login';
            console.log('redirecting to login')
        }

        fetch('http://localhost:3000/players', {
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
    <div class="col-md-6 col-lg-4 mb-3">
        <div class="card h-100">
            <a href="/games/wait-list" on:click={registerPlayer}>
                <img class="card-img-top" src="../../assets/img/elements/quiz.jpg" alt="Card image cap"/>
                <div class="card-body">
                    <h5 class="card-title">Quiz</h5>
                    <p class="card-text">
                        A funny and quick general knowledge about the destination country!
                    </p>
                </div>
            </a>
        </div>
    </div>
    <div class="col-md-6 col-lg-4 mb-3">
        <div class="card h-100">
            <a href="javascript:void(0)">
                <img class="card-img-top" src="../../assets/img/elements/clue.jpg" alt="Card image cap"/>
                <div class="card-body">
                    <h5 class="card-title">Clue</h5>
                    <p class="card-text">
                        Step into the Detective's Shoes with the Ultimate Clue Game Experience!
                    </p>
                </div>
            </a>
        </div>
    </div>
    <div class="col-md-6 col-lg-4 mb-3">
        <div class="card h-100">
            <a href="javascript:void(0)">
                <img class="card-img-top" src="../../assets/img/elements/storytelling.jpg" alt="Card image cap"/>
                <div class="card-body">
                    <h5 class="card-title">Storytelling</h5>
                    <p class="card-text">
                        Unleash your imagination and embark on a legendary journey through the power of storytelling.
                    </p>
                </div>
            </a>
        </div>
    </div>

</div>
