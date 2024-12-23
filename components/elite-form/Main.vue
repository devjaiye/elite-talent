<template>
  <div class="py-10 bg-gray-50 px-10">
    <div class="mb-4 flex justify-between max-w-6xl mx-auto">
      <div>Back</div>
      <div class="flex-col flex-1 mx-auto max-w-md">
        <h2 class="text-xl font-bold mb-2">Join Elite</h2>
        <p class="text-sm">Please fill in the relevant details to apply to join Elite</p>
      </div>
      <button @click="nextStep" :disabled="currentStep === steps.length - 1 && !isLastStepValid"
        class="w-auto px-3 bg-blue-500 text-white text-sm rounded-md hover:bg-blue-600 transition">
        {{ currentStep === steps.length - 1 ? 'Finish' : 'Save & Continue' }}
      </button>
    </div>
<!-- Header progress -->
<div class="flex max-w-xl mx-auto justify-center mb-4 items-center mt-6 space-x-4 text-gray-400">
  <!-- Step 1 -->
  <div
    class="w-6 h-6 rounded-full flex items-center justify-center text-sm"
    :class="currentStep >= 0 ? 'bg-blue-600 text-white' : 'bg-gray-300 text-gray-600'"
  >
    1
  </div>
  <span :class="currentStep >= 0 ? 'text-blue-600' : 'text-gray-400'">Application</span>
  <div>
    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
      <path fill-rule="evenodd" clip-rule="evenodd"
        d="M7.29289 14.7071C6.90237 14.3166 6.90237 13.6834 7.29289 13.2929L10.5858 10L7.29289 6.70711C6.90237 6.31658 6.90237 5.68342 7.29289 5.29289C7.68342 4.90237 8.31658 4.90237 8.70711 5.29289L12.7071 9.29289C13.0976 9.68342 13.0976 10.3166 12.7071 10.7071L8.70711 14.7071C8.31658 15.0976 7.68342 15.0976 7.29289 14.7071Z"
        fill="#9CA3AF" />
    </svg>
  </div>

  <!-- Step 2 -->
  <div
    class="w-6 h-6 rounded-full flex items-center justify-center text-sm"
    :class="currentStep >= 1 ? 'bg-blue-600 text-white' : 'bg-gray-300 text-gray-600'"
  >
    2
  </div>
  <span :class="currentStep >= 1 ? 'text-blue-600' : 'text-gray-400'">Endorsements</span>
  <div>
    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
      <path fill-rule="evenodd" clip-rule="evenodd"
        d="M7.29289 14.7071C6.90237 14.3166 6.90237 13.6834 7.29289 13.2929L10.5858 10L7.29289 6.70711C6.90237 6.31658 6.90237 5.68342 7.29289 5.29289C7.68342 4.90237 8.31658 4.90237 8.70711 5.29289L12.7071 9.29289C13.0976 9.68342 13.0976 10.3166 12.7071 10.7071L8.70711 14.7071C8.31658 15.0976 7.68342 15.0976 7.29289 14.7071Z"
        fill="#9CA3AF" />
    </svg>
  </div>

  <!-- Step 3 -->
  <div
    class="w-6 h-6 rounded-full flex items-center justify-center text-sm"
    :class="currentStep >= 2 ? 'bg-blue-600 text-white' : 'bg-gray-300 text-gray-600'"
  >
    3
  </div>
  <span :class="currentStep >= 2 ? 'text-blue-600' : 'text-gray-400'">Review & Submit</span>
</div>


    <!-- Progress Bar -->
    <div class="max-w-xl mx-auto mb-6 bg-[#EAECF0] rounded-full h-2 mt-3">
      <div class="bg-[#039855]  h-2 rounded-full" :style="{ width: progressBarWidth }"></div>
    </div>

    <div>
      <div v-if="currentStep === 0">
        <EliteFormOne />
      </div>
      <div v-if="currentStep === 1">
        <EliteFormTwo />
      </div>
      <div v-if="currentStep === 2">
        <EliteFormThree />
      </div>

    </div>
  </div>
</template>

<script setup>
import { ArrowRightCircleIcon } from '@heroicons/vue/16/solid';
import { ArrowSmallDownIcon } from '@heroicons/vue/20/solid';


const steps = [0, 1, 2]
const currentStep = ref(0)
const router = useRouter()

const progressBarWidth = computed(() => `${((currentStep.value + 1) / steps.length) * 100}%`)

const isLastStepValid = true

const nextStep = () => {
  if (currentStep.value < steps.length - 1) {
    currentStep.value++
  } else {
    router.push('/')
  }
};

const prevStep = () => {
  if (currentStep.value > 0) {
    currentStep.value--
  }
};
</script>