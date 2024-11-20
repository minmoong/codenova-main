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

<h3>웹 프로그래밍 Quiz</h3>
<hr />

<!-- Questions and Answers -->
<div>
  <p>Q1. 월드와이드웹을 제안한 사람은 누구일까요?</p>
  <button on:click={(e) => handleAnswer(e, '팀버너스리')}>정답</button>
</div>

<div>
  <p>Q2. 웹3.0의 기본정신은 무엇일까요?</p>
  <button on:click={(e) => handleAnswer(e, '참여/공유/개방')}>정답</button>
</div>

<div>
  <p>Q3. 웹3.0의 기본정신은 무엇일까요?</p>
  <button on:click={(e) => handleAnswer(e, '참여/공유/개방')}>정답</button>
</div>

<div>
  <p>Q4. 무어의 법칙은 무엇일까요?</p>
  <button on:click={(e) => handleAnswer(e, '반도체용량이 18개월마다 2배씩 증가')}>정답</button>
</div>

<div>
  <p>Q5. 혁신자의 딜레마를 주장한 사람은 누구일까요?</p>
  <button on:click={(e) => handleAnswer(e, '크레이튼크리스텐슨')}>정답</button>
</div>

<div>
  <img src={cris} alt="크레이튼 크리스텐슨" width="400px" />
</div>
