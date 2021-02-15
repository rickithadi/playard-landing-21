template>
  <div class="page-transition--biker">
    <div
      v-for="index in 5"
      :key="index"
      :class="`biker-${index}`"
      class="biker">
      <Lottie
        :options="bikerAnimation"
        class="_animation" />
    </div>
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