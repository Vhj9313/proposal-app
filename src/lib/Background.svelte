<style>
  .bg {
    position: fixed;
    inset: 0;
    z-index: -3;
    background: linear-gradient(
      120deg,
      #ff9a9e,
      #fad0c4,
      #fbc2eb
    );
    animation: gradientShift 10s ease infinite;
  }

  @keyframes gradientShift {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }
</style>

<div class="bg"></div>
