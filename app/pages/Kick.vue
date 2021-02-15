<template>
  <div class="page-transition--biker">
    <Lottie :options="bikerAnimation" class="_animation" />
  </div>
</template>

<script>
import animationBiker from '@/assets/soccer.json';
import Lottie from './Lottie.vue';

export default {
  components: {
    Lottie,
  },
  data() {
    return {
      bikerAnimation: {
        animationData: animationBiker,
      },
    };
  },
};
</script>
