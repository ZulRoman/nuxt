<script setup>
const {id} = useRoute().params;
const { data: ex } = await useFetch('https://dummyjson.com/products/' + id)

</script>

<template>
    <section class="my-[88px]">
      <div>
        <NuxtLink onclick="window.history.go(-1); return false;">
                <button class="bg-blue-500 hover:bg-blue-700 text-white text-xs font-bold py-2 px-4 mb-[40px] mt-4">
                Kembali
                </button>
            </NuxtLink>

            <div class="grid lg:grid-cols-2 sm:grid-cols-1 gap-y-3">
                <Swiper class="groupSwiper w-[400px] h-[400px] z-0"
                    :modules="[SwiperAutoplay, SwiperEffectCreative, SwiperPagination, SwiperNavigation]"
                    :slides-per-view="1" :loop="false" :effect="'creative'" :navigation="true" :hashNavigation="{
                        watchState: true,
                    }" 
                    :pagination="{ clickable: true }" :creative-effect="{
                        prev: {
                            shadow: false,
                            translate: ['-100%', 0, -1],
                        },
                        next: {
                            translate: ['100%', 0, 0],
                        },
                    }"
                    >
                    <SwiperSlide v-for="image in ex.images" class="z-0">
                        <NuxtLink :to="'/list/' + ex.id">
                            <img :src="image" alt="" class="w-[400px] h-[400px] object-cover aspect-square duration-1000 rounded-lg z-0">
                        </NuxtLink>
                    </SwiperSlide>
                    </Swiper>
                                <div class="w-[450px] h-[450px] px-2 z-20">
                                        <div>
                                            <h2 class="text-4xl text-start text-[#484848] font-bold">{{ ex.title }}</h2>                                       
                                        </div>
                                        <div>
                                            <h4 class="text-m text-start text-[#767676] font-bold uppercase mt-[8px]">{{ ex.description }}</h4>
                                        </div>
                                        <p class="text-2xl text-start text-[#484848] font-bold">Price : ${{ ex.price }}</p>
                                        <div class="flex gap-1 w-full font-bold mt-[8px]">
                                            <p class="text-2xl text-start text-[#484848]"> Rating : {{ ex.rating }}</p>
                                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="blue" class="w-[30px] h-[30px]">
      <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.007 5.404.433c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.433 2.082-5.006z" clip-rule="evenodd" />
    </svg>
                                        </div>
                                        <div>
                                        <p class="text-2xl text-start text-[#484848] font-bold">Stock : {{ ex.stock }}</p>
                                        <p class="text-2xl text-start text-[#484848] font-bold">Brand : {{ ex.brand }}</p>
                                        <p class="text-2xl text-start text-[#484848] font-bold">Category : {{ ex.category }}</p>
                                        </div>
                                        <div class="flex mt-5 duration-1000">
                                    </div>
                                        <NuxtLink :to="'/co/' + ex.id">
                                            <button class="bg-blue-500 hover:bg-blue-700 text-white text-xl font-bold py-2 px-4 mt-[40px]">
                                            Beli
                                            </button>
                                        </NuxtLink>
                                        <button class="bg-blue-500 hover:bg-blue-700 text-white text-xl font-bold py-2 px-4 mt-[40px] mx-[40px]" @click="addToCart(id, stockCounter), toggleAddcartStatus = true">
                                                <div class="flex">
                                                    + Keranjang
                                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 mt-1 ml-1">
                                            <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 00-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 00-16.536-1.84M7.5 14.25L5.106 5.272M6 20.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm12.75 0a.75.75 0 11-1.5 0 .75.75 0 011.5 0z" />
                                            </svg>
                                                </div>
                                            </button>

                <div class="flex flex-col justify-between w-[400px] h-20 rounded-lg p-4 bg-white z-20 shadow-lg mt-2" v-show="toggleAddcartStatus">
                    <div class="flex justify-start">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="black" class="w-6 h-6 hover:cursor-pointer mt-1" @click="toggleAddcartStatus = false">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M9.75 9.75l4.5 4.5m0-4.5l-4.5 4.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                            <div class="flex flex-col justify-center text-lg ml-2">
                        <div>
                            Product Berhasil Ditambahkan!
                        </div>
                        <div class="text-rose-500 hover:scale-105 active:scale-95 font-medium cursor-pointer items-center">
                                <NuxtLink to="/list/cart">
                                    Lihat Keranjang
                                </NuxtLink>
                        </div>
                    </div>
                    </div>
            </div>
                                    </div>  
                        </div>
                        <div class="px-2 z-0">
                        <p class="text-2xl text-start text-[#484848] font-bold mt-4">Description</p>
                        <div class="w-25 z-0">                            
