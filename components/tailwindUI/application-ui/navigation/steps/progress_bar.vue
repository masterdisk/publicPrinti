<template>
  <div>
    <h4 class="sr-only">
      Status
    </h4>
    <p class="text-sm font-medium text-gray-900">
      Migrating MySQL database...
    </p>
    <div class="mt-6" aria-hidden="true">
      <div class="overflow-hidden rounded-full bg-gray-200">
        <div class="h-2 rounded-full bg-indigo-600" style="width: 37.5%" />
      </div>
      <div class="mt-6 hidden grid-cols-4 text-sm font-medium text-gray-600 sm:grid">
        <div class="text-indigo-600">
          Copying files
        </div>
        <div class="text-center text-indigo-600">
          Migrating database
        </div>
        <div class="text-center">
          Compiling assets
        </div>
        <div class="text-right">
          Deployed
        </div>
      </div>
    </div>
  </div>
</template>
