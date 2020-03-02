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
</style>

<h3>Navbar</h3>
<section>
  {#each photographs as photograph (photograph.id)}
    <Photographs photograph={photograph} />
  {/each}
</section>
<!-- <section>
  {#each paintings as painting (painting.id)}
    <Paintings painting={painting} />
  {/each}
</section> -->
<!-- <section>
  {#each sculptures as sculpture (sculpture.id)}
    <Sculptures sculpture={sculpture} />
  {/each}
</section> -->
<!-- <section>
  {#each jewelry as jewelry (jewelry.id)}
    <Jewelry jewelry={jewelry} />
  {/each}
</section> -->
