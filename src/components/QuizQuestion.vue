<template>
  <div class="question-outer-wrapper">
    <div class="question-wrapper">
      <div class="question">
        <div class="question-image">
          <img :src="question.thumbnail" alt="Imatge de ka noticia" />
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
            <div :class="{ 'answer-wrapper': true, 'answered-correctly': selectedOption.points > 0, 'answered-incorrectly': selectedOption.points == 0 }">
              <div class="answer-icon">
                <Thumbs :class="{ 'upside-down': selectedOption.points == 0 }" />
              </div>
              <img :src="selectedOption.gif" alt="Gif" class="answer-gif" />
              <h4>{{ selectedOption.message }}</h4>
              <p>{{ question.message }}</p>
            </div>
          </div>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import QuizOption from './QuizOption'
import True from '../assets/images/true.svg'
import False from '../assets/images/false.svg'
import Thumbs from '../assets/images/thumbs.svg'

export default {
  name: 'quiz-question',

  components: {
    QuizOption,
    True,
    False,
    Thumbs
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
  padding: 5px;
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
    line-height: 1.25;
    margin-bottom: 1rem;
  }
}

.question-image {
  margin: -3rem -3rem 1rem -3rem;
  max-height: 200px;
  overflow: hidden;
  border-bottom: 4px $secondary-color solid;
}

.answer {
  position: relative;
  background: $white;
  margin: 0 -1.5rem -1.5rem -1.5rem;

  &-icon {
    position: absolute;
    top: 50%;
    left: 1.5rem;
    margin-top: -25px;

    svg {
      width: 50px;
      height: 50px;
      fill: $text-color-dark;
    }

    .upside-down {
      transform: rotate(180deg);
    }
  }

  &-gif {
    max-width: 100%;
  }

  h4 {
    font-weight: bold;
    font-size: 1.75rem;
  }

  p {
    font-size: 1.25rem;
    line-height: 1.25;
  }
}

.answer-wrapper {
  padding: 1.5rem;
  padding-left: 95px;
}

.answered-correctly {
  background: lighten($true-color-end, 25%);
}

.answered-incorrectly {
  background: lighten($false-color-start, 15%);
}

.slide-enter-active, .slide-leave-active {
  transition: opacity .5s;
  height: auto;
  overflow: hidden;
}
.slide-enter, .slide-leave-to {
  opacity: 0;
  height: 0;
  overflow: hidden;
}
</style>
