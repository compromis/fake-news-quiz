<template>
  <div class="true-false-quiz">
    <div v-for="question in questions">
      <transition name="slide">
        <quiz-question
          :visible="visibleQuestions.includes(question.id)"
          :question="question"
          :next-question-id="question.id + 1 <= questions.length ? question.id + 1 : false"
          @updateQuiz="updateQuiz"
          @nextQuestion="nextQuestion" />
        </transition>
    </div>

    <quiz-results
      v-if="answers.length == questions.length && answers.length > 1"
      :results="results"
      :correct-answers="correctAnswers"
      :total-questions="questions.length" />
  </div>
</template>

<script>
import QuizQuestion from './QuizQuestion'
import QuizResults from './QuizResults'

export default {
  name: 'true-false-quiz',

  components: {
    QuizQuestion,
    QuizResults
  },

  props: {
    questions: Array,
    results: Array
  },

  data () {
    return {
      visibleQuestions: [1],
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
    },

    nextQuestion (nextQuestion) {
      if (this.questions.length >= nextQuestion) {
        this.visibleQuestions.push(nextQuestion)
      }
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
</style>
