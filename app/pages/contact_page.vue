<template>
  <section class="page">
    <h1 class="page__title text-lg md:text-xl lg:text-4xl xl:text-6xl text-center py-8 md:py-16">
      Contact
    </h1>

    <div class="mx-auto flex flex-wrap flex-col items-center">
      <h4 v-if="isSignedUp">Thank you - we'll be in touch shortly.</h4>
      <form
        v-else
        @submit.prevent="handleSubmit"
        name="contact"
        netlify
        class="flex items-center border-b border-b-2 border-blue-400 py-2"
      >
        <input
          ref="emailInput"
          v-model="form.email"
          class="appearance-none mb-36 bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none"
          type="text"
          name="email"
          placeholder="your@email.com"
          aria-label="Email address"
        />
        <input
          ref="subInput"
          v-model="form.subject"
          class="appearance-none mb-36 bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none"
          type="text"
          name="subject"
          placeholder="subject"
          aria-label="subject"
        />

        <textarea
          ref="queryInput"
          v-model="form.query"
          class="appearance-none mb-36 bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none"
          type="text"
          name="query"
          placeholder="enter you query here"
          aria-label="query"
        />

        <button
          class="flex-shrink-0 bg-blue-500 hover:bg-blue-700 border-blue-500 hover:border-blue-700 text-sm border-4 text-white py-1 px-2 rounded"
          type="submit"
        >
          Submit
        </button>
      </form>
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
