<template>
  <div>
    <main class="">
      <section class="min-h-screen flex items-center bg-[url(img/bga.png)] md:bg-fixed">
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
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2">
        Berangkat
      </label>
      <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="date" type="date">
    </div>
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2">
        Pulang
      </label>
      <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="date" type="date">
    </div>
    <div class="flex items-center justify-end">
      <button class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
        Sign In
      </button>
    </div>
  </form>
  </div>
</div>
      </section>
      <section id="class">
                <h2 class="font-bold text-4xl my-6">Exploler Airbnb</h2>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 gap-y-8">
                    <div class="bg-white shadow-lg rounded" v-for="item in produkData" :key="item.id">
                      <div class="flex flex-col rounded-lg bg-white  md:max-w-xl md:flex-row">
  <img
    class="h-96 w-full rounded-t-lg object-cover md:h-auto md:w-48 md:rounded-none md:rounded-l-lg"
    :src="item.image"
    alt="" />
  <div class="flex flex-col justify-start p-6">
    <h5 class="mb-2 text-xl font-medium">
      {{ item.name }}
    </h5>
  </div>
</div>
                    </div>
                </div>
            </section>
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
            produkData: json,
        }
    },
}
</script>