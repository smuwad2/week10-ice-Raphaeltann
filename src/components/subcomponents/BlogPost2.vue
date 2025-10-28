<script>
export default {
  props: {
    subject: String,
    entry: String,
    mood: String,
  },
  emits: ['delete'],
  computed: {
    imgLoc() {
      const m = String(this.mood || '').toLowerCase().replace(/\s+/g, '-')
      return `/assets/${m || 'default'}.png`
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
    <slot></slot>
  </div>
</template>
