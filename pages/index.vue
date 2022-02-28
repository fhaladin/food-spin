<template>
  <header class="header">
    <div class="spinner-wrapper">
      <Spinner @interact="interact" />
    </div>

    <transition name="fade" mode="out-in" tag="div">
      <div :key="selected" class="header__content row">
        <div class="col-4">
          <p :class="priceClass">
            ${{ price }}
          </p>
          <h1 class="header__title">
            {{ title[selected] }}
          </h1>
          <p class="header__desc">
            {{ desc[selected] }}
          </p>

          <button class="btn" :class="buttonClass">
            ORDER NOW
          </button>
        </div>
      </div>
    </transition>
  </header>
</template>

<script>
export default {
  name: 'MainPage',
  data () {
    return {
      selected: 1,
      price: 32,
      color: 'orange',
      title: [
        'Asian Cucumber Salad',
        'Green Goddess Chicken Salad'
      ],
      desc: [
        'Asian Cucumber Salad Recipe made with crunchy cucumber, onion, rice wine vinegar, and a few secret ingredients!',
        'It is a non vegetarian salad which consists of the green goddess dressing mixed with chicken, peppers, olives and celery.'
      ]
    }
  },
  computed: {
    priceClass () {
      return `header__price${this.color === 'green' ? '--green' : ''}`
    },
    buttonClass () {
      return `header__button${this.color === 'green' ? '--green' : ''}`
    }
  },
  methods: {
    interact ({ color }) {
      this.color = color
      this.selected = this.selected === 1 ? 0 : 1
      this.price = (Math.random() * (55 - 21) + 21).toFixed(0)
    }
  }
}
</script>

<style lang="scss" scoped>
  .header {
    position: relative;
    width: 100%;
    height: 100vh;
    margin-top: -132px;
    overflow-x: hidden;

    &__content {
      padding: 0 100px;
      padding-top: 285px;
    }

    &__price {
      font-style: normal;
      font-weight: 600;
      font-size: 44px;
      line-height: 66px;
      color: $orange;
      margin: 0;
      transition: color 1s;

      &--green {
        @extend .header__price;
        transition: color 1s;
        color: $green;
      }
    }

    &__title {
      font-style: normal;
      font-weight: 500;
      font-size: 36px;
      line-height: 50px;
      color: $black;
    }

    &__desc {
      font-style: normal;
      font-weight: normal;
      font-size: 13px;
      line-height: 19px;
      color: $black;
    }

    &__button {
      width: 163px;
      height: 48px;
      background-color: $orange;
      border-radius: 69px;
      font-style: normal;
      font-weight: bold;
      font-size: 13px;
      line-height: 19px;
      color: $white;
      transition: background-color 1s;

      &--green {
        @extend .header__button;
        transition: background-color 1s;
        background-color: $green;
      }
    }
  }

  .spinner-wrapper {
    position: absolute;
    right: -180px;
    top: -645px;
  }
</style>
