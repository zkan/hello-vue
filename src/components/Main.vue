<template>
  <div class="main">
    {{ text }}
    <ul>
      <li v-for="todo in sortItems" :key="todo.time">
        <div v-if="todo.completed == false">{{ todo.text | capitalize }}</div>
        <div v-else-if="todo.completed == true">{{ todo.text | capitalize }} (Completed)</div>
        <div v-else>{{ todo.text | capitalize }}</div>
      </li>
    </ul>
    <input type="text" v-model="text">
    <button @click="save()">Save</button>
  </div>
</template>

<script>
export default {
  name: 'Main',
  computed: {
    sortItems() {
      return [...this.todos].sort((a, b) => (b.time - a.time))
    }
  },
  methods: {
    save() {
      console.log('save')
    }
  },
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
