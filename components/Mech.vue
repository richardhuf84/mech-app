<template>
  <section class="mech">
    <h3>{{ mech.name }}</h3>
    <figure v-for="({ url }, imageIndex) in mech.images" :key="imageIndex">
      <img :src="url" />
    </figure>

    <Anime :anime="mech.anime" />
  </section>
</template>

<script>
import Anime from '@/components/Anime'

export default {
  props: {
    mech: {
      type: Object,
      required: true,
    },
  },
  components: {
    Anime,
  },
}
</script>
