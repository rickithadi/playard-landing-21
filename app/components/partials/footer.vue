<template>
  <footer class="footer -mx-4 md:mx-0" style="width: 100vw;">
    <div class="container mx-auto pb-6 flex justify-center">
      <a href="https://twitter.com/playard_sg" class="social" target="_blank">
        <img style="height: 50px; weight: 50px;" alt="linkedin" src="@/assets/twitter.svg" />
      </a>
      <a href="https://linkedin.com/company/playard" class="social" target="_blank">
        <img style="height: 50px; weight: 50px;" alt="linkedin" src="@/assets/linkedin.svg" />
      </a>
      <a href="https://instagram.com/playard_sg" class="social" target="_blank">
        <img style="height: 50px; weight: 50px;" alt="linkedin" src="@/assets/insta.svg" />
      </a>
      <a href="https://t.me/playardsg" class="social" target="_blank">
        <img style="height: 50px; weight: 50px;" alt="linkedin" src="@/assets/tele.svg" />
      </a>
    </div>
  </footer>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';

@Component
export default class Footer extends Vue {}
</script>

<style lang="scss">
.social {
  padding: 10px;
}
.footer {
  background-color: $bluise;
}
</style>
