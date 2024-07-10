<template>
  <div class="flex">
    <!-- Sidebar -->
    <aside class="w-64" aria-label="Sidebar">
      <div class="overflow-y-auto py-4 px-3 bg-gray-50 rounded dark:bg-gray-800 h-screen">
        <ul class="space-y-2">
          <li>
            <NuxtLink to="/login" class="flex items-center p-2 text-base font-normal text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700">
           Login
            </NuxtLink>
          </li>
          <li>
            <NuxtLink to="/" class="flex items-center p-2 text-base font-normal text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700">
              Leave Management System
            </NuxtLink>
          </li>
          <li>
            <NuxtLink to="/leaveapply" class="flex items-center p-2 text-base font-normal text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700">
              Leave Apply
            </NuxtLink>
          </li>
          <li>
            <NuxtLink to="/leaveapproval" class="flex items-center p-2 text-base font-normal text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700">
              Leave Approval
            </NuxtLink>
          </li>
          <li>
            <NuxtLink to="/leavebalances" class="flex items-center p-2 text-base font-normal text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700">
              Leave Balances
            </NuxtLink>
          </li>
          <li>
            <NuxtLink to="/leavehistory" class="flex items-center p-2 text-base font-normal text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700">
             Leave History
            </NuxtLink>
          </li>
        </ul>
      </div>
    </aside>

    <!-- Main content -->
    <main class="flex-1">
      <header class="shadow-sm bg-white">
        <nav class="p-4 flex justify-between">
          <h1 class="font-bold">Leave</h1>
        </nav>
      </header>
      <div class="p-4">
        <slot/>
      </div>
    </main>
  </div>
</template>

<style scoped>
.router-link-exact-active {
  color: #2e1065;
  background-color: #f3f4f6; /* Lighter background on active link */
  border-left: 4px solid #2e1065; /* Add a left border to indicate active state */
}

/* Additional styling for the sidebar */
aside {
  border-right: 1px solid #ddd; /* Adds a right border to the sidebar */
}
</style>