<template>
  <footer class="footer">
    <div class="container">
      <h4>Segueix l'activitat de <a href="https://compromis.net" target="_blank"><img src="https://compromis.net/wp-content/themes/Compromis/images/logo-compromis-retina-bw.png" alt="Compromís" class="footer-logo"></a></h4>

      <div class="footer-social-plugins">
        <div>
          <iframe src="https://platform.twitter.com/widgets/follow_button.html?screen_name=compromis&amp;show_screen_name=true&amp;show_count=true&amp;size=l&amp;lang=es" class="footer-social-plugins-twitter" width="200" height="37"></iframe>
        </div>
        <div>
          <iframe src="https://www.facebook.com/plugins/like.php?href=https%3A%2F%2Ffacebook.com%2Fcoaliciocompromis&amp;width=450&amp;layout=standard&amp;action=like&amp;size=large&amp;show_faces=true&amp;share=true&amp;height=80&amp;appId=252515324782640&amp;locale=ca_ES" class="footer__social-plugins__facebook" width="450" height="80" scrolling="no" frameborder="0" allowtransparency="true"></iframe>
        </div>
      </div>
      <hr />
      <p><strong>Fake News Quiz</strong> és una campanya de <a href="https://compromis.net" target="_blank">Compromís</a></p>
      <p><a href="mailto:info@compromis.net">info@compromis.net</a> | 96 382 66 06 | Plaça del Pilar, 1 - 46001 València</p>
      <hr />
    </div>
  </footer>
</template>

<script>
export default {
  name: 'app-footer'
}
</script>

<style lang="scss" scoped>
@import '../variables';

.footer {
  color: #414142;
  padding-bottom: 2rem;

  p {
    font-size: 1rem;
  }

  a {
    color: $basic-orange;

    &:hover {
      text-decoration: underline;
    }
  }

  &-logo {
    opacity: .9;
    height: 30px;
    margin-left: 5px;
    vertical-align: middle;
  }

  &-social-plugins-twitter {
    border: none;
    overflow: hidden;
    width: 300px;
    height: 37px;
    margin-top: 1rem;
  }

  &-social-plugins-facebook {
    border: none;
    overflow: hidden;
    height: 57px;
  }
}
</style>
