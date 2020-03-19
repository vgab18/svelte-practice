<script>
  import Navbar from "./navBar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    {
      name: "Kobe Bryant",
      points: 14
    },
    {
      name: "Lebron James",
      points: 10
    },
    {
      name: "Kevin Duran",
      points: 35
    }
  ];

  const addPlayer = e => {
    const newPlayer = e.detail;
    console.log(e.detail);
    players = [...players, newPlayer];
  };

  const removePlayer = e => {
    players = players.filter(player => player.name !== e.detail);
  };
</script>

<style>

</style>

<Navbar />
<div class="container">
  <AddPlayer on:addplayer={addPlayer} />
  {#if players.length === 0}
    <h5>No Players</h5>
  {:else}
    {#each players as player, index}
      <Player
        name={player.name}
        points={player.points}
        index={player.index}
        on:removeplayer={removePlayer} />
    {/each}
  {/if}
</div>
