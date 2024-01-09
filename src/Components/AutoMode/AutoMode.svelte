<script>
  import { writable } from "svelte/store";
  import { slide } from "svelte/transition";

  const food = [
    'Суші',
    'Піцу',
    'Мак',
    'КФС',
    'Шашлик',
    'Хінкалі',
    'Хачапурі',
    'Шаурму',
    'Піту',
    'Пузату',
    'Китайську',
    'Салатік',
    'Хот дог',
    'Веганська їжу',
    'Пасту',
    'Морепродукти',
    'Сендвіч',
    'Кебаб',
    'Круасани',
    'Поке',
    'Пельмені',
    'Вареники',
    'Тако',
    'Млинці',
    'Ребра',
    'Кебаб',
  ];

  let chosen = writable('');

  const handleChoose = () => {
    $chosen = food[Math.floor(Math.random() * 26)]
  }
</script>

<article class="article" transition:slide>
  <button class="btn btn-secondary" type="button" on:click={handleChoose}>
    Поїхали
  </button>
  {#if $chosen}
  <span class="article__chosen" transition:slide>
    Будете жерти - {$chosen}
  </span>
  {/if}
</article>

<style lang="scss">
  .article {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    .btn {
      max-width: 200px;
    }

    &__chosen {
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 10px;
      margin: 20px;
      max-width: 350px;
      border: 1px groove black;
      padding: 10px;
    }
  }
</style>