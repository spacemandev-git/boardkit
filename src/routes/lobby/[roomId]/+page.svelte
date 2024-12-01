<script lang="ts">
    import { page } from "$app/stores";
    import { joinRoom, selfId } from "trystero/firebase";
    import { onMount } from "svelte";
    import type { Room } from "trystero";
    const config = {
        appId: `https://boardkit-ed83f-default-rtdb.firebaseio.com/`,
    };

    let room: Room;
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
{/if}
