<template>
  <div class="container">
    <div>
      <h1 class="title">mecha-app</h1>

      <ul>
        <li v-for="(mech, index) in mecha" :key="index">
          <Mech :mech="mech" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Mech from '@/components/Mech'

export default {
  components: {
    Mech,
  },
  data() {
    return {
      mecha: {},
      raw: {},
      api: 'http://localhost:1337',
    }
  },
  created() {
    fetch('http://localhost:1337/meches', {})
      .then((response) => {
        return response.json()
      })
      .then((data) => {
        this.raw = data

        this.mecha = data.map(({ Name, image, anime }) => {
          return {
            name: Name,
            images: image.map(({ url }) => {
              return {
                url: `${this.api}${url}`,
              }
            }),
            anime,
          }
        })
      })
      .catch((error) => console.log(error))
  },
}
</script>

<style>
body {
  padding: 10px;
}
</style>
