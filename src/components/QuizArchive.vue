<template>
  <div class="quiz-archive">
    <ul>
      <li v-for="quiz in quizzes" v-if="quiz.visible">
        <a :href="quiz.url">
          <img :src="quiz.thumbnail" :alt="quiz.name" />
          <span class="quiz-name">{{ quiz.name }}</span>
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'quiz-archive',

  data () {
    return {
      quizzes: []
    }
  },

  mounted () {
    axios.get('https://compromis.net/quiz/quizzes.php')
      .then((quizzes) => {
        this.quizzes = quizzes.data
      })
  }
}
</script>

<style lang="scss" scoped>
@import '../variables';

.quiz-archive {
  position: fixed;
  top: 50px;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0.8) 0%, rgba(0, 0, 0, 0.2) 80%);

  ul {
    list-style: none;
    margin-right: 1rem;
  }

  li {
    position: relative;
    display: inline-block;
    margin: 1rem;
    margin-right: 0;

    a {
      display: block;
      height: 210px;
      overflow: hidden;
      border: 5px transparent solid;
      transition: 0.1s ease-in-out;

      &:hover {
        border: 5px #fff solid;

        .quiz-name {
          display: block;
        }
      }

      &:active {
        border: 5px $basic-orange solid;

        .quiz-name {
          display: block;
          color: $basic-orange;
        }
      }
    }

    img {
      height: 200px;
    }

    .quiz-name {
      display: none;
      position: absolute;
      top: 5px;
      left: 5px;
      right: 5px;
      bottom: 5px;
      background: rgba(0, 0, 0, 0.5);
      color: #fff;
      padding: 1rem;
      text-shadow: 0 0 7px #000;
    }
  }
}
</style>
