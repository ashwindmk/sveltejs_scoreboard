<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    let player = {
        oldname: "",
        newname: ""
    };

    const onSubmit = (e) => {
        e.preventDefault();
        dispatch("editplayer", player);

        player = {
            oldname: "",
            newname: ""
        };
    }
</script>

<form class="grid-3" on:submit={onSubmit}>
    <input type="text" placeholder="Player old-name" bind:value={player.oldname} />
    <input type="text" placeholder="Player new-name" bind:value={player.newname} />
    <input type="submit" class="btn btn-primary" value="Edit Player" />
</form>
