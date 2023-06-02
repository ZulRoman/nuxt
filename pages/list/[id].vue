<script setup>
const {id} = useRoute().params;
const { data: ex } = await useFetch('https://dummyjson.com/products/' + id)
</script>

<template>
    <section class="my-[88px]">
      <div>
        <NuxtLink onclick="window.history.go(-1); return false;">
                <button class="bg-blue-500 hover:bg-blue-700 text-white text-xs font-bold py-2 px-4 mb-[40px] mt-4">
                Kembali
                </button>
            </NuxtLink>
            <div class="grid lg:grid-cols-2 sm:grid-cols-1 content-start gap-y-2 ">
                <Swiper class="groupSwiper w-[480px] h-[450px]"
                    :modules="[SwiperAutoplay, SwiperEffectCreative, SwiperPagination, SwiperNavigation]"
                    :slides-per-view="1" :loop="false" :effect="'creative'" :navigation="true" :hashNavigation="{
                        watchState: true,
                    }" 
                    :pagination="{ clickable: true }" :creative-effect="{
                        prev: {
                            shadow: false,
                            translate: ['-100%', 0, -1],
                        },
                        next: {
                            translate: ['100%', 0, 0],
                        },
                    }"
                    >
                    <SwiperSlide v-for="image in ex.images" class="">
                        <NuxtLink :to="'/list/' + ex.id">
                            <img :src="image" alt="" class="w-[480px] h-[450px] object-cover aspect-square duration-1000 rounded-lg">
                        </NuxtLink>
                    </SwiperSlide>
                    </Swiper>
                                <div class="w-[480px] h-[450px]">
                                        <div>
                                            <h2 class="text-6xl text-start text-[#484848] font-bold">{{ ex.title }}</h2>                                       
                                        </div>
                                        <div>
                                            <h4 class="text-xl text-start text-[#767676] font-bold uppercase mt-[8px]">{{ ex.description }}</h4>
                                        </div>
                                        <p class="text-4xl text-start text-[#484848] font-bold">Price : ${{ ex.price }}</p>
                                        <div class="flex gap-1 w-full font-bold mt-[8px]">
                                            <p class="text-4xl text-start text-[#484848]"> Rating : {{ ex.rating }}</p>
                                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="yellow" class="w-[36px] h-[36px] mt-1">
      <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.007 5.404.433c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.433 2.082-5.006z" clip-rule="evenodd" />
    </svg>
                                        </div>
                                        <div>
                                        <p class="text-4xl text-start text-[#484848] font-bold">Stock : {{ ex.stock }}</p>
                                        <p class="text-4xl text-start text-[#484848] font-bold">Brand : {{ ex.brand }}</p>
                                        <p class="text-4xl text-start text-[#484848] font-bold">Category : {{ ex.category }}</p>
                                        </div>
                                        <NuxtLink :to="'co/' + ex.id">
                                            <button class="bg-blue-500 hover:bg-blue-700 text-white text-xl font-bold py-2 px-4 my-[40px]">
                                            Beli
                                            </button>
                                        </NuxtLink>
                                    </div>  
                        </div>
                        <p class="text-4xl text-start text-[#484848] font-bold mt-2">Description</p>
                        <div class="w-25">                            
Processor :  Snapdragon 695 5G
RAM : 8 GB + 8 GB Extended RAM
ROM : 128 GB/256 GB
Network : 5G
Cooling System : 5-Layer Liquid Cooling System
Battery : 6000 mAH
Charging : 80 W Flash Charge
Rear Camera : 50+2 MP Ultra Clarity Camera
Front Camera : 8 MP
Display Size : 6.64"
Screen : IPS LCD
Refresh Rate : 120Hz
NFC : Yes
</div>
                    </div>
    </section>   
    </template>