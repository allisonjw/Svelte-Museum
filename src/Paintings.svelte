<script>
export let painting;
</script>

<article class="art_piece">
  <h3>Title: {painting.title}</h3>
  <h3>Dated: {painting.dated}</h3>
  <h3>Division: {painting.division}</h3>
  <h3 class="url_link">{painting.url}</h3>
  <img class="art" src={painting.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={painting.commentary || ""}>
</article>