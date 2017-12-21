<template>
  <div class="true-false-quiz">
    <div v-for="question in questions">
      <quiz-question :question="question" @updateQuiz="updateQuiz" />
    </div>

    <div class="result" v-if="answers.length == questions.length && answers.length > 1">
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
@import '../variables';

.true-false-quiz {
  margin-top: -2rem;
  margin-bottom: 4rem;
}

.result {
  max-width: 600px;
  margin: 0 auto;
  background: $white;
  padding: 1.5rem;
  border-radius: 10px;
  box-shadow: 0 4px 40px -5px rgba(0, 0, 0, 0.9);
  color: $text-color-dark;
}
</style>
