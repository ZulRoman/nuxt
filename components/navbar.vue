<template>
        <nav class="absolute flex flex-row items-center justify-between py-5 px-8 w-full z-10 bg-slate-800">
            <img src="/img/lg.png" class="w-6.5 h-7" alt="">
            <NuxtLink to="login" class="text white bg-blue-500 hover:bg-blue-700 text-white text-xs font-bold py-2 px-4">Login</NuxtLink>
            <Search/>
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
  </template>