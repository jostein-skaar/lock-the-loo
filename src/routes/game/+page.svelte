<script lang="ts">
  import lockOpen from '$lib/assets/lock-open.png';
  import lockLocked from '$lib/assets/lock-locked.png';

  let level = 5;
  let locks = Array.from({ length: level * level }, () => false);
  let showNextLevelButton = false;

  function toggleLock(index: number) {
    locks[index] = !locks[index];

    if (locks.every((lock) => lock)) {
      showNextLevelButton = true;
    }
  }

  function increaseLevel() {
    showNextLevelButton = false;
    level++;
    locks = Array.from({ length: level * level }, () => false);
  }

  function getFinishTextForLevel(level: number) {
    switch (level) {
      case 1:
        return "Good job! Now let's try something harder!";
      case 2:
        return 'Wow! 4 locks. Getting the hang of it now!';
      case 3:
        return "You're a pro! Can you get to level 5?";
      case 4:
        return '🎶You. Are. Amazing! 🎶';
      case 5:
        return 'You should be good to go to work now. If not sure, keep going!';
      case 6:
        return "That's the spirit!";
      case 7:
        return "That's a lot of locks!";
      default:
        return 'This is insane! Keep going!';
    }
  }
</script>

<h1>Let's lock 'em locks</h1>

<h2>Level {level}</h2>

<div class="grid-container" style="--level: {level};">
  {#each locks as isLocked, index}
    <div class="grid-item">
      <button on:click={() => toggleLock(index)}>
        <img src={isLocked ? lockLocked : lockOpen} alt="Lock" />
      </button>
    </div>
  {/each}
</div>

{#if showNextLevelButton}
  <p>{getFinishTextForLevel(level)}</p>
  <button class="next-level-button" on:click={increaseLevel}> Level {level + 1}</button>
{/if}

<style>
  .grid-container {
    display: grid;
    gap: 10px;
    grid-template-columns: repeat(var(--level), 1fr);
    grid-template-rows: repeat(var(--level), 1fr);
  }

  @media (min-width: 600px) {
    .grid-container {
      max-width: 600px;
    }
  }

  .grid-item {
    text-align: center;
  }
  button {
    border: none;
    background-color: transparent;
    cursor: pointer;
    margin: 0;
    padding: 0;
    display: block;
  }

  button img {
    max-width: min(160px, 100%);
    width: auto;
    height: auto;
    display: block;
  }

  button.next-level-button {
    display: inline-block;
    padding: 10px 20px;
    text-align: center;
    color: white;
    background-color: #007bff;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
    transition:
      background-color 0.3s,
      box-shadow 0.3s;
  }

  button.next-level-button:hover {
    background-color: #0056b3;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  }

  button.next-level-button:active {
    background-color: #004085;
    box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.3);
  }

  p {
    margin-top: 20px;
    margin-bottom: 20px;
  }
</style>
