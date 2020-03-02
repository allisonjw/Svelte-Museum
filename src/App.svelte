<script>
	import SearchBar from './SearchBar.svelte';
  import Nav from './Nav.svelte';

    let searchQuery = '';
    let searchTerm = null;
    let totalPages = null;
    let searchResults = [];
    let nextPage = 1;
    let isLoading = false;

    const handleSubmit = (e) => {
      e.preventDefault()
      searchResults = [];
    }
</script>

<style>
	main {
    margin: auto;
    overflow: hidden;
    padding: 1em;
	}

	h1 {
		color: #00ffa6;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 200;
  }
</style>

<main>
	<h1>Svelte Gallery</h1>
	<SearchBar bind:search={searchQuery} handleSubmit={handleSubmit}/>
  <Nav />
</main>