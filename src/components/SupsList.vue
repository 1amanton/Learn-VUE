<template>
  <div class="productlist">

    <div class="search">
      <p>Search Sups</p>
<!--      <input type="text" v-model="searchField">-->
      <MyInput v-model="searchField" />
      <button>Find</button>
      {{ searchField }}
    </div>


    <SupItem v-for="product in products"
             :key="product.id"
             :id="product.id"
             :img="product.img"
             :title="product.title"
             :price="product.price"
             :color="product.color"

             @addToBasket="addToBasket(product)"
    >

    </SupItem>

  </div>
</template>

<script>
import MyInput from "@/components/MyInput"
import SupItem from "@/components/SupItem"
export default {
  name: "SupsList",
  components: {
    MyInput,
    SupItem
  },

  data() {
    return {
      searchField: "",
      products: [
        {
          id: 1,
          img: "https://img2.traektoria.ru/upload/trk_iblock_img/285/12zn0cs0n2ql207nhziiesru8ifooml4.jpg",
          title: "Blue Sup",
          price: 32999,
          color: "Blue"
        },
        {
          id: 2,
          img: "https://img2.traektoria.ru/upload/trk_iblock_img/b49/0bqj0yilsxioxxszcnxlxmr9hs5nk4qv.jpg",
          title: "Light Sup",
          price: 38999,
          color: "Light"
        },
        {
          id: 3,
          img: "https://img3.traektoria.ru/upload/trk_iblock_img/98b/5x9pwsir9rel5z2ptj1mhrvzdpu9xens.jpg",
          title: "Yellow Sup",
          price: 42999,
          color: "Yellow"
        },
        {
          id: 4,
          img: "https://img4.traektoria.ru/upload/trk_iblock_img/a18/ogwro08lug4cguxzw0c9luw3u0b32zju.jpg",
          title: "Lightblue Sup",
          price: 49999,
          color: "Lightblue"
        },
        {
          id: 5,
          price: 0,
          color: "Def"
        }
      ]
    }
  },

  methods: {
    addToBasket(product) {
      console.log(`ID: ${product.id}, PRICE: ${product.price}`)
    }
  }
}
</script>

<style scoped>
.productlist {
  display: flex;
}

.search {
  display: flex;
  flex-direction: column;
}

</style>