<script setup>
import { Popover, PopoverButton, PopoverPanel } from '@headlessui/vue'
import { ChevronDownIcon } from '@heroicons/vue/20/solid'
import {
  BookmarkSquareIcon,
  BriefcaseIcon,
  BuildingOfficeIcon,
  ComputerDesktopIcon,
  GlobeAltIcon,
  InformationCircleIcon,
  NewspaperIcon,
  ShieldCheckIcon,
  UserGroupIcon,
} from '@heroicons/vue/24/outline'

const company = [
  { name: 'About', href: '#', icon: InformationCircleIcon },
  { name: 'Customers', href: '#', icon: BuildingOfficeIcon },
  { name: 'Press', href: '#', icon: NewspaperIcon },
  { name: 'Careers', href: '#', icon: BriefcaseIcon },
  { name: 'Privacy', href: '#', icon: ShieldCheckIcon },
]
const resources = [
  { name: 'Community', href: '#', icon: UserGroupIcon },
  { name: 'Partners', href: '#', icon: GlobeAltIcon },
  { name: 'Guides', href: '#', icon: BookmarkSquareIcon },
  { name: 'Webinars', href: '#', icon: ComputerDesktopIcon },
]
const blogPosts = [
  {
    id: 1,
    name: 'Boost your conversion rate',
    href: '#',
    preview: 'Eget ullamcorper ac ut vulputate fames nec mattis pellentesque elementum. Viverra tempor id mus.',
    imageUrl:
      'https://images.unsplash.com/photo-1558478551-1a378f63328e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2849&q=80',
  },
  {
    id: 2,
    name: 'How to use search engine optimization to drive traffic to your site',
    href: '#',
    preview: 'Eget ullamcorper ac ut vulputate fames nec mattis pellentesque elementum. Viverra tempor id mus.',
    imageUrl:
      'https://images.unsplash.com/photo-1486312338219-ce68d2c6f44d?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2300&q=80',
  },
]
</script>

<template>
  <Popover v-slot="{ open }" class="relative z-0">
    <div class="relative z-10 bg-white shadow">
      <div class="mx-auto flex max-w-7xl p-6 lg:px-8">
        <PopoverButton class="group inline-flex items-center rounded-md bg-white text-base font-medium hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2" :class="[open ? 'text-gray-900' : 'text-gray-500']">
          <span>Solutions</span>
          <ChevronDownIcon class="ml-2 h-5 w-5 group-hover:text-gray-500" :class="[open ? 'text-gray-600' : 'text-gray-400']" aria-hidden="true" />
        </PopoverButton>
      </div>
    </div>

    <transition enter-active-class="transition ease-out duration-200" enter-from-class="opacity-0 -translate-y-1" enter-to-class="opacity-100 translate-y-0" leave-active-class="transition ease-in duration-150" leave-from-class="opacity-100 translate-y-0" leave-to-class="opacity-0 -translate-y-1">
      <PopoverPanel class="absolute inset-x-0 z-10 transform shadow-lg">
        <div class="absolute inset-0 flex" aria-hidden="true">
          <div class="w-1/2 bg-white" />
          <div class="w-1/2 bg-gray-50" />
        </div>
        <div class="relative mx-auto grid max-w-7xl grid-cols-1 lg:grid-cols-2">
          <nav class="grid gap-y-10 bg-white py-8 px-6 sm:grid-cols-2 sm:gap-x-8 sm:py-12 lg:px-8 xl:pr-12" aria-labelledby="solutions-heading">
            <h2 id="solutions-heading" class="sr-only">
              Solutions menu
            </h2>
            <div>
              <h3 class="text-base font-medium text-gray-500">
                Company
              </h3>
              <ul role="list" class="mt-5 space-y-6">
                <li v-for="item in company" :key="item.name" class="flow-root">
                  <a :href="item.href" class="-m-3 flex items-center rounded-md p-3 text-base font-medium text-gray-900 transition duration-150 ease-in-out hover:bg-gray-50">
                    <component :is="item.icon" class="h-6 w-6 flex-shrink-0 text-gray-400" aria-hidden="true" />
                    <span class="ml-4">{{ item.name }}</span>
                  </a>
                </li>
              </ul>
            </div>
            <div>
              <h3 class="text-base font-medium text-gray-500">
                Resources
              </h3>
              <ul role="list" class="mt-5 space-y-6">
                <li v-for="item in resources" :key="item.name" class="flow-root">
                  <a :href="item.href" class="-m-3 flex items-center rounded-md p-3 text-base font-medium text-gray-900 transition duration-150 ease-in-out hover:bg-gray-50">
                    <component :is="item.icon" class="h-6 w-6 flex-shrink-0 text-gray-400" aria-hidden="true" />
                    <span class="ml-4">{{ item.name }}</span>
                  </a>
                </li>
              </ul>
            </div>
          </nav>
          <div class="bg-gray-50 py-8 px-6 sm:py-12 lg:px-8 xl:pl-12">
            <div>
              <h3 class="text-base font-medium text-gray-500">
                From the blog
              </h3>
              <ul role="list" class="mt-6 space-y-6">
                <li v-for="post in blogPosts" :key="post.id" class="flow-root">
                  <a :href="post.href" class="-m-3 flex rounded-lg p-3 transition duration-150 ease-in-out hover:bg-gray-100">
                    <div class="hidden flex-shrink-0 sm:block">
                      <img class="h-20 w-32 rounded-md object-cover" :src="post.imageUrl" alt="">
                    </div>
                    <div class="min-w-0 flex-1 sm:ml-8">
                      <h4 class="truncate text-base font-medium text-gray-900">{{ post.name }}</h4>
                      <p class="mt-1 text-sm text-gray-500">{{ post.preview }}</p>
                    </div>
                  </a>
                </li>
              </ul>
            </div>
            <div class="mt-6 text-sm font-medium">
              <a href="#" class="text-indigo-600 transition duration-150 ease-in-out hover:text-indigo-500">
                View all posts
                <span aria-hidden="true"> &rarr;</span>
              </a>
            </div>
          </div>
        </div>
      </PopoverPanel>
    </transition>
  </Popover>
</template>
