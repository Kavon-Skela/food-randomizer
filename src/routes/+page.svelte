<script>
  import { writable } from "svelte/store";
  import AutoMode from "../Components/AutoMode/AutoMode.svelte";
  import ChooseMode from "../Components/ChooseMode/ChooseMode.svelte";
  import { afterUpdate } from "svelte";

  let mode = writable('Абсолютний рандом');

  const handleChoose = ({ currentTarget }) => {
    $mode = currentTarget.innerText;
  };
</script>

<main class="main">
  <div class="dropdown">
    <button class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
      {$mode}
    </button>
    <ul class="dropdown-menu">
      <li><button class="dropdown-item" on:click={handleChoose}>Абсолютний рандом</button></li>
      <li><button class="dropdown-item" on:click={handleChoose}>Оберу зі списку</button></li>
    </ul>
  </div>

  <section>
    {#if $mode === 'Абсолютний рандом'}
      <AutoMode />
    {:else if $mode === 'Оберу зі списку'}
      <ChooseMode />
    {/if}
  </section>
</main>

<style lang="scss">
  .main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    .dropdown {
      margin: 20px;
    }
  }
</style>