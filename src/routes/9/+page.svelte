<script lang="ts">
  import { onMount } from 'svelte';
  import i1 from './1.jpg';
  import i2 from './2.jpg';
  import i3 from './3.jpg';
  import i4 from './4.jpg';

  // Set the interval time for image change in milliseconds
  const term = 2500; // 1000 ms = 1 second

  // Define the image array with the names of the images
  const images = [i2, i1, i4, i3];

  // State to manage the current image index
  let currentImage = 0;

  // Function to cycle through images
  function anigraphic() {
    currentImage = (currentImage + 1) % images.length;
  }

  // Start the slideshow on mount with a specified interval
  let interval: any;
  onMount(() => {
    interval = setInterval(anigraphic, term);
    return () => clearInterval(interval);
  });
</script>

<style>
  h2 {
    font-size: 1.5rem;
    margin-bottom: 20px;
  }
  img {
    max-width: 100%;
    height: auto;
  }
</style>

<h2>활동 사진</h2>
<div>
  <img src={images[currentImage]} alt="activity image" width="720" />
</div>
