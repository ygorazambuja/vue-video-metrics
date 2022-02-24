<script>
import Vue from "vue";
import VueVideoMetrics from "@/vue-video-metrics.vue";

export default Vue.extend({
  name: "ServeDev",
  components: {
    VueVideoMetrics,
  },
  methods: {
    onPlay(metrics) {
      console.log(metrics);
    },
  },
});
</script>

<template>
  <div id="app">
    <vue-video-metrics
      src="http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"
      @onPlay="onPlay"
    />
  </div>
</template>
