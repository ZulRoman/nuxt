<script setup>
const { category } = useRoute().params;
const { data: ex } = await useFetch('https://dummyjson.com/products/category/' + category)
</script>

<template>
      <Cat/>
    <section class="my-[88px]">
      <div class="my-[44px]">
        <NuxtLink to="/list">
                <button class="bg-blue-500 hover:bg-blue-700 text-white text-xs font-bold py-2 px-4 mb-[40px]">
                Kembali
                </button>
            </NuxtLink>
            <h1 class="mb-4 flex justify-center items-center text-4xl font-bold">{{ category.toUpperCase().split('-').join(' ')  }}</h1>
                    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-5 gap-10 gap-y-8">
                        <div class="bg-white w-[188px] h-full hover:scale-110 duration-1000" v-for="item in ex.products" :key="item.id">
                            <NuxtLink :to="'list/' + item.id">
                                <div>
                                    <Swiper 
                    class="groupSwiper"
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
                    <SwiperSlide v-for="image in item.images">
                        <NuxtLink :to="'/list/' + item.id">
                            <img :src="image" alt="" class="w-full h-56 object-cover aspect-square duration-1000 rounded-lg">
                        </NuxtLink>
                    </SwiperSlide>
                    </Swiper>
                                    <div>
                                        <div>
                                            <h2 class="text-[16px] text-start text-[#484848] font-bold mt-1">{{ item.title }}</h2>                                       </div>
                                        <div>
                                            <h4 class="text-[10px] text-start text-[#767676] font-bold uppercase mt-[8px]">{{ item.description }}</h4>
                                        </div>
                                        <p class="text-[14px] text-start text-[#484848] font-bold">${{ item.price }}</p>
                                        <div class="flex gap-1 w-full font-bold mt-[8px]">
                                            <p class="text-[12px] text-start text-[#008489]">{{ item.rating }}</p>
                                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="#008489" class="w-[8px] h-[8px] mt-1.5">
      <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.007 5.404.433c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.433 2.082-5.006z" clip-rule="evenodd" />
    </svg>
                                        </div>
                                    </div>
                                </div>  
                            </NuxtLink>
                        </div>
                    </div>
                  </div> 
    </section> 
</template>
