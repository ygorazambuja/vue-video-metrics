<template>
  <video
    ref="videoRef"
    :autoplay="autoplay"
    :controls="controls"
    :muted="muted"
    :width="width"
    :height="height"
    @timeupdate="onTimeUpdated"
    @ended="onEnded"
    @pause="onPause"
    @play="onPlay"
    @volumechange="onVolumeChanged"
    @error="onError"
  >
    <source :src="src" />
    <span>NO data</span>
  </video>
</template>

<script>
export default {
  props: {
    autoplay: {
      type: Boolean,
      default: true,
    },
    src: {
      type: String,
      default: "",
    },
    controls: {
      type: Boolean,
      default: true,
    },
    muted: {
      type: Boolean,
      default: true,
    },
    height: {
      type: Number,
      default: null,
    },
    width: {
      type: Number,
      default: null,
    },
  },
  data: () => ({
    metrics: {
      videoDuration: 0,
      secondsWatched: 0,
      ended: false,
      pausedTimes: 0,
      playedTimes: 0,
      volumeChanged: 0,
    },
  }),

  destroyed() {
    this.onDestroyed();
  },

  methods: {
    onDestroyed() {
      this.$emit("onDestroyed", this.metrics);
    },
    setEnded(status) {
      this.metrics.ended = status;
    },
    onTimeUpdated(e) {
      this.metrics.secondsWatched += 0.24;
      this.setEnded(e.target.ended);
      this.$emit("onTimeUpdated", this.metrics);
    },
    onPause() {
      this.metrics.pausedTimes = this.metrics.pausedTimes + 1;
      this.$emit("onPause", this.metrics);
    },
    onPlay(e) {
      this.metrics.videoDuration = this.$refs.videoRef.duration;
      this.metrics.playedTimes = this.metrics.playedTimes + 1;
      this.$emit("onPlay", this.metrics);
    },
    onEnded() {
      this.setEnded(true);
      this.$emit("onEnded", this.metrics);
    },
    onVolumeChanged() {
      this.metrics.volumeChanged = this.metrics.volumeChanged + 1;
      this.$emit('onVolumeChanged', this.metrics);
    },
    onError(e) {
      throw new Error(e);
    },
    resetMetrics() {
      this.metrics.videoDuration = 0;
      this.metrics.secondsWatched = 0;
      this.metrics.ended = false;
      this.metrics.pausedTimes = 0;
      this.metrics.playedTimes = 0;
      this.metrics.volumeChanged = 0;
    },
  },
};
</script>
