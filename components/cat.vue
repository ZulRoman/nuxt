<script setup>
const { data: ex } = await useFetch('https://dummyjson.com/products/categories')
</script>

<template>
    <div class="flex justify-between items-center sm:px-10 px-2 h-24 w-full top-20 bg-slate-900 z-[5]">
        <div class="w-full flex justify-between items-center px-2 mx-auto font-semibold text-sm">
            <div class="flex gap-8 mr-5 overflow-x-auto" ref="scroll_container">
                <NuxtLink to="/list" class="flex flex-col min-w-fit justify-center items-center opacity-90 hover:opacity-100 h-14 hover:cursor-pointer my-4">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="white" class="w-6 h-6">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M9.568 3H5.25A2.25 2.25 0 003 5.25v4.318c0 .597.237 1.17.659 1.591l9.581 9.581c.699.699 1.78.872 2.607.33a18.095 18.095 0 005.223-5.223c.542-.827.369-1.908-.33-2.607L11.16 3.66A2.25 2.25 0 009.568 3z" />
                    <path stroke-linecap="round" stroke-linejoin="round" d="M6 6h.008v.008H6V6z" />
                    </svg>
                    <span class="text-sm font-normal text-white">ALL CATEGORIES</span>
                </NuxtLink>
                <div class="flex flex-col min-w-fit justify-center items-center opacity-90 hover:opacity-100 h-14 hover:cursor-pointer my-4"
                    v-for="category in ex">
                    <NuxtLink :to="'/list/categories/'+category" class="flex flex-col justify-center items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="white" class="w-6 h-6">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M9.568 3H5.25A2.25 2.25 0 003 5.25v4.318c0 .597.237 1.17.659 1.591l9.581 9.581c.699.699 1.78.872 2.607.33a18.095 18.095 0 005.223-5.223c.542-.827.369-1.908-.33-2.607L11.16 3.66A2.25 2.25 0 009.568 3z" />
                        <path stroke-linecap="round" stroke-linejoin="round" d="M6 6h.008v.008H6V6z" />
                        </svg>
                        <span class="text-sm font-normal text-white">{{ category.toUpperCase().split('-').join(' ') }}</span>
                    </NuxtLink>
                </div>
            </div>
            <NavFilterModal />
        </div>
    </div>
</template>
