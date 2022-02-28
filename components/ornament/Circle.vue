<template>
  <svg width="1177" height="1177" viewBox="0 0 1177 1177" fill="none" xmlns="http://www.w3.org/2000/svg">
    <circle cx="588.5" cy="588.5" r="588.5" :fill="fill" style="transition: fill 1s ease;" />
  </svg>
</template>

<script>
export default {
  name: 'CircleOrnament',
  props: {
    color: {
      type: String,
      required: true,
      validator: (value) => {
        return ['pink', 'green'].includes(value)
      }
    }
  },
  computed: {
    fill () {
      return this.color === 'pink' ? '#FFEEDE' : '#EAFFE2'
    }
  }
}
</script>
