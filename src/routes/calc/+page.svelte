<script>
  import { onMount } from 'svelte';
  import { writable } from 'svelte/store';
  let content = writable('');

  onMount(async () => {
    const response = await fetch('/work1.htm');
    const arrayBuffer = await response.arrayBuffer();
    const decoder = new TextDecoder('euc-kr');
    const html = decoder.decode(arrayBuffer);
    content.set(html);
  });
</script>

<div>
  {@html $content}
</div>