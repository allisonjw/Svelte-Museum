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
		color: #109e6c;
		text-transform: uppercase;
		font-size: 6em;
    text-align: center;
    text-shadow: 5px 7px 7px #272727;
    margin: 3%;
  }
</style>

<main>
	<h1>Svelte Gallery</h1>
	<SearchBar bind:search={searchQuery} handleSubmit={handleSubmit}/>
  <Nav />
</main>