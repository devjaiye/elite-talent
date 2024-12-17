<template>
    <div class="max-w-xl mx-auto p-6 bg-white ring-gray-200 ring-1 rounded-lg">
<h2 class="text-2xl font-semibold mb-4">Availability and Compensation</h2>

<!-- Salary Type -->
<Listbox as="div" v-model="selectedSalary" class="mb-4">
<ListboxLabel class="block text-sm/6 font-medium text-gray-900">Salary Type</ListboxLabel>
<div class="relative mt-2">
  <ListboxButton class="grid w-full cursor-default grid-cols-1 rounded-md bg-white py-1.5 pl-3 pr-2 text-left text-gray-900 outline outline-1 -outline-offset-1 outline-gray-300 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6">
    <span class="col-start-1 row-start-1 truncate pr-6">{{ selectedSalary.name }}</span>
    <ChevronUpDownIcon class="col-start-1 row-start-1 size-5 self-center justify-self-end text-gray-500 sm:size-4" aria-hidden="true" />
  </ListboxButton>

  <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100" leave-to-class="opacity-0">
    <ListboxOptions class="absolute z-10 mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black/5 focus:outline-none sm:text-sm">
      <ListboxOption as="template" v-for="salary in salary" :key="salary.id" :value="salary" v-slot="{ active, selectedSalary }">
        <li :class="[active ? 'bg-indigo-600 text-white outline-none' : 'text-gray-900', 'relative cursor-default select-none py-2 pl-3 pr-9']">
          <span :class="[selectedSalary ? 'font-semibold' : 'font-normal', 'block truncate']">{{ salary.name }}</span>

          <span v-if="selectedSalary" :class="[active ? 'text-white' : 'text-indigo-600', 'absolute inset-y-0 right-0 flex items-center pr-4']">
            <CheckIcon class="size-5" aria-hidden="true" />
          </span>
        </li>
      </ListboxOption>
    </ListboxOptions>
  </transition>
</div>
</Listbox>

<!-- Currency -->
<Listbox as="div" v-model="selectedCurrency" class="mb-4">
<ListboxLabel class="block text-sm/6 font-medium text-gray-900">Currency</ListboxLabel>
<div class="relative mt-2">
  <ListboxButton class="grid w-full cursor-default grid-cols-1 rounded-md bg-white py-1.5 pl-3 pr-2 text-left text-gray-900 outline outline-1 -outline-offset-1 outline-gray-300 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6">
    <span class="col-start-1 row-start-1 truncate pr-6">{{ selectedCurrency.name }}</span>
    <ChevronUpDownIcon class="col-start-1 row-start-1 size-5 self-center justify-self-end text-gray-500 sm:size-4" aria-hidden="true" />
  </ListboxButton>

  <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100" leave-to-class="opacity-0">
    <ListboxOptions class="absolute z-10 mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black/5 focus:outline-none sm:text-sm">
      <ListboxOption as="template" v-for="currency in currencies" :key="currencies.id" :value="currencies" v-slot="{ active, selectedCurrency }">
        <li :class="[active ? 'bg-indigo-600 text-white outline-none' : 'text-gray-900', 'relative cursor-default select-none py-2 pl-3 pr-9']">
          <span :class="[selectedCurrency ? 'font-semibold' : 'font-normal', 'block truncate']">{{ currency.name }}</span>

          <span v-if="selectedCurrency" :class="[active ? 'text-white' : 'text-indigo-600', 'absolute inset-y-0 right-0 flex items-center pr-4']">
            <CheckIcon class="size-5" aria-hidden="true" />
          </span>
        </li>
      </ListboxOption>
    </ListboxOptions>
  </transition>
</div>
</Listbox>

<!-- Desired Salary Range -->
<div class="mb-4">
  <label for="price" class="block text-sm/6 font-medium text-gray-900">Desired Salary Range</label>
<div class="mt-2">
  <div class="flex items-center rounded-md bg-white pl-3 outline outline-1 -outline-offset-1 outline-gray-300 has-[input:focus-within]:outline 
  has-[input:focus-within]:outline-2 has-[input:focus-within]:-outline-offset-2 has-[input:focus-within]:outline-indigo-600">
    <div class="grid shrink-0 grid-cols-1 focus-within:relative mr-2">
      <select id="salary-range" name="salary-range" aria-label="Salary Range" class="col-start-1 row-start-1 w-full appearance-none rounded-md
       py-1.5 pl-3 pr-7 text-base text-gray-500 placeholder:text-gray-400 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6">
        <option>USD $</option>
        <option>CAD $</option>
        <option>EUR €</option>
      </select>
      <ChevronDownIcon class="pointer-events-none col-start-1 row-start-1 mr-2 size-5 self-center justify-self-end text-gray-500 sm:size-4" aria-hidden="true" />
    </div>
    <div class="shrink-0 select-none text-base text-gray-500 sm:text-sm/6">min</div>
    <input type="text" name="price" id="price" class="block min-w-0 grow py-1.5 pl-1 pr-3 text-base text-gray-900 placeholder:text-gray-400 focus:outline focus:outline-0 sm:text-sm/6" placeholder="0.00" />

    <div class="shrink-0 select-none text-base text-gray-500 sm:text-sm/6">max</div>
    <input type="text" name="price" id="price" class="block min-w-0 grow py-1.5 pl-1 pr-3 text-base text-gray-900 placeholder:text-gray-400 focus:outline focus:outline-0 sm:text-sm/6" placeholder="0.00" />


  </div>
