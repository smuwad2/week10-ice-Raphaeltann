<script>
export default { 
  props:{ level: Number },
  data() {
    return { soundEmojis: ['🔇', '🔈', '🔉', '🔊'] }
  }
}
</script>

<template>
  <span>{{ soundEmojis[level] }}</span>
</template>
