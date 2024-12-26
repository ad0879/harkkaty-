<script>
  import Tehtava from './Tehtava.svelte';
  import Lista from './Lista.svelte';
  import Suositut from './Suosituimmat.svelte';

  let tehtavat = []; // Lista projekteista
  let naytaSuositut = false; // Suosituimmat valikon tila

  // Uuden projektin lisääminen
  function lisaaTehtava(event) {
    tehtavat = [...tehtavat, { nimi: event.detail, valmis: false }];
  }

  // Projektin lisääminen suosituista
  function lisaaSuosittu(nimi) {
    tehtavat = [...tehtavat, { nimi, valmis: false }];
    naytaSuositut = false; // Suositut-valikon sulku
  }

  // Projektin tilan vaihtaminen (suoritettu tai ei)
  function vaihdaTila(index) {
    tehtavat = tehtavat.map((tehtava, i) =>
      i === index ? { ...tehtava, valmis: !tehtava.valmis } : tehtava
    );
  }
</script>

<main>
  <div class="header">
    <h1>Bucket-List</h1>
    <button
      class="suosituimmat-nappula"
      on:click={() => (naytaSuositut = !naytaSuositut)}
    >
      Suosituimmat
    </button>
  </div>

  {#if naytaSuositut}
    <Suositut on:lisaaSuosittu={(event) => lisaaSuosittu(event.detail)} />
  {/if}

  <!-- Projektin lisääminen -->
  <Tehtava on:lisaaTehtava={lisaaTehtava} />

  <!-- Lista projekteista -->
  <Lista {tehtavat} on:vaihdaTila={vaihdaTila} />
</main>

<style>
  main {
    font-family: Arial, sans-serif;
    text-align: center;
    margin: 2rem auto;
    width: 600px;
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  h1 {
    color: #ff5733;
    font-size: 5rem;
  }

  .suosituimmat-nappula {
    padding: 10px 15px;
    background-color: #ffbd33;
    color: black;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1rem;
  }
</style>
