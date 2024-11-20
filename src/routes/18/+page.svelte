<script lang="ts">
  import { onMount } from 'svelte';
  import { writable } from 'svelte/store';

  let canvas: HTMLCanvasElement | null = null;
  let context: CanvasRenderingContext2D | null = null;

  // 사용자 입력으로 선 두께와 색상 조정
  let lineWidth = 5;
  let strokeColor = "#00f420";

  // 이전 좌표와 마우스 이벤트 상태
  let prevX = 0;
  let prevY = 0;
  let inbound = false;

  onMount(() => {
    if (canvas) {
      context = canvas.getContext("2d");
      if (context) {
        context.lineWidth = lineWidth;
        context.strokeStyle = strokeColor;
        
        canvas.addEventListener("mousemove", move);
        canvas.addEventListener("mouseenter", over);
        canvas.addEventListener("mouseleave", out);
      }
    }
  });

  function updateLineWidth() {
    if (context) context.lineWidth = lineWidth;
  }

  function updateStrokeColor() {
    if (context) context.strokeStyle = strokeColor;
  }

  function move(e: MouseEvent) {
    if (!context) return;

    const curX = e.offsetX;
    const curY = e.offsetY;

    if (!inbound) {
      prevX = curX;
      prevY = curY;
      inbound = true;
    }

    context.beginPath();
    context.moveTo(prevX, prevY);
    context.lineTo(curX, curY);
    context.stroke();

    prevX = curX;
    prevY = curY;
  }

  function over(e: MouseEvent) {
    inbound = true;
    prevX = e.offsetX;
    prevY = e.offsetY;
  }

  function out() {
    inbound = false;
  }
</script>

<h2>나만의 작은 그림판</h2>
<hr />
<label>
  선두께:
  <input
    type="number"
    bind:value={lineWidth}
    min="0"
    max="50"
    step="1"
    on:change={updateLineWidth}
  />
</label>
<label>
  선 색:
  <input type="color" bind:value={strokeColor} on:change={updateStrokeColor} />
</label>

<br /><br />

<canvas bind:this={canvas} width="300" height="400" style="background-color: ivory;"></canvas>
