<template>
  <header class="navbar is-fixed-top">
    <div class="navbar-brand">
      <a href="https://compromis.net">
        <img src="https://compromis.net/wp-content/themes/Compromis/images/logo-compromis-retina.png" alt="Compromís" />
      </a>
    </div>
  </header>
</template>

<script>
export default {
  name: 'quiz-header'
}
</script>

<style lang="scss" scoped>
@import '../variables';

.navbar {
  background: linear-gradient(270deg, $orange-start, $orange-end);
  background-size: 200% 100%;
  animation: HeaderOrange 15s ease infinite;
}

.navbar-brand {
  background: #fff;
  padding: 0.5rem 1.5rem;

  img {
    width: 180px;
    margin-bottom: -0.5rem;
  }
}

@keyframes HeaderOrange {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
</style>
