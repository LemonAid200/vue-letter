<template>
  <div class="wrapper">
    <div class="info-wrapper">
      <h3>{{user.company}}</h3>
      <div class="info-inner">
        <button class="random-user-button" @click="setRandomUser">Загрузить случайного пользователя</button>
        <p class="info-inner-text">Имя пользователя</p>
        <input v-model="user.name" class="user-info-input" type="text">
        <p class="info-inner-text">Адрес e-mail</p>
        <input v-model="user.email" class="user-info-input" type="text">
        <p class="info-inner-text">Контактный телефон</p>
        <input v-model="user.phoneNumber" class="user-info-input" type="text">
        <p class="info-inner-text">Основной веб-сайт</p>
        <input v-model="user.link" class="user-info-input" type="text">
      </div>
    </div>

    <div class="letter-wrapper">
      <div class="tokens">
        <span class="input-token-text"><p>Вставить токен:</p></span>
        <span v-for="(token) in tokens" @click="pushToLetter(token)" :key=token class="token"><p>{{ token }}</p></span>
      </div>
        <textarea  v-model="letter" ref="letterInput" placeholder="Dear John..." class="letter-input"> </textarea>
        <div class="localStorage-buttons">
        <button class="localStorage-button" @click="getAndSetLetterFromLocalStorage">Загрузить из localStorage</button>
        <button class="localStorage-button" @click="pushLetterToLocalStorage">Сохранить в localStorage</button>
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
      user: { name: 'Name', email: 'E-mail', phoneNumber: 'p-number', company: 'company', link: 'link' },
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
      this.$refs.letterInput.focus()
    },

    pushToLetter (token) {
      if (this.letter.length !== 0) {
        this.letter += ' '
      }
      this.letter += token
      this.$refs.letterInput.focus()
    },

    pushLetterToLocalStorage () {
      localStorage.setItem('saved-letter', this.letter)
    },

    getAndSetLetterFromLocalStorage () {
      this.letter = localStorage.getItem('saved-letter')
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

template{
  overflow-x: hidden;
}

p{
  margin: 0;
}

html,body { margin: 0 !important;}

.wrapper{
  overflow-x: hidden;
  display: grid;
  grid-template-columns: 20% 80%;
}

@media display and (max-width: 480px) {
  wrapper{
    background-color: red;
  }
}

@media (max-width: 481px) {
  wrapper{
    background-color: rgb(0, 255, 13);
  }
}

.info-wrapper{
  min-width: fit-content;
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
  cursor: pointer;
}

.tokens{
  padding: 10px;
  width: fit-content;
  height: fit-content;
  display: grid;
  grid-template-columns: auto auto auto auto;
}

.random-user-button{
  min-width: fit-content;
  background-color: gray;
  border: 2px solid darkgray;
  cursor: pointer;
}

.info-inner{
  text-align: center;
}

.info-inner-text{
  margin: 3px;
}

.localStorage-button{
  margin-left: 20px;
  margin-top: 5px;
  background-color: rgb(45, 45, 185);
  cursor: pointer;
}

.user-info-input{
  width: 90%;
}

.letter-wrapper{
  background-color: aqua;
}

.letter-input{
  border: 2px solid black ;
  border-radius: 5px;
  width: 90%;
  height: 60%;
  margin-left: 10px;
  padding: 5px;
}

</style>
