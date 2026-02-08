<script>
  import { createEventDispatcher } from 'svelte';
  import { fade, scale } from 'svelte/transition';

  const dispatch = createEventDispatcher();

  function yes() {
    dispatch('yes');
  }

  function no() {
    dispatch('no');
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
    background: rgba(255, 255, 255, 0.25);
    backdrop-filter: blur(12px);
    border-radius: 18px;
    padding: 22px 18px;
    max-width: 290px;
    width: 100%;
    box-shadow: 0 18px 36px rgba(255, 77, 109, 0.3);
  }

  h1 {
    font-size: 1.15rem;
    color: #7a0c2e;
    margin-bottom: 24px;
    line-height: 1.5;
  }

  .buttons {
    display: flex;
    gap: 14px;
    justify-content: center;
  }

  button {
    flex: 1;
    padding: 12px 0;
    border-radius: 999px;
    border: none;
    font-size: 0.95rem;
    font-weight: 600;
    cursor: pointer;
  }

  .yes {
    background: linear-gradient(135deg, #ff4d6d, #ff758f);
    color: white;
    box-shadow: 0 8px 16px rgba(255, 77, 109, 0.4);
  }

  .no {
    background: rgba(255, 255, 255, 0.6);
    color: #7a0c2e;
  }

  @media (max-width: 360px) {
    h1 {
      font-size: 1.05rem;
    }

    .card {
      padding: 18px 16px;
    }
  }
</style>

<div class="wrapper">
  <div in:fade={{ duration: 600 }}>
    <div class="card" in:scale={{ duration: 500 }}>
      <h1>
        If every beautiful moment had a reason…<br />
        would you like to be mine?
      </h1>

      <div class="buttons">
        <button class="yes" on:click={yes}>Yes 💖</button>
        <button class="no" on:click={no}>No 🙈</button>
      </div>
    </div>
  </div>
</div>
