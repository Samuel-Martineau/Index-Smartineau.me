<script>
  export let url = '';
  export let title = '';
  export let collab = '';
  export let description = '';
</script>

<style lang="scss">
  a {
    color: initial;
    text-decoration: none;
  }

  div {
    width: 100%;
    border-style: solid;
    border-radius: 7px;
    border-width: 1px;
    border-color: #f8f0e7;
    padding: 10px;
    box-shadow: 5px 5px 5px #f0dbc7;
    background-color: #f8f0e7;
    transition: transform 0.2s;

    h2 {
      transition: color 0.5s;
      font-weight: 100;
      font-size: 1.7rem;
    }

    p {
      font-size: 1.2rem;
    }

    small {
      color: gray;
    }

    &:hover {
      cursor: pointer;
      transform: translateY(-5px);
      box-shadow: 8px 8px 5px #f0dbc7;

      h2 {
        text-decoration: underline;
        color: #6166fa;
      }
    }
  }
</style>

<a href={url}>
  <div>
    <h2>{title}</h2>
    <p>{description}</p>
    {#if collab}
      <small>En collaboration avec {collab}</small>
    {/if}
  </div>
</a>
