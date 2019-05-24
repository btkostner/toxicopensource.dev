<template>
  <!-- An extra div to avoid parents setting width and messing with sizing -->
  <div>
    <div
      :style="style"
      class="container"
    >
      <iframe
        v-bind="$attrs"
        :src="src"
        :width="width"
        :height="height"
        frameborder="0"
        allow="autoplay; encrypted-media"
        allowfullscreen
        v-on="$listeners"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'ResponsiveYoutube',

  props: {
    autoplay: {
      type: Boolean,
      default: false
    },

    height: {
      type: Number,
      default: () => 315
    },

    /**
     * Youtube video ID.
     *
     * @example `3cZFPRrRN_g` from `/watch?v=3cZFPRrRN_g`
     *
     * @var {string}
     */
    video: {
      type: String,
      required: true
    },

    width: {
      type: Number,
      default: () => 560
    }
  },

  computed: {
    ratio () {
      return ((this.height / this.width) * 100)
    },

    style () {
      return { 'padding-bottom': `${this.ratio}%` }
    },

    src () {
      let url = `https://www.youtube-nocookie.com/embed/${this.video}?rel=0&controls=0&showinfo=0`

      if (this.autoplay) {
        url += '&autoplay=1'
      }

      return url
    }
  }
}
</script>


<style scoped>
  .container {
    position: relative;
    padding: 0;
    height: 0;
  }

  iframe {
    height: 100%;
    left: 0;
    position: absolute;
    top: 0;
    width: 100%;
  }
</style>
