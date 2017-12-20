<template>
  <div class="question-wrapper">
    <h3>{{ question.name }}</h3>
    <quiz-option
      v-for="option in question.options"
      :key="question.options.indexOf(option)"
      :option="option"
      :selected="selectedOption.name == option.name"
      :question-id="question.id"
      :disabled="selectedOption.name != null"
      @change="selectOption" />

      <div class="answer" v-if="selectedOption.name">
        <h3>{{ selectedOption.message }}</h3>
        <p>{{ question.message }}</p>
      </div>
  </div>
</template>

<script>
import QuizOption from './QuizOption'

export default {
  name: 'quiz-question',

  components: {
    QuizOption
  },

  props: {
    question: Object
  },

  data () {
    return {
      selectedOption: { name: null }
    }
  },

  methods: {
    selectOption (option) {
      this.selectedOption = option
      this.$emit('updateQuiz', option)
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
