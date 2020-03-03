<script>
  export let coin;
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
    <h3>Title: {coin.title}</h3>
    <h3>Dated: {coin.dated}</h3>
    <h3>Division: {coin.division}</h3>
    <h3 class="url_link">{coin.url}</h3>
  </div>
  <img class="art" src={coin.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={coin.commentary || ""}>
</article>
{#if showModal}
	<Modal on:close="{() => showModal = false}">
		<img class="modal_img" src={coin.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={coin.commentary || ""}>
	</Modal>
{/if}
