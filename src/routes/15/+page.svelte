<script lang="ts">
  import { onMount } from 'svelte';

  let colors = ["blue", "red", "green", "yellow", "gray"];
  let dang = ["국민의힘", "더불어민주당", "조국혁신당", "개혁신당", "진보당"];
  let values = [0, 0, 0, 0, 0]; // 각 당의 지지율을 담을 배열
  let canvas: HTMLCanvasElement | null = null;
  let context: CanvasRenderingContext2D | null = null;

  // 컴포넌트가 로드될 때 캔버스와 컨텍스트를 초기화
  onMount(() => {
    if (canvas) {
      context = canvas.getContext("2d");
    }
  });

  function drawChart() {
    const total = values.reduce((acc, val) => acc + val, 0);

    if (total === 0 || !context) return;

    context.clearRect(0, 0, canvas!.width, canvas!.height);
    
    const x = canvas!.width / 2;
    const y = canvas!.height / 2;
    const radius = Math.min(x, y) - 20;
    let startAngle = 0;

    values.forEach((value, i) => {
      if (value <= 0) return;

      const deg = (360 * value) / total;
      const rad = (deg * Math.PI) / 180;
      const endAngle = startAngle + rad;

      context!.beginPath();
      context!.moveTo(x, y);
      context!.arc(x, y, radius, startAngle, endAngle);
      context!.closePath();
      context!.strokeStyle = colors[i];
      context!.fillStyle = colors[i];
      context!.fill();
      context!.stroke();

      startAngle = endAngle;
    });

    context.font = "normal 15px Gothic";
    context.fillStyle = "blue";
    values.forEach((value, i) => {
      const percentage = Math.floor((value * 100) / total);
      context!.fillText(`${dang[i]} 지지율 ${percentage}% : ${colors[i]}`, 10, 30 + i * 16);
    });
  }
</script>

<h3>정당별 지지율 조사 결과</h3>
<hr />
<div>
  {#each dang as party, i}
    <label>{party} 지지
      <input type="number" bind:value={values[i]} min="0" /> 명
    </label>
    <br />
  {/each}
</div>
<button on:click={drawChart}>결과보기</button>
<canvas bind:this={canvas} width="500" height="400" style="background-color: ivory"></canvas>
