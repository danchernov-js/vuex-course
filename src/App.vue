<template>
  <div id="app">
    <PostForm />
    <h1>{{postsCount}}</h1>
    <div class="post" v-for="post in validPosts" :key="post.id">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
import PostForm from '@/components/PostForm.vue'
export default {
  name: 'App',
  //1 variant
  // data() {
  //   return {
  //     posts: []
  //   }
  // },
  // 2 variant
  // computed: {
  //   allPosts() {
  //     return this.$store.getters.allPosts;
  //   }
  // },
  components: {PostForm},
  computed: mapGetters(['validPosts', 'postsCount']),
  methods: mapActions(['fetchPosts']),
  async mounted() {
    //1 variant with data
    // const resp = await fetch('https://jsonplaceholder.typicode.com/posts?_limit=3');
    // const posts = await resp.json();
    // this.posts = posts;

    //2 variant
    // this.$store.dispatch('fetchPosts');
    this.fetchPosts(4);
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 400px;
}

.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 1rem;
}
</style>
