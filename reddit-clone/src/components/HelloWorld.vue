<template>
  <div class="hello">
    <h1>Posts</h1>
    <div>
      <ul class="list-unstyled">
        <li v-for="(post,i) in posts" :key="i" class="media mb-4 border">
          <a :href="post.data.url" target="_blank"><img :src="post.data.thumbnail" class="mr-3" alt="..."></a>
          <div class="media-body p-3">
            <h3 class="mt-0 mb-1">{{post.data.title}}</h3>
            <div class="badge badge-primary m-1 p-2">{{post.data.ups}} 👍</div>
            <div class="badge badge-primary m-1 p-2">{{post.data.num_comments}} 💬</div>
            <div class="badge badge-primary m-1 p-2">{{post.data.author}} ✍️</div> <br>
            <div class="badge badge-primary m-1 p-2">{{formatDate(post.data.created)}} ⌛️</div> <br>
            <div class="badge bg-dark m-1 p-2 text-danger"><a target="_blank" :href="post.data.url">View Post 🔗</a></div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import {parse, distanceInWords} from 'date-fns'
export default {
  name: "HelloWorld",
  props: {},
  mounted() {
    this.load();
  },
  data() {
    return {
      posts: []
    };
  },
  methods: {
    load() {
      const URL = "https://www.reddit.com/r/rarepuppers/.json";
      fetch(URL)
        .then(response => response.json())
        .then(result => {
          this.posts = result.data.children;
          console.log(this.posts)
        });
    },
    formatDate(date){
      return distanceInWords(parse(date * 1000), new Date())
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
