<template>
    <div class="fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-50">
      <div class="bg-white rounded-lg shadow-lg max-w-lg w-full p-6">
        <div class="flex justify-between items-center">
         <div >
            <h2 class="text-xl font-semibold">Signature</h2>
            <h2 class="text-sm text-gray-500">Draw, type or upload a signature to continue</h2>
         </div>
          
          <button @click="$emit('close-modal')" class="text-gray-400 hover:text-gray-600">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
              <path d="M15 5L5 15M5 5L15 15" stroke="#667085" stroke-width="1.66667" stroke-linecap="round"
                stroke-linejoin="round" />
            </svg>
          </button>
        </div>
        <div class="mt-1">
            <ContractComplianceSignTabs/>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>

  </script>