<template>
  <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
    <circle cx="20" cy="20" r="20" :fill="fill" style="transition: fill 1s ease;" />
    <path d="M20 26L26 20M20 26L14 20M20 26V14" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
  </svg>
</template>

<script>
export default {
  name: 'ArrowDownCircle',
  props: {
    color: {
      type: String,
      required: true,
      validator: (value) => {
        return ['orange', 'green'].includes(value)
      }
    }
  },
  computed: {
    fill () {
      return this.color === 'orange' ? '#FF922C' : '#54BF29'
    }
  }
}
</script>
