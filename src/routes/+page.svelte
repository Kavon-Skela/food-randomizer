<script>
  import { writable } from "svelte/store";
  import AutoMode from "../Components/AutoMode/AutoMode.svelte";

  let mode = writable('Абсолютний рандом');
</script>

<main class="main">
  <h3 class="main__title">Абсолютний рандом</h3>

  <section>
      <AutoMode />
  </section>
</main>

<style lang="scss">
  .main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    &__title {
      margin-top: 40px;
    }
  }
</style>