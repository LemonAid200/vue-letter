<template>
  <div class="wrapper">
    <div class="info">
      <h3>{{user.company}}</h3>
      <div class="info-inner">
        <button class="random-user-button" @click="setRandomUser">Загрузить случайного пользователя</button>
        <p>Имя пользователя</p>
        <input v-model="user.name" class="user-info-input" type="text">
        <p>Адрес e-mail</p>
        <input v-model="user.email" class="user-info-input" type="text">
        <p>Контактный телефон</p>
        <input v-model="user.phoneNumber" class="user-info-input" type="text">
        <p>Основной веб-сайт</p>
        <input v-model="user.link" class="user-info-input" type="text">
      </div>

    </div>
    <div class="letter">
      <div class="tokens">
        <span class="input-token-text"><p>Вставить токен:</p></span>
        <span v-for="(token) in tokens" :key=token class="token"><p>{{ token }}</p></span>
      </div>
      <input v-model="letter" type="text" class="letter-input">
      <div class="localStorage-buttons">
        <button class="localStorage-button">Загрузить из localStorage</button>
        <button class="localStorage-button">Сохранить в localStorage</button>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data () {
    return {
      users: [
        { name: 'Brad Pitt', email: 'lokoroko@mail.ru', phoneNumber: '8(108) 16-16-76', company: 'google', link: 'google.com' },
        { name: 'Sam Normy', email: 'hellothere@mail.ru', phoneNumber: '8(123) 16-16-34', company: 'yandex', link: 'yandex.ru' },
        { name: 'Naruto Uzumaki', email: 'hokage5@mail.ru', phoneNumber: '8(321) 12-23-45', company: 'konoha.inc', link: 'naruto.com' },
        { name: 'Sakura Haruno', email: 'sakura1998@mail.ru', phoneNumber: '8(243) 43-56-45', company: 'goodgate', link: 'gate.com' }
      ],
      user: { name: 'empty', email: 'empty', phoneNumber: 'empty', company: 'empty', link: 'empty' },
      letter: ''
    }
  },
  computed: {
    tokens () {
      return [this.user.name, this.user.email, this.user.phoneNumber]
    }
  },

  methods: {
    setRandomUser () {
      const index = Math.floor(Math.random() * (this.users.length))
      this.user = this.users[index]
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 0;
  margin: 0;
}

html,body { margin: 0 !important;}

.wrapper{
  display: grid;
  grid-template-columns: 20% 80%;
}

.info{
  background-color: lightgray;
  border: 3px solid grey;
  padding: 10px;
}

.input-token-text{
  text-align: center;
  margin: 10px;
  padding: 5px;
}

.token{
  text-align: center;
  margin: 10px;
  background-color: rgb(29, 153, 29);
  border-radius: 3px;
  padding: 5px;
}

.tokens{
  padding: 10px;
  width: fit-content;
  height: fit-content;
  display: grid;
  grid-template-columns: auto auto auto auto;
}

.random-user-button{
  width: 90%;
  background-color: gray;
  border: 2px solid darkgray;
}

.info-inner{
  text-align: center;
}

.localStorage-button{
  margin: 20px;
  background-color: rgb(45, 45, 185);
}

.user-info-input{
  width: 90%;
}

.letter-input{
  width: 80%;
  height: 40%;
}

</style>
