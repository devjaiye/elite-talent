<template>
    <div class="max-w-3xl mx-auto p-6">
      <!-- Section Title -->
      <h1 class="text-2xl font-semibold">
        Join <span class="font-bold">Elite</span>
      </h1>
      <p class="text-gray-600 mt-2">
        Please fill in the relevant details to apply to join <strong>Elite</strong>
      </p>
  
      <!-- Steps Progress -->
      <div class="flex items-center mt-6 space-x-2 text-gray-400">
        <div
          class="w-6 h-6 rounded-full bg-blue-600 text-white flex items-center justify-center text-sm"
        >
          1
        </div>
        <span>Application</span>
        <span>&gt;</span>
        <div class="w-6 h-6 rounded-full bg-gray-300 text-white flex items-center justify-center text-sm">
          2
        </div>
        <span>Endorsements</span>
        <span>&gt;</span>
        <div class="w-6 h-6 rounded-full bg-gray-300 text-white flex items-center justify-center text-sm">
          3
        </div>
        <span>Review & Submit</span>
      </div>
  
      <!-- Progress Bar -->
      <div class="w-full bg-gray-200 rounded-full h-1 mt-3">
        <div class="bg-blue-600 h-1 rounded-full" style="width: 33%"></div>
      </div>
  
      <!-- Video Introduction Section -->
      <div
        class="bg-white border border-gray-200 shadow-sm rounded-md mt-8 p-6 space-y-4"
      >
        <div class="flex items-center space-x-2">
          <span
            class="flex items-center justify-center w-8 h-8 rounded-full bg-blue-100 text-blue-600"
          >
            📹
          </span>
          <h2 class="text-lg font-semibold">Video Introduction</h2>
        </div>
  
        <p class="text-gray-600">
          <strong>Tell Us About Yourself</strong>
        </p>
        <p class="text-sm text-gray-500">
          In 3 minutes or less tell us about yourself and your previous experiences up
          until now.
        </p>
  
        <p class="text-sm text-blue-600">
          <a href="#" class="hover:underline">Get recording tips</a>
        </p>
  
        <!-- Dropdown and Record Button -->
        <div class="flex flex-col sm:flex-row sm:justify-between sm:items-center">
      
          <div class="flex items-center space-x-4">
            <select
              v-model="selectedDevice"
              class="p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            >
              <option>Macbook Pro</option>
              <option>External Camera</option>
              <option>FaceTime HD</option>
            </select>
          </div>
  
        
          <button
            @click="handleRecord"
            class="mt-4 sm:mt-0 px-4 py-2 bg-blue-600 text-white font-medium rounded hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500"
          >
            Record Response
          </button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>

  const selectedDevice = ref("Macbook Pro");

  const handleRecord = () => {
    alert(`Recording started with: ${selectedDevice.value}`);
  };
  </script>