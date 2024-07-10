<template>
  <div class="min-h-screen bg-gray-100 py-10">
    <div class="container mx-auto">
      <h2 class="text-3xl font-semibold text-center mb-8">Leave Requests</h2>
      <div class="flex justify-center mb-4">
        <button @click="fetchLeaveRequests" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
          Refresh List
        </button>
      </div>
      <div v-for="request in leaveRequests" :key="request.leave_request_id" class="max-w-md mx-auto bg-white rounded-lg shadow-md overflow-hidden mb-4">
        <div class="p-4">
          <h3 class="text-lg font-semibold">Request ID: {{ request.leave_request_id }}</h3>
          <p class="text-gray-700">Employee ID: {{ request.employee_id }}</p>
          <p class="text-gray-700">Leave Type ID: {{ request.leave_type_id }}</p>
          <p class="text-gray-700">Start Date: {{ request.start_date }}</p>
          <p class="text-gray-700">End Date: {{ request.end_date }}</p>
          <p class="text-gray-700">Reason: {{ request.reason }}</p>
          <p class="text-gray-700">Status: {{ request.status }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const leaveRequests = ref([]);

// Fetch leave requests when the component is mounted
onMounted(() => {
  fetchLeaveRequests();
});

const fetchLeaveRequests = async () => {
  try {
    const response = await axios.get('http://127.0.0.1:8000/leave-requests/');
    leaveRequests.value = response.data;
  } catch (error) {
    console.error('Error fetching leave requests:', error);
  }
};
</script>

<style scoped>
/* Tailwind CSS is utility-first, so most styling is done via class attributes. Add any additional styles here if needed. */
</style>