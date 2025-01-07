<template>
    <div  v-if="isModalVisible">
        <div class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50 z-50">
            <div class="bg-white max-w-2xl w-full p-6 rounded-lg shadow-lg relative">

                <div class="flex items-center justify-between  py-3 mb-3">
                    <div class="flex items-center">
                        <!-- Icon -->

                     <svg enable-background="new 0 0 48 48" class="w-5 h-5 text-gray-500" height="48px" id="Layer_1" version="1.1" viewBox="0 0 48 48" width="48px" xml:space="preserve" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path clip-rule="evenodd" d="M6,47V20c0-2.209,1.791-4,4-4l0,0v-4c0-1.104,0.896-2,2-2h2V2c0-0.552,0.447-1,1-1  s1,0.448,1,1v8h2c1.104,0,2,0.896,2,2v4l0,0l0,0c2.209,0,4,1.791,4,4v8h7v-6h4v-3h6v3h1v25H6z M18,13c0-0.552-0.447-1-1-1h-4  c-0.553,0-1,0.448-1,1v3h6V13z M22,20c0-1.104-0.896-2-2-2H10c-1.104,0-2,0.896-2,2v25h14V20z M31,30h-7v15h7V30z M40,24h-7v21h7V24  z M36,27h1c0.553,0,1,0.447,1,1v1c0,0.553-0.447,1-1,1h-1c-0.553,0-1-0.447-1-1v-1C35,27.447,35.447,27,36,27z M36,33h1  c0.553,0,1,0.447,1,1v1c0,0.553-0.447,1-1,1h-1c-0.553,0-1-0.447-1-1v-1C35,33.447,35.447,33,36,33z M36,39h1c0.553,0,1,0.447,1,1v1  c0,0.553-0.447,1-1,1h-1c-0.553,0-1-0.447-1-1v-1C35,39.447,35.447,39,36,39z M27,33h1c0.553,0,1,0.447,1,1v1c0,0.553-0.447,1-1,1  h-1c-0.553,0-1-0.447-1-1v-1C26,33.447,26.447,33,27,33z M27,39h1c0.553,0,1,0.447,1,1v1c0,0.553-0.447,1-1,1h-1  c-0.553,0-1-0.447-1-1v-1C26,39.447,26.447,39,27,39z M18,42h-1c-0.553,0-1-0.447-1-1v-1c0-0.552,0.447-1,1-1h1c0.553,0,1,0.448,1,1  v1C19,41.553,18.553,42,18,42z M18,36h-1c-0.553,0-1-0.447-1-1v-1c0-0.552,0.447-1,1-1h1c0.553,0,1,0.448,1,1v1  C19,35.553,18.553,36,18,36z M18,30h-1c-0.553,0-1-0.447-1-1v-1c0-0.552,0.447-1,1-1h1c0.553,0,1,0.448,1,1v1  C19,29.553,18.553,30,18,30z M18,24h-1c-0.553,0-1-0.447-1-1v-1c0-0.552,0.447-1,1-1h1c0.553,0,1,0.448,1,1v1  C19,23.553,18.553,24,18,24z M13,42h-1c-0.553,0-1-0.447-1-1v-1c0-0.553,0.447-1,1-1h1c0.553,0,1,0.447,1,1v1  C14,41.553,13.553,42,13,42z M13,36h-1c-0.553,0-1-0.447-1-1v-1c0-0.553,0.447-1,1-1h1c0.553,0,1,0.447,1,1v1  C14,35.553,13.553,36,13,36z M13,30h-1c-0.553,0-1-0.447-1-1v-1c0-0.552,0.447-1,1-1h1c0.553,0,1,0.448,1,1v1  C14,29.553,13.553,30,13,30z M13,24h-1c-0.553,0-1-0.447-1-1v-1c0-0.552,0.447-1,1-1h1c0.553,0,1,0.448,1,1v1  C14,23.553,13.553,24,13,24z" fill-rule="evenodd"/></svg>
                    </div>

              
                    <button @click="closeModal" class="text-gray-500 hover:text-gray-800 focus:outline-none">
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="none" viewBox="0 0 24 24"
                            stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M6 18L18 6M6 6l12 12" />
                        </svg>
                    </button>
                </div>

    
                <div class="mb-4">
                    <h2 class="text-xl font-semibold text-gray-800">Self-Employment Status Checker</h2>
                    <p class="text-gray-500 text-sm">
                        Check if you will be classified as a Sole trader
                    </p>
                    <hr class="mt-3" />
                </div>

                <div class="bg-gray-100 px-4 py-4 grid grid-cols-2 gap-x-3" v-if="!isSubmitted">
                    <div class=" px-2 py-4">
                        <!-- Progress Bar -->
                        <div class="w-full rounded-full h-2 mb-6 bg-gray-50">
                            <div class="bg-green-500 h-2 rounded-full" :style="{ width: `${progressPercentage}%` }">
                            </div>
                        </div>
                        <div>
                            <h3 class="text-md font-semibold mb-4 text-sm">
                                {{ currentStep }}. {{ questions[currentStep - 1] }}
                            </h3>
                        </div>
                    </div>

                    <div class="bg-white  py-4 ring-1 ring-gray-300 rounded-lg">
                        <div class="space-y-3 px-4">
                            <label class="flex items-center text-sm mb-8">
                                <input type="radio" :name="`step-${currentStep}`" value="Yes"
                                    v-model="selectedOptions[`step${currentStep}`]"
                                    class="form-radio text-blue-600 focus:ring focus:ring-blue-300" />
                                <span class="ml-2 text-gray-700">Yes</span>
                            </label>
                            <label class="flex items-center text-sm">
                                <input type="radio" :name="`step-${currentStep}`" value="No"
                                    v-model="selectedOptions[`step${currentStep}`]"
                                    class="form-radio text-blue-600 focus:ring focus:ring-blue-300" />
                                <span class="ml-2 text-gray-700">No</span>
                            </label>
                        </div>
                        <hr class="mt-8">

                        <!-- Action Buttons -->
                        <div class="mt-6 flex justify-center space-x-4 text-sm px-4">
                            <button @click="onBackOrCancel"
                                class="text-gray-500 hover:text-gray-700 px-8 py-2 rounded-lg ring-1 ring-gray-300 w-full">
                                {{ currentStep === 1 ? "Cancel" : "Back" }}
                            </button>

                            <button v-if="currentStep < totalSteps" @click="onNext"
                                class=" bg-blue-600 text-white hover:bg-blue-700 px-8 py-2 rounded-lg  ring-gray-300 w-full">
                                Next
                            </button>
                            <button v-else @click="onSubmit"
                                class=" bg-blue-600 text-white hover:bg-blue-700 px-8 py-2 rounded-lg ring-1 ring-gray-300 w-full">
                                Submit
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Submitted Content Design -->
                <div v-else="!isSubmitted">
                    <div class="flex flex-col items-center justify-center bg-gray-100">
                        <div class="w-full  p-4">
                            <div class="flex p-4 mb-4 border border-green-200 rounded-lg bg-green-50 items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-green-600 flex-shrink-0"
                                    fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M5.121 17.804A4.992 4.992 0 017 15h10a4.992 4.992 0 011.879 2.804M9 10h6m-6 4h6M9 6h6m-8 16a2 2 0 100-4 2 2 0 000 4zm10 0a2 2 0 100-4 2 2 0 000 4z" />
                                </svg>
                                <div class="ml-3 text-sm">
                                    <strong class="block text-base font-medium">Strong Self-Employment
                                        Indication</strong>
                                    <span class="text-gray-400">Your responses strongly suggest a self-employed business
                                        structure. You meet most criteria for self-employment.</span>
                                </div>
                            </div>
                            <button @click=""
                                class="px-20 py-2 text-white bg-blue-600 rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-400 focus:ring-opacity-75">
                                Continue Application
                            </button>
                        </div>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<script setup>
