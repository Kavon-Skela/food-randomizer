<script>
  import { afterUpdate } from "svelte";
  import { writable } from "svelte/store";
  import { slide } from "svelte/transition";

  let food = [
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
  $: chosenMeals = [];

  const handleChoose = () => {
    const length = chosenMeals.length;
    $chosen = chosenMeals[Math.floor(Math.random() * length)];
  };
</script>

<article class="article" transition:slide>
  <select class="form-select" multiple aria-label="Multiple select example">
    {#each food as type}
      <option value={type} on:click={() => {
        if (chosenMeals.includes(type)) {
          chosenMeals = chosenMeals.filter(item => item !== type);

          return;
        } else {
          chosenMeals.push(type);
        }
      }}
      >{type}</option>
    {/each}
  </select>

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
      margin-top: 20px;
    }

    .form-select {
      height: 400px;
      width: 200px;
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