Processor :  Snapdragon 695 5G
RAM : 8 GB + 8 GB Extended RAM
ROM : 128 GB/256 GB
Network : 5G
Cooling System : 5-Layer Liquid Cooling System
Battery : 6000 mAH
Charging : 80 W Flash Charge
Rear Camera : 50+2 MP Ultra Clarity Camera
Front Camera : 8 MP
Display Size : 6.64"
Screen : IPS LCD
Refresh Rate : 120Hz
NFC : Yes
</div>
</div>
                    </div>
    </section>   
</template>


<script>
export default {
    data() {
        return {
            stockCounter: 1,
            toggleAddcartStatus: false
        }
    },
    methods: {
        accumulateStock(n, stock) {
            if (n == 1) {
                if (this.stockCounter < stock) {
                    this.stockCounter += n;
                } else if (this.stockCounter >= stock) {
                    this.stockCounter = stock;
                }
            } else if (n == -1) {
                if (this.stockCounter < 1) {
                    this.stockCounter = 1;
                } else if (this.stockCounter > 1) {
                    this.stockCounter += n;
                }
            } else if (this.stockCounter > stock) {
                this.stockCounter = stock;
            } else if (this.stockCounter < 1) {
                this.stockCounter = 1;
            }
            console.log(this.stockCounter, stock);
        },
        async addToCart(id, qty) {
            let { data: product }  = await useFetch('https://dummyjson.com/products/' + id);
            let dataProduct        = product._rawValue;
            dataProduct.qty        = qty;
            dataProduct.noteStatus = false;

            //if localStorage products didn't exist
            if (!localStorage.getItem("products")) {
                let array = [];
                dataProduct.cartId = 1;
                dataProduct.subTotal = (this.price * this.stockCounter) + this.cleaningPrice + this.adminPrice;
                array.push(dataProduct);
                localStorage.setItem("products", JSON.stringify(array));
                console.log(JSON.parse(localStorage.getItem("products")));
            } 
            //if localStorage products is exist
            else {
                //get all data from localStorage
                let productAtCart = JSON.parse(localStorage.getItem("products"));
                let listProductId = [];
                //get ListProductId in localStorage
                for (let i = 0; i < productAtCart.length; i++) {
                    if (!listProductId.includes(productAtCart[i].id)) {
                        listProductId.push(productAtCart[i].id)
                    }
                }
                console.log(listProductId);
                
                //check if the id already exists or not
                if (!listProductId.includes(dataProduct.id)) {
                    //if not exist save to localStorage
                    dataProduct.cartId   = productAtCart.length + 1;
                    dataProduct.subTotal = (this.price * this.stockCounter) + this.cleaningPrice + this.adminPrice;
                    productAtCart.push(dataProduct);
                    localStorage.setItem("products", JSON.stringify(productAtCart));
                    console.log(JSON.parse(localStorage.getItem("products")));
                    console.log(listProductId);
                } else {
                    //if exist
                    //get data with the same id from localStorage
                    for (let j = 0; j < productAtCart.length; j++) {
                        //if data found
                        if (productAtCart[j].id === id) {
                            productAtCart[j].subTotal += (this.price * this.stockCounter) + this.cleaningPrice + this.adminPrice;
                            productAtCart[j].qty      += qty;
                            localStorage.setItem("products", JSON.stringify(productAtCart));
                            console.log(JSON.parse(localStorage.getItem("products")));
                        }
                    }
                }
                console.log(JSON.parse(localStorage.getItem("products")));
            }
        }
    },
    mounted() {

    }
}
</script>