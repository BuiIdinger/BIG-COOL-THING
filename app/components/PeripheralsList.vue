<template>
  <div class="m-[20px] flex flex-col gap-y-[25px]">
    <PeripheralsItem
      name="Outlet #1"
      description="Garage"
      link="H"
      :icon="IconsPower"
    />
  </div>
</template>

<script setup lang="ts">
import IconsPower from "~/components/icons/Power.vue"
</script>