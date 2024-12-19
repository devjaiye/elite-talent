<template>
  <div class="max-w-xl mx-auto">
    <!-- Video Introduction Section -->
    <div class="bg-white border  border-gray-200 shadow-sm rounded-md mt-8 p-2 space-y-4">
      <div class="flex items-center space-x-2">
        <span class="flex items-center justify-center w-8 h-8 rounded-full bg-blue-100 text-blue-600">
          <svg xmlns="http://www.w3.org/2000/svg" width="21" height="16" viewBox="0 0 21 16" fill="none">
            <path
              d="M7.90909 5.31818H4.45455M14.6404 4.21095C14.8182 5.04436 14.8182 6.16074 14.8182 7.90909C14.8182 9.65711 14.8182 10.7734 14.6405 11.6068M14.6404 4.21095C14.5722 3.89154 14.4779 3.6137 14.3475 3.35777C13.9335 2.54525 13.2729 1.88465 12.4604 1.47065C11.5367 1 10.3275 1 7.90909 1C5.49068 1 4.28148 1 3.35777 1.47065C2.54525 1.88465 1.88465 2.54525 1.47065 3.35777C1 4.28148 1 5.49068 1 7.90909C1 10.3275 1 11.5367 1.47065 12.4604C1.88465 13.2729 2.54525 13.9335 3.35777 14.3475C4.28148 14.8182 5.49068 14.8182 7.90909 14.8182C10.3275 14.8182 11.5367 14.8182 12.4604 14.3475C13.2729 13.9335 13.9335 13.2729 14.3475 12.4604C14.478 12.2044 14.5723 11.9264 14.6405 11.6068M14.6404 4.21095L14.8182 4.12788L15.1622 3.97754C17.3454 3.0236 18.437 2.54663 19.2185 3.05801C20 3.56939 20 4.76062 20 7.14308V8.6751C20 11.0576 20 12.2488 19.2185 12.7602C18.437 13.2716 17.3454 12.7946 15.1622 11.8406L14.8182 11.6903L14.6405 11.6068"
              stroke="#0B6CF4" stroke-width="1.5" stroke-linecap="round" />
          </svg>
        </span>
        <h2 class="text-lg font-semibold py-2">Video Introduction</h2>
      </div>
      <p class="text-gray-900 font-medium">Tell Us About Yourself</p>
      <p class="text-sm text-gray-500">
        In 3 minutes or less tell us about yourself and your previous
        experiences up until now.
      </p>
      <div class="flex items-center space-x-2">
        <div class="w-6 h-6 flex items-center justify-center bg-blue-100 rounded-full">
          <span class="text-blue-500 text-sm font-bold">!</span>
        </div>
        <p class="text-gray-700 text-sm">
          Don’t know what to record?
          <a href="#" class="text-blue-600 underline">Get recording tips</a>
        </p>
      </div>
      <div class="flex items-center space-x-4 py-2">
    <!-- Microphone Selector -->
      <Listbox as="div" v-model="selectedAudio" class="">
          <div class="relative">
            <ListboxButton
              class="flex w-full space-x-2 cursor-default grid-cols-1 rounded-md bg-white py-1.5 pl-3 pr-2 text-left text-gray-900 outline outline-1 -outline-offset-1 outline-gray-300 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6">
              <div>
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
                  <path
                    d="M15.8337 9.16666C15.8337 12.3883 13.222 15 10.0003 15M10.0003 15C6.77866 15 4.16699 12.3883 4.16699 9.16666M10.0003 15V18.3333M10.0003 18.3333H6.66699M10.0003 18.3333H13.3337M10.0003 11.6667C8.61961 11.6667 7.50033 10.5474 7.50033 9.16666V4.16666C7.50033 2.78594 8.61961 1.66666 10.0003 1.66666C11.381 1.66666 12.5003 2.78594 12.5003 4.16666V9.16666C12.5003 10.5474 11.381 11.6667 10.0003 11.6667Z"
                    stroke="#6B7280" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
                </svg>
              </div>
              <span class="col-start-1 row-start-1 truncate pr-3">
                {{ selectedAudio?.name || 'Select Audio' }}
              </span>
              <ChevronUpDownIcon
                class="col-start-1 row-start-1 size-5 self-center justify-self-end text-gray-500 sm:size-4"
                aria-hidden="true" />
            </ListboxButton>
            <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100"
              leave-to-class="opacity-0">
              <ListboxOptions
                class="absolute z-10 mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black/5 focus:outline-none sm:text-sm">
                <ListboxOption as="template" v-for="audio in audios" :key="audio.id" :value="audio"
                  v-slot="{ active, selected }">
                  <li :class="[
                    active
                      ? 'bg-indigo-600 text-white outline-none'
                      : 'text-gray-900',
                    'relative cursor-default select-none py-2 pl-3 pr-9',
                  ]">
                    <span :class="[
                      selected ? 'font-semibold' : 'font-normal',
                      'block truncate',
                    ]">{{ audio.name }}</span>
                    <span v-if="selected" :class="[
                      active ? 'text-white' : 'text-indigo-600',
                      'absolute inset-y-0 right-0 flex items-center pr-4',
                    ]">
                      <CheckIcon class="size-5" aria-hidden="true" />
                    </span>
                  </li>
                </ListboxOption>
              </ListboxOptions>
            </transition>
          </div>
        </Listbox>

    <!-- Camera Selector -->
    <Listbox as="div" v-model="selectedVideo" class="">
          <div class="relative">
            <ListboxButton
              class="flex w-full space-x-2 cursor-default grid-cols-1 rounded-md bg-white py-1.5 pl-3 pr-2 text-left text-gray-900 outline outline-1 -outline-offset-1 outline-gray-300 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6">
              <div>
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
                  <path
                    d="M2.5 7.50001C2.5 6.57954 3.24619 5.83334 4.16667 5.83334H4.94136C5.49862 5.83334 6.019 5.55484 6.32811 5.09118L7.00522 4.07551C7.31433 3.61185 7.83472 3.33334 8.39197 3.33334H11.608C12.1653 3.33334 12.6857 3.61185 12.9948 4.07551L13.6719 5.09118C13.981 5.55484 14.5014 5.83334 15.0586 5.83334H15.8333C16.7538 5.83334 17.5 6.57954 17.5 7.50001V15C17.5 15.9205 16.7538 16.6667 15.8333 16.6667H4.16667C3.24619 16.6667 2.5 15.9205 2.5 15V7.50001Z"
                    stroke="#6B7280" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
                  <path
                    d="M12.5 10.8333C12.5 12.2141 11.3807 13.3333 10 13.3333C8.61929 13.3333 7.5 12.2141 7.5 10.8333C7.5 9.45263 8.61929 8.33334 10 8.33334C11.3807 8.33334 12.5 9.45263 12.5 10.8333Z"
                    stroke="#6B7280" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
                </svg>
              </div>
              <span class="col-start-1 row-start-1 truncate pr-3">
                {{ selectedVideo?.name || 'Select Video' }}
              </span>
              <ChevronUpDownIcon
                class="col-start-1 row-start-1 size-5 self-center justify-self-end text-gray-500 sm:size-4"
                aria-hidden="true" />
            </ListboxButton>
            <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100"
              leave-to-class="opacity-0">
              <ListboxOptions
                class="absolute z-10 mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black/5 focus:outline-none sm:text-sm">
                <ListboxOption as="template" v-for="video in videos" :key="video.id" :value="video"
                  v-slot="{ active, selected }">
                  <li :class="[
                    active
                      ? 'bg-indigo-600 text-white outline-none'
                      : 'text-gray-900',
                    'relative cursor-default select-none py-2 pl-3 pr-9',
                  ]">
                    <span :class="[
                      selected ? 'font-semibold' : 'font-normal',
                      'block truncate',
                    ]">{{ video.name }}</span>
                    <span v-if="selected" :class="[
                      active ? 'text-white' : 'text-indigo-600',
                      'absolute inset-y-0 right-0 flex items-center pr-4',
                    ]">
                      <CheckIcon class="size-5" aria-hidden="true" />
                    </span>
                  </li>
                </ListboxOption>
              </ListboxOptions>
            </transition>
          </div>
        </Listbox>

    <!-- Record Button -->
    <button @click="handleRecord"
          class="sm:mt-0 px-4 py-2 bg-blue-600 text-white font-medium text-sm
          rounded hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500">
          Record Response
        </button>
  </div>
    </div>

    <div class="bg-white border border-gray-200 shadow-sm rounded-md mt-8 p-6 space-y-4">
      <div class="flex items-center space-x-2">
        <span class="flex items-center justify-center w-8 h-8 rounded-full bg-blue-100 text-blue-600">
          <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24" fill="none">
            <path
              d="M19 21V5C19 3.89543 18.1046 3 17 3H7C5.89543 3 5 3.89543 5 5V21M19 21L21 21M19 21H14M5 21L3 21M5 21H10M9 6.99998H10M9 11H10M14 6.99998H15M14 11H15M10 21V16C10 15.4477 10.4477 15 11 15H13C13.5523 15 14 15.4477 14 16V21M10 21H14"
              stroke="#0B6CF4" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </span>
        <h2 class="text-lg font-semibold">Professional Status Update</h2>
      </div>
      <div class="flex flex-col sm:flex-row sm:justify-between sm:items-center">
        <!-- Employment Dropdown -->
        <Listbox as="div" v-model="selectedStatus" class="">
          <div class="relative mt-2 ">
            <ListboxButton
              class="flex w-full space-x-2 cursor-default grid-cols-1 rounded-md bg-white py-1.5 pl-3 pr-2 text-left text-gray-900 outline outline-1 -outline-offset-1 outline-gray-300 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6">
              <span class="col-start-1 row-start-1 truncate pr-6">
                {{ selectedStatus?.name || 'Employment Type' }}
              </span>
              <ChevronUpDownIcon
                class="col-start-1 row-start-1 size-5 self-center justify-self-end text-gray-500 sm:size-4"
                aria-hidden="true" />
            </ListboxButton>
            <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100"
              leave-to-class="opacity-0">
              <ListboxOptions
                class="absolute z-10 mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black/5 focus:outline-none sm:text-sm">
                <ListboxOption as="template" v-for="status in employmentStatuses" :key="status.id" :value="status"
                  v-slot="{ active, selected }">
                  <li :class="[
                    active
                      ? 'bg-indigo-600 text-white outline-none'
                      : 'text-gray-900',
                    'relative cursor-default select-none py-2 pl-3 pr-9',
                  ]">
                    <span :class="[
                      selected ? 'font-semibold' : 'font-normal',
                      'block truncate',
                    ]">{{ status.name }}</span>
                    <span v-if="selected" :class="[
                      active ? 'text-white' : 'text-indigo-600',
                      'absolute inset-y-0 right-0 flex items-center pr-4',
                    ]">
                      <CheckIcon class="size-5" aria-hidden="true" />
                    </span>
                  </li>
                </ListboxOption>
              </ListboxOptions>
            </transition>
          </div>
        </Listbox>
      </div>
    </div>

    <!-- Skill Verification -->
    <div class="bg-white border border-gray-200 shadow-sm rounded-md mt-8 p-6 space-y-4">
      <div class="flex items-center space-x-2 mb-6">
        <span class="flex items-center justify-center w-8 h-8 rounded-full bg-blue-100 text-blue-600">
          <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24" fill="none">
            <path
              d="M19 21V5C19 3.89543 18.1046 3 17 3H7C5.89543 3 5 3.89543 5 5V21M19 21L21 21M19 21H14M5 21L3 21M5 21H10M9 6.99998H10M9 11H10M14 6.99998H15M14 11H15M10 21V16C10 15.4477 10.4477 15 11 15H13C13.5523 15 14 15.4477 14 16V21M10 21H14"
              stroke="#0B6CF4" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </span>
        <h2 class="text-lg font-semibold">Skill Verification</h2>
      </div>

      <div class="mb-4">
        <p class="block text-lg text-gray-900 mb-4">Years of Professional Experience</p>
        <SelectMultiSelect :options="options1" v-model="selectedOptions1" placeholder="0-2 Years" />
        <p class="text-sm/snug text-gray-600 mt-2">Years of experience in your primary profession</p>
      </div>

      <div class="mb-4">
        <p class="block text-lg text-gray-900 mb-2">Primary Professional Domain</p>
        <!-- <p class="text-sm/snug text-gray-600 mb-4">Select your professional domain</p> -->
        <SelectMultiSelect :options="options2" v-model="selectedOptions2" placeholder="Select professional domain" />
      </div>

      <div class="mb-4">
        <p class="block text-lg text-gray-900 mb-2">Select Technologies and Frameworks relevant to your domain</p>
        <SelectMultiSelect :options="options3" v-model="selectedOptions3" placeholder="Select professional domain" />

        <div class="flex items-center space-x-2 mt-6">
          <p class="text-gray-700">Do you have a second professional domain?</p>
          <button v-if="!showInput" @click="toggleInput" class="text-blue-500 hover:text-blue-700 flex items-center">
            <span class="mr-1">Add Secondary Domain</span>
            <span class="text-lg">+</span>
          </button>
        </div>

        <!-- Input Field -->
        <div v-if="showInput" class="mt-2">
          <input v-model="inputValue" type="text" placeholder="Enter domain"
            class="border rounded p-2 w-64 focus:outline-blue-500" @keyup.enter="addDomain" />
          <button @click="addDomain" class="ml-2 bg-blue-500 text-white px-4 py-1 rounded hover:bg-blue-600">
            Add
          </button>
        </div>

        <!-- Selected Domains -->
        <div v-if="domains.length > 0" class="mt-4">
          <p class="text-gray-700 font-semibold">Selected Domains:</p>
          <ul class="mt-2 space-y-1">
            <li v-for="(domain, index) in domains" :key="index"
              class="flex items-center justify-between bg-gray-100 rounded p-2 w-64">
              <span class="text-gray-700">{{ domain }}</span>
              <button @click="removeDomain(index)" class="text-red-500 hover:text-red-700">
                x
              </button>
            </li>
          </ul>
        </div>
      </div>



    </div>
  </div>
