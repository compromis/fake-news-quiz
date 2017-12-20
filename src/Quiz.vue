<template>
  <div class="quizz-wrapper">
    <true-false-quiz :questions="questions" />
  </div>
</template>

<script>
import TrueFalseQuiz from './components/TrueFalseQuiz'
import questions from './data/questions.json'

export default {
  name: 'quizz',

  components: {
    TrueFalseQuiz
  },

  data () {
    return {
      questions: []
    }
  },

  mounted () {
    this.questions = questions
  },
}
</script>

<style lang="scss" scoped>
.quizz-wrapper {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
