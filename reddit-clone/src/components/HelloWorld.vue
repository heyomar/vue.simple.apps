<template>
  <div class="hello">
    <h1>Posts</h1>
    <div>
      <ul class="list-unstyled">
        <li v-for="(post,i) in posts" :key="i" class="media mb-4 border">
          <a :href="post.data.url" target="_blank">
            <img
              v-show="post.data.thumbnail !== 'self'"
              :src="post.data.thumbnail"
              class="img-fluid"
              alt="..."
            >
          </a>
          <div class="media-body p-3">
            <h3 class="mt-0 mb-1">
              <a
                :href="'https://www.reddit.com' + post.data.permalink"
                target="_blank"
              >{{post.data.title}}</a>
            </h3>
            <div class="badge badge-primary m-1 p-2">{{post.data.ups}} 👍</div>
            <div class="badge badge-primary m-1 p-2">{{post.data.num_comments}} 💬</div>
            <div class="badge badge-primary m-1 p-2">{{post.data.author}} ✍️</div>
            <br>
            <div class="badge badge-primary m-1 p-2">{{formatDate(post.data.created_utc)}} ago ⌛️</div>
            <br>
            <div class="badge bg-dark m-1 p-2 text-danger">
              <a target="_blank" :href="post.data.url">View Post 🔗</a>
            </div>
            <button
              v-show="isImage(post)"
              @click="post.showImage = !post.showImage"
              class="btn btn-sm btn-success float-right"
            >{{post.showImage ? 'Hide' : 'Show'}} Image</button>
            <div v-show="post.showImage">
              <img class="img-fluid" :src="post.data.url" alt="post-image">
            </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { parse, distanceInWords } from "date-fns";
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
          result.data.children.forEach(child => {
            child.showImage = false;
          });
          this.posts = result.data.children;
        });
    },
    formatDate(date) {
      return distanceInWords(parse(date * 1000), new Date());
    },
    isImage(post){
      
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
