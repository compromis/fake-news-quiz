<template>
  <div class="quizz-wrapper">
    {{ answers }}
    <div v-for="question in questions">
      <question :question="question" :update="updateQuiz" />
    </div>
  </div>
</template>

<script>
import Question from './components/Question'
import questions from './data/questions.json'

export default {
  name: 'quizz',

  components: {
    Question
  },

  data () {
    return {
      questions: [],
      answers: []
    }
  },

  mounted () {
    this.questions = questions

    this.$on('updateQuiz', this.updateQuiz)
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
