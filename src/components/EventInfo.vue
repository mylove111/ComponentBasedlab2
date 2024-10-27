<!-- EventInfo.vue -->
<template>
    <div class="event-class">
     <div class="event-info">
        <p>Category: {{ category }}</p>
        <p>Organizer: {{ organizer }}</p>
        </div>
    </div>
  </template>
  
  <script setup>
  defineProps({
    category: String,
    organizer: String
  });
  </script>
  
  <style scoped>
  .event-info {
    padding: 20px;
    width: 250px;
    text-align: right;
    font-size: 12px; /* 设置相同的字体大小 */
  }
  .event-info {
  display: flex;
  flex-direction: column;
  align-items: center; 
  border: 1px solid #39495c; /* 可选：添加边框 */
  padding: 20px; /* 可选：添加内边距 */
  margin-bottom: 10px;
}
.event-info:hover {
      transform: scale(1.01);
      box-shadow: 0 3px 12px 0 rgba(0,0,0,0.2);
}
  </style>