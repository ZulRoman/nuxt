<script setup>
const { data: data } = await useFetch('https://dummyjson.com/products/categories')
</script>

<template>
    <div>
        <div class="flex justify-center mb-2 mt-[88px] text-4xl font-bold">
            <h1>Product Categories</h1>
        </div>
    <div class="mx-[80px] bg-gray-900 text-white max-w-[1000px]">
        <div class="flex justify-center">
            <div class="flex gap-2 mx-2 overflow-x-scroll" >
                <div class="flex flex-col w-[109px] justify-center items-center h-14 hover:cursor-pointer hover:scale-110 duration-1000 my-4"
                    v-for="category in data">
                    <NuxtLink :to="'/list/categories/' + category" class="flex flex-col bg-blue-500 justify-center items-center text-white px-2 py-2 h-[56px]">
                        <span class="text-sm">{{ category.toLowerCase().split('-').join(' ') }}</span>
                    </NuxtLink>
                </div>
            </div>
        </div>
    </div>
    </div>
</template>

<script>
</script>