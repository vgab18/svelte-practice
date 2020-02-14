<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let name;
  export let points;
  let showToggle = false;

  const handleAddPoint = () => {
    points += 1;
  };
  const handleRemovePoint = () => {
    points -= 1;
  };
  const toggleControls = () => {
    showToggle = !showToggle;
  };
  const onRemove = () => {
    dispatch("removeplayer", name);
  };
</script>

<style>
  .card {
    margin-bottom: 15px;
    width: 49%;
    padding: 30px;
    display: inline-block;
    margin: 5px;
  }
  .btn-danger {
    float: right;
    margin-top: -70px;
    margin-right: -15px;
  }
</style>

<div class="card">
  <h1>{name}</h1>
  <span>
    <button class="btn btn-danger" on:click={onRemove}>X</button>
  </span>
  <h1>points: {points}</h1>
  <button on:click={toggleControls}>
    {#if !showToggle}Show{:else}Hide{/if}

  </button>
  {#if showToggle}
    <button class="btn btn-dark" on:click={handleRemovePoint}>-</button>
    <button class="btn btn-primary" on:click={handleAddPoint}>+</button>
    <input type="number" bind:value={points} />
  {/if}
</div>
