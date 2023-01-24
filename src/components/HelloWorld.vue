<template>
  <h1>
    {{ header || "welcome" }}
  </h1>
  <label for="new-todo">Add a todo</label>
  <input
    v-model="newTodoText"
    placeholder="E.g. Feed the cat"
    @keyup.enter="additem"
  />
  <p>{{ charactercount }}/200</p>
  <button @click="additem" :disabled="newTodoText.length === 0">Add</button>
  <p v-if="todos.length === 0">welcome!!!!</p>
  <a v-bind:href="todos">dynamic link</a>
  <ul>
    <li v-for="(todo, index) in todos" :key="index">
      {{ todo.title }}
      <button @click="removeitem">Remove</button>
    </li>
  </ul>
</template>
<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      header: "Shopping List App",
      newTodoText: "",
      // charactercount: "",
      todos: [
        {
          id: 1,
          title: "Do the dishes",
        },
        {
          id: 2,
          title: "Take out the trash",
          purchase: true,
        },
        {
          id: 3,
          title: "Mow the lawn",
        },
      ],
      nextTodoId: 4,
    };
  },
  computed: {
    charactercount() {
      return this.newTodoText.length;
    },
  },
  methods: {
    additem() {
      this.todos.push({ id: this.todos.length + 1, title: this.newTodoText });
      this.newTodoText = "";
    },
    removeitem() {
      this.todos.pop();
    },
  },
};
</script>

<style scoped>
ul li{
  list-style-type: none;
}
</style>
