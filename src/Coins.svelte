<script>
export let coin;
</script>
<style>
    div {
        margin: 0;
    }
</style>

<article class="art_piece">
  <div>
    <h3>Title: {coin.title}</h3>
    <h3>Dated: {coin.dated}</h3>
    <h3>Division: {coin.division}</h3>
    <h3 class="url_link">{coin.url}</h3>
  </div>
  <img class="art" src={coin.primaryimageurl || "https://homestaymatch.com/images/no-image-available.png"} alt={coin.commentary || ""}>
</article>