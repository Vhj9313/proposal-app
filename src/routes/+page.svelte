<script>
  import Background from '$lib/Background.svelte';
  import FloatingHearts from '$lib/FloatingHearts.svelte';
  import QuestionStage from '$lib/QuestionStage.svelte';
  import NoEscape from '$lib/NoEscape.svelte';
  import YesCelebration from '$lib/YesCelebration.svelte';



  let stage = 'question';
  let noCount = 0;

  function handleYes() {
    stage = 'yes';
  }

  function handleNo() {
    noCount += 1;
    stage = 'no';
  }

  function backToQuestion() {
    stage = 'question';
  }


</script>

<Background />

<FloatingHearts />

{#if stage === 'question'}
  <QuestionStage on:yes={handleYes} on:no={handleNo} />
{:else if stage === 'no'}
  <NoEscape {noCount} on:yes={handleYes} />

{:else if stage === 'yes'}
  <YesCelebration />
{/if}
