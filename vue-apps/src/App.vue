<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo" />
    <AddTodo v-on:add-todo="addTodo" />
    <Counter
      v-bind:count="count"
      v-on:add-count="addCount"
      v-on:down-count="downCount"
    />
    <Temp v-bind:info="info" />
  </div>
</template>

<script>
import axios from "axios";
import dotenv from 'dotenv'

import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import Counter from "./components/Counter";
import Temp from "./components/Temp";

dotenv.config()

export default {
  name: "app",
  components: {
    Todos,
    AddTodo,
    Counter,
    Temp,
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
      info: null,
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
      this.count = currCount += 1;
    },
    downCount(currCount) {
      if (currCount !== 0) {
        this.count = currCount -= 1;
      }
    },
  },
  mounted() {
    const options = {
      method: "GET",
      url: "https://weatherbit-v1-mashape.p.rapidapi.com/current",
      params: { lon: "-111.876183", lat: "40.758701" },
      headers: {
        "x-rapidapi-key": process.env.VUE_APP_X_RAPIDAPI_KEY,
        "x-rapidapi-host": "weatherbit-v1-mashape.p.rapidapi.com",
      },
    };

    axios
      .request(options)
      .then((response) => {
        this.info = response.data.data[0].temp;
      })
      .catch(function (error) {
        console.error(error);
      });
  },
};
</script>

<style>
</style>