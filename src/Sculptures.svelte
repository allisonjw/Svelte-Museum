<script>
export let sculpture;
</script>

<article class="art_piece">
  <h3>Title: {sculpture.title}</h3>
  <h3>Dated: {sculpture.dated}</h3>
  <h3>Division: {sculpture.division}</h3>
  <h3 class="url_link">{sculpture.url}</h3>
  <img class="art" src={sculpture.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={sculpture.commentary || ""}>
</article>