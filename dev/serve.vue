<script>
import Vue from 'vue';
import VueVideoMetrics from '@/vue-video-metrics.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    VueVideoMetrics
  }
});
</script>

<template>
  <div id="app">
    <vue-video-metrics />
  </div>
</template>
