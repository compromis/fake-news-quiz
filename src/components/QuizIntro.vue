<template>
  <section class="intro container">
    <p><span class="intro-flair">QUIZ</span></p>
    <div class="columns intro-icons">
      <div class="column intro-icon-true is-hidden-mobile">
        <True />
      </div>
      <div class="column">
        <Newspaper />
      </div>
      <div class="column intro-icon-false is-hidden-mobile">
        <False />
      </div>
    </div>
    <h1 class="intro-heading">FAKE NEWS</h1>
    <h2 class="intro-subheading">Eres inmune?</h2>
    <p class="intro-description">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. </p>
    <p class="intro-action"><a href="#q1" v-scroll-to="'#q1'">START</a></p>
  </section>
</template>

<script>
import Newspaper from '../assets/images/newspaper.svg'
import True from '../assets/images/true.svg'
import False from '../assets/images/false.svg'

export default {
  name: 'quiz-intro',

  components: {
    Newspaper,
    True,
    False
  }
}
</script>

<style lang="scss" scoped>
@import '../variables';

.intro {
  padding: 2.5rem;
  text-align: center;
}

.intro-heading {
  font-family: $font-intro;
  font-size: 5rem;
  position: relative;
  text-shadow: 10px 10px 0 $secondary-color;
  transform: skew(0deg, -10deg);
  line-height: 1;
  margin: 2rem 0;
}

.intro-subheading {
  font-size: 2rem;
  letter-spacing: -1px;
  margin-top: 3rem;
  line-height: 1;
}

.intro-flair {
  border: 1px $white solid;
  padding: 0.25rem 1rem;
  border-radius: 20px;
  opacity: 0.75;
}

.intro-icons {
  max-width: 400px;
  margin: 0.5rem auto -2.5rem auto;

  .intro-icon-true svg {
    width: 53px;
  }

  .intro-icon-false svg {
    width: 50px;
  }

  svg {
    width: 100px;
  }
}

.intro-description {
  max-width: 700px;
  margin: 1rem auto;
}

.intro-action {
  margin-top: 2rem;

  a {
    color: #fff;
    border: 2px #fff solid;
    border-radius: 30px;
    padding: 0.5rem 2rem;
    transition: 0.25s ease-in-out;

    &:hover {
      background: #fff;
      color: $background;
    }
  }
}

@media (min-width: 769px) {
  .intro {
    padding: 5rem;

    &-heading {
      font-size: 7rem;
    }

    &-subheading {
      font-size: 2.5rem;
    }

    p {
      font-size: 1.25rem;
    }
  }
}

@media (max-height: 700px) {
  .intro {
    padding-top: 2.5rem;

    &-icons {
      display: none;
    }
  }
}
</style>