</template>


<script setup>
import {
  Listbox,
  ListboxButton,
  ListboxOption,
  ListboxOptions,
} from "@headlessui/vue";
import { ChevronUpDownIcon } from "@heroicons/vue/16/solid";
import { CheckIcon } from "@heroicons/vue/20/solid";

const selectedOptions1 = ref([])
const selectedOptions2 = ref([])
const selectedOptions3 = ref([])
const selectedOptions4 = ref([])

    const recordResponse = () => {
      console.log("Recording started with:", {
        microphone: selectedMic.value,
        camera: selectedCamera.value,
      })
    }

const selectedAudio = ref(null)
const selectedVideo = ref(null)
const selectedStatus = ref(null)

const showInput = ref(false)
const inputValue = ref("")
const domains = ref([])

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
])

const audios = [
  { id: 1, name: "Mac Book Pro" },
  { id: 2, name: "HP Laptop" },
];

const videos = [
  { id: 1, name: "Facetime HD" },
  { id: 2, name: "Facetime HHD" },
];

const employmentStatuses = [
  { id: 1, name: "Employed" },
  { id: 2, name: "Unemployed" },
  { id: 3, name: "Self-Employed" },
  { id: 4, name: "Student" },
];



const handleRecord = () => {
  alert(`Recording started with: ${selectedAudio?.value?.name || "No Audio Device Selected"}`);
}

const toggleInput = () => {
  showInput.value = true;
};

// Add domain to list
const addDomain = () => {
  if (inputValue.value.trim() !== "") {
    domains.value.push(inputValue.value.trim());
    inputValue.value = "";
    showInput.value = false;
  }
};

// Remove a domain
const removeDomain = (index) => {
  domains.value.splice(index, 1);
};

</script>

<style scoped>
input:focus {
  border-color: #3b82f6;
  box-shadow: 0 0 0 1px #3b82f6;
}
</style>