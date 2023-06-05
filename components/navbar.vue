<template>
        <nav class="absolute flex flex-row items-center justify-between py-5 px-8 w-full mb-8 top-0 bg-slate-800 w-screen">           
            <img src="/img/lg.png" class="w-6.5 h-7" alt="">
            <div class="flex">
            <NuxtLink to="/login" class="text white bg-blue-500 hover:bg-blue-700 text-white text-xs font-bold py-2 px-4 mx-1" v-show="auth==false">Login</NuxtLink>
            <NuxtLink onclick="location.reload();" class="text white bg-blue-500 hover:bg-blue-700 text-white text-xs font-bold py-2 px-4 mx-1 hover:cursor-pointer" v-show="auth==true" @click="logout()">Logout</NuxtLink>
            <NuxtLink to="/list/cart" class="text white bg-blue-500 hover:bg-blue-700 text-white text-xs font-bold py-2 px-4 mr-1">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
  <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 00-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 00-16.536-1.84M7.5 14.25L5.106 5.272M6 20.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm12.75 0a.75.75 0 11-1.5 0 .75.75 0 011.5 0z" />
</svg>
            </NuxtLink>
        </div>
            <Search/>
            <div class=" item-center space-x-6 py-2 px-3 text-white font-roboto hidden lg:block">
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

<script>
export default {
    data() {
        return {
            auth: false
        }
    },
    methods: {
        login() {
            localStorage.setItem('user', this.username);
            this.auth = true;
        },
        logout() {
                localStorage.removeItem('user');
        },
        checkAuth() {
            const user = localStorage.getItem('user');
            if (user) {
            console.log(localStorage.getItem('user'));
            this.auth = true;
            }
        }
    },
    mounted() {
        this.checkAuth();
    }
}
</script>