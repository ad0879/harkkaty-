<script>
  export let teksti = ''; // Nappiin tuleva teksti
  export let onClick = () => {}; // Klikkaustapahtuma
</script>

<button on:click={onClick}>
  {teksti}
</button>

<style>
  button {
    padding: 5px 10px;
    background-color: #ff4d4d;
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 4px;
  }

  button:hover {
    background-color: #e60000;
  }
</style>
