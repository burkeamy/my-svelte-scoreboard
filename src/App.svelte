<script>
	import Navbar from './Navbar.svelte';
	import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte';

	let players = [
		{
			name: "Janet",
			points: 65
		},
		{
			name: "Bob",
			points: 55
		},
		{
			name: "June",
			points: 75
		}
	];

	const addPlayer = e => {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	};

	const removePlayer = e => {
		players = players.filter( player => player.name !== e.detail);
	}
</script>

<main>
	<Navbar/>
	<div class = "container">
		<AddPlayer class = "gridItem"  on:addplayer={addPlayer}/>
		{#if players.length === 0}
			<p>No Players</p>
		{:else}
			{#each players as player}
				<Player name={player.name} points={player.points}
				on:removeplayer={removePlayer}/>
			{/each}		
		{/if}
			
	</div>
</main>

<style>
	    .container  {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        grid-gap: 10px;
    }
</style>