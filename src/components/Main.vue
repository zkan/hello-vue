<template>
  <div class="main">
    {{text}}
    <ul>
      <li v-for="todo in todos" v-html="todo.text" :key="todo.time">
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Main',
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
