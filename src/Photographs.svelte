<script>
export let photograph
</script>

<article class="art_piece">
  <h3>Title: {photograph.title}</h3>
  <h3>Dated: {photograph.dated}</h3>
  <h3>Division: {photograph.division}</h3>
  <h3 class="url_link">{photograph.url}</h3>
  <img class="art" src={photograph.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={photograph.commentary || ""}>
</article>