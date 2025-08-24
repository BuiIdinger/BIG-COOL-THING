<template>
  <div>
    <TopNavBar
      v-if="id[0]"
      :current-page="id[0]"
    />
    <TopNavBar
      v-else
      current-page="Unknown peripheral"
    />
  </div>
  <NavigationBar />

  <div class="flex justify-center mt-[50px]">
    <div class="flex items-center justify-center bg-gray-200 p-[30px] rounded-[100%]">
      <IconsPower class="w-[50px] h-[50px] stroke-[1.7px]" />
    </div>
  </div>

  <PeripheralsSettingsSection title="Status">
    <div>
      <div>
        <p>On</p>
      </div>
    </div>
  </PeripheralsSettingsSection>
</template>

<script setup lang="ts">
import { useRoute } from "#vue-router"
import { computed } from "vue"

const route = useRoute()

const id = computed(() => {
  const param = route.params.id

  if (Array.isArray(param)) {
    return param;
  }
  if (typeof param === "string") {
    return [param];
  }

  return [];
})

</script>