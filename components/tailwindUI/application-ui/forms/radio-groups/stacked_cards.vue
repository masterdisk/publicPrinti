<script setup>
import { ref } from 'vue'
import { RadioGroup, RadioGroupDescription, RadioGroupLabel, RadioGroupOption } from '@headlessui/vue'

const plans = [
  { name: 'Hobby', ram: '8GB', cpus: '4 CPUs', disk: '160 GB SSD disk', price: '$40' },
  { name: 'Startup', ram: '12GB', cpus: '6 CPUs', disk: '256 GB SSD disk', price: '$80' },
  { name: 'Business', ram: '16GB', cpus: '8 CPUs', disk: '512 GB SSD disk', price: '$160' },
  { name: 'Enterprise', ram: '32GB', cpus: '12 CPUs', disk: '1024 GB SSD disk', price: '$240' },
]

const selected = ref(plans[0])
</script>

<template>
  <RadioGroup v-model="selected">
    <RadioGroupLabel class="sr-only">
      Server size
    </RadioGroupLabel>
    <div class="space-y-4">
      <RadioGroupOption v-for="plan in plans" :key="plan.name" v-slot="{ checked, active }" as="template" :value="plan">
        <div class="relative block cursor-pointer rounded-lg border bg-white px-6 py-4 shadow-sm focus:outline-none sm:flex sm:justify-between" :class="[checked ? 'border-transparent' : 'border-gray-300', active ? 'border-indigo-500 ring-2 ring-indigo-500' : '']">
          <span class="flex items-center">
            <span class="flex flex-col text-sm">
              <RadioGroupLabel as="span" class="font-medium text-gray-900">{{ plan.name }}</RadioGroupLabel>
              <RadioGroupDescription as="span" class="text-gray-500">
                <span class="block sm:inline">{{ plan.ram }} / {{ plan.cpus }}</span>
                {{ ' ' }}
                <span class="hidden sm:mx-1 sm:inline" aria-hidden="true">&middot;</span>
                {{ ' ' }}
                <span class="block sm:inline">{{ plan.disk }}</span>
              </RadioGroupDescription>
            </span>
          </span>
          <RadioGroupDescription as="span" class="mt-2 flex text-sm sm:mt-0 sm:ml-4 sm:flex-col sm:text-right">
            <span class="font-medium text-gray-900">{{ plan.price }}</span>
            <span class="ml-1 text-gray-500 sm:ml-0">/mo</span>
          </RadioGroupDescription>
          <span class="pointer-events-none absolute -inset-px rounded-lg" :class="[active ? 'border' : 'border-2', checked ? 'border-indigo-500' : 'border-transparent']" aria-hidden="true" />
        </div>
      </RadioGroupOption>
    </div>
  </RadioGroup>
</template>
