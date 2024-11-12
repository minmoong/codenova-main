<script lang="ts">
  import { onMount } from 'svelte';
  import e1 from './Egypt1.jpg';
  import e2 from './Egypt2.jpg';
  import e3 from './Egypt3.jpg';
  import e4 from './Egypt4.jpg';

  // Set the interval time for image change in milliseconds
  const term = 1000; // 1000 ms = 1 second

  // Define the image array with the names of the images
  const images = [e1, e2, e3, e4];

  // State to manage the current image index
  let currentImage = 0;

  // Function to cycle through images
  function anigraphic() {
    currentImage = (currentImage + 1) % images.length;
  }

  // Start the slideshow on mount with a specified interval
  let interval: NodeJS.Timer;
  onMount(() => {
    interval = setInterval(anigraphic, term);
    return () => clearInterval(interval);
  });
</script>

<style>
  body {
    background-color: black;
    color: white;
    text-align: center;
  }
  h3 {
    font-size: 1.5rem;
  }
  img {
    max-width: 100%;
    height: auto;
  }
</style>

<h3>* 이집트를 감상합시다!!</h3>
<p>
  <!-- Display the current image -->
  <img src={images[currentImage]} alt="Egypt Image" />
</p>
