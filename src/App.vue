/* eslint-disable vue/require-v-for-key */
<template>
  <div id="app">
    <ul>
      // v for (por cada post acrescenta um li)
      <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
    </ul>
  </div>
</template>

<script>
//import axios and require it
import axios from "axios";
export default {
  data() {
    return {
      posts: {},
    };
  },
  mounted: function() {
    // eslint-disable-next-line no-unused-vars
    const url = "https://jsonplaceholder.typicode.com/posts";
    axios
      .get(url)
      .then((response) => (this.posts = response.data))
      .then((response) => {
        console.log(response);
      })
      //send a error message if for some reason we cant acess the data
      // eslint-disable-next-line no-unused-vars
      .catch((error) => (this.posts = [{ title: "no posts found !!" }]));
  },
};
</script>

<style></style>
