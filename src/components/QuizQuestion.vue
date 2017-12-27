<template>
  <div :class="{ 'question-outer-wrapper': true, 'question-hidden': !visible }" :id="'q' + question.id">
    <div class="question-wrapper">
      <div class="question">
        <div class="question-image">
          <img :src="question.thumbnail" alt="Imatge de la noticia" />
        </div>
        <h3>{{ question.name }}</h3>

        <div class="columns question-options">
          <div class="column" v-for="option in question.options">
            <quiz-option
              :key="question.options.indexOf(option)"
              :option="option"
              :selected="selectedOption.name == option.name"
              :question-id="question.id"
              :disabled="selectedOption.name != null || !visible"
              @change="selectOption" />
          </div>
        </div>

        <div :id="'a' + question.id">
          <transition name="slide">
            <div class="answer" v-if="selectedOption.name">
              <div :class="{ 'answer-wrapper': true, 'answered-correctly': selectedOption.points > 0, 'answered-incorrectly': selectedOption.points == 0 }">
                <div class="answer-icon">
                  <Thumbs :class="{ 'upside-down': selectedOption.points == 0 }" />
                </div>
                <img :src="selectedOption.gif" alt="Gif" class="answer-gif" />
                <h4>{{ selectedOption.message }}</h4>
                <p>{{ question.message }}</p>
                <p v-if="nextQuestionId" class="next-button"><a :href="'#q' + nextQuestionId" v-scroll-to="'#q' + nextQuestionId">Següent notícia</a></p>
                <p v-else class="next-button"><a href="#results" v-scroll-to="'#results'">Resultats</a></p>
              </div>
            </div>
          </transition>
        </div>
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
    question: Object,
    visible: Boolean,
    nextQuestionId: [Number, Boolean]
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
      this.$emit('nextQuestion', this.question.id + 1)
      this.$scrollTo('#a' + this.question.id, 500, { offset: -140 })
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

.question-hidden {
  opacity: 0.5;
}

.question-wrapper {
  border: 3px rgba(255, 255, 255, 0.2) solid;
  padding: 5px;
  border-radius: 15px;
}

.next-button {
  margin-top: 1.5rem;

  a {
    color: $text-color-dark;
    border:  2px $text-color-dark solid;
    padding: 0.25rem 1rem;
    border-radius: 20px;
    transition: 0.2s ease-in-out;

    &:hover {
      background: $text-color-dark;
      color: #fff;
    }

    &:hover {

    }
  }
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
    font-size: 1.5rem;
    padding: 0.5rem 0;
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

.question-options {
  margin-bottom: 0;

  .column {
    padding-bottom: 0;
  }
}

.answer {
  position: relative;
  background: $white;
  margin: 1.5rem -1.5rem -1.5rem -1.5rem;

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

@media (min-width: 769px) {
  .question {
    h3 {
      font-size: 2rem;
      padding: 1rem 1.5rem 1.5rem 1.5rem;
    }
  }
}
</style>
