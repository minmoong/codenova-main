<script>
  import "../app.css";
</script>

<div class="navbar">
  <a href="/">홈</a>
  <a href="/7">명언 제조기</a> <!-- 7 -->
  <a href="/9">이집트 감상</a> <!-- 9 -->
  <a href="/15">연예인 선호도</a> <!-- 15 -->
  <a href="/18">그림판</a> <!-- 18 -->
  <a href="/19">퀴즈</a> <!-- 19 -->
</div>

<div class="slot">
  <slot></slot>
</div>

<style>
  .slot {
    padding: 20px;
  }


  /* 네비게이션 바 스타일 */
  .navbar {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #1077ff; /* 네비게이션 바 배경색 */
    padding: 10px 20px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }

  /* 네비게이션 바 링크 스타일 */
  .navbar a {
    text-decoration: none;
    color: white; /* 텍스트 색상 */
    margin: 0 15px; /* 링크 간 간격 */
    font-size: 16px; /* 폰트 크기 */
    font-weight: 500; /* 텍스트 굵기 */
    transition: color 0.3s ease, transform 0.3s ease;
  }

  /* 링크 호버 스타일 */
  .navbar a:hover {
    color: white; /* 호버 시 텍스트 색상 변경 */
    transform: scale(1.1); /* 약간 확대 효과 */
  }

  /* 현재 활성화된 페이지 링크 강조 (선택적) */
  .navbar a.active {
    color: #f39c12; /* 활성화된 링크 색상 */
    border-bottom: 2px solid #f39c12; /* 하단 강조선 */
  }

  /* 모바일 반응형 디자인 */
  @media (max-width: 768px) {
    .navbar {
      flex-direction: column; /* 세로 정렬 */
      align-items: flex-start; /* 좌측 정렬 */
      padding: 15px;
    }
    .navbar a {
      margin: 10px 0; /* 위아래 간격 */
      font-size: 18px; /* 모바일에서 폰트 크기 증가 */
    }
  }
</style>

