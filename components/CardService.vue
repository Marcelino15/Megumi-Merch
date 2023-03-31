<template>
  <div class="card-services flex-col w-96">
    <div class="px-5">
      <h1 class="text-3xl font-bold">{{ service.title }}</h1>
      <p class="text-xl mt-8">{{ service.desc }}</p>
    </div>
    <img
      :src="service.link"
      alt="service-image"
      class="thumb rounded-b-lg pt-5"
    />
  </div>
</template>

<script setup>
const { service } = defineProps(["service"]);
</script>

<style scoped>
.thumb {
  height: 300px;
  max-width: 100%;
  margin: 0 auto;
}
</style>
