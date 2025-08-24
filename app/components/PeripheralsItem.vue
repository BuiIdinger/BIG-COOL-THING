<template>
  <NuxtLink
    :to="'/peripheral/' + link"
    target="_self"
  >
    <div class="items-center flex justify-between">
      <div class="flex gap-x-[10px]">
        <!-- Icon -->
        <div class="flex items-center justify-center bg-gray-200 p-[14px] rounded-[20%]">
          <component
            :is="icon"
            v-if="icon"
            class="w-[24px] h-[24px] stroke-[1.7px]"
          />
        </div>

        <!-- Title Block -->
        <div class="flex flex-col justify-between flex-grow h-full">
          <h1>{{ name }}</h1>
          <h2 class="opacity-50 text-[14px]">{{ description }}</h2>
        </div>
      </div>

      <!-- Chevron -->
      <div>
        <IconsChevron />
      </div>
    </div>
  </NuxtLink>
</template>

<script setup lang="ts">
defineProps<{
  name: string
  description: string
  icon: Component
  link: string
}>()
</script>