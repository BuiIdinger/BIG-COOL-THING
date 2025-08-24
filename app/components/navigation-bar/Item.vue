<template>
  <div class="flex flex-col gap-y-[14px] items-center leading-none">
    <!-- Icon -->
    <div>
      <component :is="icon" v-if="icon" />
    </div>

    <!-- Tab -->
    <div class="text-[14px] opacity-75 font-medium">
      <p>{{ tab }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">

defineProps<{
  tab: string
  icon: Component
}>()
</script>