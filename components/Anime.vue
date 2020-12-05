<template>
  <section>
    <h1 class="">Anime: {{ anime.name }}</h1>
    <ul>
      <li v-for="({ videoId, name }, vIndex) in videos" :key="vIndex">
        <h2>{{ name }}</h2>
        <Video :video-id="videoId" />
      </li>
    </ul>
  </section>
</template>

<script>
import Video from '@/components/Video'

export default {
  components: {
    Video,
  },
  props: {
    anime: {
      type: Object,
      required: true,
    },
  },
  computed: {
    videos() {
      return this.anime.video.map((video) => {
        return {
          name: video.video_name,
          videoId: video.url,
        }
      })
    },
  },
}
</script>
