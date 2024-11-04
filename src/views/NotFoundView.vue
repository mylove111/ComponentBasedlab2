<template>
  <div>
    <h1>Oops!</h1>
    <p>The page you're looking for is not here.</p>
    <p v-if="resource">Resource: {{ resource }}</p>
    <RouterLink to="/">Back to the home page</RouterLink>
  </div>
</template>

<script setup lang="ts">
import { RouterLink } from 'vue-router'
import { defineProps } from 'vue'

defineProps({
  resource: {
    type: String,
    required: false // 确保 resource 是可选的
  }
})
</script>

<style scoped>
/* 添加一些样式使页面看起来更好 */
div {
  text-align: center;
  margin-top: 50px;
}

h1 {
  color: #42b983;
}

p {
  color: #2c3e50;
}

a {
  color: #42b983;
  text-decoration: none;
  font-weight: bold;
}

a:hover {
  text-decoration: underline;
}
</style>