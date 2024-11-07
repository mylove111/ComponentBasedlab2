<!-- src/views/StudentListView.vue -->
<template>
      <div>
        <h1 class="text-3xl font-bold mb-6">Student Information</h1>
        <div class="student-list flex flex-wrap justify-center">
          <div v-for="student in students" :key="student.id" class="student-card">
            <h2 class="text-xl font-semibold">{{ student.name }} {{ student.surname }}</h2>
            <span class="block mt-2">GPA: {{ student.gpa }}</span>
          </div>
        </div>
      </div>
    </template>
    
    <script setup lang="ts">
    import { ref, onMounted } from 'vue';
    import StudentService from '@/services/StudentService';
    import type { Student } from '@/type';
    
    const students = ref<Student[]>([]);
    
    onMounted(async () => {
      try {
        const response = await StudentService.getStudents();
        students.value = response.data;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    });
    </script>
    
    <style scoped>
 
 .student-card {
      padding: 20px;
      width: 250px;
      cursor: pointer;
      border: 1px solid #39495c;
      margin: 10px;
      text-align: center;
    }
    
    .student-card:hover {
      transform: scale(1.01);
      box-shadow: 0 3px 12px 0 rgba(0,0,0,0.2);
    }
    </style>