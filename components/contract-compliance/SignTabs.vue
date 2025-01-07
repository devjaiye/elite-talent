<template>
    <div class="max-w-md mx-auto bg-white rounded-lg">

  
      <!-- Tabs -->
      <div class="flex border-b border-gray-200">
        <button
          v-for="(tab, index) in tabs"
          :key="tab"
          @click="selectTab(index)"
          class="flex-1 text-center px-4 py-2 font-medium text-gray-500 transition duration-300"
          :class="{
            'border-b-2 border-blue-500 text-blue-500': selectedTab === index,
            'hover:text-blue-500': selectedTab !== index,
          }"
        >
          {{ tab }}
        </button>
      </div>
  
      <!-- Tab Content -->
      <div class="mt-4">
        <div v-if="selectedTab === 0">
            <ContractComplianceDraw/>
        </div>
        <div v-else-if="selectedTab === 1">
         <ContractComplianceType/>
        </div>
        <div v-else-if="selectedTab === 2">
        <ContractComplianceUpload/>
        </div>
      </div>
  
      <button
        class="mt-6 w-full py-2 bg-blue-500 text-white font-medium rounded-md hover:bg-blue-600 transition duration-300"
      >
      Sign and Continue

      </button>
    </div>
  </template>
  
  <script setup>
    
      const tabs = ["Draw", "Type", "Upload"]
      const selectedTab = ref(0)
  
      const selectTab = (index) => {
        selectedTab.value = index
      };
  
  </script>
  
  <style scoped>
  </style>
  