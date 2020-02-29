<script>
	import SearchBar from './SearchBar.svelte';
	import Artwork from './Artwork.svelte';

const apiKey = '?apikey=fb6b7390-5a53-11ea-b877-8f943796feb8';
const baseUrl = 'https://api.harvardartmuseums.org/classification/';
	

  let searchQuery = '';
  let searchTerm = null;
  let totalPages = null;
  let searchResults = [];
  let nextPage = 1;
  let isLoading = false;

  function handleSubmit() {
    searchTerm = searchQuery.trim();
    searchResults = [];
    totalPages = null;
    nextPage = 1;

    if (!searchTerm) return;

    searchUnsplash();
  }

  function searchUnsplash() {
    isLoading = true;

    const endpoint =
      `${baseUrl}17${apiKey}`;

    fetch(endpoint)
      .then(response => {
        if (!response.ok) {
          throw Error(response.statusText);
        }
        return response.json();
      })
      .then(data => {
        if (data.total === 0) {
          alert("No photos were found for your search query.")
          return;
        }

        searchResults = [...searchResults, ...data.results];
        totalPages = data.total_pages;

        if (nextPage < totalPages) {
          nextPage += 1;
        }
      })
      .catch(() => alert("An error occured!"))
      .finally(() => {
        isLoading = false;
      });
  }
</script>


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #00ffa6;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
</style>

<main>
	<h1>Gallery</h1>
	<SearchBar />
	<Artwork />

</main>