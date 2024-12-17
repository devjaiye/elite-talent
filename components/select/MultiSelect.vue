<template>
    <div class="relative">
      <div @click="toggleDropdown" class="border outline outline-1 -outline-offset-1 outline-gray-300 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6 rounded-md px-3 py-2 cursor-pointer flex items-center w-full">
        <span class="text-gray-400">{{ placeholder }}</span>
  
        <div class="ml-auto text-gray-500">
          <ChevronDownIcon
            class="pointer-events-none col-start-1 row-start-1 mr-2 size-5 self-center justify-self-end text-gray-500 sm:size-4"
            aria-hidden="true" />
        </div>
      </div>
  
      <div v-if="isOpen" class="absolute w-full mt-2 bg-white border border-gray-300 rounded-md shadow-lg z-10">
        <ul class="max-h-60 overflow-auto">
          <li v-for="(option, index) in options" :key="index" @click="toggleOption(option)"
            class="px-4 py-2 hover:bg-gray-100 cursor-pointer" :class="{
              'bg-gray-200': selectedOptions.includes(option),
              'pointer-events-none text-gray-400': selectedOptions.length >= 5 && !selectedOptions.includes(option),
            }">
            {{ option }}
          </li>
        </ul>
      </div>
  
      <div v-if="selectedOptions.length" class="flex flex-wrap gap-2 mb-2 mt-2">
        <div v-for="(option, index) in selectedOptions" :key="index"
          class="bg-white text-gray-700 px-2 py-1 rounded-md ring-1 ring-gray-300 flex items-center gap-1 text-sm">
          <span>{{ option }}</span>
          <button @click="removeOption(index)" class="text-gray-500 hover:text-gray-800">
            &times;
          </button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ChevronDownIcon } from '@heroicons/vue/16/solid'
  
  const props = defineProps({
    options: {
      type: Array,
      required: true
    },
    placeholder: {
      type: String,
      default: 'Select'
    }
  });
  
  const emit = defineEmits(['update:modelValue'])
  
  const isOpen = ref(false)
  const selectedOptions = ref([])
  
  const toggleDropdown = () => {
    isOpen.value = !isOpen.value;
  };
  
  const toggleOption = (option) => {
    if (selectedOptions.value.includes(option)) {
      selectedOptions.value = selectedOptions.value.filter((o) => o !== option)
    } else if (selectedOptions.value.length < 5) {
      selectedOptions.value.push(option)
    }
    emit('update:modelValue', selectedOptions.value)
  }
  
  const removeOption = (index) => {
    selectedOptions.value.splice(index, 1)
    emit('update:modelValue', selectedOptions.value)
  };
  </script>