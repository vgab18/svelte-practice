<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let player = {
    name: "",
    points: 0
  };

  const onSubmit = e => {
    e.preventDefault();
    dispatch("addplayer", player);
    player = {
      name: "",
      points: 0
    };
  };
</script>

<style>
  form {
    margin-bottom: 30px;
    padding: 2em;
    border: 1px dashed #0069d9;
    text-align: center;
  }
  input {
    width: 100%;
    margin-bottom: 10px;
  }
</style>

<form on:submit={onSubmit} class="grid-3">
  <h2>Add Player</h2>
  <input type="text" placeholder="Player Name" bind:value={player.name} />
  <input type="number" placeholder="Player Points" bind:value={player.points} />
  <input type="submit" class="btn btn-primary" value="Add" />
</form>
<!-- <form class="grid-3">
  <h2>Add Team</h2>
  <input type="text" placeholder="Team Name" bind:value={player.name} />
  <input type="submit" class="btn btn-primary" value="Add" />
</form> -->
