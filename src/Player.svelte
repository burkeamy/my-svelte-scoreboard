<script>
    import { createEventDispatcher } from 'svelte';
    export let name;
    export let points;

    let showControls = false;

    const dispatch = createEventDispatcher();

    const addPoint = () => (points +=1);
    const removePoint = () => (points -=1);
    const toggleControls =() => (showControls = !showControls);
    const deletePlayer = () => dispatch("removeplayer", name);
</script>

<style>
    h1 {
        color: darkblue;
    }
    div {
        margin: 2px;
        padding: 9px;
        background-color: wheat;
        border: 1px solid brown;
    }
    .btn {
        font-size: small;
        box-shadow: brown 1px 3px;
    }
</style>

<div class = "container">
    <h1>
        {name}
        <br>
		<button class = "btn"on:click={toggleControls}>
			{#if showControls}-{:else}+{/if}
        </button>
        <button class = "btn" on:click={deletePlayer}>bye</button>
	</h1>
	<h3>Points: {points}</h3>
	{#if showControls}
		<button class = "btn" on:click={addPoint}>+1</button>
		<button class = "btn" on:click={removePoint}>-1</button>
		<input type="number" bind:value={points} />
	{/if}
</div>