<script lang="ts">
    import { page } from "$app/stores";
    import { joinRoom, selfId } from "trystero/firebase";
    import { onMount } from "svelte";
    import type { Room } from "trystero";
    import Game from "./game.svelte";
    const config = {
        appId: `https://boardkit-ed83f-default-rtdb.firebaseio.com/`,
    };

    let room: Room;
    let inRoom: boolean = false;

    onMount(() => {
        console.log(selfId);
        room = joinRoom(config, $page.params.roomId);
    });
</script>

<h1>Room: {$page.params.roomId}</h1>
<p>Self: {selfId}</p>
{#if room}
    <h3>Peers:</h3>
    {#each Object.keys(room.getPeers()) as peerId}
        <p>{peerId}</p>
    {/each}
    <div>
        <h3>Load Module from Zip</h3>
        <h3>Load Save File for Module</h3>
    </div>

    <button on:click={() => (inRoom = true)}>Start Room</button>
{/if}

{#if inRoom}
    <Game />
{/if}
