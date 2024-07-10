<template>
  <div class="min-h-screen bg-gray-100 py-10">
    <div class="container mx-auto">
      <h2 class="text-3xl font-semibold text-center mb-8">My Leave Balances</h2>
      <div v-for="balance in leaveBalances" :key="balance.balance_id" class="max-w-md mx-auto bg-white rounded-lg shadow-md overflow-hidden mb-4">
        <div class="p-4">
          <h3 class="text-lg font-semibold">Leave Type ID: {{ balance.leave_type_id }}</h3>
          <p class="text-gray-700">Year: {{ balance.year }}</p>
          <p class="text-gray-700">Total Days: {{ balance.total_days }}</p>
          <p class="text-gray-700">Days Taken: {{ balance.days_taken }}</p>
          <p class="text-gray-700">Remaining Days: {{ balance.remaining_days }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>

import { ref, onMounted } from 'vue';

const leaveBalances = ref([]);
const leaveApplication = ref({
  name: '',
  type: '',
  startDate: '',
  endDate: '',
  reason: ''
});

// Fetch leave balances when the component is mounted
onMounted(async () => {
  console.log("Fetching leave balances...");
  await fetchLeaveBalances();
});

// Function to fetch leave balances
const fetchLeaveBalances = async () => {
  try {
    const response = await fetch('http://127.0.0.1:8000/leave-balances/?skip=0&limit=100');
    if (!response.ok) {
      throw new Error('Failed to fetch leave balances');
    }
    const data = await response.json();
    leaveBalances.value = data;
  } catch (error) {
    console.error('Error fetching leave balances:', error);
  }
};

// Function to submit leave application
const submitLeaveApplication = async () => {
  try {
    const response = await fetch('http://127.0.0.1:8000/leave-requests/', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(leaveApplication.value),
    });
    if (!response.ok) {
      throw new Error('Failed to submit leave application');
    }
    const data = await response.json();
    console.log('Leave application submitted successfully:', data);
    // Reset form after successful submission
    leaveApplication.value = { name: '', type: '', startDate: '', endDate: '', reason: '' };
    alert('Leave application submitted successfully.');
  } catch (error) {
    console.error('Error submitting leave application:', error);
  }
};
</script>

<style scoped>
/* Tailwind CSS is utility-first, so most styling is done via class attributes. Add any additional styles here if needed. */
</style>