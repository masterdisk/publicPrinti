<!--
  This example requires some changes to your config:

  ```
  // tailwind.config.js
  module.exports = {
    // ...
    plugins: [
      // ...
      require('@tailwindcss/forms'),
    ],
  }
  ```
-->
<script setup>
import { ref } from 'vue'
import { FaceSmileIcon as FaceSmileIconOutline, PaperClipIcon } from '@heroicons/vue/24/outline'
import { Listbox, ListboxButton, ListboxLabel, ListboxOption, ListboxOptions } from '@headlessui/vue'
import {
  FaceFrownIcon,
  FaceSmileIcon as FaceSmileIconMini,
  FireIcon,
  HandThumbUpIcon,
  HeartIcon,
  XMarkIcon,
} from '@heroicons/vue/20/solid'

const moods = [
  { name: 'Excited', value: 'excited', icon: FireIcon, iconColor: 'text-white', bgColor: 'bg-red-500' },
  { name: 'Loved', value: 'loved', icon: HeartIcon, iconColor: 'text-white', bgColor: 'bg-pink-400' },
  { name: 'Happy', value: 'happy', icon: FaceSmileIconMini, iconColor: 'text-white', bgColor: 'bg-green-400' },
  { name: 'Sad', value: 'sad', icon: FaceFrownIcon, iconColor: 'text-white', bgColor: 'bg-yellow-400' },
  { name: 'Thumbsy', value: 'thumbsy', icon: HandThumbUpIcon, iconColor: 'text-white', bgColor: 'bg-blue-500' },
  { name: 'I feel nothing', value: null, icon: XMarkIcon, iconColor: 'text-gray-400', bgColor: 'bg-transparent' },
]

const selected = ref(moods[5])
</script>

<template>
  <div class="flex items-start space-x-4">
    <div class="flex-shrink-0">
      <img class="inline-block h-10 w-10 rounded-full" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="">
    </div>
    <div class="min-w-0 flex-1">
      <form action="#">
        <div class="border-b border-gray-200 focus-within:border-indigo-600">
          <label for="comment" class="sr-only">Add your comment</label>
          <textarea id="comment" rows="3" name="comment" class="block w-full resize-none border-0 border-b border-transparent p-0 pb-2 focus:border-indigo-600 focus:ring-0 sm:text-sm" placeholder="Add your comment..." />
        </div>
        <div class="flex justify-between pt-2">
          <div class="flex items-center space-x-5">
            <div class="flow-root">
              <button type="button" class="-m-2 inline-flex h-10 w-10 items-center justify-center rounded-full text-gray-400 hover:text-gray-500">
                <PaperClipIcon class="h-6 w-6" aria-hidden="true" />
                <span class="sr-only">Attach a file</span>
              </button>
            </div>
            <div class="flow-root">
              <Listbox v-model="selected" as="div">
                <ListboxLabel class="sr-only">
                  Your mood
                </ListboxLabel>
                <div class="relative">
                  <ListboxButton class="relative -m-2 inline-flex h-10 w-10 items-center justify-center rounded-full text-gray-400 hover:text-gray-500">
                    <span class="flex items-center justify-center">
                      <span v-if="selected.value === null">
                        <FaceSmileIconOutline class="h-6 w-6 flex-shrink-0" aria-hidden="true" />
                        <span class="sr-only"> Add your mood </span>
                      </span>
                      <span v-if="!(selected.value === null)">
                        <span class="flex h-8 w-8 items-center justify-center rounded-full" :class="[selected.bgColor]">
                          <component :is="selected.icon" class="h-5 w-5 flex-shrink-0 text-white" aria-hidden="true" />
                        </span>
                        <span class="sr-only">{{ selected.name }}</span>
                      </span>
                    </span>
                  </ListboxButton>

                  <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100" leave-to-class="opacity-0">
                    <ListboxOptions class="absolute z-10 -ml-6 w-60 rounded-lg bg-white py-3 text-base shadow ring-1 ring-black ring-opacity-5 focus:outline-none sm:ml-auto sm:w-64 sm:text-sm">
                      <ListboxOption v-for="mood in moods" :key="mood.value" v-slot="{ active }" as="template" :value="mood">
                        <li class="relative cursor-default select-none py-2 px-3" :class="[active ? 'bg-gray-100' : 'bg-white']">
                          <div class="flex items-center">
                            <div class="w-8 h-8 rounded-full flex items-center justify-center" :class="[mood.bgColor]">
                              <component :is="mood.icon" class="flex-shrink-0 h-5 w-5" :class="[mood.iconColor]" aria-hidden="true" />
                            </div>
                            <span class="ml-3 block truncate font-medium">{{ mood.name }}</span>
                          </div>
                        </li>
                      </ListboxOption>
                    </ListboxOptions>
                  </transition>
                </div>
              </Listbox>
            </div>
          </div>
          <div class="flex-shrink-0">
            <button type="submit" class="inline-flex items-center rounded-md border border-transparent bg-indigo-600 px-4 py-2 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">
              Post
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>
