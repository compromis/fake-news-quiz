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
    <h2 class="intro-subheading">N'ets inmune?</h2>
    <p class="intro-description">Ets dels qui pensen que només els “cunyaos” són carnassa de fake news i que estàs prou informat per a diferenciar entre una notícia falsa i una que no ho és? Posa't a prova en el següent quiz!</p>
    <p class="intro-note"><strong>Avís:</strong> Encara que ho semble, estes notícies no van ser publicades el Dia dels Innocents</p>
    <p class="intro-action"><a href="#q1" v-scroll-to="'#q1'">Comença</a></p>
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

.intro .intro-note {
  font-size: 1rem;
  opacity: 0.5;
  strong {
    color: #fff;
  }
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
    padding: 3rem 5rem;

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
