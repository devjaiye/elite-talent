<template>
  <div class="mx-auto py-10">

    <div class="mb-4 flex justify-between max-w-6xl mx-auto">
      <div>Back</div>
      <div class="flex-col">
        <h2 class="text-xl font-bold mb-2">Work and Compensation Preferences</h2>
        <p class="text-sm">Set Up your work and compensation preferences, this can be adjusted anytime</p>
      </div>

      <button @click="finishStep" :disabled="currentStep === steps.length - 1"
        class="w-auto px-3 bg-blue-500 text-white text-sm rounded-md hover:bg-blue-600 transition">
        {{ currentStep === steps.length - 1 ? 'Finish' : 'Save & Continue' }}
      </button>
    </div>
    <div class="relative mb-6 max-w-xl mx-auto">
      <div class="h-2 bg-[#EAECF0] rounded-full">
        <div class="h-2 bg-[#039855] rounded-full transition-all duration-300" :style="{ width: progressBarWidth }">
        </div>
      </div>

    </div>

    <div>
      <div v-if="currentStep === 0">
          <WorkPreferencesFormOne/>
      </div>
      <div v-if="currentStep === 1">
      <WorkPreferencesFormTwo/>
      </div>
    </div>
  </div>
</template>

<script setup>

    const steps = [0, 1]
    const currentStep = ref(0)

    const handleSubmit = () => {
      console.log("Form Data Submitted:", form)
    };

    const progressBarWidth = computed(() => `${((currentStep.value + 1) / steps.length) * 100}%`)

    const nextStep = () => {
      if (currentStep.value < steps.length - 1) {
        currentStep.value++
      }
    };

    const prevStep = () => {
      if (currentStep.value > 0) {
        currentStep.value--
      }
    }

    const finishStep = () => {
  if (currentStep.value === steps.length - 1) {
    router.push('/');
  }
}
</script>