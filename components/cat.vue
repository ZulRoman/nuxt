<script setup>
const { data: ex } = await useFetch('https://dummyjson.com/products/categories')
</script>
<template>
    <div>
    <div class="flex flex-col gap-5 mt-2 text-slate-700 justify-center">
        <div class="flex justify-start gap-6 overflow-x-auto py-2">
            <NuxtLink to="/list">
            <div class="border bg-white flex items-center min-w-[175px] rounded-xl hover:shadow hover:cursor-pointer hover:scale-110 duration-1000 active:bg-black h-[40px] w-fit">
                <div class="flex mx-6 text-xs">   
                ALL CATEGORIES
                </div>
            </div>
        </NuxtLink>
            <NuxtLink :to="'/list/categories/' + category"
                class="border bg-white h-[40px] flex items-center w-fit rounded-xl hover:shadow hover:cursor-pointer hover:scale-110 duration-1000 active:bg-black"
                v-for="category in ex">
                        <div class="flex mx-6 overflow-x-auto text-xs justify-center">
                            {{ category.toUpperCase().split('-').join(' ') }}
                        </div>
            </NuxtLink>
        </div>
    </div>
    </div>
</template>