<script>
  import { onMount } from 'svelte';	
  import SearchBar from './SearchBar.svelte';
  import Photographs from './Photographs.svelte';
  import Paintings from './Paintings.svelte';
  import Sculptures from './Sculptures.svelte';
  import Jewelry from './Jewelry.svelte';
  import Coins from './Coins.svelte';
  import Drawings from './Drawings.svelte'
  import { fly } from 'svelte/transition';

let photographs = [];
let paintings = [];
let sculptures = [];
let jewelry = [];
let drawings = [];
let coins = [];
export let menu = 1;

const apiKey = 'apikey=fb6b7390-5a53-11ea-b877-8f943796feb8';
const baseUrl = 'https://api.harvardartmuseums.org/object?classification=';
const photoEndpoint = `${baseUrl}Photographs&${apiKey}&size=16&page=14&sort=&sortorder=ASC`;
const paintingEndpoint = `${baseUrl}Paintings&Century=21&${apiKey}&size=16&page=1`;
const sculptureEndpoint = `${baseUrl}Sculpture&${apiKey}&size=16&page=9`;
const jewelryEndpoint = `${baseUrl}Jewelry&${apiKey}&size=16&page=4&sort=&sortorder=ASC`;
const drawingEndpoint = `${baseUrl}Drawings&${apiKey}&size=16&page=1`;
const coinEndpoint = `${baseUrl}Coins&${apiKey}&size=16&page=1`;


onMount(async() => {
    const res = await fetch(photoEndpoint);
    let result = await res.json()
    photographs = result.records
});

onMount(async() => {
    const res = await fetch(paintingEndpoint);
    let result = await res.json()
    paintings = result.records
});

onMount(async() => {
    const res = await fetch(sculptureEndpoint);
    let result = await res.json()
    sculptures = result.records
});

onMount(async() => {
    const res = await fetch(jewelryEndpoint);
    let result = await res.json()
    jewelry = result.records
});

onMount(async() => {
    const res = await fetch(drawingEndpoint);
    let result = await res.json()
    drawings = result.records
});
$: console.log('drawings', drawings)

onMount(async() => {
    const res = await fetch(coinEndpoint);
    let result = await res.json()
    coins = result.records
});
$: console.log('coins', coins)

let searchQuery = '';
let searchResults = []

    // $: filteredArtwork = seachQuery
		// ? artwork.filter(art => {
		// 	const title = `${art.title}`;
		// 	return title.toLowerCase().startsWith(seachQuery.toLowerCase());
		// })
    // : artwork;

    // const displayArtsSearch = (searchQuery) => {
    //   return artworks.filter((artwork) => artwork.title.toLowerCase().includes(searchQuery));
    // }

    const handleSubmit = (e, seachQuery) => {
      e.preventDefault()
      return photographs.find((artwork) => artwork.title.toLowerCase().includes(searchQuery));

    }
</script>

<style>
section {
    list-style: none;
    display: grid;
    gap: 40px 20px;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  }
  li {
    display : inline;
    font-size: 1.5em;
    font-weight: 700;
  }
    a {
    color: #707976;
    /* text-shadow: 2px 3px 2px #101010d1; */
  }
  a:hover {
    color: #109e6c;
  }
  div {
      display: flex;
      flex-direction: row;
      justify-content: center;
      align-items: center;
  }
</style>

<div>
    <ul>
        <li><a href="/" on:click|preventDefault={() => (menu = 1)}>Photographs</a></li> |
        <li><a href="/" on:click|preventDefault={() => (menu = 2)}>Paintings</a></li> | 
        <li><a href="/" on:click|preventDefault={() => (menu = 3)}>Sculptures</a></li> |
        <li><a href="/" on:click|preventDefault={() => (menu = 4)}>Jewelry</a></li>
    </ul>
</div>

<SearchBar bind:search={searchQuery} handleSubmit={handleSubmit}/>
<section in:fly={{ y: 300, duration: 2000 }}>
    {#if menu === 1}
    {#each photographs as photograph (photograph.id)}
        <Photographs photograph={photograph} />
    {/each}
    {:else if menu === 2}
    {#each paintings as painting (painting.id)}
        <Paintings painting={painting} />
    {/each}
    {:else if menu === 3}
    {#each sculptures as sculpture (sculpture.id)}
        <Sculptures sculpture={sculpture} />
    {/each}
    {:else if menu === 4}
    {#each jewelry as jewelry (jewelry.id)}
        <Jewelry jewelry={jewelry} />
    {/each}
    {:else}  
    <h1>
        Page Not Found
    </h1>
    {/if}
</section>