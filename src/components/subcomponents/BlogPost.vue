<script>
export default {
  props: {
    subject: String,
    entry: String,
    mood: String,
  },
  computed: {
    // If your images are in /public/assets/*.png
    imgLoc() {
      return `/assets/${this.mood.toLocaleLowerCase()}.png`
    }
  }
}
</script>

<template>
  <div class="card" style="width: 18rem;">
    <img :src="imgLoc" class="card-img-top" :alt="mood || 'mood'">
    <div class="card-body">
      <h5 class="card-title">{{ subject }}</h5>
      <p class="card-text">{{ entry }}</p>
    </div>
  </div>
</template>
