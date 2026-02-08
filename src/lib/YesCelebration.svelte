<script>
  import { fade, scale } from 'svelte/transition';
  import { onMount } from 'svelte';
  import RosePetals from '$lib/RosePetals.svelte';

  const hearts = Array.from({ length: 28 });

  let showLine1 = false;
  let showLine2 = false;
  let showLine3 = false;
  let showPizza = false;

  onMount(() => {
    if (navigator.vibrate) {
      navigator.vibrate(200);
    }

    localStorage.setItem('saidYes', 'true');

    setTimeout(() => (showLine1 = true), 600);
    setTimeout(() => (showLine2 = true), 1600);
    setTimeout(() => (showLine3 = true), 2800);
    setTimeout(() => (showPizza = true), 4200);
  });
</script>

<style>
  .wrapper {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
    text-align: center;
    overflow: hidden;
  }

  .card {
    background: rgba(255, 255, 255, 0.32);
    backdrop-filter: blur(16px);
    border-radius: 20px;
    padding: 26px 22px;
    max-width: 340px;
    width: 100%;
    box-shadow: 0 25px 50px rgba(255, 77, 109, 0.45);
    z-index: 2;
  }

  p {
    font-size: 1rem;
    color: #7a0c2e;
    line-height: 1.6;
    margin: 10px 0;
  }

  /* 🍕 Pizza animation */
  .pizza {
    margin-top: 18px;
  }

  .pizza-emoji {
    font-size: 64px;
    animation: pizza-pop 1s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
  }

  @keyframes pizza-pop {
    0% {
      transform: scale(0) rotate(-180deg);
      opacity: 0;
    }
    60% {
      transform: scale(1.2) rotate(10deg);
      opacity: 1;
    }
    100% {
      transform: scale(1) rotate(0deg);
    }
  }

  .heart {
    position: fixed;
    font-size: 22px;
    animation: burst 2.5s ease forwards;
    opacity: 0;
  }

  @keyframes burst {
    0% {
      transform: translate(0, 0) scale(0.5);
      opacity: 0;
    }
    20% {
      opacity: 1;
    }
    100% {
      transform: translate(var(--x), var(--y)) scale(1.5);
      opacity: 0;
    }
  }
</style>

<div class="wrapper">
  <!-- 🌹 Falling roses -->
  <RosePetals />

  <!-- ❤️ Heart burst -->
  {#each hearts as _}
    <div
      class="heart"
      style="
        left: 50%;
        top: 50%;
        --x: {Math.random() * 280 - 140}px;
        --y: {Math.random() * 280 - 140}px;
        animation-delay: {Math.random()}s;
      "
    >
      ❤️
    </div>
  {/each}

  <!-- 💖 Message card -->
  <div in:fade={{ duration: 800 }}>
    <div class="card" in:scale={{ duration: 700 }}>
      {#if showLine1}
        <p in:fade>I had a feeling you’d say yes 💖</p>
      {/if}

      {#if showLine2}
        <p in:fade>
          Some answers just feel right ✨
        </p>
      {/if}

      {#if showLine3}
        <p in:fade>
          Happy Propose Day 🌹<br />
          This is just the beginning.
        </p>
      {/if}

      {#if showPizza}
        <div class="pizza" in:fade>
          <p>And about that thing I said I’m making for you… 😌</p>
          <div class="pizza-emoji">🍕</div>
          <p><strong>Yes. Pizza. On me ❤️</strong></p>
        </div>
      {/if}
    </div>
  </div>
</div>
