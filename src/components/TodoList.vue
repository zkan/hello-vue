<template>
  <ul>
    <li v-for="todo in todoItems" :key="todo.time">
      <div v-if="todo.completed == false">{{ todo.text | capitalize }}</div>
      <div v-else-if="todo.completed == true">{{ todo.text | capitalize }} (Completed)</div>
      <div v-else>{{ todo.text | capitalize }}</div>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'TodoList',
  filters: {
    capitalize (val) {
      return val.toUpperCase()
    }
  },
  // props: ['todoItems',],
  props: {
    todoItems: {
      type: Array,
      default: () => []
    }
  }
}
</script>
