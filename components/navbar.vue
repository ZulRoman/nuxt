<template>
    <header>
        <nav class="absolute flex flex-row items-center justify-between py-5 px-8 w-full z-10">
            <img src="/img/lg.png" class="w-6.5 h-7" alt="">
            <div class="flex item-center space-x-6 py-2 px-3 text-white font-roboto">
                <NuxtLink to="/">Français (FR)</NuxtLink>
                <NuxtLink to="/">EUR €</NuxtLink>
                <NuxtLink to="/">Devenir hôte</NuxtLink>
                <NuxtLink to="/">Créer son expérience</NuxtLink>
                <NuxtLink to="/">Aide</NuxtLink>
                <NuxtLink to="/">Inscription</NuxtLink>
                <NuxtLink to="/">Connexion</NuxtLink>
            </div>
        </nav>
        <section class="min-h-screen flex items-center bg-[url(/img/bga.png)] md:bg-fixed bg-cover h-[750px]">
        <div class="max-w-sm rounded overflow-hidden shadow-lg ml-[80px] bg-white">
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
  </header>
  </template>