<script>
export let artwork
</script>

<style>
    .art_piece {
        animation: show 0.5s forwards ease-in-out;
        background-color: #00ffa6;
        padding: .7em;
    }

    @keyframes show {
        0% {
        opacity: 0;
        transform: translateY(100px);
        }
        100% {
        opacity: 1;
        transform: translateY(0);
        }
    }

    .artwork {
        width: 100%;
        object-fit: cover;
        height: 300px;
        background-color: #ccc;
        margin-bottom: 10px;
    }
    .url_link {
        overflow: scroll;
        color: blue;
    }

    .url_link:hover {
        text-decoration: underline;
        color: cornflowerblue;
    }
</style>


<article class="art_piece">
  <h3>Title: {artwork.title}</h3>
  <h3>Dated: {artwork.dated}</h3>
  <h3>Culture: {artwork.culture}</h3>
  <!-- <h3>{artwork.title}</h3> -->
  <h3 class="url_link">{artwork.url}</h3>
  <img class="artwork" src={''} alt={artwork.commentary || ""}>
  
</article>