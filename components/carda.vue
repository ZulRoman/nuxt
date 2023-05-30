<template>
      <section class="my-[88px]">
                <h2 class="font-bold text-xl mb-[24px]">Exploler Airbnb</h2>
                <div class="grid grid-cols-1 lg:grid-cols-3 gap-4 gap-y-8">
                    <div class="bg-white shadow-md rounded hover:scale-110 hover:shadow-lg duration-1000" v-for="item in ex.a" :key="item.id">    
                      <NuxtLink to="list">                
                      <div class="flex flex-row items-center w-full md:w-[391px]">
  <img
    class="w-[121px] h-[85px] rounded-l-[12px]"
    :src="item.image"
    alt="" />
  <div class="flex flex-col justify-start p-6">
    <h5 class="mb-2 text-xl font-medium">
      {{ item.name }}
    </h5>
  </div>
                      </div></NuxtLink> 
                    </div>
                </div>
            </section>
</template>

<script>
import json from '@/assets/data/ex.json';
export default {
    data() {
        return {
            layouts: {
                header: "header",
                footer: "footer"
            },
            ex: json,
        }
    },
}
</script>