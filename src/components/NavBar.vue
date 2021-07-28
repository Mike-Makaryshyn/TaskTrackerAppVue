<template>
  <header>
    <router-link class="title" to="/">{{ title }}</router-link>
    <Button 
    v-show="homePage"
    @btn-click="$emit('show-task')"
    :text="showAddTask ? 'Close' : 'Add Task'" 
    :color="!showAddTask ? 'green' : 'darkred'"
    />
  </header>
</template>

<script>
import Button from '@/components/Button'
  export default {
    name: 'Header',
    components: { Button },
    props: {
      title: String,
      showAddTask: Boolean
    },
    computed: {
      homePage() {
        if(this.$route.path === '/') {
          return true
        }
        return false
      }
    },
  }
</script>

<style scoped>
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 50px;
  }
  .title {
    color: black;
    text-decoration: none;
    display: block;
    font-size: 2em;
    font-weight: bold;
  }
</style>