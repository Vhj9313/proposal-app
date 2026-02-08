<script>
  const hearts = Array.from({ length: 20 });
</script>

<style>
  .heart {
    position: fixed;
    bottom: -20px;
    font-size: 20px;
    animation: floatUp linear infinite;
    opacity: 0.7;
  }

  @keyframes floatUp {
    from {
      transform: translateY(0) scale(1);
      opacity: 0.8;
    }
    to {
      transform: translateY(-110vh) scale(1.4);
      opacity: 0;
    }
  }
</style>

{#each hearts as _, i}
  <div
    class="heart"
    style="
      left: {Math.random() * 100}%;
      animation-duration: {6 + Math.random() * 6}s;
      animation-delay: {Math.random() * 5}s;
    "
  >
    ❤️
  </div>
{/each}
