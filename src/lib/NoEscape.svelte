<script>
  import { createEventDispatcher } from 'svelte';
  import { fly, fade } from 'svelte/transition';

  export let noCount = 0;

  const dispatch = createEventDispatcher();

  let x = 0;
  let y = 0;

  const messages = [
    "Wait… are you sure? 🥺",
    "Hmm… that didn’t feel right 😌",
    "The universe says try again ✨",
    "Okay now you’re just playing hard to get 😏",
    "At this point… just say yes 💖"
  ];

  function moveButton() {
    x = Math.random() * 120 - 60;
    y = Math.random() * 120 - 60;
  }

function yes() {
  dispatch('yes');
}

</script>

<style>
  .wrapper {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
    text-align: center;
  }

  .card {
    background: rgba(255, 255, 255, 0.28);
    backdrop-filter: blur(14px);
    border-radius: 18px;
    padding: 22px 18px;
    max-width: 320px;
    width: 100%;
    box-shadow: 0 18px 36px rgba(255, 77, 109, 0.3);
  }

  h2 {
    font-size: 1.1rem;
    color: #7a0c2e;
    margin-bottom: 22px;
    line-height: 1.5;
  }

  .buttons {
    position: relative;
    height: 90px;
  }

  button {
    padding: 12px 22px;
    border-radius: 999px;
    border: none;
    font-size: 0.95rem;
    font-weight: 600;
    cursor: pointer;
    position: absolute;
    left: 50%;
    transform: translate(-50%, 0);
    transition: transform 0.25s ease;
  }

  .no {
    background: rgba(255, 255, 255, 0.7);
    color: #7a0c2e;
  }

  .yes {
    background: linear-gradient(135deg, #ff4d6d, #ff758f);
    color: white;
    box-shadow: 0 8px 16px rgba(255, 77, 109, 0.4);
    bottom: -70px;
  }
</style>

<div class="wrapper">
  <!-- fade wrapper -->
  <div in:fade={{ duration: 500 }}>
    <!-- fly card -->
    <div class="card" in:fly={{ y: 30, duration: 500 }}>
      <h2>
        {messages[Math.min(noCount, messages.length - 1)]}
      </h2>

      <div class="buttons">
        <button
          class="no"
          style="transform: translate(calc(-50% + {x}px), {y}px);"
          on:mouseenter={moveButton}
          on:touchstart={moveButton}
        >
          No 🙈
        </button>

<button class="yes" on:click={yes}>
  Fine… Yes 💖
</button>

      </div>
    </div>
  </div>
</div>
