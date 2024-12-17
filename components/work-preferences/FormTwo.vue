<template>
  <div class="relative max-w-xl mx-auto">
    <div class="mb-4">
      <p class="block text-sm/6 font-medium text-gray-600 mb-4">Select 5 important things to you on your new role?</p>
      <SelectMultiSelect
        :options="options1"
        v-model="selectedOptions1"
        placeholder="Select (Max 5)"
      />
    </div>

    <div class="mb-4">
      <p class="block text-sm/6 font-medium text-gray-600 mb-4">What size of company would you like to work?</p>
      <SelectMultiSelect
        :options="options2"
        v-model="selectedOptions2"
        placeholder="Select company size"
      />
    </div>

    <div class="mb-4">
      <p class="block text-sm/6 font-medium text-gray-600 mb-4">What is your preferred workplace type?</p>
      <SelectMultiSelect
        :options="options3"
        v-model="selectedOptions3"
        placeholder="Select workplace type"
      />
    </div>

    <div class="mb-4">
      <p class="block text-sm/6 font-medium text-gray-600 mb-4">What languages do you work with?</p>
      <SelectMultiSelect
        :options="options4"
        v-model="selectedOptions4"
        placeholder="Select Languages you know"
      />
    </div>
  </div>
</template>

<script setup>
const selectedOptions1 = ref([])
const selectedOptions2 = ref([])
const selectedOptions3 = ref([])
const selectedOptions4 = ref([])

const options1 = ref([
  "Challenging Work",
  "Recognition and Reward",
  "Career Advancement",
  "Great Tech & Tools",
  "Development and Progression",
  "Work-Life Balance",
  "Supportive Leadership",
  "Collaborative Environment",
  "Innovation Opportunities",
  "Inclusive and Diverse Workplace",
  "Competitive Compensation", "Flexible Work Arrangements",
  "Learning and Training Programs",
  "Strong Company Vision and Values",
  "Employee Well-being Programs"
]);

const options2 = ref([
  "Small (1-50)",
  "Medium (51-250)",
  "Large (251-1000)",
  "Enterprise (1000+)"
]);

const options3 = ref([
  "Remote",
  "Hybrid",
  "In-Office"
]);

const options4 = ref([
  "JavaScript",
  "Python",
  "Java",
  "C++",
  "C#",
  "PHP",
  "Ruby",
  "Go",
  "Swift",
  "Kotlin",
  "TypeScript"
]);
</script>