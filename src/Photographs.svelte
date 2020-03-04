<script>
  export let photograph;
  import Modal from './Modal.svelte';

  let showModal = false;
</script>

<style>
    h3 {
        margin: 4px;
    }
    .modal_img {
        height: 100%;
        width: 100%;
    }
    button {
        background-color: #109e6c;
        color: #333;
        border: 1px solid gray;
        border-radius: 3px;
        font-size: 1.2em;
    }
    button:hover {
        opacity: 0.8;
        transform: scale(.95);
        transition: all .1s ease-in-out;
    }
</style>
<article class="art_piece">
    <h3>Type: Photograph</h3>
    <h3>Title: {photograph.title}</h3>
    <h3>Artist/Name: {photograph.people[0].displayname}</h3>
    <h3>Dated: {photograph.dated}</h3>
    <h3>Division: {photograph.division}</h3>
    <h3 class="url_link">{photograph.url}</h3>
  <button on:click="{() => showModal = true}">
	See Full Size Image
  </button>
  <img class="art" src={photograph.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={photograph.commentary || ""}>
</article>
{#if showModal}
	<Modal on:close="{() => showModal = false}">
		<img class="modal_img" src={photograph.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={photograph.commentary || ""}>
	</Modal>
{/if}
