<template>
  <div class="todos-container">
    <h1>Daftar Todos</h1>
    <input type="text" v-model="newTodo" @keyup.enter="addTodo" placeholder="Tambahkan Todo baru"/>
    <button @click="addTodo">Tambah Todo</button>

    <ul>
      <li v-for="(todo, index) in todos" :key="todo.id">
        <input type="checkbox" v-model="todo.completed" @change="updateTodo(todo)">
        <span :class="{ 'completed': todo.completed }">{{ todo.text }}</span>
        <button @click="deleteTodo(index)">Hapus</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Todos',
  data() {
    return {
      todos: [],
      newTodo: ''
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({
          id: Date.now(),
          text: this.newTodo,
          completed: false
        });
        this.newTodo = '';
      }
    },
    updateTodo(todo) {
      const index = this.todos.findIndex(t => t.id === todo.id);
      if (index !== -1) {
        this.todos[index] = todo;
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>

