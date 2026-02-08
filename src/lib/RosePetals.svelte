<script>
  const petals = Array.from({ length: 25 });
</script>

<style>
  .petal {
    position: fixed;
    top: -10%;
    font-size: 18px;
    animation: fall linear infinite;
    opacity: 0.8;
    pointer-events: none;
  }

  @keyframes fall {
    from {
      transform: translateY(0) rotate(0deg);
      opacity: 0.9;
    }
    to {
      transform: translateY(110vh) rotate(360deg);
      opacity: 0;
    }
  }
</style>

{#each petals as _, i}
  <div
    class="petal"
    style="
      left: {Math.random() * 100}%;
      animation-duration: {8 + Math.random() * 6}s;
      animation-delay: {Math.random() * 5}s;
    "
  >
    🌹
  </div>
{/each}
