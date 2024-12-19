<template>
  <!-- Consent Form -->
  <div v-if="!showForm" class="flex items-center justify-center mt-6">
    <div class="bg-white max-w-xl mx-auto rounded-lg  py-8 ring-1 ring-gray-100 w-full text-center">
      <div class="flex justify-center mb-4">
        <div class="w-24 h-24 bg-blue-100 rounded-full flex items-center justify-center">
          <img src="../../assets/endorsement.svg" alt="Professional Endorsements" class="w-46 h-46" />
        </div>
      </div>

      <h2 class="text-lg font-semibold text-gray-800">Professional Endorsements</h2>
      <p class="text-gray-600 mt-2 mb-4 text-sm items-center max-w-sm mx-auto">
        Provide information about at least<strong class="text-gray-800">two (2)</strong> people who can speak for your skills
        and endorse you for Elite
      </p>

      <!-- Consent Checkbox -->
      <div class="flex items-center justify-center mb-4">
        <input type="checkbox" id="consent" v-model="isChecked" class="form-checkbox h-3 w-4 text-blue-600" />
        <label for="consent" class="ml-2 text-gray-800 text-xs">
          I consent to background and reference checks including endorsements
        </label>
      </div>

      <button @click="onProceed" :disabled="!isChecked"
        class="w-1/2 bg-blue-500 text-white font-medium py-2 rounded-md hover:bg-blue-600 transition disabled:bg-blue-300">
        Proceed
      </button>
    </div>
  </div>

  <!-- Endorsement Form -->
  <div v-if="showForm" class="flex items-center justify-center p-6 bg-gray-50">
    <div class="w-full max-w-xl bg-white rounded-lg shadow-md p-8 ring-1 ring-gray-100">
      <div class="flex items-center mb-6">
        <div class="w-12 h-12 bg-blue-100 rounded-full flex items-center justify-center mr-4">
          <img src="../../assets/images/person.svg" alt="person icon" class="w-6 h-6" />
        </div>
        <div>
          <h2 class="text-xl font-semibold text-gray-800">Professional Endorsement</h2>
          <p class="text-gray-500 text-sm">Provide information about people who can speak for your skills</p>
        </div>
      </div>

      <!-- Form -->
      <form @submit.prevent="onSubmit" class="space-y-4">
        <!-- Prefix -->
        <div>
          <label for="prefix" class="block text-base font-medium text-gray-800 mb-2">Prefix</label>
          <input v-model="form.prefix" id="prefix" type="text" placeholder="E.g Dr, Mr"
            class="w-full rounded-md ring-1 ring-gray-300 px-3 py-2 text-gray-900 placeholder-gray-400 shadow-sm focus:outline-indigo-500 focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
        </div>

        <!-- First and Last Name -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div>
            <label for="first-name" class="block text-base font-medium text-gray-800 mb-2">First Name</label>
            <input v-model="form.firstName" id="first-name" type="text"
              placeholder="First name of the person endorsing you"
              class="w-full rounded-md ring-1 ring-gray-300 px-3 py-2 text-gray-900 placeholder-gray-400 shadow-sm focus:outline-indigo-500 focus:ring-indigo-500 focus:border-indigo-500 sm:text-base" />
          </div>
          <div>
            <label for="last-name" class="block text-base font-medium text-gray-800 mb-2">Last Name</label>
            <input v-model="form.lastName" id="last-name" type="text"
              placeholder="Last name of the person endorsing you"
              class="w-full rounded-md ring-1 ring-gray-300 px-3 py-2 text-gray-900 placeholder-gray-400 shadow-sm focus:outline-indigo-500 focus:ring-indigo-500 focus:border-indigo-500 sm:text-base" />
          </div>
        </div>

        <!-- Professional Email Address -->
        <div>
          <label for="email" class="block text-base font-medium text-gray-800 mb-2">Professional Email Address</label>
          <input v-model="form.email" id="email" type="email" placeholder="E.g mail@work.com"
            class="w-full rounded-md ring-1 ring-gray-300 px-3 py-2 text-gray-900 placeholder-gray-400 shadow-sm focus:outline-indigo-500 focus:ring-indigo-500 focus:border-indigo-500 sm:text-base" />
        </div>

        <!-- LinkedIn URL -->
        <div>
          <label for="linkedin" class="block text-base font-medium text-gray-800 mb-2">Endorser's LinkedIn</label>
          <input v-model="form.linkedin" id="linkedin" type="url" placeholder="LinkedIn URL of endorser"
            class="w-full rounded-md ring-1 ring-gray-300 px-3 py-2 text-gray-900 placeholder-gray-400 shadow-sm focus:outline-indigo-500 focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" />
        </div>

        <!--  Endorser Dropdown-->
        <Listbox as="div" v-model="selectedEndorser" class="mb-4">
          <ListboxLabel class="block font-medium text-base text-gray-800">Relationship with Endorser</ListboxLabel>
          <div class="relative mt-2">
            <ListboxButton
              class="grid w-full cursor-default grid-cols-1 rounded-md bg-white py-1.5 pl-3 pr-2 text-left text-gray-900 outline outline-1 -outline-offset-1 outline-gray-300 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6">
              <span class="col-start-1 row-start-1 truncate pr-6">
                {{ selectedEndorser?.name || 'Select a relationship...' }}
              </span>
              <ChevronUpDownIcon
                class="col-start-1 row-start-1 size-5 self-center justify-self-end text-gray-500 sm:size-4"
                aria-hidden="true" />
            </ListboxButton>

            <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100"
              leave-to-class="opacity-0">
              <ListboxOptions
                class="absolute z-10 mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black/5 focus:outline-none sm:text-sm">
                <ListboxOption as="template" v-for="endorser in endorsers" :key="endorser.id" :value="endorser"
                  v-slot="{ active, selected }">
                  <li
                    :class="[active ? 'bg-indigo-600 text-white outline-none' : 'text-gray-900', 'relative cursor-default select-none py-2 pl-3 pr-9']">
                    <span :class="[selected ? 'font-semibold' : 'font-normal', 'block truncate']">{{ endorser.name
                      }}</span>

                    <span v-if="selected"
                      :class="[active ? 'text-white' : 'text-indigo-600', 'absolute inset-y-0 right-0 flex items-center pr-4']">
                      <CheckIcon class="size-5" aria-hidden="true" />
                    </span>
                  </li>
                </ListboxOption>
              </ListboxOptions>
            </transition>
          </div>
        </Listbox>

        <!-- Personalized Message -->
        <div>
         

     <label for="message" class="block text-base font-medium text-gray-800 mb-2">Personalized Message</label>
          <p class="text-sm/snug text-gray-600 mb-2">Add a personalized message to show your endorser</p>
          <div class="relative bg-blue-50 rounded-lg p-4 border border-blue-100 flex items-start justify-between mb-3">
      <div class="flex items-start">
        <!-- Icon -->
        <div class="flex-shrink-0 mr-3">
          <div class="w-8 h-8 rounded-full bg-blue-500 flex items-center justify-center">
            <svg
              class="w-5 h-5 text-white"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M8 10h.01M12 10h.01M16 10h.01M9 16h6M21 12c0 4.418-3.582 8-8 8s-8-3.582-8-8 3.582-8 8-8 8 3.582 8 8z"
              />
            </svg>
          </div>
        </div>
        <!-- Text -->
        <div>
          <p class="text-sm font-medium text-gray-900">Don’t Know what to type?</p>
          <p class="text-sm text-gray-500">Ask Ammie to suggest a message</p>
        </div>
      </div>
      <!-- Buttons -->
      <div class="flex items-center space-x-2">
        <button
          class="w-4 h-4 rounded-full text-blue-500 hover:text-blue-600 focus:outline-none"
          @click=""
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-4 h-4"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
        <button
          class="w-4 h-4 rounded-full text-blue-500 hover:text-blue-600 focus:outline-none"
          @click=""
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-4 h-4"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M4.5 12.75l6 6 9-13.5"
            />
          </svg>
        </button>
      </div>
    </div>

          <textarea v-model="form.message" id="message" rows="4" placeholder="E.g Hello, I would like you to endorse me"
            class="w-full rounded-md ring-1 ring-gray-300 px-3 py-2 text-gray-900 placeholder-gray-400 shadow-sm focus:outline-indigo-500 focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"></textarea>
        
          </div>


 


        <!-- Skills -->
        <div class="mb-4">
        <p class="block text-base font-medium text-gray-800 mb-2">SKills they can endorse you for.</p>
        <!-- <p class="mt-2 mb-2 text-sm text-gray-600">List relevant skills</p> -->
        <SelectMultiSelect :options="skills" v-model="selectedSkills" placeholder="List relevant skills" />

      </div>


        <div class="pt-4">
          <button type="submit"
            class="w-full bg-blue-600 text-white font-medium py-2 rounded-md hover:bg-blue-700 transition focus:ring-2 focus:ring-indigo-500 focus:outline-none">
            Submit Endorsement
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>
import { Listbox, ListboxButton, ListboxLabel, ListboxOption, ListboxOptions } from '@headlessui/vue'
import { ChevronUpDownIcon } from '@heroicons/vue/16/solid'

const showForm = ref(false)
const isChecked = ref(false)
const selectedEndorser = ref(null)
const selectedSkills = ref([])

const form = reactive({
  prefix: "",
  firstName: "",
  lastName: "",
  email: "",
  linkedin: "",
  message: "",
  skills: [],
})

const endorsers = [
  { id: 1, name: 'Current Employer' },
  { id: 2, name: 'Former Manager' },
  { id: 3, name: 'Mentor' },
]


const skills = ["Communication", "Leadership", "Teamwork", "Problem-solving", "Technical Skills"];

const onProceed = () => {
  if (isChecked.value) {
    showForm.value = true;
  }
};

const onSubmit = () => {
  console.log("Form Submitted:", form)
  alert("Endorsement submitted successfully!")
}
</script>
