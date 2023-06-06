
<template>
    <label for="searchInput" class="sm:flex flex-row justify-center items-center 
                    gap-2 lg:ml-5 px-5 py-1 text-sm border border-gray-300 rounded-lg
                    hover:shadow hover:cursor-pointer w-fit hidden font-normal mx-[80px]" @click="toggleSearch = !toggleSearch, filterData(),keyWord = ''">
        <a class="text-white">Search Here</a>
        <span class="px-2 py-1 rounded-full">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="white" class="w-6 h-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
</svg>
        </span>
    </label>
    <!-- mobile responsive -->
    <label for="searchInput"
        class="sm:hidden flex items-center justify-between border border-gray-300 w-full p-1 text-small font-normal hover:cursor-pointer ml-4"
        @click="toggleSearch = !toggleSearch, filterData(), keyWord = ''">
        <div class="flex h-ful justify-center items-center text-slate-400">
        <span class="px-2 py-1 rounded-full flex">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="white" class="w-6 h-6">
            <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
            </svg>
            <a class="text-white mx-2">Search here</a>
        </span>
        </div>
    </label>
    <Transition>
        <div class="flex h-screen w-screen absolute top-0 sm:right-10 lg:left-0 cursor-default" v-show="toggleSearch">
            <div class="absolute h-screen w-screen z-[1]" @click="toggleSearch = !toggleSearch, keyWord = ''"></div>
            <div class="relative flex bg-gray-900 h-fit sm:w-[400px] w-full py-3 px-2 lg:left-[162px] sm:left-[90px] left-0 sm:mx-0 mx-2 top-[5px] rounded-xl z-[99]">
                <div class="flex flex-col w-full overflow-y-auto">
                    <label for="searchInput">
                        <div
                            class="flex items-center justify-between border border-white w-full p-1 text-small font-normal">
                            <div class="flex h-full justify-center items-center">
                                <span class="flex items-center justify-center bg-red-bnb p-2 rounded-full mr-3">
                                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="white" class="w-6 h-6">
                                        <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
                                    </svg>
                                </span>
                                <input type="text" name="" id="searchInput"
                                    class="py-1 px-3 sm:w-[300px] w-[35vh] text-small text-slate-500 accent-rose-400"
                                    placeholder="Search Here..." v-model="keyWord"
                                    @keyup="filterData()">
                            </div>
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="white" class="w-6 h-6 sm:hidden hover:cursor-pointer" @click="toggleSearch = !toggleSearch">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M9.75 9.75l4.5 4.5m0-4.5l-4.5 4.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                        </div>
                    </label>
                    <div class="flex flex-col w-full max-h-[600px]" v-for="product in productData.products" :key="product.id">
                            <NuxtLink :to="'/list/' + product.id">
                                <div class="flex items-center w-full border-b px-2 py-2 hover:cursor-pointer hover:scale-110 duration-1000 rounded mt-2"
                                    id="list">
                                    <img :src="product.thumbnail" alt="" class="h-[40px] w-[70px]">
                                    <p id="listItem" class="text-[16px] text-white mx-2">{{ product.title }} - {{
                                        product.brand }} - {{ product.category }}</p>
                                </div>
                            </NuxtLink>
                    </div>
                </div>
            </div>
        </div>
    </Transition>
</template>

<script>
export default {
    data() {
        return {
            toggleSearch: false,
            keyWord: "",
            productData: []
        }
    },
    methods: {
        async filterData() {
            if (this.keyWord === '') {
                let { data: data } = await useFetch('https://dummyjson.com/products?limit=5');
                    this.productData = data;
                    console.log(this.productData);
                } else {
                    let { data: data } = await useFetch('https://dummyjson.com/products/search?q='+this.keyWord.toLowerCase());
                        this.productData = data;
                        console.log(this.productData);
            }
        }
    },
}
</script>
