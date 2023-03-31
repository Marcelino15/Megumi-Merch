<template>
  <div>
    <Loading v-if="loading" />
    <div class="bg-[url('/public/images/hero.jpg')] h-128 bg-cover bg-top">
      <div class="bg-slate-950 bg-opacity-25 h-full">
        <div class="container mx-auto flex-row py-52">
          <h1 class="text-5xl text-fourth font-bold">
            Shopping And <br />
            Department Store.
          </h1>
          <p class="font-light text-fourth pt-5 text-xl">
            Find your goods product, only in one shop. Cheap, fast, best product
          </p>
        </div>
      </div>
    </div>
    <div class="container mx-auto">
      <h2 class="text-2xl font-medium mt-10">Shop Our Top Categories</h2>
      <div class="flex flex-nowrap pt-5">
        <div v-for="cat in categories">
          <CardCategory :category="cat" />
        </div>
      </div>
      <h2 class="text-2xl font-medium mt-10">Top Products</h2>
      <Swiper
        :modules="[SwiperAutoplay]"
        :slides-per-view="5"
        :loop="true"
        :autoplay="{
          delay: 900,
          disableOnInteraction: false,
        }"
      >
        <SwiperSlide v-for="(product, index) in products" :key="index">
          <CardProduct :product="product" />
        </SwiperSlide>
      </Swiper>
      <h2 class="text-2xl font-medium mt-10">Official Brand</h2>
      <div class="grid grid-cols-6 mt-5">
        <div class="flex" v-for="partner in officialPartners">
          <img
            :src="partner.link"
            alt="official-partner"
            class="logo-partner self-center"
          />
        </div>
      </div>
    </div>
    <div class="bg-[url('/public/images/hero-card.jpg')] h-128 bg-cover my-20">
      <div class="bg-slate-950 bg-opacity-25 h-full flex">
        <div class="container mx-auto flex-col py-52 self-center">
          <h1 class="text-5xl text-fourth font-bold">Get 5% Cash Back</h1>
          <p class="font-medium text-fourth pt-3 text-xl">On megumimerch.com</p>
          <button class="btn mt-3 text-lg rounded-xl">Learn More</button>
        </div>
      </div>
    </div>
    <div class="container mx-auto">
      <h2 class="text-2xl font-medium mt-10 mb-5">Services</h2>
      <div class="grid grid-cols-3 mb-20">
        <div v-for="service in services">
          <CardService :service="service" />
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const loading = ref(false);
const categories = ref([]);
const products = ref([]);

onMounted(() => {
  loadCategory();
  loadProduct();
});
const loadCategory = () => {
  loading.value = true;
  $fetch("/api/category/getAll", {
    method: "GET",
    baseURL: "/",
  }).then(function (category) {
    loading.value = false;
    categories.value = category;
  });
};
const loadProduct = () => {
  loading.value = true;
  $fetch("/api/products/getAll", {
    method: "GET",
    baseURL: "/",
  }).then(function (product) {
    loading.value = false;
    products.value = product;
  });
};
const officialPartners = [
  {
    id: 1,
    link: "/images/logo-consina.jpeg",
  },
  {
    id: 2,
    link: "/images/logo-eiger.png",
  },
  {
    id: 3,
    link: "/images/logo-acer.png",
  },
  {
    id: 4,
    link: "/images/logo-sandisk.png",
  },
  {
    id: 5,
    link: "/images/logo-samsung.png",
  },
  {
    id: 6,
    link: "/images/logo-lv.jpeg",
  },
];
const services = [
  {
    id: 1,
    link: "/images/service-customer-questions.jpg",
    title: "Frequently Asked Questions",
    desc: "Updates on safe shopping in this merch",
  },
  {
    id: 2,
    link: "/images/service-online-payment.jpg",
    title: "Online Payment Process",
    desc: "Easy, Fast confirmation and save payment",
  },
  {
    id: 3,
    link: "/images/service-delivery.jpg",
    title: "COD or Home Delivery Options",
    desc: "Only waiting on home and spend your time",
  },
];
</script>

<style scoped>
.logo-partner {
  filter: grayscale(100%);
  max-width: 200px;
  height: auto;
  cursor: pointer;
}
.logo-partner:hover {
  filter: grayscale(0%);
}
</style>
