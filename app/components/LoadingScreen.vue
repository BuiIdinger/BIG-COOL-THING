<template>
  <Transition>
    <div
      v-if="show"
      class="fixed z-[9999] top-0 left-0 right-0 bottom-0 h-screen w-screen bg-white flex justify-center items-center"
    >
      <div class="font-semibold text-[30px]">
        <p>SmartHub</p>
      </div>
    </div>
  </Transition>
</template>

<script setup lang="ts">
import { ref } from "vue"

const show = ref<boolean>(true);

const timeout = setTimeout(() => {
  show.value = false;
}, 500);

onMounted(() => {
  show.value = true;
});

onUnmounted(() => {
  clearTimeout(timeout);
});
</script>

<style lang="css" scoped>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>