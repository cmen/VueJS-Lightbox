<template>
  <div class="lightbox" v-if="image" @click="close">
    <transition :name="transition">
      <lightbox-image :image="image" :key="image"></lightbox-image>
    </transition>
    <div class="lightbox-close" @click="close"></div>
    <div class="lightbox-btn lightbox-prev" @click.stop.prevent="prev"></div>
    <div class="lightbox-btn lightbox-next" @click.stop.prevent="next"></div>
  </div>
</template>

<script>
import './LightboxDirective'
import LightboxImage from './LightboxImage'
import store from './LightboxStore'

export default {
  name: 'Lightbox',
  components: {
    LightboxImage
  },
  data () {
    return {
      state: store.state,
      direction: 'next'
    }
  },
  methods: {
    close () { store.close() },
    prev () {
      this.direction = 'prev'
      store.prev()
    },
    next () {
      this.direction = 'next'
      store.next()
    }
  },
  computed: {
    image () {
      if (this.state.index !== false) {
        return this.state.images[this.state.group][this.state.index]
      }
    },
    transition () {
      return 'lightbox-' + this.direction
    }
  }
}
</script>

<style src="./lightbox.scss" lang="scss"></style>
