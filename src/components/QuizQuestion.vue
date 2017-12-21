<template>
  <div class="question-outer-wrapper">
    <div class="question-wrapper">
      <div class="question">
        <div class="question-image">
          <img src="http://junkee.com/wp-content/uploads/2017/01/transflag.jpg" alt="" />
        </div>
        <h3>{{ question.name }}</h3>

        <div class="columns question-options">
          <div class="column" v-for="option in question.options">
            <quiz-option
              :key="question.options.indexOf(option)"
              :option="option"
              :selected="selectedOption.name == option.name"
              :question-id="question.id"
              :disabled="selectedOption.name != null"
              @change="selectOption" />
          </div>
        </div>

        <transition name="slide">
          <div class="answer" v-if="selectedOption.name">
            <h4>{{ selectedOption.message }}</h4>
            <p>{{ question.message }}</p>
          </div>
        </transition>
      </div>
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
@import '../variables';

.question-outer-wrapper {
  max-width: 650px;
  margin: 2rem auto;
  padding: 0 1rem;
}

.question-wrapper {
  border: 3px rgba(255, 255, 255, 0.2) solid;
  padding: 0.25rem;
  border-radius: 15px;
}

.question {
  background: $white;
  background-image: url(../assets/images/texture.jpg);
  color: $text-color-dark;
  border-radius: 10px;
  padding: 1.5rem;
  box-shadow: 0 4px 40px -5px rgba(0, 0, 0, 0.9);
  overflow: hidden;

  h3 {
    font-family: $font-headline;
    font-size: 2rem;
    padding: 1rem 1.5rem 1.5rem 1.5rem;
  }
}

.question-image {
  margin: -3rem -3rem 1rem -3rem;
  max-height: 200px;
  overflow: hidden;
  border-bottom: 4px $secondary-color solid;
}
</style>
