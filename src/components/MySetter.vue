<template>
  <div>
    <div class="sttr">
      <div class="fields">

        <h1>Поля</h1>

        <div v-for="(fieldValue, fieldKey, index) in user"
             :key="index"
        >
          <label :for="fieldKey">{{ fieldKey }}: </label>
          <input
              :id="fieldKey"
              type="text"
              v-model="user[fieldKey]"
          >
        </div>

        <div class="addField">
          <button
              @click="fieldAdd"
          >Добавить поле</button>

          <label for="addInp"></label>
          <input id="addInp"
                 type="text"
                 v-model="additionalField"
          >
        </div>
      </div>

      <div class="rndr">
        <h1>Предпросмотр</h1>
        <div v-for="(fieldValue, fieldKey, index) in user"
             :key="index"
        >
          <h1>{{ fieldKey }} :</h1>
          <p>{{ fieldValue }}</p>
        </div>
      </div>
    </div>



    <hr>
    <hr>
    <hr>
  </div>
</template>

<script>
export default {
  name: "MySetter",

  data() {
    return {
      user: {
        name:"",
        secondName: "",
        lastName: ""
      },
      additionalField: ""
    }
  },

  methods: {
    fieldAdd() {
      // this.user[this.additionalField] = ""

      this.$set(this.user, this.additionalField, "")
    }
  }
}
</script>

<style scoped>
.sttr {
  padding: 3rem;
  display: flex;
  justify-content: space-around;
}

</style>