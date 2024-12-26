<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();
  // Suosituimmat projektit
  const suositutTehtavat = [
    'Benji-hyppy',
    'Lue 100 kirjaa',
    'Laskuvarjohyppy',
    'Matkusta',
    'Opi koodaamaan',
  ];

  // Lähettää valitun tehtävän App.svelte:lle
  function lisaaTehtava(tehtava) {
    dispatch('lisaaSuosittu', tehtava); // Lähetetään pelkkä nimi
  }
</script>

<div class="suosituimmat-valikko">
  <h2>Suosituimmat projektit</h2>
  <ul>
    {#each suositutTehtavat as tehtava}
      <li>
        <button on:click={() => lisaaTehtava(tehtava)}>
          {tehtava}
        </button>
      </li>
    {/each}
  </ul>
</div>

<style>
  .suosituimmat-valikko {
    background: transparent;
    color: white;
    border: 1px solid #444;
    border-radius: 5px;
    padding: 15px;
    margin: 10px auto;
    width: 300px;
  }

  h2 {
    font-size: 1.5rem;
    margin-bottom: 10px;
  }

  ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  li {
    margin: 5px 0;
  }

  button {
    background-color: #ffbd33;
    color: black;
    border: none;
    padding: 8px 12px;
    border-radius: 4px;
    cursor: pointer;
    width: 100%;
  }

  button:hover {
    background-color: #ffdb80;
  }
</style>
