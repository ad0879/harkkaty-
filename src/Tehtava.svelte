<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();
  let uusiTehtava = ''; // Uuden projektin nimi

  // Lähetä uuden projektin eteenpäin
  function lisaa() {
    if (uusiTehtava.trim() !== '') {
      dispatch('lisaaTehtava', uusiTehtava);
      uusiTehtava = '';
    }
  }
</script>

<div class="tehtava-lomake">
  <input
    type="text"
    placeholder="Syötä uusi projekti"
    bind:value={uusiTehtava}
  />
  <button on:click={lisaa}>Lisää</button>
</div>

<style>
  .tehtava-lomake {
    display: flex;
    gap: 20px;
    margin-bottom: 20px;
  }

  input {
    flex: 1;
    padding: 15px;
    font-size: 1.5rem;
    border: 2px solid #ccc;
    border-radius: 6px;
  }

  button {
    padding: 15px 25px;
    font-size: 1.5rem;
    background-color: #ff5733;
    color: white;
    border: none;
    border-radius: 6px;
    cursor: pointer;
  }

  button:hover {
    background-color: #ff784f;
  }
</style>
