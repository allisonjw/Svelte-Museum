<script>
export let drawing;
</script>

<style>
    div {
        margin: 0;
    }
</style>

<article class="art_piece">
  <div>
    <h3>Title: {drawing.title}</h3>
    <h3>Artist/Name: {drawing.people[0].displayname}</h3>
    <h3>Dated: {drawing.dated}</h3>
    <h3>Division: {drawing.division}</h3>
    <h3 class="url_link">{drawing.url}</h3>
  </div>
  <img class="art" src={drawing.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={drawing.commentary || ""}>
</article>

