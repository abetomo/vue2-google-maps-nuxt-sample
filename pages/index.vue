<template>
  <section class="container">
    <div>
      <app-logo/>
      <h1 class="title">
        vue2-google-maps-sample
      </h1>
      <h2 class="subtitle">
        vue2-google-maps-sample
      </h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green">Documentation</a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey">GitHub</a>
      </div>
    </div>
    <div>
      <gmap-map
        :center=center
        :zoom=zoom
        style="width: 500px; height: 500px">
        <gmap-marker
          :key="index"
          v-for="(m, index) in markers"
          :position="m.position"
          :clickable="true"
          :draggable="true"
          @click="markerClick(m.position)" />
      </gmap-map>
    </div>
  </section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue'
import Vue from 'vue'
import * as VueGoogleMaps from 'vue2-google-maps'

Vue.use(VueGoogleMaps, {
  load: {
    key: API_KEY,
    libraries: 'places,drawing,visualization',
    language: 'ja',
    region: 'JP'
  }
})

export default {
  components: {
    AppLogo
  },
  data () {
    return {
      center: {
        lat: 35.6588126,
        lng: 139.6985006
      },
      zoom: 15,
      markers: [
        {
          position: {
            lat: 35.6588126,
            lng: 139.6985006
          }
        }
      ]
    }
  },
  methods: {
    markerClick: function (position) {
      console.log(JSON.stringify(position))
    }
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

