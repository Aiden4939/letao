<script setup lang="ts">
defineProps<{ id: number; name: string }>();
</script>
<template>
  <div class="">
    <p class="text-nowrap pe-3">{{ name }}</p>
  </div>
</template>
<style scoped lang="scss"></style>
