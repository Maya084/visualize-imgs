<script>
  let imageUrlJSON = '';
  let imageUrls = [];

  function visualizeImages() {
    try {
      imageUrls = JSON.parse(imageUrlJSON);
    } catch (error) {
      console.error('Invalid JSON format:', error);
      imageUrls = [];
    }
  }

</script>

<div class="json-input">
  <textarea
    bind:value={imageUrlJSON}
    placeholder="Enter JSON list of image URLs"
  ></textarea>
  <button on:click={visualizeImages}>Visualize Images</button>
</div>

<div class="custom-grid">
  {#each imageUrls as url (url)}
    <article>
      <img src={url} alt="Image" loading="lazy"/>
    </article>
  {/each}
</div>

<style>
  .custom-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  }

  main {
    padding: 1em;
  }
</style>

