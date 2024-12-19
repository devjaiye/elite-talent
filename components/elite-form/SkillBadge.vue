<template>
    <div class="px-2 py-1 bg-blue-50 text-[#0B6CF4] rounded-md text-xs cursor-pointer">
      {{ label }}
    </div>
  </template>
  
  <script setup>
  
 const props = defineProps({
    label: {
        type: String,
        required: true,
    }
 })
  </script>
  