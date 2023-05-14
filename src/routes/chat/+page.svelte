<script>
    import {onMount} from 'svelte';
    import store from "../../components/chat/store.js";

    let message;
    let messages = [];

    onMount(() => {
        store.subscribe(currentMessage => {
            messages = [...messages, currentMessage];
        })
    })

    function onSendMessage() {
        if (message.length > 0) {
            store.sendMessage(message);
            message = "";
        }
    }
</script>

<div class="col app-chat-history bg-body">
    <div class="chat-history-wrapper">
        <div class="chat-history-header border-bottom">
            <div class="d-flex justify-content-between align-items-center">
                <div class="d-flex overflow-hidden align-items-center">
                    <i
                            class="ti ti-menu-2 ti-sm cursor-pointer d-lg-none d-block me-2"
                            data-bs-toggle="sidebar"
                            data-overlay
                            data-target="#app-chat-contacts"></i>
                    <div class="flex-shrink-0 avatar">
                        <img
                                src="../../assets/img/avatars/2.png"
                                alt="Avatar"
                                class="rounded-circle"
                                data-bs-toggle="sidebar"
                                data-overlay
                                data-target="#app-chat-sidebar-right" />
                    </div>
                    <div class="chat-contact-info flex-grow-1 ms-2">
                        <h6 class="m-0">Felecia Rower</h6>
                        <small class="user-status text-muted">Vueling Staff</small>
                    </div>
                </div>
                <div class="d-flex align-items-center">
                    <i class="ti ti-phone-call cursor-pointer d-sm-block d-none me-3"></i>
                    <i class="ti ti-video cursor-pointer d-sm-block d-none me-3"></i>
                    <i class="ti ti-search cursor-pointer d-sm-block d-none me-3"></i>
                    <div class="dropdown d-flex align-self-center">
                        <button
                                class="btn p-0"
                                type="button"
                                id="chat-header-actions"
                                data-bs-toggle="dropdown"
                                aria-haspopup="true"
                                aria-expanded="false">
                            <i class="ti ti-dots-vertical"></i>
                        </button>
                        <div class="dropdown-menu dropdown-menu-end" aria-labelledby="chat-header-actions">
                            <a class="dropdown-item" href="javascript:void(0);">View Contact</a>
                            <a class="dropdown-item" href="javascript:void(0);">Mute Notifications</a>
                            <a class="dropdown-item" href="javascript:void(0);">Block Contact</a>
                            <a class="dropdown-item" href="javascript:void(0);">Clear Chat</a>
                            <a class="dropdown-item" href="javascript:void(0);">Report</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="chat-history-body bg-body">
            <ul class="list-unstyled chat-history">
                {#each messages as message, i}
                    <li class={'chat-message' + i % 2 == 0 ? "left" :  "right" + 'chat-message-right mt-4'}>
                        <div class="d-flex overflow-hidden">
                            <div class="chat-message-wrapper flex-grow-1">
                                <div class="chat-message-text">
                                    <p class="mb-0">How can we help? We're here for you! 😄</p>
                                </div>
                            </div>
                        </div>
                    </li>
                {/each}

            </ul>
        </div>
        <!-- Chat message form -->
        <div class="chat-history-footer shadow-sm">
            <form class="form-send-message d-flex justify-content-between align-items-center">
                <input bind:value={message}
                       class="form-control message-input border-0 me-3 shadow-none"
                        placeholder="Type your message here" />
                <div class="message-actions d-flex align-items-center">
                    <i class="speech-to-text ti ti-microphone ti-sm cursor-pointer"></i>
                    <label for="attach-doc" class="form-label mb-0">
                        <i class="ti ti-photo ti-sm cursor-pointer mx-3"></i>
                        <input type="file" id="attach-doc" hidden />
                    </label>
                    <button class="btn btn-primary d-flex send-msg-btn" on:click={onSendMessage}>
                        <i class="ti ti-send me-md-1 me-0"></i>
                        <span class="align-middle d-md-inline-block d-none">Send</span>
                    </button>
                </div>
            </form>
        </div>
    </div>
</div>
