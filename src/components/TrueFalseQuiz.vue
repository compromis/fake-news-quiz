<template>
  <div class="true-false-quiz">
    <div v-for="question in questions">
      <quiz-question :question="question" @updateQuiz="updateQuiz" />
    </div>

    <div class="result" v-if="answers.length == questions.length">
      Final {{ correctAnswers }} correct answers out of {{ questions.length }}
    </div>
  </div>
</template>

<script>
import QuizQuestion from './QuizQuestion'

export default {
  name: 'true-false-quiz',

  components: {
    QuizQuestion
  },

  props: {
    questions: Array
  },

  data () {
    return {
      answers: []
    }
  },

  computed: {
    correctAnswers: function () {
      return this.answers.reduce((sum, current) => sum + current.points, 0)
    }
  },

  methods: {
    updateQuiz (question) {
      const questionIndex = this.answers.findIndex(q => q.id === question.id)

      if (questionIndex) {
        this.answers.splice(questionIndex, 1)
      }

      this.answers.push(question)
    }
  }
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
