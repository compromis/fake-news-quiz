<template>
  <div class="results" id="results">
    Final {{ correctAnswers }} correct answers out of {{ questions.length }}
  </div>
</template>

<script>
import Thumbs from '../assets/images/thumbs.svg'

export default {
  name: 'quiz-results',

  props: {
    correctAnswers: Number,
    totalQuestions: Number
  },

  components: {
    Thumbs
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
}
</style>
