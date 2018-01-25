<template>
  <header class="top-header is-fixed-top">
    <div class="top-header-brand">
      <a href="https://compromis.net">
        <img src="https://compromis.net/wp-content/themes/Compromis/images/logo-compromis-retina.png" alt="Compromís" />
      </a>
    </div>

    <div class="top-header-band-title">
      <a href="#" @click.prevent="toggleArchive" class="quiz-archive-link">
        Quizzes
        <span :class="{ 'chevron': true, 'chevron-open': archiveShown }">
          <Chevron />
        </span>
      </a>
    </div>
    <div class="top-header-band-social">
      <div class="navbar-item">
        <div class="field is-grouped">
          <p class="control">
           <iframe src="https://www.facebook.com/plugins/like.php?href=https://compromis.net/fake-news/&width=198&layout=button_count&action=like&size=large&show_faces=false&share=true&height=37&appId=252515324782640&locale=ca_ES" width="213" allowtransparency="true" scrolling="no" class="header-social-plugins-facebook" frameborder="0" height="30"></iframe>
          </p>
          <p class="control">
            <iframe :src="'https://platform.twitter.com/widgets/tweet_button.html?size=l&url=https://compromis.net/fake-news&via=compromis&related=compromis&text=' + encodeURIComponent(tweet) + '&lang=es'" class="header-social-plugins-twitter" width="140" height="30" allowtransparency="true" scrolling="no" frameborder="0"></iframe>
          </p>
        </div>
      </div>
    </div>
    <transition name="slide">
      <quiz-archive v-show="archiveShown" />
    </transition>
  </header>
</template>

<script>
import QuizArchive from './QuizArchive'
import Chevron from '../assets/images/chevron.svg'

export default {
  name: 'app-header',

  components: {
    QuizArchive,
    Chevron
  },

  data () {
    return {
      archiveShown: false,
      tweet: 'QUIZ: Com de vulnerable ets a les Fake News?'
    }
  },

  methods: {
    toggleArchive () {
      if (this.archiveShown) {
        this.archiveShown = false
      } else {
        this.archiveShown = true
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../variables';

.top-header {
  display: flex;
  position: fixed;
  z-index: 10000;
  top: 0;
  left: 0;
  right: 0;
  height: 50px;
  background: linear-gradient(270deg, $orange-start, $orange-end);
  background-size: 200% 100%;
  animation: HeaderOrange 15s ease infinite;
  box-shadow: 0 1px 100px -10px rgba(0, 0, 0, 0.6);
}

.top-header-brand {
  background: #fff;
  padding: 0.5rem 1.5rem;
  flex-shrink: 0;

  img {
    width: 160px;
    margin-bottom: -0.5rem;
  }
}

.top-header-band-title {
  display: flex;
  align-items: center;
  margin-right: auto;

  .quiz-archive-link {
    color: #fff;
    font-size: 1.25rem;
    margin: 0 0 0 20px;

    &:hover {
      text-decoration: underline;
    }
  }
}

.top-header-band-social {
  display: none;
}

.header-social-plugins {
  &-facebook,
  &-twitter {
    margin-top: 4px;
    margin-bottom: -5px;
  }
}

.chevron svg {
  position: relative;
  top: 5px;
  width: 20px;
  height: 20px;
}

.chevron-open svg {
  transform: rotate(180deg);
}

@keyframes HeaderOrange {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

@media (min-width: 769px) {
  .top-header-band-social {
    display: flex;
  }
}
</style>
