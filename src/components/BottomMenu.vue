<script setup lang="ts">
defineProps<{ id: number; name: string | undefined }>();
</script>
<template>
  <div v-if="id == 1" class="px-3 py-2" style="border-bottom: 4px solid white;">
    <p class="text-nowrap px-3">{{ name }}</p>
  </div>
  <div v-else class="" >
    <p class="text-nowrap px-3">{{ name }}</p>
  </div>
</template>
<style scoped lang="scss"></style>
