<template>
    <div class="flex items-center sm:px-10 px-2 h-20 w-full sticky top-0 border-b bg-slate-900 z-10 text-slate-950">
        <div class="w-full flex justify-between mx-auto font-semibold text-lg">
            <div class="flex flex-row sm:justify-start items-center w-full" >  
                <NuxtLink to="/list">
                    <img src="/svg/airbnb.svg" alt="AirBnBlogo" srcset="" class="h-8 lg:block hidden">
                </NuxtLink>
                <NuxtLink to="/list">
                    <img src="/svg/airbnb-1.svg" alt="AirBnBlogo" srcset="" class="h-10 lg:hidden sm:block mr-2">
                </NuxtLink>
                <Search />
                <Menu class="min-w-fit sm:hidden ml-3 text-small"/>
            </div>
            <div class="sm:flex justify-between items-center gap-4 text-sm min-w-fit hidden">
                <Menu />
            </div>
        </div>
    </div>
</template>

