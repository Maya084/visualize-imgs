<script lang="ts">
  let imageUrlJSON:string  = "";
  let imageUrls: string[] = [];

  function visualizeImages() {
    try {
      imageUrls = JSON.parse(imageUrlJSON);
    } catch (error) {
      alert(`Invalid JSON format: ${error}`);
      imageUrls = [];
    }
  }
</script>
<main>

<div class="json-input">
  <textarea
    bind:value={imageUrlJSON}
    placeholder="Enter JSON list of image URLs"
  />
  <button on:click={visualizeImages}>Visualize Images</button>
</div>

<div class="custom-grid">
  {#each imageUrls as url (url)}
    <article>
      <img src={url} alt="Image" loading="lazy" />
    </article>
  {/each}
</div>
</main>

<style>
  .custom-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  }

  main {
    padding: 1em;
  }

  article{
    height: fit-content;
  }
</style>
