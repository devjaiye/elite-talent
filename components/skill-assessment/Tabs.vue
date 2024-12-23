<template>
  <div class="p-6 bg-gray-100 min-h-screen">
    <!-- Back Button -->
    <div class="max-w-full flex items-center text-gray-500 gap-x-64 mb-6">
      <a href="/" class="text-gray-600 text-lg hover:text-gray-800 flex items-center -mt-7">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
          <path d="M15 18L9 12L15 6" stroke="#475467" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
        </svg>
        Back
      </a>


      <div class="inline-block">
        <p class="text-gray-900 text-xl font-medium mb-2">Skill Assessment</p>
        <p class="text-gray-500 text-sm">
          Skill assessments help us understand your skills and proficiency
        </p>
      </div>

    </div>
    <div class="max-w-3xl mx-auto bg-white rounded-lg shadow p-6">

      <!-- Tabs -->
      <div class="mt-6 flex border-b mb-4">
        <button class="pb-2 border-b-2" :class="{
          'text-elite-blue border-blue-500 font-medium text-base': activeTab === 'core',
          'text-gray-700 font-medium text-base': activeTab !== 'core',
        }" @click="activeTab = 'core'">
          Core Skill
        </button>
        <button class="ml-4 pb-2" :class="{
          'text-elite-blue border-b-2 border-blue-500 font-medium text-base': activeTab === 'secondary',
          'text-gray-700 font-medium text-base': activeTab !== 'secondary',
        }" @click="activeTab = 'secondary'">
          Secondary Skill
        </button>
      </div>

      <!-- Dynamic Component -->
      <div class="mt-6">
        <component :is="activeTabComponent" />
      </div>
    </div>
  </div>
</template>

<script setup>

import SkillAssessmentCoreSkill from ".././skill-assessment/CoreSkill.vue"
import SkillAssessmentSecondarySkill from ".././skill-assessment/SecondarySkill.vue"

const activeTab = ref("core")

const activeTabComponent = computed(() =>
  activeTab.value === "core"
    ? SkillAssessmentCoreSkill
    : SkillAssessmentSecondarySkill
);

</script>

<style scoped></style>