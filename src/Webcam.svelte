<script>
  let videoSource = null;
  let loading = false;
  const obtenerVideoCamara = async () => {
    try {
      loading = true;
      const stream = await navigator.mediaDevices.getUserMedia({
        video: true,
      });
      videoSource.srcObject = stream;
      videoSource.play();
      loading = false;
    } catch (error) {
      console.log(error);
    }
  };
</script>

<div>
  {#if loading}
    <h1>CARGANDO</h1>
  {/if}
  <!-- svelte-ignore a11y-media-has-caption -->
  <video bind:this={videoSource} />
  <button on:click={obtenerVideoCamara}>CLICK</button>
</div>
