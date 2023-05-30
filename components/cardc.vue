<template>
<section class="my-[88px]">
  <div>
    <div class="mb-[24px]">
            <h1 class="text-xl font-bold">Logements dans le monde entier</h1>
            <p class="font-light">Voyages de plusieurs jours organisés par des experts locaux avec activités, repas et logements compris</p>
        </div>
                <div class="grid grid-cols-2 sm:grid-cols-2 lg:grid-cols-4 gap-3 gap-y-8">
                    <div class="bg-white w-[290px] h-full" v-for="item in ex.c" :key="item.id">
                        <div class="w-full md:w-[289px]">
        <div class="w-[289px] h-[200px] overflow-hidden">
            <img class="w-full rounded-[4px] hover:scale-110 duration-1000" :src="item.image" :alt="alt">
        </div>        
        <div class="flex flex-row justify-between items-center mt-2">
            <div class="flex flex-row items-center gap-3">
                <div>
        <h1 class="text-[10px] text-[#484848] font-bold uppercase border border-[#484848] p-2">Superhost</h1>
    </div>
                <h1 class="text-[12px] text-[#767676] font-normal">{{ item.description }}</h1>
            </div>
            <div class="flex flex-row items-center gap-1">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="red" class="w-[8px] h-[8px] mt-0.5">
  <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.007 5.404.433c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.433 2.082-5.006z" clip-rule="evenodd" />
</svg>
                <h1 class="text-[12px] text-[#484848] font-medium">{{ item.rating }}</h1>
            </div>            
        </div>
        <h1 class="text-start text-[14px] text-[#484848] font-normal mt-2">{{ item.price }}</h1>
    </div>
                    </div>
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