<script>
export default { 
  props: { task: Object, idx: Number },
  emits: ['removeTask'],
  data() {
    return {}
  }
}
</script>

<template>
  <div class="card" style="width: 18rem; display:inline-block">
    <div class="card-body">
      <h5 class="card-title">Deadline: {{ task.deadline }}</h5>
      <hr>
      <p class="card-text">{{ task.desc }}</p>
      <button type="button" class="btn btn-primary" @click="$emit('removeTask', idx)">Done</button>
    </div>
  </div>
</template>
