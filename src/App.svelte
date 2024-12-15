<script>
  import { moodList } from './lib/MoodList.js';
  
  let selectedMood = null;
  let showPositive = false;
  
  function handleSelect(mood) {
    selectedMood = mood;
    showPositive = false;
  }
  
  function flipMood() {
    showPositive = true;
  }
</script>

<main class="container py-4">
  <div class="text-center mb-4">
    <h1 class="display-4">MoodFlip 🔄</h1>
    <p class="lead">Turn that frown upside down!</p>
  </div>

  <div class="row">
    <div class="col-md-8 mx-auto">
      <div class="list-group mb-4">
        {#each moodList as mood}
          <button
            class="list-group-item list-group-item-action {selectedMood === mood ? 'active' : ''}"
            on:click={() => handleSelect(mood)}
          >
            {mood.negative}
          </button>
        {/each}
      </div>

      <div class="text-center">
        <button
          class="btn btn-primary btn-lg"
          disabled={!selectedMood}
          on:click={flipMood}
        >
          Flip it! 🔄
        </button>
      </div>

      {#if showPositive && selectedMood}
        <div class="alert alert-success mt-4" role="alert">
          <h4 class="alert-heading">Here's a bright side! ✨</h4>
          <p class="mb-0">{selectedMood.positive}</p>
        </div>
      {/if}
    </div>
  </div>
</main>