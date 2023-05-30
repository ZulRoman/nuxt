<template>
  <div>
    <main class="">
      <div class="mx-[80px]">
<Carda/>
<section class="">
  <div>
    <div>
            <h1 class="text-xl font-bold">Hébergements Airbnb Plus</h1>
            <p class="font-light mb-[24px]">Une sélection de logements vérifiés selon des critères de qualité et de design</p>
        </div>
<div
  class="relative overflow-hidden rounded-lg bg-cover bg-no-repeat p-12 text-center"
  style="background-image: url('/img/g1.png'); height: 400px">
    <div class="flex h-full items-center justify-center">
      <div class="text-white">
        <img src="/img/j1.png" class="ml-20 mb-4">
        <button type="button"
          class="bg-white rounded border-2 border-neutral-50 px-7 pb-[8px] pt-[10px] text-xs font-medium uppercase leading-normal text-black flex justify-start">
          Découvrir des logements
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-5 h-5 justify-end ml-2">
  <path fill-rule="evenodd" d="M7.21 14.77a.75.75 0 01.02-1.06L11.168 10 7.23 6.29a.75.75 0 111.04-1.08l4.5 4.25a.75.75 0 010 1.08l-4.5 4.25a.75.75 0 01-1.06-.02z" clip-rule="evenodd" />
  </svg>
        </button>
      </div>
    </div>
</div>

              </div> 
</section>  

 <Cardb/>

 <Cardc/>

 <Cardd/>

 <Carde/>

</div>
    </main>
  </div>
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
