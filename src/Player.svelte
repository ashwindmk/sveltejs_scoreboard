<script>
    import Navbar from './Navbar.svelte';
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

	export let name;
    export let points;
    let author = "Ashwin Dinesh";
    let showControls = false;

    const plusPoint = () => points += 1;
    const minusPoint = () => points -= 1;
    const toggleControls = () => showControls = !showControls;
    const onRemove = () => dispatch("removeplayer", name);
</script>

<div class="card">
    <h2>
        {name}
        <button class="btn btn-sm" on:click={toggleControls}>
            {#if showControls} - {:else} + {/if}
        </button>
        <button class="btn btn-danger btn-sm" on:click={onRemove}> x </button>
    </h2>

    <h3>Points: {points}</h3>

    {#if showControls}
        <button class="btn" on:click={plusPoint}> +1 </button>
        <button class="btn" on:click={minusPoint}> -1 </button>

        <input type="number" bind:value={points}>
    {/if}
</div>

<style>
    h3 {
        margin-bottom: 1em;
    }
</style>
