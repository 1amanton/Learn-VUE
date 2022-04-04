<template>
  <div class="imgz">
    <div class="imgz__wrapper">
      <img v-if="imgVisible"
           class="imgz__monkey"
           :class="imgFilters"
           :style="changeImgSize"
           src="@/assets/monkey.png"

           >

      <p v-else class="imgz__monkey__text">Monkey will come back soon</p>
    </div>

    <button
        @click="imgVisible = !imgVisible" class="show"
    >SHOW/HIDE</button>

    <button class="btnz"
            :class="imgFilters.zsepia ? 'btnz__active' : ''"
            @click="imgFilters.zsepia = !imgFilters.zsepia"
    >sepia</button>

    <button class="btnz"
            :class="imgFilters.zborder ? 'btnz__active' : ''"
            @click="imgFilters.zborder = !imgFilters.zborder"
    >border</button>
    <button class="btnz"
            :class="imgFilters.zcontrast ? 'btnz__active' : ''"
            @click="imgFilters.zcontrast = !imgFilters.zcontrast"
    >contrast</button>

    <label>
      WIDTH : {{ imgSize.currentW }}
      <input type="range"
             :max="imgSize.maxW"
             :min="imgSize.minW"
             :value="imgSize.currentW"
             @input="imgSize.currentW = $event.target.value"
      >
    </label>

    <label>
      HEIGHT : {{ imgSize.currentH }}
      <input type="range"
             :max="imgSize.maxH"
             :min="imgSize.minH"
             :value="imgSize.currentH"
             @input="imgSize.currentH = $event.target.value"
      >
    </label>
  </div>
</template>

<script>
export default {
  name: "ChangeClasses",

  data() {
    return {
      imgVisible: true,

      imgFilters: {
        zsepia: false,
        zborder: false,
        zcontrast: false
      },

      imgSize: {
        maxW: 200,
        minW: 20,
        maxH: 300,
        minH: 30,
        currentW: 100,
        currentH: 150
      }
    }
  },

  computed: {
    changeImgSize() {
      return {
        width: `${this.imgSize.currentW}px`,
        height: `${this.imgSize.currentH}px`
      }
    }
  }
}
</script>

<style scoped lang="sass">
.imgz
  display: flex
  &__wrapper
    height: 300px
    width: 200px
    background-color: aqua
  &__monkey
    width: 100%


.zborder
  border: 3px dashed red
.zsepia
  filter: sepia(100%)
.zcontrast
  filter: contrast(500%)

.show
  background-color: antiquewhite
  height: 3rem
  cursor: pointer

.btnz
  height: 3rem
  cursor: pointer
  &__active
    background-color: aquamarine
</style>