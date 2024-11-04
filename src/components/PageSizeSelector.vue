<template>
    <div>
      <button @click="openDialog">Select the number of displays per page</button>
      <dialog :open="isOpen">
        <form @submit.prevent="handleSelect">
          <label for="pageSize">the number of displays per page:</label>
          <select id="pageSize" v-model="selectedPageSize">
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="4">4</option>
            <option value="6">6</option>
          </select>
          <button type="submit">Confirm</button>
          <button type="button" @click="closeDialog">cancel</button>
        </form>
      </dialog>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref } from 'vue'
  import { useRouter } from 'vue-router'
  
  const isOpen = ref(false)
  const selectedPageSize = ref('4')
  const router = useRouter()
  
  const openDialog = () => {
    isOpen.value = true
  }
  
  const closeDialog = () => {
    isOpen.value = false
  }
  
  const handleSelect = () => {
    const currentQuery = router.currentRoute.value.query
    const newQuery = { ...currentQuery, pageSize: selectedPageSize.value }
    router.push({ query: newQuery })
    closeDialog()
  }
  </script>
  
  <style scoped>
  dialog {
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 20px;
    background-color: white;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  }
  
  form {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  
  button {
    padding: 10px;
    cursor: pointer;
  }
  
  button[type="submit"] {
    background-color: #42b983;
    color: white;
  }
  
  button[type="button"] {
    background-color: #ff7675;
    color: white;
  }
  </style>