<template>
  <div>
    <main class="">
      <section class="min-h-screen flex items-center bg-[url(/img/bga.png)] md:bg-fixed bg-cover">
        <div class="max-w-sm rounded overflow-hidden shadow-lg ml-10 bg-white">
  <div class="px-6 py-4">
    <div class="font-bold text-xl mb-2">Rencanakan Perjalanan Anda Sekarang.</div>
    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2">
        Username
      </label>
      <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="Username">
    </div>
    <div class="mb-4 flex">
      <label class="block text-gray-700 text-sm font-bold mb-2">
        Berangkat
      </label>      
      <label class="block text-gray-700 text-sm font-bold ml-20">
        Pulang
      </label>
    </div>
      <div class="mb-4 flex justify-center">
      <input class="shadow rounded w-full py-2 px-3" id="date" type="date">
      <input class="shadow rounded w-full py-2 px-3" id="date" type="date">
    </div>
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2">
        Tujuan
      </label>
      <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="Tujuan">
    </div>
    <div class="flex items-center justify-end">
      <button class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
        Cari
      </button>
    </div>
  </form>
  </div>
</div>
      </section>
<Carda/>
<section class="mx-7">
  <div>
                <h2 class="font-bold text-4xl my-6">Hébergements Airbnb Plus</h2>
                <span>Une sélection de logements vérifiés selon des critères de qualité et de design</span>
<div
  class="relative overflow-hidden rounded-lg bg-cover bg-no-repeat p-12 text-center"
  style="background-image: url('/img/g1.png'); height: 400px">
  <div
    class="absolute bottom-0 left-0 right-0 top-0 h-full w-full overflow-hidden bg-fixed"
    style="background-color: rgba(0, 0, 0, 0.6)">
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

              </div> 
</section>  

 <Cardb/>

 <Cardc/>

 <Cardd/>

 <Carde/>


<p class="text-white">
  Airbnb adalah jaringan pasar daring dan penginapan rumahan sejawat yang memungkinkan pengguna mendaftarkan atau menyewa properti untuk digunakan dalam jangka pendek. Harga sewanya ditetapkan oleh pemilik properti. Airbnb menerima sebagian tarif jasa pembukuan dari tamu dan tuan rumah.
          </p>
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
