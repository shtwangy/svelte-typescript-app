<script>
  export let url;
  export let title;
  const handleClick = async () => {
    try {
      await navigator.clipboard.writeText(`${title}\n${url}`);
      alert('copy success');
    } catch (err) {
      console.log('copy failed: ', err)
    }
  }
</script>

<div class="button-content">
    <button
      class="button"
      on:click={handleClick}
    >
      Copy
    </button>
</div>

<style>
.button-content {
    width: 100%;
    text-align: right;
}
.button {
    margin: 16px 8px 0 0;
    padding: 8px 16px;
    background-color: #dee7e6;
    color: #002227;
    border: none;
    border-radius: 4px;
}
</style>
