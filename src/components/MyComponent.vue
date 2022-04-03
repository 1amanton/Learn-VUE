<template>
  <div class="comp">
    <h1>I am {{ name }}</h1>

    <label>
      Your E-mail
      <input
          type="email"
          :value="account.email"
          @input="emailInput($event.target.value)"
      >
    </label>
    EMAIL: {{ account.email }}

    <br>

    <label>
      Your Password
      <input
          type="password"
          :value="account.pswrd"
          @input="pswrdInput($event.target.value)"
      >
    </label>
    PSWRD: {{ account.pswrd }}

    <br>

    Choose number from 1 to 10:
    <button @click="decrs">-</button>
    <input
        type="number"
        :value="numbers.current"
    >
    <button @click="incrs">+</button>
  </div>

</template>

<script>
export default {
  name: "MyComponent",

  data() {
    return {
      name: "Anton",
      account: {
        email: "mymail@asd.com",
        pswrd: "qwerty"
      },
      numbers: {
        current: 0,
        min: 0,
        max: 10
      }
    }
  },

  methods: {
    emailInput(value) {
      this.account.email = value
    },

    pswrdInput(value) {
      this.account.pswrd = value
    },

    incrs() {
      if (this.numbers.current < this.numbers.max) {
        this.numbers.current++
      } else {
        console.log(`число не может быть больше чем ${this.numbers.max}`)
      }
    },

    decrs() {
      if (this.numbers.current > this.numbers.min ) {
        this.numbers.current --
      } else {
        console.log(`число не может быть меньше чем ${this.numbers.min}`)
      }
    }
  }
}
</script>

<style>

input {
  margin-top: 1rem;
}

</style>