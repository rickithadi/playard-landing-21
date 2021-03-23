<template>
  <div>
    <section class="home">
      <div
        class="py-24 md:py-36 mx-auto flex flex-wrap flex-col md:flex-row items-center"
        style="padding-top: 0px;"
      >
        <div class="flex flex-col w-full xl:w-3/5 justify-center lg:items-start overflow-y-hidden">
          <div v-html="$md.render(welcomeText)" class="home__welcome markdown" />

          <div class="mb-12 xl:mb-0">
            <h4 v-if="isSignedUp">Thank you - we'll be in touch shortly.</h4>

            <form
              v-else
              @submit.prevent="handleSubmit"
              name="signups"
              netlify
              netlify-honeypot="bot-field"
              class="flex items-center border-b border-b-2 border-blue-400 py-2"
            >
              <p class="hidden">
                <input name="bot-field" />
              </p>
              <input
                ref="emailInput"
                v-model="form.email"
                class="appearance-none mb-36 bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none"
                required
                type="text"
                name="email"
                placeholder="your@email.com"
                aria-label="Email address"
              />

              <button
                class="flex-shrink-0 bg-blue-500 hover:bg-blue-700 border-blue-500 hover:border-blue-700 text-sm border-4 text-white py-1 px-2 pb-2 rounded"
                type="submit"
              >
                I'm keen
              </button>
            </form>
          </div>
        </div>
        <div class="flex flex-col w-full xl:w-2/5">
          <Kick alt="Playard kick man" />
        </div>
      </div>
    </section>

    <div class="py-12 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="lg:text-center">
          <h2 class="text-base text-indigo-600 font-semibold tracking-wide uppercase">
            Come join the revolution
          </h2>
          <p
            class="py-1 mt-2 text-3xl leading-8 font-extrabold tracking-tight text-gray-900 sm:text-4xl"
          >
            The social sport platform for the 21st century
          </p>
          <p class="py-1 mt-4 max-w-2xl text-xl text-gray-500 lg:mx-auto">
            Playard is a modern solution to an age old problem
          </p>
        </div>

        <div class="mt-5">
          <dl class="space-y-10 md:space-y-0 md:grid md:grid-cols-2 md:gap-x-8 md:gap-y-10">
            <div class="py-5 flex mt-0">
              <div class="flex-shrink-0">
                <div
                  class="flex items-center justify-center h-12 w-12 rounded-md bg-indigo-500 text-white"
                >
                  <!-- Heroicon name: outline/globe-alt -->
                  <svg
                    class="h-6 w-6"
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                    aria-hidden="true"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 9a9 9 0 01-9-9m9 9c1.657 0 3-4.03 3-9s-1.343-9-3-9m0 18c-1.657 0-3-4.03-3-9s1.343-9 3-9m-9 9a9 9 0 019-9"
                    />
                  </svg>
                </div>
              </div>
              <div class="ml-4">
                <dt class="text-lg leading-6 font-medium text-gray-900">
                  Connect to a global network of like minded players
                </dt>
                <div class="mt-1 text-base text-gray-500">
                  Join a community of social sportsmen from all over the world. Compete, befriend
                  and connect.
                </div>
              </div>
            </div>

            <div class="py-5 flex mt-0">
              <div class="flex-shrink-0">
                <div
                  class="flex items-center justify-center h-12 w-12 rounded-md bg-indigo-500 text-white"
                >
                  <!-- Heroicon name: outline/scale -->
                  <svg
                    class="h-6 w-6"
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                    aria-hidden="true"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M3 6l3 1m0 0l-3 9a5.002 5.002 0 006.001 0M6 7l3 9M6 7l6-2m6 2l3-1m-3 1l-3 9a5.002 5.002 0 006.001 0M18 7l3 9m-3-9l-6-2m0-2v2m0 16V5m0 16H9m3 0h3"
                    />
                  </svg>
                </div>
              </div>
              <div class="ml-4">
                <dt class="text-lg leading-6 font-medium text-gray-900">No hidden fees</dt>
                <dd class="mt-1 text-base text-gray-500">
                  Our transparent fee structure combined with a freemium model ensures you never get
                  blindsided and ensures a fair playing model.
                </dd>
              </div>
            </div>

            <div class="py-5 flex mt-0">
              <div class="flex-shrink-0">
                <div
                  class="flex items-center justify-center h-12 w-12 rounded-md bg-indigo-500 text-white"
                >
                  <!-- Heroicon name: outline/lightning-bolt -->
                  <svg
                    class="h-6 w-6"
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                    aria-hidden="true"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M13 10V3L4 14h7v7l9-11h-7z"
                    />
                  </svg>
                </div>
              </div>
              <div class="ml-4">
                <dt class="text-lg leading-6 font-medium text-gray-900">Find games instantly</dt>
                <dd class="mt-1 text-base text-gray-500">
                  Harness the power of modern tech to solve the age old problem of finding suitable
                  sports kakis.
                </dd>
              </div>
            </div>

            <div class="py-5 flex mt-0">
              <div class="flex-shrink-0">
                <div
                  class="flex items-center justify-center h-12 w-12 rounded-md bg-indigo-500 text-white"
                >
                  <!-- Heroicon name: outline/annotation -->
                  <svg
                    class="h-6 w-6"
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                    aria-hidden="true"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M7 8h10M7 12h4m1 8l-4-4H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-3l-4 4z"
                    />
                  </svg>
                </div>
              </div>
              <div class="ml-4">
                <dt class="text-lg leading-6 font-medium text-gray-900">Mobile notifications</dt>
                <dd class="mt-1 text-base text-gray-500">
                  Use playard anywhere. Mobile, desktop or tablet you receive updates anywhere
                  anytime.
                </dd>
              </div>
            </div>
          </dl>
        </div>
      </div>
    </div>

    <div class="grid grid-flow-row auto-rows-max md:auto-rows-min">
      <div class="p-8">
        <img
          src="@/assets/Frame1.png"
          alt="screenshot"
          class="float-right md:float-left"
          style="height: 70vh; width: auto;"
        />
        <p
          class="mt-2 text-3xl leading-8 font-extrabold tracking-tight text-center text-gray-900 sm:text-4xl leading-loose"
          style="padding-top: 20%;"
        >
          Select from a curated range of Sports
        </p>
      </div>
      <div class="p-8">
        <img
          src="@/assets/Frame2.png"
          alt="screenshot"
          class="float-left md:float-right"
          style="height: 70vh; width: auto;"
        />
        <p
          class="mt-2 text-3xl leading-8 font-extrabold tracking-tight text-center text-gray-900 sm:text-4xl leading-loose"
          style="padding-top: 20%;"
        >
          Search for a game according to your preferences
        </p>
      </div>

      <div class="p-8">
        <img
          src="@/assets/Frame3.png"
          alt="screenshot"
          class="float-right md:float-left"
          style="height: 70vh; width: auto;"
        />
        <p
          class="mt-2 text-3xl leading-8 font-extrabold tracking-tight text-center text-gray-900 sm:text-4xl leading-loose"
          style="padding-top: 20%;"
        >
          View potential opponents in the pre game Lobby
        </p>
      </div>
      <div class="p-8">
        <img
          src="@/assets/Frame4.png"
          alt="screenshot"
          class="float-left md:float-right"
          style="height: 70vh; width: auto;"
        />
        <p
          class="mt-2 text-3xl leading-8 font-extrabold tracking-tight text-center text-gray-900 sm:text-4xl leading-loose"
          style="padding-top: 20%;"
        >
          Keep track of your progress and earn achievements. Gamify your sport!
        </p>
      </div>
    </div>
    <section class="contact">
      <div class="mb-12 xl:mb-0">
        <h4 v-if="isContacted">Thank you - we'll be in touch shortly.</h4>

        <form
          v-else
          @submit.prevent="handleSubmitContact"
          name="contact"
          netlify
          netlify-honeypot="bot-field"
        >
          <p class="hidden">
            <input name="bot-field" />
            <input type="hidden" value="contact" name="contact" />
          </p>

          <h3 class="text-2xl text-gray-900 font-semibold">Get in touch!</h3>
          <p class="text-gray-600">Alternatively email us at hello@playard.sg</p>
          <div class="flex space-x-5 mt-3">
            <input
              type="text"
              required
              v-model="contactForm.name"
              name="name"
              aria-label="playard"
              placeholder="Your Name"
              class="border p-2 w-1/2"
            />
            <input
              aria-label="playard"
              type="text"
              name="subject"
              required
              v-model="contactForm.subject"
              placeholder="Subject"
              class="border p-2 w-1/2"
            />
            <input
              aria-label="playard"
              type="email"
              ref="CemailInput"
              name="email"
              required
              v-model="contactForm.email"
              placeholder="Your Email"
              class="border p-2 w-1/2"
            />
          </div>
          <textarea
            name="query"
            id="query"
            aria-label="playard"
            cols="10"
            rows="3"
            placeholder="How can we help?"
            required
            v-model="contactForm.query"
            class="border p-2 mt-3 w-full"
          ></textarea>
          <p class="font-bold text-sm mt-3">GDPR Agreement *</p>
          <div class="flex items-baseline space-x-2 mt-2 pb-5">
            <input aria-label="playard" type="checkbox" id="" class="inline-block" required />
            <p class="text-gray-600 text-sm">
              I consent to having this website store my submitted information so they can respond to
              my inquiry.
            </p>
          </div>

          <button
            class="flex-shrink-0 bg-blue-500 hover:bg-blue-700 border-blue-500 hover:border-blue-700 text-sm border-4 text-white py-1 px-2 rounded p-2"
            type="submit"
          >
            Submit
          </button>
        </form>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';
import settings from '@/content/settings/general.json';
import Kick from './Kick.vue';

@Component({
  // Called to know which transition to apply
  transition() {
    return 'slide-left';
  },
  components: {
    Kick,
  },
})
export default class Home extends Vue {
  welcomeText = settings.welcomeText;

  get posts(): Post[] {
    return this.$store.state.posts;
  }

  isSignedUp = false;

  isContacted = false;

  contactForm = {
    name: '',
    email: '',
    subject: '',
    query: '',
  };

  form = {
    email: '',
  };

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
        body: this.encode({ 'form-name': 'signups', ...this.form }),
      });

      this.isSignedUp = true;
    } catch (error) {
      console.error(error);
    }
  }

  async handleSubmitContact(): Promise<void> {
    if (!this.validEmail(this.contactForm.email)) {
      this.$refs.CemailInput.focus();
      return;
    }

    try {
      await fetch('/', {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
        body: this.encode({ 'form-name': 'contact', ...this.contactForm }),
      });

      this.isContacted = true;
    } catch (error) {
      console.error(error);
    }
  }
}
</script>
