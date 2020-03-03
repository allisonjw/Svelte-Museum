<script>
  export let search;
  export let handleSubmit;
  // export this functions from App
</script>

<style>
  form {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
  input {
    width: 100%;
    max-width: 40%;
    border-radius: 4px;
    border: 1px solid rgb(131, 131, 131);
    padding: 10px 20px;
    font-size: 1.3em;
  }
  button {
    background: grey;
    color: #333;
    font-size: 1.3em;
    border: none;
    cursor: pointer;
    outline: none;
  }
  button:hover {
    opacity: 0.8;
    transition: opacity 0.2s ease-in;
    transform: scale(1.1);
    transition: all .1s ease-in-out;
  }
</style>

<div class="search">
  <form>
    <input bind:value={search} type="search"
    placeholder="Search Artwork by Name" />
    <button on:submit|preventDefault={handleSubmit}>Search</button>
  </form>
</div>