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
  }
	h1 {
    color: #109e6c;
		text-transform: uppercase;
		font-size: 4.3em;
    text-shadow: 5px 7px 7px #272727;
    margin: 1%;
  }
</style>

<main>
	  <h1>Svelte Gallery</h1>
	<SearchBar bind:search={searchQuery} handleSubmit={handleSubmit}/>
    <Nav />
</main>
