<script setup>
import BlogPost from './subcomponents/BlogPost2.vue'
</script>

<script>
import axios from 'axios'

export default {
  data() {
    return { posts: [] }
  },
  computed: {
    baseUrl() {
      if (window.location.hostname == 'localhost') return 'http://localhost:3000'
      const codespace_host = window.location.hostname.replace('5173', '3000')
      return `https://${codespace_host}`
    }
  },
  created() {
    axios.get(`${this.baseUrl}/posts`)
      .then(response => { this.posts = response.data })
      .catch(error => {
        this.posts = [{
          id: 'err',
          subject: 'Error',
          entry: 'There was an error: ' + error.message,
          mood: 'default'
        }]
      })
  },
  methods: {
    async deletePost(id) {
      try {
        await axios.get(`${this.baseUrl}/deletePost`, { params: { id } })
        this.posts = this.posts.filter(p => p.id !== id)
      } catch (error) {
        console.error(error)
      }
    }
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
  >
    <button class="btn btn-primary" @click="deletePost(post.id)">Delete</button>
  </BlogPost>
</template>
