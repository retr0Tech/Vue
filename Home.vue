<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <div class="posts" v-for="post in posts" :key="post.id">
      {{ post }}
    </div>
  </div>
</template>

<script>
      import axios from 'axios'
      import { Post } from '@/models/post'

      export default{
        data() {
          return{
            posts: [] as Array<Post>
          }
        },
        mounted(){
          var self = this;
          axios.get('https://jsonplaceholder.typicode.com/posts')
          .then(function(response){
            posts = response.data
            self.posts = response.data;
            console.log('Data: ', respones.data);
          })
          .catch( function(error){
            console.log('Error: ', error)
          })
        }
      }
</script>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "posts",
  components: {
    HelloWorld
  }
};
</script>
