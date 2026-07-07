

<template>
  <div className="user">
    <button @click="deleteUser(index)">Удалить</button>
    <h3>{{user.name}}</h3>
    <p>{{user.email}} - <b>{{user.password}}</b></p>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      typeL: Object,
      required: true
    },
    index: {
      tye: Number,
      required: true
    },
    deleteUser: {
      type: Function,
      required: true
    }
  }
}
</script>

<style scoped>

button{
  border: 0;
  border-radius: 5px;
  outline: none;
  padding: 10px 15px;
  background: #a51ccb;
  color: #600c3c;
  font-weight: bold;
  cursor: pointer;
  transition: trasform 5s ease;
  float: right;
}
button:hover{
  transform: translateY(-5px);
}
</style>