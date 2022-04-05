<template>

  <div class="product">
    <span>ID: {{ id }}</span>
    <img class="product__img" :src="img" alt="">
    <span>TITLE: {{ title }}</span>
    <span>PRICE: {{ price }}</span>
    <span>COLOR: {{ color }}</span>

  </div>
</template>

<script>
export default {
  name: "SupItem",

  props: {
    id: Number,
    img: {
      type: String,
      default: "http://cdn.onlinewebfonts.com/svg/img_167183.png"
    },
    title: {
      type: String,
      default: "Default Title"
    },
    price: {
      type: Number,
      required: true
    },
    color: {
      type: String,
      validator(value) {
        return value.length < 50
      }
    }
  },

  data() {
    return {
    }
  }
}
</script>

<style scoped lang="sass">
.product
  height: 420px
  width: 300px
  border: 1px solid black
  padding: 0.5rem
  display: flex
  flex-direction: column

  &__img
    height: 300px
    width: 250px



</style>