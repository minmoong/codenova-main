<script>
  import { onMount } from 'svelte';
  let d = '';
  let results = [];

  function generateTable() {
    // 문자열이 숫자로 변환 가능한지 확인
    const number = parseInt(d);
    if (isNaN(number)) {
      alert('숫자를 입력해주세요.');
      return;
    }
    results = [];
    for (let j = 1; j <= 9; j++) {
      results.push(`${number} * ${j} = ${number * j}`);
    }
  }
</script>

<h3>구구단을 입력하세요</h3>
<input bind:value={d} placeholder="구구단 단수 입력" />
<button on:click={generateTable}>구구단 출력</button>

{#if results.length > 0}
  <h3>당신이 입력한 {d}단입니다</h3>
  <div>
    {#each results as result}
      <p>{result}</p>
    {/each}
  </div>
{/if}
