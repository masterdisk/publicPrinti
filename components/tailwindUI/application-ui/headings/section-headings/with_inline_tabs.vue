<script setup>
const tabs = [
  { name: 'Open', href: '#', current: true },
  { name: 'Closed', href: '#', current: false },
]
</script>

<template>
  <div class="border-b border-gray-200">
    <div class="sm:flex sm:items-baseline">
      <h3 class="text-lg font-medium leading-6 text-gray-900">
        Issues
      </h3>
      <div class="mt-4 sm:mt-0 sm:ml-10">
        <nav class="-mb-px flex space-x-8">
          <a v-for="tab in tabs" :key="tab.name" :href="tab.href" class="whitespace-nowrap pb-4 px-1 border-b-2 font-medium text-sm" :class="[tab.current ? 'border-indigo-500 text-indigo-600' : 'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300']" :aria-current="tab.current ? 'page' : undefined">{{ tab.name }}</a>
        </nav>
      </div>
    </div>
  </div>
</template>
