<script>
  // @ts-nocheck
  import apple from './apple.png'

  function rotate(event) {
    event.currentTarget.style.transform = 'rotate(90deg)';
  }
</script>

<div>
  <h3>90도 회전!!- 클릭하기</h3>
  <hr />
  <img
    src={apple}
    width="100"
    height="100"
    alt="animation"
    on:click={rotate}
  />
</div>
