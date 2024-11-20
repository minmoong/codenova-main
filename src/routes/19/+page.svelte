<script lang="ts">
  import cris from "./cris.jpg";
  // Answering logic
  const handleAnswer = (event: MouseEvent, answer: string) => {
    const button = event.currentTarget as HTMLButtonElement;
    const parent = button.parentElement;

    if (!parent || parent.lastElementChild !== button) return;

    // Check if answer already exists
    const existingAnswer = parent.querySelector("p.answer");
    if (existingAnswer) {
      existingAnswer.remove(); // Remove the existing answer if any
    }

    const newP = document.createElement("p");
    newP.className = "answer";
    newP.textContent = answer;

    // Add click listener to remove the answer
    newP.onclick = () => parent.removeChild(newP);

    parent.appendChild(newP);
  };
</script>

<style>
  /* Add any styles here */
  div {
    margin-bottom: 1rem;
  }
  button {
    margin-left: 0.5rem;
  }
  .answer {
    color: green;
    margin-top: 0.5rem;
    cursor: pointer;
  }
</style>

<h2>컴퓨터 퀴즈!!</h2>
<hr />

<!-- Questions and Answers -->
<div>
  <p>Q1. 웹 페이지를 구성할 때 사용하는 언어는 무엇인가요?</p>
  <button on:click={(e) => handleAnswer(e, 'HTML')}>정답</button>
</div>

<div>
  <p>Q2. 프로그램이 어떤 조건에 따라 다른 동작을 하도록 만드는 것을 무엇이라고 하나요?</p>
  <button on:click={(e) => handleAnswer(e, '조건문')}>정답</button>
</div>

<div>
  <p>Q3. 램은 중고상품이 2기가짜리밖에 없는 이유?</p>
  <button on:click={(e) => handleAnswer(e, '4기가 애매하고 8기가 애매해서')}>정답</button>
</div>

<div>
  <p>Q4. 열명의 스님이 쉬면?</p>
  <button on:click={(e) => handleAnswer(e, '열중쉬어')}>정답</button>
</div>

<div>
  <p>Q5. PC방의 날씨는?</p>
  <button on:click={(e) => handleAnswer(e, '갬')}>정답</button>
</div>


<div>
  <img src={cris} alt="크레이튼 크리스텐슨" width="400px" />
</div>
