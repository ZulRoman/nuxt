<template>
  <div class="max-w-sm rounded overflow-hidden shadow-lg px-6 py-4 mx-2 bg-gray-800">
    <img class="" :src= image >
    <div class="px-6 py-4">
      <div class="font-bold text-xl mb-2 text-white">{{ title }}</div>
      <p class="text-white text-base">
        Lihat produk selengkapnya disini
      </p>
<slot/>
    </div>
  </div>
    </template>
  
  <script setup>
  const props = defineProps({
      image: String,
      title: String,
  });
</script>