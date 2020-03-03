<script>
  export let photograph;
  import Modal from './Modal.svelte';

  let showModal = false;
</script>

<style>
    div {
        margin: 0;
    }
    .modal_img {
        height: 100%;
        width: 100%;
    }
</style>

<article class="art_piece">
  <div>
    <h3>Title: {photograph.title}</h3>
    <h3>Artist/Name: {photograph.people[0].displayname}</h3>
    <h3>Dated: {photograph.dated}</h3>
    <h3>Division: {photograph.division}</h3>
    <h3 class="url_link">{photograph.url}</h3>
  </div>
  <button on:click="{() => showModal = true}">
	See Larger Image
  </button>
  <img class="art" src={photograph.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={photograph.commentary || ""}>
</article>

{#if showModal}
	<Modal on:close="{() => showModal = false}">
		<img class="modal_img" src={photograph.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={photograph.commentary || ""}>
	</Modal>
{/if}
