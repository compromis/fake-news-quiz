<template>
  <div class="results" id="results">
    <h3>Has encertat {{ correctAnswers }} de {{ totalQuestions }}</h3>
    <img :src="result.gif" alt="Gif reacció" />
    <p>{{ result.message }}</p>
  </div>
</template>

<script>
import Thumbs from '../assets/images/thumbs.svg'

export default {
  name: 'quiz-results',

  props: {
    correctAnswers: Number,
    totalQuestions: Number,
    results: Array
  },

  components: {
    Thumbs
  },

  computed: {
    result: function () {
      return this.results.find((element) => this.correctAnswers <= element.points)
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../variables';

.results {
  max-width: 600px;
  margin: 0 auto;
  background: $white;
  padding: 1.5rem;
  border-radius: 10px;
  box-shadow: 0 4px 40px -5px rgba(0, 0, 0, 0.9);
  color: $text-color-dark;
  text-align: center;

  h3 {
    font-weight: bold;
    font-size: 1.75rem;
  }

  p {
    font-size: 1.15rem;
    max-width: 400px;
    margin: 0 auto;
  }

  img {
    border-radius: 5px;
    margin: 1rem 0;
    max-width: 100%;
  }
}
</style>
