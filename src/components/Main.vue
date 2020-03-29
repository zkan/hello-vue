<template>
  <div class="main">
    <TodoList :todoItems="getSortedItems" @save="addTodoItem" />
  </div>
</template>

<script>
import TodoList from './TodoList'

export default {
  name: 'Main',
  components: {
    TodoList
  },
  watch: {
    todos(oldVal, newVal) {
      console.log(oldVal, newVal)
    }
  },
  beforeCreate() {
    console.log('beforeCreate')
  },
  mounted() {
    console.log('mounted')
  },
  computed: {
    getSortedItems() {
      return [...this.todos].sort((a, b) => (b.time - a.time))
    }
  },
  methods: {
    addTodoItem(text) {
      this.todos.push({
        text,
        time: Date.now(),
        completed: false
      })
    }
  },
  data () {
    return {
      todos: [
        {
          text: '<strong>Todo1</strong>',
          time: 12145,
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
