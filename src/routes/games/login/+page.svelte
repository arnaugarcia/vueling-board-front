<script>

    import {setCookie} from "svelte-cookie";

    let setUsername = (event) => {
        const username = event.target.user.value;
        if (username && document) {
            setCookie('username', username, {expires: 1})
            window.location.href = '/games/quizz';
        }
    }
</script>

<div class="card">
    <div class="card-body">
        <h4 class="mb-1 pt-2">Welcome to VuelingBoard Games! 👋</h4>
        <p class="mb-4">Please sign-in to start the adventure</p>

        <form id="formAuthentication" class="mb-3" on:submit|preventDefault={setUsername}>
            <div class="mb-3">
                <label for="user" class="form-label">Username</label>
                <input
                        type="text"
                        class="form-control"
                        id="user"
                        name="user"
                        placeholder="Enter your username"
                        autofocus />
            </div>
            <div class="mb-3">
                <button class="btn btn-primary d-grid w-100" type="submit">Enter</button>
            </div>
        </form>
    </div>
</div>
