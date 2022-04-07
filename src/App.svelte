<script>
  const min = 0;
  const max = 999999;

  let hinta = 0;
  let alennus = 25;
  let lopullinenHinta;

  $: if (hinta >= min && hinta <= max) {
    lopullinenHinta = (hinta - (hinta * alennus) / 100).toFixed(2);
  } else {
    hinta = min;
  }
</script>

<main>
  <h1>ALE-laskuri</h1>

  <label for="hinta">Hinta</label>
  <input id="hinta" type="number" min="0" max="999999" bind:value={hinta} />

  <label for="alennus">Alennus</label>
  <input
    id="alennus"
    type="range"
    min="0"
    max="100"
    step="1"
    bind:value={alennus}
  />

  <p>Ale-prosentti: <b>{alennus} %</b></p>

  <p>
    {#if hinta}
      Alennettu hinta: <b>{lopullinenHinta}</b>
    {:else}
      Ei hintaa
    {/if}
  </p>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
