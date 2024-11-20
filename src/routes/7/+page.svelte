<script lang="ts">
  import { onMount } from 'svelte';

  // State to manage the currently visible quote
  let nowDiv = 0;

  // Quotes array for display
  const quotes = [
    `See far`,
    `익숙해지지 마라.`,
    `너무 연연하지 마라.`,
    `인생은 꿀벌처럼`,
    `인생에 성공과 실패는 없다, 성공과 그 과정이 있을 뿐`,
    `실패가 성공의 어머니라고 하는 사람들은 실패한 적 없는 사람이다.`,
    `시간은 어떻게든 흘러간다.`,
    `하고싶은 거 하면서 즐기자`,
    `나누면서 살자`,
    `세상을 변화시키고 싶다면, 자신을 변화시키자.`,
    `포기는 하지 말자`,
    `과거는 잊어라, 미래를 가질 뿐이니까.`,
  ];

  const names = [
    '김민규',
    '나영민',
    '김대경',
    '이재진',
    '나현빈',
    '정민우',
    '박경빈',
    '이정우',
    '김유담',
    '강경민',
    '기현수',
    '정진우',
  ];

  // Function to update the displayed quote
  function showDiv(nn: number) {
    nowDiv = nn;
  }
</script>

<style>
  .my {
    text-align: center;
    font-size: 25px;
    margin-left: 50px;
    margin-right: 50px;
    margin-top: 30px;
    margin-bottom: 30px;
    font-style: italic;
  }
  .marquee {
    text-align: center;
    color: #990033;
    font-weight: bold;
    padding: 10px;
    font-size: 25px;
    font-weight: bold;
  }
  .button-container {
    display: flex;
    justify-content: center;
    margin-top: 10px;
    white-space: nowrap;
  }
  .button-container button {
    margin: 0 5px;
  }
</style>

<h1 class="marquee">동아리 부원들의 좌우명</h1>

<div class="button-container">
  {#each names as name, i}
    <button on:click={() => showDiv(i)}>{name}</button>
  {/each}
</div>


<div class="my">
  ❝ {quotes[nowDiv]} ❞ <br> - {names[nowDiv]}
</div>