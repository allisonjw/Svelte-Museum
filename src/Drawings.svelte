<script>
  export let drawing;
  import Modal from './Modal.svelte';

  let showModal = false;
</script>

<style>    div {
        margin: 0;
        display: flex;
        flex-direction: column;
        align-items: normal;
    }
    h3 {
        margin: 2px;
    }
    .modal_img {
        height: 100%;
        width: 100%;
    }
    button {
        background-color: #109e6c;
        color: #333;
        width: 50%;
        border: 1px solid gray;
        border-radius: 3px;
        font-size: 1.2em;
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
    <h3>Title: {drawing.title}</h3>
    <h3>Artist/Name: {drawing.people[0].displayname}</h3>
    <h3>Dated: {drawing.dated}</h3>
    <h3>Division: {drawing.division}</h3>
    <h3 class="url_link">{drawing.url}</h3>
  </div>
  <img class="art" src={drawing.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={drawing.commentary || ""}>
</article>
{#if showModal}
	<Modal on:close="{() => showModal = false}">
		<img class="modal_img" src={drawing.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={drawing.commentary || ""}>
	</Modal>
{/if}

