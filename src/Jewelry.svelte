<script>
export let jewelry;
</script>

<style>
    div {
        margin: 0;
    }
</style>

<article class="art_piece">
  <div>
    <h3>Title: {jewelry.title}</h3>
    <h3>Dated: {jewelry.dated}</h3>
    <h3>Division: {jewelry.division}</h3>
    <h3 class="url_link">{jewelry.url}</h3>
  </div>
  <img class="art" src={jewelry.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={jewelry.commentary || ""}>
</article>