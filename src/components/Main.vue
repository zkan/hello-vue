<template>
  <div class="main">
    {{ text }}
    <TodoList :todoItems="getSortedItems" />
    <input type="text" v-model="text">
    <button @click="save()">Save</button>
  </div>
</template>

<script>
import TodoList from './TodoList.vue'

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
    save() {
      console.log('save')
    }
  },
  data () {
    return {
      text: 'Hello World',
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
