<script setup lang="ts">
import IconsPackage from "~/components/icons/Package.vue"
import IconsHome from "~/components/icons/Home.vue"
import IconsSettings from "~/components/icons/Settings.vue"
import IconsClock from "~/components/icons/Clock.vue"
</script>

<template>
  <div class="fixed bottom-0 left-0 right-0 z-[999] w-full border-t-[0.3px] border-black border-opacity-10 pb-[20px]">
    <div class="px-[40px] py-[15px] flex justify-between w-full">
      <!-- Home -->
      <NavigationBarItem
        tab="Home"
        :icon="IconsHome"
      />

      <!-- Groups -->
      <NavigationBarItem
        tab="Groups"
        :icon="IconsPackage"
      />

      <!-- Automation -->
      <NavigationBarItem
        tab="Automation"
        :icon="IconsClock"
      />

      <!-- Settings -->
      <NavigationBarItem
        tab="Settings"
        :icon="IconsSettings"
      />
    </div>
  </div>
</template>