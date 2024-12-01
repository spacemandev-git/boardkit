<script lang="ts">
    import { goto } from "$app/navigation";
    import { nanoid } from "nanoid";

    let roomId = nanoid(6);
</script>

<div class="container">
    <h1>BoardKit</h1>
    <p>Play multiplayer 2D board games with friends!</p>
    <div>
        <input type="text" bind:value={roomId} placeholder={roomId} />
        <button on:click={() => goto(`/lobby/${roomId}`)}
            >Create/Join Lobby</button
        >
    </div>
</div>
<div class="footer">Made by Spacemandev</div>

<style>
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
    }

    .footer {
        position: fixed;
        bottom: 0;
        width: 100%;
        text-align: center;
    }
</style>
