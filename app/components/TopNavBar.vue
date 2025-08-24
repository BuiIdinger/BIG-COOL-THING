<template>
  <div class="sticky top-0 z-[999] bg-white px-[20px] py-[24px]">
    <div class="flex justify-between items-center leading-none">
      <!-- Empty spacer -->
      <div class="w-[24px] h-[24px]" />

      <!-- Current tab -->
      <div class="font-medium text-[18px] text-center">
        <p>{{ currentPage }}</p>
      </div>

      <!-- Add peripheral icon -->
      <div>
        <IconsPlus />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  currentPage: string
}>()
</script>