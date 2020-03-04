<script>
  export let painting;
  import Modal from './Modal.svelte';

  let showModal = false;
</script>

<style>    
    h3 {
        margin: 4px;
        color: #ffffffc2;
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
    <h3>Type: Painting</h3>
    <h3>Title: {painting.title}</h3>
    <h3>Dated: {painting.dated}</h3>
    <h3>Division: {painting.division}</h3>
    <h4 class="url_link">{painting.url}</h4>
  <button on:click="{() => showModal = true}">
	See Full Size Image
  </button>
  <img class="art" src={painting.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={painting.commentary || ""}>
</article>
{#if showModal}
	<Modal on:close="{() => showModal = false}">
		<img class="modal_img" src={painting.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={painting.commentary || ""}>
	</Modal>
{/if}