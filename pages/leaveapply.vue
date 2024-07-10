<template>
  <div class="min-h-screen bg-gray-100 flex items-center justify-center">
    <div class="max-w-md w-full bg-white rounded-lg shadow-md p-6">
      <h2 class="text-2xl font-semibold text-center mb-6">Apply for Leave</h2>
      <form @submit.prevent="submitLeaveApplication">
        <div class="mb-4">
          <label for="employeeId" class="block text-sm font-medium text-gray-700">Employee ID</label>
          <input type="number" id="employeeId" v-model="leaveApplication.employee_id" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500" required>
        </div>
        <div class="mb-4">
          <label for="leaveTypeId" class="block text-sm font-medium text-gray-700">Leave Type ID</label>
          <input type="number" id="leaveTypeId" v-model="leaveApplication.leave_type_id" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500" required>
        </div>
        <div class="mb-4">
          <label for="startDate" class="block text-sm font-medium text-gray-700">Start Date</label>
          <input type="date" id="startDate" v-model="leaveApplication.start_date" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500" required>
        </div>
        <div class="mb-4">
          <label for="endDate" class="block text-sm font-medium text-gray-700">End Date</label>
          <input type="date" id="endDate" v-model="leaveApplication.end_date" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500" required>
        </div>
        <div class="mb-4">
          <label for="reason" class="block text-sm font-medium text-gray-700">Reason</label>
          <textarea id="reason" v-model="leaveApplication.reason" rows="4" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500" required></textarea>
        </div>
        <button type="submit" class="w-full bg-blue-600 text-white rounded-md py-2 hover:bg-blue-700">Submit Application</button>
      </form>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      leaveApplication: {
        employee_id: '',
        leave_type_id: '',
        start_date: '',
        end_date: '',
        reason: '',
        status: 'pending' // Assuming 'pending' is the default status
      },
    };
  },
  methods: {
    async submitLeaveApplication() {
      try {
        await axios.post('http://127.0.0.1:8000/leave-requests/', this.leaveApplication);
        alert('Leave application submitted successfully.');
        // Reset form
        this.leaveApplication = { employee_id: '', leave_type_id: '', start_date: '', end_date: '', reason: '', status: 'pending' };
      } catch (error) {
        console.error('Error submitting leave application:', error);
        alert('Failed to submit leave application.');
      }
    },
  },
};
</script>

<style scoped>
/* Tailwind CSS is utility-first, so most styling is done via class attributes. Add any additional styles here if needed. */
</style>