<script lang="ts">
  import { onMount } from 'svelte';
  import { writable } from 'svelte/store';

  // Svelte store for the calculator display
  const acc = writable("0");

  // Function to add input to the display
  function addInput(value: string) {
    acc.update((currentValue) => (currentValue === "0" ? value : currentValue + value));
  }

  // Function to delete the last character
  function backward() {
    acc.update((currentValue) => (currentValue.length <= 1 ? "0" : currentValue.slice(0, -1)));
  }

  // Function to evaluate the expression
  function calculate() {
    acc.update((currentValue) => {
      try {
        return eval(currentValue).toString();
      } catch {
        return "Error";
      }
    });
  }

  // Function to clear the display
  function clearLcd() {
    acc.set("0");
  }
</script>

<style>
  table {
    text-align: center;
    border: 0;
    width: 300px;
    margin: auto;
  }
  tr {
    text-align: center;
  }
  td {
    width: 100px;
  }
  input[type="button"] {
    width: 60px;
    background: ivory;
    border-radius: 50px;
  }
  h3 {
    text-align: center;
  }
  hr {
    margin-bottom: 20px;
  }
</style>

<h3>계산기 만들기</h3>
<hr>

<form name="cal">
  <table>
    <tbody>
      <tr>
        <td colspan="4">
          <input type="text" bind:value={$acc} readonly size="50" />
        </td>
      </tr>
      <tr>
        <td><input type="button" value="뒤로" on:click={backward} /></td>
        <td><input type="button" value="CE" on:click={clearLcd} /></td>
        <td><input type="button" value="C" on:click={clearLcd} /></td>
        <td><input type="button" value="=" on:click={calculate} /></td>
      </tr>
      <tr>
        <td><input type="button" value="7" on:click={() => addInput("7")} /></td>
        <td><input type="button" value="8" on:click={() => addInput("8")} /></td>
        <td><input type="button" value="9" on:click={() => addInput("9")} /></td>
        <td><input type="button" value="/" on:click={() => addInput("/")} /></td>
      </tr>
      <tr>
        <td><input type="button" value="4" on:click={() => addInput("4")} /></td>
        <td><input type="button" value="5" on:click={() => addInput("5")} /></td>
        <td><input type="button" value="6" on:click={() => addInput("6")} /></td>
        <td><input type="button" value="*" on:click={() => addInput("*")} /></td>
      </tr>
      <tr>
        <td><input type="button" value="1" on:click={() => addInput("1")} /></td>
        <td><input type="button" value="2" on:click={() => addInput("2")} /></td>
        <td><input type="button" value="3" on:click={() => addInput("3")} /></td>
        <td><input type="button" value="-" on:click={() => addInput("-")} /></td>
      </tr>
      <tr>
        <td><input type="button" value="0" on:click={() => addInput("0")} /></td>
        <td><input type="button" value="+" on:click={() => addInput("+")} /></td>
        <td><input type="button" value=" " disabled /></td>
        <td><input type="button" value=" " disabled /></td>
      </tr>
    </tbody>
  </table>
</form>
