<template>
  <div class="mx-[20px]">
    <!-- Section title -->
    <div class="font-medium text-[22px]">
      <p>{{ title }}</p>
    </div>

    <!-- Section content -->
    <slot />
  </div>
</template>

<script setup lang="ts">
defineProps<{
  title: string
}>()
</script>