<script>
  import { scale } from "svelte/transition";

  let dodosuko = [];

  const interval = setInterval(() => {
    dodosuko.push(getRandomInt(0, 2));
    const check = dodosuko.slice(dodosuko.length - 4 * 3, dodosuko.length);
    if (check.join("") === "011101110111") {
      dodosuko.push(2);
      clearInterval(interval);
    }
    dodosuko = dodosuko;
  }, 1);

  const getRandomInt = (min, max) => {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min) + min);
  };
</script>

<main>
  {#each dodosuko as v}
    {#if v === 0}<span in:scale>ドド</span>{/if}
    {#if v === 1}<span in:scale>スコ</span>{/if}
    {#if v === 2}<span in:scale class="love">ラブ注入♡</span>{/if}
  {/each}
</main>

<style>
  main {
    margin-bottom: 20vh;
  }
  .love {
    color: hotpink;
    font-weight: bold;
  }
</style>
