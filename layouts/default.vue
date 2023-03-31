<template>
  <div>
    <header class="shadow-sm bg-white">
      <nav class="container mx-auto p-4 flex justify-between">
        <NuxtLink to="/" class="flex">
          <img src="/images/logo.png" alt="logos" class="w-12 h-12" />
          <span class="self-center ml-4 font-mono text-lg">Megumi Merch</span>
        </NuxtLink>
        <ul class="flex gap-4 self-center">
          <li class="self-center"><NuxtLink to="/">Home</NuxtLink></li>
          <li class="self-center">
            <NuxtLink to="/product">Products</NuxtLink>
          </li>
          <li class="self-center">
            <NuxtLink
              class="border-b-2 border-b-secondary font-semibold"
              to="/login"
              >Login</NuxtLink
            >
          </li>
          <li class="btn"><NuxtLink to="/login">Register</NuxtLink></li>
        </ul>
      </nav>
    </header>
    <div>
      <slot />
    </div>
    <footer class="static bottom-0 w-full text-center py-2 bg-fourth">
      Made with ♥
    </footer>
  </div>
</template>

<script setup></script>

<style scoped>
li > .router-link-exact-active {
  padding: 10px;
  border-radius: 5px;
  background-color: #fe6244;
  color: #fff;
}
</style>
