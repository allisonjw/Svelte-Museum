<script>
	import SearchBar from './SearchBar.svelte';
  import Artwork from './Artwork.svelte';
  import { onMount } from 'svelte';	

    let searchQuery = '';
    let searchTerm = null;
    let totalPages = null;
    let searchResults = [];
    let nextPage = 1;
    let isLoading = false;
    let artworks = [];

    const handleSubmit = (e) => {
      e.preventDefault()
      searchResults = [];
    }
  
  // http://api.harvardartmuseums.org/object?classification=Photographs&apikey=fb6b7390-5a53-11ea-b877-8f943796feb8&size=100
    const apiKey = 'apikey=fb6b7390-5a53-11ea-b877-8f943796feb8';
    const baseUrl = 'https://api.harvardartmuseums.org/object?classification=';
    const endpoint = `${baseUrl}Photographs&${apiKey}&size=30`;

    onMount(async() => {
      const res = await fetch(endpoint);
      let result = await res.json()
      artworks = result.records
    });

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
		font-weight: 100;
  }
  section {
    list-style: none;
    display: grid;
    gap: 40px 20px;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  }
</style>

<main>
	<h1>Gallery</h1>
	<SearchBar bind:search={searchQuery} handleSubmit={handleSubmit}/>
  <section>
  {#each artworks as artwork (artwork.id)}
    <Artwork artwork={artwork} />
  {/each}
  </section>
</main>