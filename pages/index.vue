<template>
  <main>
    <responsive-youtube
      :height="480"
      :width="854"
      autoplay
      class="video"
      video="LOZuxwVk7TU"
    />
  </main>
</template>

<script>
import ResponsiveYoutube from '~/components/responsive-youtube.vue'

export default {
  components: {
    ResponsiveYoutube
  },

  head: {
    title: "Don't you know that you're toxic?"
  }
}
</script>

<style scoped>
  main {
    align-content: center;
    align-items: center;
    background-color: #000;
    display: flex;
    height: 100%;
    justify-content: center;
    width: 100%;
  }

  .video {
    flex: 1 1 auto;
    width: 100%;
  }
</style>
