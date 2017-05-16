<template>
  <div class="TodoList">
    <input type="text" name="todo" @change="addItem">
    <ul>
      <li v-for='todo in todos'>
       <input type="checkbox" :value="todo.text"/>{{todo.text}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data () {
    return {
      todos: [
        {text: '学习JavaScript'},
        {text: '学习vue'},
        {text: '学习css'}
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li{
  list-style: none;
}
</style>
