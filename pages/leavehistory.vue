<template>
  <div class="min-h-screen bg-gray-100 py-10">
    <div class="container mx-auto">
      <h2 class="text-3xl font-semibold text-center mb-8">My Leave History</h2>
      <div class="overflow-x-auto bg-white rounded-lg shadow overflow-y-auto relative" style="max-height: 405px;">
        <table class="border-collapse table-auto w-full whitespace-no-wrap bg-white table-striped relative">
          <thead>
            <tr class="text-left">
              <th class="bg-blue-100 sticky top-0 px-6 py-4">Leave Type</th>
              <th class="bg-blue-100 sticky top-0 px-6 py-4">Start Date</th>
              <th class="bg-blue-100 sticky top-0 px-6 py-4">End Date</th>
              <th class="bg-blue-100 sticky top-0 px-6 py-4">Status</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(request, index) in leaveHistory" :key="index" class="hover:bg-gray-100">
              <td class="px-6 py-4">{{ request.type }}</td>
              <td class="px-6 py-4">{{ request.startDate }}</td>
              <td class="px-6 py-4">{{ request.endDate }}</td>
              <td class="px-6 py-4">
                <span :class="statusClasses(request.status)">{{ request.status }}</span>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const leaveHistory = ref([
  { type: 'Annual', startDate: '2023-04-10', endDate: '2023-04-15', status: 'Approved' },
  { type: 'Sick', startDate: '2023-05-01', endDate: '2023-05-03', status: 'Rejected' },
  // Add more history items as needed
]);

const statusClasses = (status) => {
  switch (status.toLowerCase()) {
    case 'approved':
      return 'text-green-500';
    case 'rejected':
      return 'text-red-500';
    case 'pending':
      return 'text-yellow-500';
    default:
      return 'text-gray-500';
  }
};
</script>

<style scoped>
/* Add any additional styles you need here */
</style>