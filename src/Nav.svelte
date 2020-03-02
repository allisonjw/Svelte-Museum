<script>
  import { onMount } from 'svelte';	
  import Photographs from './Photographs.svelte';
  import Paintings from './Paintings.svelte';
  import Sculptures from './Sculptures.svelte';
  import Jewelry from './Jewelry.svelte';

let photographs = [];
let paintings = [];
let sculptures = [];
let jewelry = [];
export let menu = 1;

const apiKey = 'apikey=fb6b7390-5a53-11ea-b877-8f943796feb8';
const baseUrl = 'https://api.harvardartmuseums.org/object?classification=';
const photoEndpoint = `${baseUrl}Photographs&Century=21st&${apiKey}&size=16`;
const paintingEndpoint = `${baseUrl}Paintings&${apiKey}&size=16`;
const sculptureEndpoint = `${baseUrl}Sculpture&${apiKey}&size=16`;
const jewelryEndpoint = `${baseUrl}Jewelry&${apiKey}&size=16`;

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
$: console.log('paintings', paintings)

onMount(async() => {
    const res = await fetch(sculptureEndpoint);
    let result = await res.json()
    sculptures = result.records
});
$: console.log('sculptures', sculptures)

onMount(async() => {
    const res = await fetch(jewelryEndpoint);
    let result = await res.json()
    jewelry = result.records
});
$: console.log('jewelry', jewelry)


</script>

<style>
  section {
    list-style: none;
    display: grid;
    gap: 40px 20px;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  }
  ul#menu li{
    display : inline;
  }
</style>

<ul id="menu">
	<li><a href="/" on:click|preventDefault={() => (menu = 1)}>Photgraphs</a></li> |
	<li><a href="/" on:click|preventDefault={() => (menu = 2)}>Paintings</a></li> | 
    <li><a href="/" on:click|preventDefault={() => (menu = 3)}>Sculptures</a></li> |
	<li><a href="/" on:click|preventDefault={() => (menu = 4)}>Jewelry</a></li>
</ul>
<section>
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
<h3>Navbar</h3>
