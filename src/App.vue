<template>
<!--  Выводим обьект в тег-->
  <h3> {{info}} </h3>
  <p>{{someInfo}}</p>

  <button type="button" @click="rewriteTitle()">Изменить Заголовок</button>
  <br>
  <br>
  <button type="button" @mouseenter="rewriteParagraph()">Изменить Параграф</button>

</template>

<!--
Скрипты
Атербут setup нужен если у меня есть другие
компоненты
-->
<script>
// Экспорт обьектов из файла
export default {
  // Создаем функцию
  data() {
    return{
      info: 'Title!', // Свойство | Значение
      someInfo: 'Anons of message'
    }
  },
  methods: {
    rewriteParagraph() {
      this.someInfo = "Some New Message"
    },
    rewriteTitle() {
      this.info = "Some New"
    }
  }
}
</script>
<!--Стили-->
<style scoped>
  h3{
    font-weight: lighter;
  }
  p{
    color: rgb(15, 119, 36);
  }
</style>
