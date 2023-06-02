<script setup>
const { data: ex } = await useFetch('https://dummyjson.com/products/categories')
</script>
<template>
    <div class="mt-[88px]">
        <p class="flex justify-center text-4xl font-bold">Product Categories</p>
    </div>
    <div class="flex flex-col gap-5 mt-8 text-slate-700 justify-center">
        <div class="flex justify-start gap-6 overflow-x-auto py-2">
            <NuxtLink :to="'/list/categories/' + category"
                class="border bg-white h-20 flex items-center min-w-[175px] rounded-xl hover:shadow hover:cursor-pointer hover:scale-110 duration-1000 active:bg-black"
                v-for="category in ex">
                        <div class="flex mx-6 overflow-x-auto">
                            {{ category.toUpperCase().split('-').join(' ') }}
                        </div>
            </NuxtLink>
        </div>
    </div>
</template>