</div>
</div>

<!-- Work Availability -->
<Listbox as="div" v-model="selectedAvailability" class="mb-4">
<ListboxLabel class="block text-sm/6 font-medium text-gray-900">What is your availability for work?</ListboxLabel>
<div class="relative mt-2">
  <ListboxButton class="grid w-full cursor-default grid-cols-1 rounded-md bg-white py-1.5 pl-3 pr-2 text-left text-gray-900 outline outline-1 -outline-offset-1 outline-gray-300 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6">
    <span class="col-start-1 row-start-1 truncate pr-6">{{ selectedAvailability.name }}</span>
    <ChevronUpDownIcon class="col-start-1 row-start-1 size-5 self-center justify-self-end text-gray-500 sm:size-4" aria-hidden="true" />
  </ListboxButton>

  <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100" leave-to-class="opacity-0">
    <ListboxOptions class="absolute z-10 mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black/5 focus:outline-none sm:text-sm">
      <ListboxOption as="template" v-for="availability in availability" :key="availability.id" :value="availability" v-slot="{ active, selectedAvailability }">
        <li :class="[active ? 'bg-indigo-600 text-white outline-none' : 'text-gray-900', 'relative cursor-default select-none py-2 pl-3 pr-9']">
          <span :class="[selectedAvailability ? 'font-semibold' : 'font-normal', 'block truncate']">{{ availability.name }}</span>

          <span v-if="selectedAvailability" :class="[active ? 'text-white' : 'text-indigo-600', 'absolute inset-y-0 right-0 flex items-center pr-4']">
            <CheckIcon class="size-5" aria-hidden="true" />
          </span>
        </li>
      </ListboxOption>
    </ListboxOptions>
  </transition>
</div>
</Listbox>

<!-- Start Date -->
<Listbox as="div" v-model="selectedStart" class="mb-4">
<ListboxLabel class="block text-sm/6 font-medium text-gray-900">How soon can you start working?</ListboxLabel>
<div class="relative mt-2">
  <ListboxButton class="grid w-full cursor-default grid-cols-1 rounded-md bg-white py-1.5 pl-3 pr-2 text-left text-gray-900 outline outline-1 -outline-offset-1 outline-gray-300 focus:outline focus:outline-2 focus:-outline-offset-2 focus:outline-indigo-600 sm:text-sm/6">
    <span class="col-start-1 row-start-1 truncate pr-6">{{ selectedStart.name }}</span>
    <ChevronUpDownIcon class="col-start-1 row-start-1 size-5 self-center justify-self-end text-gray-500 sm:size-4" aria-hidden="true" />
  </ListboxButton>

  <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100" leave-to-class="opacity-0">
    <ListboxOptions class="absolute z-10 mt-1 max-h-60 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black/5 focus:outline-none sm:text-sm">
      <ListboxOption as="template" v-for="availability in availability" :key="availability.id" :value="availability" v-slot="{ active, selectedStart }">
        <li :class="[active ? 'bg-indigo-600 text-white outline-none' : 'text-gray-900', 'relative cursor-default select-none py-2 pl-3 pr-9']">
          <span :class="[selectedStart ? 'font-semibold' : 'font-normal', 'block truncate']">{{ availability.name }}</span>

          <span v-if="selectedStart" :class="[active ? 'text-white' : 'text-indigo-600', 'absolute inset-y-0 right-0 flex items-center pr-4']">
            <CheckIcon class="size-5" aria-hidden="true" />
          </span>
        </li>
      </ListboxOption>
    </ListboxOptions>
  </transition>
</div>
</Listbox>
</div>
 
</template>

<script setup>
import { ChevronDownIcon } from '@heroicons/vue/16/solid'
import { Listbox, ListboxButton, ListboxLabel, ListboxOption, ListboxOptions } from '@headlessui/vue'
import { ChevronUpDownIcon } from '@heroicons/vue/16/solid'
import { CheckIcon } from '@heroicons/vue/20/solid'

const salary = [
  { id: 1, name: 'Annual Salary' },
  { id: 2, name: 'Hourly Rate' },
]

const currencies = [
  { id: 1, name: 'USD' },
  { id: 2, name: 'EUR' },
]

const availability = [
{ id: 1, name: 'Full time' },
{ id: 2, name: 'Part time' },
{ id: 3, name: 'Remote' },
{ id: 4, name: 'Contract' },
]

const startDate = [
{ id: 1, name: 'As soon as possible' },
{ id: 2, name: '2 weeks' },
{ id: 3, name: '4 weeks' },
{ id: 4, name: '8 weeks' },
{id: 5, name: 'Three months' },
]

const selectedSalary = ref(salary[0])
const selectedCurrency = ref(currencies[0])
const selectedAvailability = ref(availability[1])
const selectedStart = ref(startDate[1])
</script>
