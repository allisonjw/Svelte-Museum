<script>
export let painting;
</script>

<style>
    .art_piece {
        background-color: palegoldenrod;
    }
    div {
        margin: 0;
    }
</style>

<article class="art_piece">
  <div>
    <h3>Title: {painting.title}</h3>
    <h3>Dated: {painting.dated}</h3>
    <h3>Division: {painting.division}</h3>
    <h3 class="url_link">{painting.url}</h3>
  </div>
  <img class="art" src={painting.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={painting.commentary || ""}>
</article>