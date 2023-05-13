<div class="card">
    <div class="card-body">
        <h4 class="mb-1 pt-2">Welcome to VuelingBoard Games! 👋</h4>
        <p class="mb-4">Please sign-in to start the adventure</p>

        <form id="formAuthentication" class="mb-3" action="index.html" method="POST">
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
                <label for="seat" class="form-label">Seat Number</label>
                <input
                        type="text"
                        class="form-control"
                        id="seat"
                        name="seat"
                        placeholder="Enter your seat number"
                        autofocus />
            </div>
            <div class="mb-3">
                <button class="btn btn-primary d-grid w-100" type="submit">Enter</button>
            </div>
        </form>
    </div>
</div>