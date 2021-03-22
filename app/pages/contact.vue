<template>
  <section class="page">
    <h1 class="page__title text-lg md:text-xl lg:text-4xl xl:text-6xl text-center py-8 md:py-16">
      Contact us
    </h1>

    <h4 v-if="isSignedUp">Thank you - we'll be in touch shortly.</h4>

    <form v-else @submit.prevent="handleSubmit" name="contact" netlify netlify-honeypot="bot-field">
      <p class="hidden">
        <input name="bot-field" />
        <input type="hidden" value="contact" name="contact" />
      </p>

      <div
        class="icon bg-blue-600 text-white w-6 h-6 absolute flex items-center justify-center p-5"
        style="left: -40px;"
      ></div>
      <h3 class="text-2xl text-gray-900 font-semibold">Get in touch!</h3>
      <p class="text-gray-600">Alternatively email us at hello@playard.sg</p>
      <div class="flex space-x-5 mt-3">
        <input
          type="text"
          required
          ref="nameInput"
          v-model="form.name"
          name="name"
          id="name"
          aria-label="playard"
          placeholder="Your Name"
          class="border p-2 w-1/2"
        />
        <input
          aria-label="playard"
          type="text"
          ref="subInput"
          name="subject"
          required
          v-model="form.subject"
          id="subject"
          placeholder="Subject"
          class="border p-2 w-1/2"
        />
        <input
          aria-label="playard"
          type="email"
          ref="emailInput"
          name="email"
          required
          v-model="form.email"
          id="email"
          placeholder="Your Email"
          class="border p-2 w-1/2"
        />
      </div>
      <textarea
        name="query"
        id="query"
        aria-label="playard"
        ref="queryInput"
        cols="10"
        rows="3"
        placeholder="How can we help?"
        required
        v-model="form.query"
        class="border p-2 mt-3 w-full"
      ></textarea>
      <p class="font-bold text-sm mt-3">GDPR Agreement *</p>
      <div class="flex items-baseline space-x-2 mt-2 pb-5">
        <input aria-label="playard" type="checkbox" id="" class="inline-block" required />
        <p class="text-gray-600 text-sm">
          I consent to having this website store my submitted information so they can respond to my
          inquiry.
        </p>
      </div>

      <button
        class="flex-shrink-0 bg-blue-500 hover:bg-blue-700 border-blue-500 hover:border-blue-700 text-sm border-4 text-white py-1 px-2 rounded p-2"
        type="submit"
        value="submit"
      >
        Submit
      </button>
    </form>
  </section>
</template>

<script lang="ts">
import { Vue } from 'nuxt-property-decorator';

export default class Contact extends Vue {
  form = {
    email: '',
    name: '',
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

    console.log('fuc', this.form);
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
