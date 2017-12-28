<template>
  <header class="navbar is-fixed-top">
    <div class="navbar-brand">
      <a href="https://compromis.net">
        <img src="https://compromis.net/wp-content/themes/Compromis/images/logo-compromis-retina.png" alt="Compromís" />
      </a>
    </div>
    <div id="narbarSocialPlugins" class="navbar-menu">
      <div class="navbar-end">
        <div class="navbar-item">
          <div class="field is-grouped">
            <p class="control">
             <iframe src="https://www.facebook.com/plugins/like.php?href=https://compromis.net/fake-news&width=198&layout=button_count&action=like&size=large&show_faces=false&share=true&height=37&appId=252515324782640&locale=ca_ES" width="213" allowtransparency="true" scrolling="no" class="header-social-plugins-facebook" frameborder="0" height="30"></iframe>
            </p>
            <p class="control">
              <iframe :src="'https://platform.twitter.com/widgets/tweet_button.html?size=l&url=https://compromis.net/fake-news&via=compromis&related=compromis&text=' + encodeURIComponent(tweet) + '&lang=es'" class="header-social-plugins-twitter" width="140" height="30" allowtransparency="true" scrolling="no" frameborder="0"></iframe>
            </p>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'app-header',

  data () {
    return {
      tweet: 'Fake News! Posa\'t a prova amb este quiz'
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../variables';

.navbar {
  background: linear-gradient(270deg, $orange-start, $orange-end);
  background-size: 200% 100%;
  animation: HeaderOrange 15s ease infinite;
}

.navbar-brand {
  background: #fff;
  padding: 0.5rem 1.5rem;

  img {
    width: 160px;
    margin-bottom: -0.5rem;
  }
}

.header-social-plugins {
  &-facebook,
  &-twitter {
    margin-top: 4px;
    margin-bottom: -5px;
  }
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
</style>
