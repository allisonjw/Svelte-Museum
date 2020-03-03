<script>
  export let photograph;
  import Modal from './Modal.svelte';

  let showModal = false;
</script>

<style>
    div {
        margin: 0;
        display: flex;
        flex-direction: column;
        align-items: normal;
    }
    h4 {
        margin: 2px;
    }
    .modal_img {
        height: 100%;
        width: 100%;
    }
    button {
        background-color: grey;
        color: #333;
        width: 50%;
        border: 1px solid gray;
        /* margin: auto; */
    }
    button:hover {
        opacity: 0.8;
        transform: scale(1.1);
        transition: all .1s ease-in-out;
    }
</style>

<article class="art_piece">
  <button on:click="{() => showModal = true}">
	See Larger Image
  </button>
  <div>
    <h4>Title: {photograph.title}</h4>
    <h4>Artist/Name: {photograph.people[0].displayname}</h4>
    <h4>Dated: {photograph.dated}</h4>
    <h4>Division: {photograph.division}</h4>
    <h4 class="url_link">{photograph.url}</h4>
  </div>
  <img class="art" src={photograph.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={photograph.commentary || ""}>
</article>
{#if showModal}
	<Modal on:close="{() => showModal = false}">
		<img class="modal_img" src={photograph.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={photograph.commentary || ""}>
	</Modal>
{/if}
