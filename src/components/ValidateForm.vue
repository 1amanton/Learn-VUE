<template>
  <div>
    <form action="" class="validateForm"
          @submit.prevent="checkForm"
    >

      <div>
        <label for="login">Login: </label>
        <input id="login" type="text"
               :class="$v.user.login.$error ? 'inperror' : '' "
               v-model.trim="user.login">
        <p v-if="$v.user.login.$dirty && !$v.user.login.required" class="perror">Обязательное поле</p>
        <p v-if="$v.user.login.required && !$v.user.login.minLength" class="perror">Длинна должна быть больше 5 символов</p>
      </div>

      <div>
        <label for="mail">Mail: </label>
        <input id="mail" type="email"
               :class="$v.user.mail.$error ? 'inperror' : '' "
               v-model.trim="user.mail">
        <p v-if="$v.user.mail.$dirty && !$v.user.mail.required" class="perror">Обязательное поле</p>
        <p v-if="$v.user.mail.required && !$v.user.mail.email" class="perror">Email должен быть в формате mymail@mail.ru</p>
      </div>

      <div>
        <label for="pswrd">Password: </label>
        <input id="pswrd" type="password"
               :class="$v.user.pswrd.$error ? 'inperror' : '' "
               v-model.trim="user.pswrd">
        <p v-if="$v.user.pswrd.$dirty && !$v.user.pswrd.required" class="perror">Обязательное поле</p>
        <p v-if="$v.user.pswrd.required && !$v.user.pswrd.minLength" class="perror">Пароль должен содержать не менее 8 символов</p>
      </div>

      <div>
        <label for="emailAgree">I agree</label>
        <input type="checkbox" name="" id="emailAgree"
               v-model="user.iagree"
        >
      </div>

      <div>
        <label for="male">Male</label>
        <input type="radio" name="gender" id="male"
               value="male"
               v-model="user.gender"
        >

        <label for="famale">Famale</label>
        <input type="radio" name="gender" id="famale"
               value="famale"
               v-model="user.gender"
        >
      </div>

      <div>
        <label for="yesone">Yes One</label>
        <input type="checkbox" name="" id="yesone"
               value="yesone"
               v-model="user.yesArr"
        >
        <label for="yestwo">Yes Two</label>
        <input type="checkbox" name="" id="yestwo"
               value="yestwo"
               v-model="user.yesArr"
        >

      </div>



      <div>
        <label for="country">Country</label>
        <select name="" id="country"
                v-model="user.currentCountry"
        >
          <option
                  v-for="(country, index) in countrys"
                  :key="index"
                  :value="country.val"
          >
            {{ country.label }}
          </option>

        </select>
      </div>

      <div>
        <label for="interest">Interest</label>
        <select name="" id="interest" multiple
                v-model="user.currentInterest"

        >
          <option v-for="(interest, index) in interests"
                  :key="index"
                  :value="interest.val"
          >
            {{ interest.label }}
          </option>

        </select>
      </div>

      <button>VALIDATE!</button>

    </form>

    <hr>
    <hr>
    <hr>
  </div>

</template>

<script>
import { validationMixin } from 'vuelidate'
import { required, minLength, email } from 'vuelidate/lib/validators'

export default {
  mixins: [validationMixin],
  name: "ValidateForm",
  data() {
    return {
      user:{
        login: "",
        mail: "",
        pswrd: "",
        iagree: false,
        gender: "",
        yesArr: [],
        currentCountry: "RU",
        currentInterest: ["IT"],
      },

      countrys: [
        {
          label: "Россия",
          val: "RU"
        },
        {
          label: "Украина",
          val: "UA"
        },
        {
          label: "США",
          val: "USA"
        }
      ],

      interests: [
        {
          label: "Айти",
          val: "it"
        },
        {
          label: "Тату",
          val: "tattoo"
        },
        {
          label: "Грепплинг",
          val: "grappling"
        }
      ]
    }
  },
  validations: {
    user: {
      login: { required, minLength: minLength(5) },
      mail: { required, email },
      pswrd: { required, minLength: minLength(8) }
    }
  },

  methods: {
    checkForm() {
      this.$v.user.$touch()
      if(!this.$v.user.$error) {
        console.log("Валидация прошла успешно")
      }
    }
  }
}
</script>

<style scoped>

.validateForm {
  padding: 3rem ;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  justify-content: center;
  align-items: center;
}

.perror {
  color: red;
}

.inperror {
  border: 3px solid red;
}

</style>