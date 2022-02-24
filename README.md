# Vue Video Metrics

VueVideoMetrics is a HTML5 Video abstraction to get simple video metrics

## Installation

Use the package manager [yarn](https://yarnpkg.com/) or [npm](https://www.npmjs.com/) to install vue-video-metrics.

```bash
yarn add vue-video-metrics
```

or

```bash
npm install vue-video-metrics
```

## Usage

```vue
<template>
  <video-metrics
    :src="require('@/assets/video.mp4')"
    @onDestroyed="handleDestroy"
    @onEnded="handleEnded"
    @onPlay="onPlay"
  />
</template>

<script>
import VideoMetrics from "vue-video-metrics";
export default {
  components: { VideoMetrics },
  methods: {
    onPlay(metrics) {
      console.log(metrics);
    },
    handleDestroy(metrics) {
      console.log(metrics);
    },
    handleEnded(metrics) {
      console.log(metrics);
    },
  },
};
</script>
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)
