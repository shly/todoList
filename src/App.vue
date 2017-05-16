<template>
  <div id="app">
    <h1 v-text="title">{{title}}</h1>
    <input v-model="newItem" @keyup.enter="addNew">
    <ul>
      <li v-for="item in items" :class="{finished: item.isFinished}" @click="toggleClass(item)">
        {{item.label}}
      </li>
    </ul>
  </div>
</template>

<script>
import Store from './store'
export default {
  data () {
    return {
      title: 'this is a todo list',
      items: Store.fetch(),
      newItem: ''
    }
  },
  methods: {
    toggleClass (item) {
      console.log(item.isFinished = !item.isFinished)
    },
    addNew () {
      this.items.push({
        label: this.newItem,
        isFinished: false
      })
    }
  },
  watch: {
    items: {
      handler (items) {
        console.log(items)
        Store.save(items)
      },
      deep: true
    }
  }
}
</script>

<style>
.finished{
  text-decoration: underline;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
ul,li{
  list-style: none;
}
</style>
