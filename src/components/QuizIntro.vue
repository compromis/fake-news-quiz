<template>
  <section class="intro container">
    <p><span class="intro-flair">QUIZ</span></p>
    <h1 class="intro-heading">FAKE NEWS</h1>
    <h2 class="intro-subheading">Eres inmune?</h2>
    <p class="intro-description">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
  </section>
</template>

<script>
export default {
  name: 'quiz-intro'
}
</script>

<style lang="scss" scoped>
@import '../variables';

.intro {
  padding: 5rem;
  text-align: center;
}

.intro-heading {
  font-family: $font-headings;
  font-size: 7rem;
  position: relative;
  text-shadow: 10px 10px 0 $secondary-color;
  transform: skew(0deg, -10deg);
  line-height: 1;
  margin: 2rem 0;
}

.intro-subheading {
  font-size: 2.5rem;
  letter-spacing: -1px;
  margin-top: 3rem;
}

.intro-flair {
  border: 1px $white solid;
  padding: 0.25rem 1rem;
  border-radius: 20px;
  opacity: 0.75;
}

.intro-description {
  margin-top: 1rem;
}
</style>
