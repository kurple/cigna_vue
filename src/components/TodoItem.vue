<template>
  <div v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="toggleComplete">
      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    toggleComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style scoped>
  div {
    background: gray;
    padding: 10px;
    border-bottom: 1px;
  }

  .is-complete {
    text-decoration: line-through;
  }
</style>