const currentStep = ref(1)
const totalSteps = 10
const selectedOptions = ref({})
const isSubmitted = ref(false)
const isModalVisible = ref(true)

const questions = [
    "Ownership and Control: Are you the sole owner of your business, with full control over its operations?",
    "Legal Entity: Do you and your business share the same legal identity, meaning you are personally responsible for its debts?",
    "Condition for business: Do you have a registered business name?",
    "Lorem Ipsum: Are you personally responsible for paying taxes on your earnings?",
    "Terms: Do you own or lease the tools and equipment needed for your business?",
    "Employees: Are you free to choose how, when, and where you work?",
    "Do you invoice clients for your work instead of being paid a salary?",
    "Simplicity: Is your business structure simple, with minimal paperwork and compliance requirements?",
    "Profit Retention: Do you retain all profits after tax, rather than disturbing them to shareholders or partners?",
    "Limited External Perception: Do you acknowledge that your business might face challenges raising capital or being perceived as professional compared to a limited company ",
]

const progressPercentage = computed(() => (currentStep.value / totalSteps) * 100)

const onNext = () => {
    if (selectedOptions.value[`step${currentStep.value}`]) {
        currentStep.value += 1
    } else {
        alert("Please select an option before proceeding!")
    }
}

const onBackOrCancel = () => {
    if (currentStep.value === 1) {
        alert("Form canceled.")
    } else {
        currentStep.value -= 1
    }
}

const onSubmit = () => {
    console.log("Form Submitted with:", selectedOptions.value)
    isSubmitted.value = true
}

const closeModal = () => {
   isModalVisible.value = false
};

</script>