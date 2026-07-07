<template>
<!--  Работа с переменными и методами-->
<!--  Выводим обьект в тег-->
<!--  <h3> {{info}} </h3>
  <p>{{someInfo}}</p>

  <button type="button" @click="rewriteTitle()">Изменить Заголовок</button>
  <br>
  <br>
  <button type="button" @mouseenter="rewriteParagraph()">Изменить Параграф</button>-->
<!-- Один из способов вывести полученные данные из поля в переменные
     @input="insertData($event.target.value)"-->
  <input type="text" v-model="userName" placeholder="Имя">
  <input type="password" v-model="userPassword" placeholder="Пароль">
  <input type="email" v-model="userEmail" placeholder="Email">
  <p className="error">{{error}}</p>

  <button @click="sendData()">Отправить</button>

  <div v-if="users.length === 0" className="user" >
    У нас нет пользователей.
  </div>

  <User v-for="(el, index) in users" :key="index" :user="el" :index="index" :deleteUser="deleteUser"/>

<!--  <p> Имя: {{userName}} </p>-->
<!--  <p> Пароль: {{userPassword}} </p>-->
<!--  <p> Email: {{userEmail}} </p>-->

</template>

<!--
Скрипты
Атербут setup нужен если у меня есть другие
компоненты
-->
<script>
import User from "./components/User.vue";
// Экспорт обьектов из файла
export default {
  components: {
    User
  },
  // Создаем функцию
  data() {
    return{
      users: [],
      error: "",
      userName: "",
      userPassword: "",
      userEmail: ""

      /*info: 'Title!', // Свойство | Значение
      someInfo: 'Anons of message'*/
    }
  },
  methods: {
    sendData() {
      if (this.userName === '') {
        this.error = 'Имя не найдено';
        return;
      }else if (this.userPassword === '') {
        this.error = 'Пароль не введен';
        return;
      }else if (this.userEmail === '') {
        this.error = 'Email не введен';
        return;
      }

      this.error = '';

      this.users.push({
        name: this.userName,
        password: this.userPassword,
        email: this.userEmail
      })
    },
    deleteUser(index) {
      this.users.splice(index, 1);
    }

    /*insertData(val) {
      this.userName = val
    }*/

    /*rewriteParagraph() {
      this.someInfo = "Some New Message"
    },
    rewriteTitle() {
      this.info = "Some New"
    }*/
  }
}
</script>
<!--Стили-->
<style scoped>
  h3{
    font-weight: lighter;
  }
  
  input{
    display: block;
    margin-bottom: 10px;
    border-radius: 3px;
    border: 1px solid silver;
    outline: none;
    padding: 10px 15px;
    background: #fafafa;
    color: #333;
  }
  
  button{
    border: 0;
    border-radius: 5px;
    outline: none;
    padding: 10px 15px;
    background: #6cd670;
    color: #167f3d;
    font-weight: bold;
    cursor: pointer;
    transition: trasform 500ms ease;
  }
  button:hover{
    transform: translateY(-5px);
  }

  .user{
    width: 500px;
    margin-top: 20px;
    border: 1px solid silver;
    background: #e3e3e3;
    color: #222;
    padding: 20px;
    border-radius: 5px;
  }

  p{
    color: rgb(15, 119, 36);
  }
</style>
