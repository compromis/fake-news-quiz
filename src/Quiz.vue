<template>
  <div class="quizz-wrapper">
    <quiz-header />
    <true-false-quiz :questions="questions" />
  </div>
</template>

<script>
import QuizHeader from './components/QuizHeader'
import TrueFalseQuiz from './components/TrueFalseQuiz'
import questions from './data/questions.json'

export default {
  name: 'quizz',

  components: {
    QuizHeader,
    TrueFalseQuiz
  },

  data () {
    return {
      questions: []
    }
  },

  mounted () {
    this.questions = questions
  }
}
</script>

<style lang="scss">
@import 'variables';

html,
body {
  font-family: $font-base;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: $text-color;
  background: $background;
}
</style>
