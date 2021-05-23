<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo" />
    <AddTodo v-on:add-todo="addTodo" />
    <Counter
      v-bind:count="count"
      v-on:add-count="addCount"
      v-on:down-count="downCount"
    />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import Counter from "./components/Counter";

export default {
  name: "app",
  components: {
    Todos,
    AddTodo,
    Counter,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Go workout",
          completed: false,
        },
        {
          id: 2,
          title: "Do laundry",
          completed: false,
        },
        {
          id: 3,
          title: "Cook food",
          completed: false,
        },
        {
          id: 4,
          title: "Clean up room",
          completed: false,
        },
        {
          id: 5,
          title: "Finish work",
          completed: false,
        },
      ],
      count: 0,
    };
  },
  methods: {
    addTodo(newTodoObj) {
      this.todos = [...this.todos, newTodoObj];
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter((todo) => todo.id !== todoId);
    },
    addCount(currCount) {
      this.count = (currCount += 1);
    },
    downCount(currCount) {
      this.count = (currCount -= 1);
    },
  },
};
</script>

<style>
</style>