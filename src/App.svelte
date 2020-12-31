<script>
    import Navbar from './Navbar.svelte';
    import Player from './Player.svelte';
    import AddPlayer from './AddPlayer.svelte';
    import EditPlayer from './EditPlayer.svelte';

    let players = [
        {
            name: "John Doe",
            points: 54
        },
        {
            name: "Sam Smith",
            points: 75
        },
        {
            name: "Sara Wilson",
            points: 50
        }
    ];

    const addPlayer = (e) => {
        const newPlayer = e.detail;
        players = [... players, newPlayer];
    }

    const removePlayer = (e) => {
        const name = e.detail;
        players = players.filter(p => p.name !== name);
    }

    const editPlayer = (e) => {
        const player = e.detail;
        players = players.map(p => {
            if (p.name === player.oldname) {
                p.name = player.newname;
            }
            return p;
        });
    }
</script>

<main>
    <Navbar />
    <div class="container">
        <AddPlayer on:addplayer={addPlayer} />

        <EditPlayer on:editplayer={editPlayer} />

        {#if players.length === 0}
            <p>No players</p>
        {:else}
            {#each players as player}
                <Player name={player.name} points={player.points} on:removeplayer={removePlayer} />
            {/each}
        {/if}
    </div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;
	}
</style>
