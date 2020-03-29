<template>
  <div class="main">
    {{text}}
    <ul>
      <li v-for="todo in todos" :key="todo.time">
        <div v-if="todo.completed == false">{{todo.text | capitalize }}</div>
        <div v-else-if="todo.completed == true">{{todo.text | capitalize }} (Completed)</div>
        <div v-else>{{todo.text | capitalize }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Main',
  filters: {
    capitalize (val) {
      return val.toUpperCase()
    }
  },
  data () {
    return {
      text: 'Hello World',
      todos: [
        {
          text: '<strong>Todo1</strong>',
          time: 12345,
          completed: true
        },
        {
          text: 'Todo2',
          time: 12541,
          completed: false
        }
      ]
    }
  }
}
</script>
