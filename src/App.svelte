<script>
  import { fade } from 'svelte/transition';
  import WebsiteCard from './WebsiteCard.svelte';
  import Spinner from 'svelte-spinner';

  async function getWebsites() {
    const res = await fetch('/websites.json', { cache: 'reload' });
    const websites = (await res.json()).websites;
    return websites;
  }
</script>

<style lang="scss" global>
  * {
    margin: 0;
    padding: 0;
    font-family: 'Comic Sans MS', sans-serif;
  }

  body {
    background-color: #faf5ef;
  }

  ::-webkit-scrollbar {
    display: none;
  }

  .title {
    text-align: center;
    margin: 5px 0;
    margin-top: 15px;
  }

  #title {
    margin-top: 15px;
    font-size: 2.5rem;
  }

  #subtitle {
    font-size: 1.9rem;
  }

  #grid {
    margin: 15px;
    margin-bottom: 30px;
    .box {
      margin: 15px 0;
      width: calc(100vw - 54px);
    }
  }

  #spinner {
    width: 100vw;
    text-align: center;
  }
</style>

<svelte:head>
  <title>Smartineau.me</title>
</svelte:head>

<h1 class="title" id="title">Smartineau.me</h1>
<h2 class="title" id="subtitle">Index des sites web hébergés</h2>
{#await getWebsites()}
  <div id="spinner">
    <Spinner
      id="spinner"
      size="100"
      speed="750"
      color="#ff9d00"
      thickness="2"
      gap="40" />
  </div>
{:then websites}
  <div id="grid">
    {#each websites as website}
      <div class="box" in:fade>
        <WebsiteCard {...website} />
      </div>
    {/each}
  </div>
{/await}
