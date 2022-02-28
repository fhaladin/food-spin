<template>
  <div :class="thumbnailClass" :style="style">
    <img :src="src" alt="Food Thumbnail" width="100%">
  </div>
</template>

<script>
export default {
  name: 'SpinnerThumbnail',
  props: {
    thumbnailClass: {
      type: String,
      default: 'spinner__thumbnail'
    },
    deg: {
      type: [String, Number],
      required: true
    },
    src: {
      type: String,
      required: true
    }
  },
  computed: {
    style () {
      const deg = parseInt(this.deg)

      return {
        transform: `translate(-50%, -50%) rotate(${deg}deg)`,
        transition: '1s'
      }
    }
  }
}
</script>
