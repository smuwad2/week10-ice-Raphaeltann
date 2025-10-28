<script>
import BlogPost from './subcomponents/BlogPost.vue'
import axios from 'axios'

export default {
  components: { BlogPost },                 // fix: register component
  data() {
    return {
      posts: []                              // array of post objects
    }
  },
  computed: {
    baseUrl() {
      if (window.location.hostname === 'localhost') return 'http://localhost:3000'
      const codespace_host = window.location.hostname.replace('5173', '3000')
      return `https://${codespace_host}`
    }
  },
  created() {
    axios.get(`${this.baseUrl}/posts`)
      .then(response => { this.posts = response.data })
      .catch(error => {
        this.posts = [{ id: 'err', subject: 'Error', entry: 'There was an error: ' + error.message, mood: 'Error' }]
      })
  }
}
</script>

<template>
  <BlogPost
    v-for="post in posts"
    :key="post.id"
    :subject="post.subject"
    :entry="post.entry"
    :mood="post.mood"
  />
</template>
