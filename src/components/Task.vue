<template>
  <div
    @click.right.prevent="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task flex']"
   >
    <div class="task__wrapper">
      <h3>{{ task.text }}</h3>
      <p>{{ task.day }}</p>
    </div>
    <i
    @click="onDelete(task.id)" 
    class="fas fa-times"
    ></i>
  </div>
</template>

<script>
export default {
  props: {
    task: Object,
  },
  methods: {
    onDelete(id) {
      this.$emit('delete-task', id)
    }
  }
};
</script>

<style scoped>
.fas {
  color: rgb(197, 90, 90);
  transition: all 0.1s;
  padding: 10px;
}
.fas:hover {
  color: rgb(173, 39, 39);
  transform: scale(1.3);
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>