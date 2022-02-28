<template>
  <div class="spinner__selected" :class="customClass">
    <img :src="src" alt="Selected Food" srcset="">
  </div>
</template>

<script>
export default {
  name: 'SpinnerSelected',
  props: {
    customClass: {
      type: String,
      default: ''
    },
    src: {
      type: String,
      required: true
    }
  }
}
</script>
