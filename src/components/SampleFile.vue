<template>
  <div>
    <h1>Testing Chart Component</h1>
    <ul>
      <p v-for="item in list" :key="item.id">
        {{ item.id }}{{ item.title }}
      </p>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      list: [],
    };
  },
  async mounted() {
    let result = await axios.get("https://jsonplaceholder.typicode.com/posts");
    console.log("sadas", result.data);
    this.list = result.data;
  },
};
</script>
