<template>
  <div class="card flex flex-col">
    <img :src="product.image" alt="img-product" class="thumb" />
    <p class="font-medium text-gray-500 my-2 truncate text-xl">
      {{ product.title }}
    </p>
    <span>{{ product.category }}</span>
    <span class="font-bold">${{ product.price }}</span>
    <NuxtLink class="btn text-center font-semibold my-2">View Detail</NuxtLink>
  </div>
</template>

<script setup>
const { product } = defineProps(["product"]);
</script>

<style scoped>
.thumb {
  height: 120px;
  max-width: 70%;
  margin: 0 auto;
}
</style>
