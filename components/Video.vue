<template>
  <iframe
    :width="width"
    :height="height"
    :src="videoUrl"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
  ></iframe>
</template>

<script>
export default {
  props: {
    videoId: {
      type: String,
      required: true,
    },
    width: {
      type: Number,
      required: false,
      default: 560,
    },
    height: {
      type: Number,
      required: false,
      default: 315,
    },
  },
  computed: {
    videoUrl() {
      return `https://www.youtube.com/embed/${this.videoId}`
    },
  },
}
</script>
