<template>
  <div class="spinner">
    <div class="spinner__inner">
      <OrnamentCircle :color="color.ornament" />

      <div class="spinner__line">
        <SpinnerThumbnail
          v-for="i in 10"
          :key="`food-${i}`"
          :src="list[i - 1]"
          :deg="(i + step - 1) * 36"
        />
      </div>
    </div>

    <transition name="twist" tag="div">
      <SpinnerSelected :key="selected" custom-class="shadow" :src="list[selected]" />
    </transition>

    <a class="spinner__left-button" href="#" @click.prevent="spinLeft()">
      <IconArrowDownCircle :color="color.button" />
    </a>
    <a class="spinner__right-button" href="#" @click.prevent="spinRight()">
      <IconArrowDownCircle :color="color.button" />
    </a>
  </div>
</template>

<script>
export default {
  name: 'FoodSpinner',
  data () {
    return {
      step: 0,
      selected: 0,
      list: [
        '/img/food/food-1.png',
        '/img/food/food-2.png',
        '/img/food/food-3.png',
        '/img/food/food-4.png',
        '/img/food/food-5.png',
        '/img/food/food-6.png',
        '/img/food/food-7.png',
        '/img/food/food-8.png',
        '/img/food/food-9.png',
        '/img/food/food-10.png'
      ]
    }
  },
  computed: {
    color () {
      const isEven = this.step % 2 === 0

      return {
        ornament: isEven ? 'pink' : 'green',
        button: isEven ? 'orange' : 'green'
      }
    }
  },
  watch: {
    step () {
      this.$emit('interact', {
        color: this.color.button
      })
    }
  },
  methods: {
    spinLeft () {
      this.step--

      if (this.selected === 9) {
        this.selected = 0
        return
      }

      this.selected++
    },
    spinRight () {
      this.step++

      if (this.selected === 0) {
        this.selected = 9
        return
      }

      this.selected--
    }
  }
}
</script>

<style lang="scss" scoped>
  .spinner {
    position: relative;
    width: 1177px;
    height: 1177px;

    &__inner {
      position: relative;
      width: 100%;
      height: 100%;
      border-radius: 100%;
      overflow: hidden;
    }

    &__line {
      position: absolute;
      transform: translateX(-50%);
      bottom: -280px;
      left: 50%;
      width: 560px;
      height: 560px;
      background-image: url('/img/ornament/dashed-circle.png');
    }

    &__thumbnail {
      position: absolute;
      top: 0;
      left: 50%;
      transform: translate(-50%, -50%) rotate(0deg);
      transform-origin: 50px 330px;
      width: 100px;
      height: 100px;
      border-radius: 100%;
    }

    &__selected {
      position: absolute;
      bottom: -150px;
      left: calc(50% - 150px);
      width: 300px;
      height: 300px;
      border-radius: 100%;
    }

    &__left-button {
      position: absolute;
      bottom: -150px;
      left: 295px;
    }

    &__right-button {
      position: absolute;
      bottom: -150px;
      right: 295px;
    }
  }
</style>
