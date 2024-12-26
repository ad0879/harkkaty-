<script>
  import { createEventDispatcher } from 'svelte';
  import { scale } from 'svelte/transition';

  export let tehtavat = []; // Tehtävien lista
  const dispatch = createEventDispatcher();

  // Lähettää tapahtuman tehtävän tilan vaihtamiseksi
  function vaihda(index) {
    dispatch('vaihdaTila', index);
  }
</script>

<!--Ei projekteja teksti näkyy jos yhtään projektia ei ole luotu-->
{#if tehtavat.length > 0}
  <ul>
    {#each tehtavat as tehtava, index}
      <li in:scale={{ duration: 400 }}>
        <label>
          <!-- Tehtävän suoritustilan vaihtaminen checkboxilla -->
          <input
            type="checkbox"
            checked={tehtava.valmis}
            on:change={() => vaihda(index)}
          />
          {tehtava.nimi}
        </label>
      </li>
    {/each}
  </ul>
{:else}
  <p class="empty">Ei projekteja</p>
{/if}

<style>
  ul {
    list-style: none;
    padding: 0;
  }

  li {
    margin-bottom: 10px;
    display: flex;
    align-items: center;
  }

  label {
    display: flex;
    gap: 10px;
    align-items: center;
    font-size: 2rem;
    color: #fcfcfc;
  }

  input[type='checkbox'] {
    /*perusnäkymä*/
    width: 30px;
    height: 30px;
    appearance: none; /* Poistaa selaimen oletustyylin */
    border: 2px solid #999;
    border-radius: 4px;
    cursor: pointer;
  }

  input[type='checkbox']:checked {
    /* Kun checkbox on valittu */
    background-color: #28a745;
    border-color: #28a745;
  }

  input[type='checkbox']:checked::before {
    content: '✔'; /* Check-merkki */
    display: block;
    color: white;
    font-size: 30px;
    text-align: center;
    line-height: 25px;
  }

  .empty {
    font-size: 1.5rem;
    font-style: italic;
    color: #888;
    text-align: center;
  }
</style>
