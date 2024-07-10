<template>
  <div class="flex items-center justify-center min-h-screen bg-gray-100">
    <div class="px-8 py-6 mt-4 text-left bg-white shadow-lg">
      <h3 class="text-2xl font-bold text-center">Register for an account</h3>
      <form @submit.prevent="handleSignUp">
        <div>
          <div class="mt-4">
            <label class="block" for="name">Name</label>
            <input type="text" placeholder="Name" 
              class="w-full px-4 py-2 mt-2 border rounded-md focus:outline-none focus:ring-1 focus:ring-blue-600"
              v-model="signUpForm.name" id="name" required>
          </div>
          <div class="mt-4">
            <label class="block" for="email">Email</label>
            <input type="email" placeholder="Email" 
              class="w-full px-4 py-2 mt-2 border rounded-md focus:outline-none focus:ring-1 focus:ring-blue-600"
              v-model="signUpForm.email" id="email" required>
          </div>
          <div class="mt-4">
            <label class="block">Password</label>
            <input type="password" placeholder="Password" 
              class="w-full px-4 py-2 mt-2 border rounded-md focus:outline-none focus:ring-1 focus:ring-blue-600"
              v-model="signUpForm.password" required>
          </div>
          <div class="mt-4">
            <label class="block">Confirm Password</label>
            <input type="password" placeholder="Confirm Password" 
              class="w-full px-4 py-2 mt-2 border rounded-md focus:outline-none focus:ring-1 focus:ring-blue-600"
              v-model="signUpForm.confirmPassword" required>
          </div>
          <div class="flex items-baseline justify-between">
            <button type="submit" class="px-6 py-2 mt-4 text-white bg-blue-600 rounded-lg hover:bg-blue-900">Register</button>
            <a href="#" class="text-sm text-blue-600 hover:underline">Already have an account?</a>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const signUpForm = ref({
  name: '',
  email: '',
  password: '',
  confirmPassword: ''
});

const handleSignUp = () => {
  // Simulate a sign-up process
  console.log('Signing up with:', signUpForm.value);
  // Here you would typically send a request to your backend to register the user
  // For demonstration, we'll just log to the console
  alert(`Registration attempted for email: ${signUpForm.value.email}`);
  // You should also include validation, especially to check if the passwords match
  if (signUpForm.value.password !== signUpForm.value.confirmPassword) {
    alert("Passwords do not match!");
    return;
  }
};
</script>

<style scoped>
/* You can add additional global styles here */
</style>