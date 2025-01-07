<template>
  <div>
    <div class="p-6 max-w-2xl mx-auto bg-white border rounded-lg shadow-md">
      <div class="flex gap-4">
        <svg class="bg-[#EBF3FE] p-2 h-10 w-10  rounded-full" width="24" height="24" viewBox="0 0 24 24" fill="none">
          <path d="M20 21V19C20 16.7909 18.2091 15 16 15H8C5.79086 15 4 16.7909 4 19V21" stroke="#0B6CF4"
            stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
          <path fill-rule="evenodd" clip-rule="evenodd"
            d="M12 11C14.2091 11 16 9.20914 16 7C16 4.79086 14.2091 3 12 3C9.79086 3 8 4.79086 8 7C8 9.20914 9.79086 11 12 11Z"
            stroke="#0B6CF4" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
        </svg>
        <div class="mb-8">
          <h3 class="text-gray-900 font-medium text-lg">Tax Residence</h3>
          <p class="flex text-xs text-gray-500 gap-x-2">
            Provide information about where yoy are registered to pay tax
          </p>
        </div>
      </div>

      <div class="mb-6">
        <h3 class="text-base font-medium text-gray-800 mb-4">How do you operate?</h3>

        <div class="space-y-4">
          <label class="flex items-center space-x-3">
            <input type="radio" name="operationType" value="Independent Contractor/SoleTrader" v-model="operationType"
              class="text-blue-600 focus:ring focus:ring-blue-300 focus:ring-opacity-50" />
            <span class="text-gray-700 text-sm font-medium">
              As an Independent Contractor/ SoleTrader
              <span class="block text-sm text-gray-500">Pick this if you are self-employed</span>
              <button @click="toggleClassifiedModal" class="text-elite-blue font-semibold underline text-xs cursor-pointer">
                Check if you will be classified as a Sole trader
              </button>
            </span>
          </label>

          <label class="flex items-center space-x-3">
            <input type="radio" name="operationType" value="Limited Liability Company" v-model="operationType"
              class="text-blue-600 focus:ring focus:ring-blue-300 focus:ring-opacity-50" />
            <div class="inline-block">
              <span class="text-gray-700 text-sm font-medium">
                As a limited liability company
              </span>
              <span class="block text-sm text-gray-500">Pick this if you have a company</span>
            </div>

          </label>

          <label class="flex items-center space-x-3">
            <input type="radio" name="operationType" value="Umbrella Company/Third-Party Company"
              v-model="operationType" class="text-blue-600 focus:ring focus:ring-blue-300 focus:ring-opacity-50" />
            <span class="text-gray-700 text-sm font-medium">
              As an Umbrella company/ through a Third-Party Company
              <span class="block text-sm text-gray-500">
                Pick this if you are employed via a third-party company/ an FCSA-approved umbrella company
              </span>
            </span>
          </label>
        </div>
      </div>

      <Listbox as="div" v-model="selectedAvailability" class="mb-4">
        <ListboxLabel class="block text-sm/6 font-medium text-gray-900">Where do you or your business operate from?
        </ListboxLabel>
        <div class="relative mt-2">
          <ListboxButton
            class="grid w-full cursor-default grid-cols-1 rounded-md bg-white py-1.5 pl-3 pr-2 text-left text-gray-900 outline outline-1 -outline-offset-1 outline-gray-300 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6">
            <span class="col-start-1 row-start-1 truncate pr-6">{{ selectedAvailability.name }}</span>
            <ChevronUpDownIcon
              class="col-start-1 row-start-1 size-5 self-center justify-self-end text-gray-500 sm:size-4"
              aria-hidden="true" />
          </ListboxButton>

          <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100"
            leave-to-class="opacity-0">
            <ListboxOptions
              class="absolute z-10 mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black/5 focus:outline-none sm:text-sm">
              <ListboxOption as="template" v-for="availability in availability" :key="availability.id"
                :value="availability" v-slot="{ active, selectedAvailability }">
                <li
                  :class="[active ? 'bg-indigo-600 text-white outline-none' : 'text-gray-900', 'relative cursor-default select-none py-2 pl-3 pr-9']">
                  <span :class="[selectedAvailability ? 'font-semibold' : 'font-normal', 'block truncate']">{{
                    availability.name }}</span>

                  <span v-if="selectedAvailability"
                    :class="[active ? 'text-white' : 'text-indigo-600', 'absolute inset-y-0 right-0 flex items-center pr-4']">
                    <CheckIcon class="size-5" aria-hidden="true" />
                  </span>
                </li>
              </ListboxOption>
            </ListboxOptions>
          </transition>

          <p class="text-xs text-gray-500 mt-2">
            If you are an individual, this would be the country you operate in. If you have a business, this would be
            where it is registered.
          </p>
        </div>
      </Listbox>

      <Listbox as="div" v-model="selectedAvailability" class="mb-4">
        <ListboxLabel class="block text-sm/6 font-medium text-gray-900">Where are you personally registered for tax?
        </ListboxLabel>
        <div class="relative mt-2">
          <ListboxButton
            class="grid w-full cursor-default grid-cols-1 rounded-md bg-white py-1.5 pl-3 pr-2 text-left text-gray-900 outline outline-1 -outline-offset-1 outline-gray-300 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6">
            <span class="col-start-1 row-start-1 truncate pr-6">{{ selectedAvailability.name }}</span>
            <ChevronUpDownIcon
              class="col-start-1 row-start-1 size-5 self-center justify-self-end text-gray-500 sm:size-4"
              aria-hidden="true" />
          </ListboxButton>

          <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100"
            leave-to-class="opacity-0">
            <ListboxOptions
              class="absolute z-10 mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black/5 focus:outline-none sm:text-sm">
              <ListboxOption as="template" v-for="availability in availability" :key="availability.id"
                :value="availability" v-slot="{ active, selectedAvailability }">
                <li
                  :class="[active ? 'bg-indigo-600 text-white outline-none' : 'text-gray-900', 'relative cursor-default select-none py-2 pl-3 pr-9']">
                  <span :class="[selectedAvailability ? 'font-semibold' : 'font-normal', 'block truncate']">{{
                    availability.name }}</span>

                  <span v-if="selectedAvailability"
                    :class="[active ? 'text-white' : 'text-indigo-600', 'absolute inset-y-0 right-0 flex items-center pr-4']">
                    <CheckIcon class="size-5" aria-hidden="true" />
                  </span>
                </li>
              </ListboxOption>
            </ListboxOptions>
          </transition>
        </div>
      </Listbox>
      <div>
        <label for="uniqueId" class="block text-sm/6 font-medium text-gray-900">Unique Tax Identification Number</label>
        <div class="mt-2">
          <input type="uniqueId" name="uniqueId" id="uniqueId" aria-label="uniqueId"
            class="block w-full rounded-md bg-white px-3 py-1.5 text-base text-gray-900 outline outline-1 -outline-offset-1 outline-gray-300 placeholder:text-gray-400 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6" />
        </div>
      </div>

      <ContractComplianceClassifiedModal v-if="open"  @close="toggleClassifiedModal" />
    </div>
  </div>
</template>

<script setup>
import { ChevronDownIcon } from '@heroicons/vue/16/solid'
import { Listbox, ListboxButton, ListboxLabel, ListboxOption, ListboxOptions } from '@headlessui/vue'
import { ChevronUpDownIcon } from '@heroicons/vue/16/solid'
import { CheckIcon } from '@heroicons/vue/20/solid'

const availability = [
  { id: 1, name: 'Full time' },
  { id: 2, name: 'Part time' },
  { id: 3, name: 'Remote' },
  { id: 4, name: 'Contract' },
]

const open = ref(false)

const selectedAvailability = ref(availability[1])

const toggleClassifiedModal = () =>{
 open.value = !open.value
};

</script>