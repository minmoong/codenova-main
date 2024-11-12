<script lang="ts">
  import { onMount } from 'svelte';

  // State to manage the currently visible quote
  let nowDiv = 0;

  // Quotes array for display
  const quotes = [
    "",
    `진정한 천재란, 비범한 일을 수행하는 능력을 가진 자가 아니라 평범한 일을 비범하게 수행하는 능력을 가진 자를 말한다. - 루이스 윌턴`,
    `성공이란 당신이 가장 즐기는 일을 당신이 감탄하고 존경하는 사람들 속에서 당신이 가장 원하는 방식으로 행하는것이다. - Brian Tracy`,
    `어떤 일이든 열정만으로 90%의 문제를 해결할 수 있다. - Donald Trumph`
  ];

  // Initialize to hide all quotes except the first on mount
  onMount(() => {
    showDiv(0);
  });

  // Function to update the displayed quote
  function showDiv(nn: number) {
    nowDiv = nn;
  }
</script>

<style>
  .my {
    text-align: center;
    font-size: 10pt;
    margin-left: 50px;
    margin-right: 50px;
  }
  .marquee {
    text-align: center;
    background-color: #990033;
    color: #ffcccc;
    font-weight: bold;
    padding: 10px;
  }
  .button-container {
    display: flex;
    justify-content: center;
    margin-top: 10px;
  }
  .button-container button {
    margin: 0 5px;
  }
</style>

<div class="marquee">생활 속의 모티베이션</div>

<div class="button-container">
  <button on:click={() => showDiv(1)}>천재란?</button>
  <button on:click={() => showDiv(2)}>성공이란?</button>
  <button on:click={() => showDiv(3)}>열정이란?</button>
</div>

<hr size="10" color="#990033">

<div class="button-container">
  <button on:click={() => showDiv(0)}>처음부터</button>
</div>

{#if nowDiv !== 0}
  <div class="my">
    {quotes[nowDiv]}
  </div>
{/if}
