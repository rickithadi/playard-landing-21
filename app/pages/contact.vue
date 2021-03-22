<template>
  <section class="page">
    <h1 class="page__title text-lg md:text-xl lg:text-4xl xl:text-6xl text-center py-8 md:py-16">
      Get in Touch
    </h1>

    <div class="mb-12 xl:mb-0">
      <h4 v-if="isSignedUp">Thank you - we'll be in touch shortly.</h4>

      <form
        v-else
        @submit.prevent="handleSubmit"
        name="contact"
        netlify
        netlify-honeypot="bot-field"
        class="w-full max-w-sm"
      ></form>
    </div>
  </section>
</template>

<script lang="ts">
import { Vue } from 'nuxt-property-decorator';

export default class Contact extends Vue {
  form = {
    email: '',
    subject: '',
    query: '',
  };

  isSignedUp = false;

  encode(data): string {
    return Object.keys(data)
      .map((key) => `${encodeURIComponent(key)}=${encodeURIComponent(data[key])}`)
      .join('&');
  }

  validEmail(email): boolean {
    // eslint-disable-next-line
    const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    return re.test(email);
  }

  async handleSubmit(): Promise<void> {
    if (!this.validEmail(this.form.email)) {
      this.$refs.emailInput.focus();
      return;
    }

    try {
      await fetch('/', {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
        body: this.encode({ 'form-name': 'contact', ...this.form }),
      });

      this.isSignedUp = true;
    } catch (error) {
      console.error(error);
    }
  }
}
</script>
