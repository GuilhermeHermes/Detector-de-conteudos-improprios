<script>
  let userInput = '';
  let showUserInput = false;
  let userInputCopy = '';
  let hasCurse = false;
  let dontHas = false
  let curseList = [];
  import { curseWords } from './palavroes.js';
  
  
  function hasCurseWord(text){
    curseList = [];
    
    let copyText = text.toLowerCase().split(' ');
  
    for (let i = 0; i < copyText.length; i++) {
      if (curseWords.includes(copyText[i])) {
          curseList.push(copyText[i]);
      
      }
    }
  
    if(curseList.length){
        return true;
      }else{
        return false;
    }
  }

    function toAnalyze() {
    hasCurse = hasCurseWord(userInput);
    dontHas = !hasCurse;
    showUserInput = true;
    userInputCopy = userInput;
  }

</script>
<h1>Analise se há algum conteúdo impróprio no seu texto!</h1>

<label for="user-input">Digite seu texto:</label>
<textarea id="user-input" name="user-input" rows="6" cols="50"bind:value={userInput}></textarea>

<button on:click={toAnalyze}>Analisar</button>

{#if showUserInput}
  <p>Você digitou: {userInputCopy}</p>
  
{/if}

{#if hasCurse}
  <p>Conteúdo impróprio detectado: {curseList}</p>
  
  {:else}
  {#if dontHas}
	<p>Não detectamos nenhum conteúdo impróprio no seu texto! 😅</p>
  {/if}
{/if}