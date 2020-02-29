<script>
  export let search;
  export let handleSubmit;
  // export this functions from App
</script>

<style>
  .search-input {
    width: 100%;
    max-width: 800px;
    border-radius: 4px;
    border: 1px solid #ccc;
    padding: 10px 20px;
    font-size: 1.7em;
    margin-bottom: 50px;
  }

  .search_btn {
    background: grey;
    color: #333;
    font-size: 1.7em;
    border: none;
    cursor: pointer;
    outline: none;
  }

  .search_btn:hover {
    opacity: 0.8;
    transition: opacity 0.2s ease-in;
  }

</style>

<div class="search">
  <form class="search-form">
    <input bind:value={search} class="search-input" type="search"
    placeholder="Search Artwork by Name" />
    <button class="search_btn" on:submit|preventDefault={handleSubmit}>Search</button>
  </form>
</div>