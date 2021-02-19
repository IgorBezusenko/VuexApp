<template>
  <div id="app">
     <h2>Posts count: {{postsCount}}</h2>
    <PostForm/>
  <div class="post"  v-for="post in validPost" :key="post.id">
    <h2>{{post.title}}</h2>
    <p>{{post.body}}</p>
  </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from "vuex"
import PostForm from "./components/PostForm"

export default {
  name: 'App',
  // computed:{
  //   allPosts(state) {
  //     return this.$store.getters.allPosts;
  //   }
  // },
  computed: mapGetters(["validPost","allPosts","postsCount"]),
  methods: mapActions(['fetchPosts']),
  components:{PostForm},
  async mounted() {
      // this.$store.dispatch("fetchPosts")
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

.post{
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 1rem;
}
</style>
