<template>
  <div
    class="border-2 border-primary rounded-full px-5 py-2 mr-4 cursor-pointer"
  >
    {{ category }}
  </div>
</template>

<script setup>
const { category } = defineProps(["category"]);
</script>

<style lang="scss" scoped></style>
