<script>
export let photograph
</script>

<style>
    .art_piece {
        background-color: #00ffa6;
    }
    div {
        margin: 0;
    }
</style>

<article class="art_piece">
  <div>
    <h3>Title: {photograph.title}</h3>
    <h3>Dated: {photograph.dated}</h3>
    <h3>Division: {photograph.division}</h3>
    <h3 class="url_link">{photograph.url}</h3>
  </div>
  <img class="art" src={photograph.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={photograph.commentary || ""}>
</article>