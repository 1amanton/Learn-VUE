<template>
  <div id="user-card">
    <img src="@/assets/monkey.png" alt="">

    <div class="description">
      <span id="fullname">{{ getAuthorFullName }}</span>
      <ul class="list">
        <li>Harder</li>
        <li>Better</li>
        <li>Faster</li>
        <li>Stronger</li>
      </ul>
    </div>

    <div class="members">
      <span class="members__title">Участников: {{ members.length }}</span>
      <ul class="list">
        <li
            v-for="member in members"
            :key="member.id"
        >
          {{ member.id }} - {{ member.name }}
        </li>
      </ul>
      <div class="pages">
        <div class="pages__btn">
          <button
              @click="prevPage"
          >Пред</button>

          <button
              v-for="page in pages"
              :key="page"
              @click="currentPage = page"
          > {{ page }}</button>

          <button
              @click="nextPage"
          >След</button>
        </div>
        <span>Страница {{ currentPage }} из {{ pages }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserCard",

  data() {
    return {
      author: {
        firstName: "Anton",
        secondName: "Vasil'evich",
        lastName: "Ltvn"
      },

      members: [
        {
          id: 1,
          name: "Иван Петров"
        },
        {
          id: 2,
          name: "Петр Иванов"
        },
        {
          id: 3,
          name: "Василий Сидоров"
        },
        {
          id: 4,
          name: "Илья Андреев"
        }
      ],

      pages: 5,
      currentPage: 1
    }
  },

  methods: {
    loadUsers(page) {
      console.log(`Загрузка пользователей: страница ${page}`)
    },

    nextPage() {
      if(this.currentPage < this.pages) {
        this.currentPage++
      } else {
        console.log(`Вы находитесь на последней странице`)
      }
    },

    prevPage() {
      if(this.currentPage > 1) {
        this.currentPage--
      } else {
        console.log(`Вы находитесь на первой странице`)
      }
    }
  },

  computed: {
    getAuthorFullName() {
      return `${this.author.firstName} ${this.author.secondName} ${this.author.lastName}`.toUpperCase()
    }
  },

  watch: {
    currentPage(newValue, oldValue) {
      console.log(`newValue: ${newValue}`)
      console.log(`oldValue: ${oldValue}`)
      this.loadUsers(newValue)

    }
  }
}
</script>

<style>
#user-card {
  margin-top: 2rem;
  display: flex;
}
#fullname {
  font-size: 1.5rem;
  letter-spacing: 2px;
  font-weight: 700;
  margin-bottom: 1rem;
}

.description {
  display: flex;
  flex-direction: column;
  margin-left: 1rem;
}
.list {
  list-style-type: none;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.members {
  border: 1px solid #666;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  margin-left: 3rem;
}

.members__title {
  margin-bottom: 1rem;
  font-weight: 700;
  font-size: 1.5rem;
}

.pages {
  margin-top: 1rem;
}

button {
  padding: 0.25rem;
}
</style>