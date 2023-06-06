<script setup>
const {id} = useRoute().params;
const { data: ex } = await useFetch('https://dummyjson.com/products/' + id)

</script>

<template>
    <section class="my-[88px]">
      <div>
        <NuxtLink onclick="window.history.go(-1); return false;">
                <button class="bg-blue-500 hover:bg-blue-700 text-white text-xs font-bold py-2 px-4 mb-[40px]">
                Kembali
                </button>
            </NuxtLink>
            <div class="flex items-center px-2">
            <h1 class="text-xl font-semibold mx-2">{{ ex.title }}</h1>
            </div>
            <div class="flex justify-between items-center mt-2 text-small px-2">
            <div class="flex gap-2 items-center">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
  <path stroke-linecap="round" stroke-linejoin="round" d="M11.48 3.499a.562.562 0 011.04 0l2.125 5.111a.563.563 0 00.475.345l5.518.442c.499.04.701.663.321.988l-4.204 3.602a.563.563 0 00-.182.557l1.285 5.385a.562.562 0 01-.84.61l-4.725-2.885a.563.563 0 00-.586 0L6.982 20.54a.562.562 0 01-.84-.61l1.285-5.386a.562.562 0 00-.182-.557l-4.204-3.602a.563.563 0 01.321-.988l5.518-.442a.563.563 0 00.475-.345L11.48 3.5z" />
</svg>
                <span class="-ml-1">{{ ex.rating }}</span> -
                <span class="underline">{{ ex.stock }} Stok tersedia</span> -
                <span class="underline">{{ ex.brand }}</span>
            </div>
        </div>
            <div class="hidden lg:block md:block">
            <Image :images="ex.images" :thumbnail="ex.thumbnail" /></div>
            <div class="flex lg:flex-col flex-col gap-y-2">
                <div class="sm:hidden">
                <Swiper class="groupSwiper lg:w-[400px] lg:h-[400px] w-[360px] h-[360px] px-10 sm:hidden"
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
                            <img :src="image" alt="" class="object-cover aspect-square duration-1000 rounded-lg z-0">
                        </NuxtLink>
                    </SwiperSlide>
                    </Swiper></div>
                    <div>
        <div class="flex item gap-5 mt-14 px-2 md:flex-row flex-col">
            <div>
                                        <div>
                                            <h2 class="text-4xl text-start text-[#484848] font-bold">{{ ex.title }}</h2>                                       
                                        </div>
                                        <div>
                                            <h4 class="text-m text-start text-[#767676] font-bold uppercase mt-[8px]">{{ ex.description }}</h4>
                                        </div>
                                        <p class="text-2xl text-start text-[#484848] font-bold">Price : ${{ ex.price }}</p>
                                        <div class="flex gap-1 w-full font-bold mt-[8px]">
                                            <p class="text-2xl text-start text-[#484848]"> Rating : {{ ex.rating }}</p>
                                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="blue" class="w-[25px] h-[25px] mt-1">
      <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.007 5.404.433c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.433 2.082-5.006z" clip-rule="evenodd" />
    </svg>
                                        </div>
                                        <div>
                                        <p class="text-2xl text-start text-[#484848] font-bold">Stock : {{ ex.stock-stockCounter }}</p>
                                        <p class="text-2xl text-start text-[#484848] font-bold">Brand : {{ ex.brand }}</p>
                                        <p class="text-2xl text-start text-[#484848] font-bold">Category : {{ ex.category }}</p>
                                        </div>
                                        <div class="px-2 z-0">
                        <p class="text-2xl text-start text-[#484848] font-bold mt-4">Description</p>
                        <div class="w-25 z-0">                            
Processor :  Snapdragon 695 5G <br>
RAM : 8 GB + 8 GB Extended RAM<br>
ROM : 128 GB/256 GB<br>
Network : 5G<br>
Cooling System : 5-Layer Liquid Cooling System<br>
Battery : 6000 mAH<br>
Charging : 80 W Flash Charge<br>
Rear Camera : 50+2 MP Ultra Clarity Camera<br>
Front Camera : 8 MP<br>
Display Size : 6.64"<br>
Screen : IPS LCD<br>
Refresh Rate : 120Hz<br>
NFC : Yes
</div>
</div>
                                </div>
            <div class="flex justify-center flex-[40%]">
                <div class="flex w-full h-full justify-center py-5 lg:ml-24">
                    <div class="flex h-fit flex-col sticky top-10">
                        <div class="mt-4 ml-4 rounded-lg shadow-lg">    
                            <div class="bg-white border border-gray-300 shadow-lg rounded-xl h-fit p-5 w-[372px] duration-1000 ">
        <div class="flex justify-between items-center">
            <h1 class="text-lg font-medium">{{ ex.price }} <span class="font-normal text-slate-700">/pcs</span>
            </h1>
            <div class="flex gap-1 text-small">
                <div class="flex items-center gap-1">
                    {{ ex.stock-stockCounter }}
                    <span class="text-slate-500 font-semibold">Stock</span>
                </div>
            </div>
        </div>
        <div class="flex mt-5 duration-1000">
            <div class="flex flex-col w-full border-gray-400 rounded-lg duration-1000">
                <div class="flex justify-between w-full h-full rounded-lg">
                    <div class="flex justify-center shadow-lg hover:shadow-xl items-center h-full flex-col w-full hover:scale-105 rounded-tl-lg hover:cursor-pointer"
                        @click="accumulateStock(-1, ex.stock)">
                        <h1 class="text-[25px] text-left font-bold">-</h1>
                    </div>
                    <input type="number"
                        class="flex text-lg py-5 text-center justify-center items-center h-full flex-col w-full"
                        v-model="stockCounter" :on-keyup="accumulateStock(0, ex.stock)" />
                    <div class="flex justify-center shadow-lg items-center h-full flex-col w-full hover:scale-105 rounded-tr-lg hover:cursor-pointer"
                        @click="accumulateStock(1, ex.stock)">
                        <h1 class="text-[20px] text-left font-bold">+</h1>
                    </div>
                </div>
            </div>
        </div>
            <div @click="Sum = true"
                class="active:scale-95 flex justify-center items-center rounded-lg bg-blue-500 h-12 cursor-pointer duration-100">
                <h1 class="text-white font-semibold">Pesan Sekarang</h1>
            </div>
        <div @click="addToCart(id, stockCounter), toggleAddcartStatus = true"
            class="active:scale-95 border border-blue-500 flex justify-center items-center rounded-lg mt-4 bg-whit h-12 cursor-pointer duration-100">
            <div class="flex justify-center">
                + Keranjang
                 <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 mt-1 ml-1">
                   <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 00-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 00-16.536-1.84M7.5 14.25L5.106 5.272M6 20.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm12.75 0a.75.75 0 11-1.5 0 .75.75 0 011.5 0z" />
                  </svg>
             </div>
        </div>
        <div class="flex flex-col gap-4 mt-4 pb-6 border-gray-300 border-b">
            <div class="flex justify-between w-full">
                <div class="text-slate-600 cursor-pointer">
                    ${{ ex.price }} x {{ stockCounter }} pcs
                </div>
                <div class="font-bold">
                    ${{ ex.price * stockCounter }}
                </div>
            </div>
        </div>
    </div>
                <div class="flex flex-col justify-between w-fit h-20 rounded-lg p-4 bg-white z-20 shadow-lg mt-2" v-show="toggleAddcartStatus">
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
                </div>
            </div>
        </div>
    </div>
                    </div>
                </div>
    </section>   
    <Transition>
        <div class="flex fixed top-0 right-0 justify-center items-center w-screen h-screen z-[999]"
            v-show="Sum === true">
            <div class="flex absolute h-screen w-screen top-0 right-0 bg-slate-800 opacity-50 z-[1]"
                @click="Sum = false"></div>
            <div class="flex flex-col justify-between w-[400px] h-[650px] rounded-lg p-4 bg-white z-[2]">
                <div class="flex justify-end">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="black" class="w-6 h-6 hover:cursor-pointer mt-1" @click="Sum = false">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M9.75 9.75l4.5 4.5m0-4.5l-4.5 4.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                </div>
                <div class="flex justify-center">
                        <p class="font-bold text-xl">Summary</p>
                </div>
                <div class="overflow-y-scroll">
                    <div class="flex flex-col mt-6 mb-8 duration-1000">
                        <div class="flex justify-center">
                        <p class="font-bold">Item Yang Dipilih</p>
                </div>
                <div class="flex flex-col py-2">
                    <div class="flex">
                        <div class="flex">
                            <img :src="ex.thumbnail" alt="" class="h-[128px] object-cover aspect-square mx-1">
                            <div class="flex flex-col mx-6">
                                <div class="flex w-full justify-between">
                                    <NuxtLink :to="'/detail/'+ex.id">
                                        <h2 class="active:scale-95 duration-300">{{ ex.title }}</h2>
                                    </NuxtLink>
                                </div>
                                <div class="flex items-center">
                                    <span class="font-semibold">${{ ex.price }}</span>
                                </div>
                                <div class="flex items-center">
                                    <span class="font-semibold">Qty : <input type="number" id="qty" class="text-slate-800 font-semibold text-center px-4 w-20" :value="stockCounter" disabled/></span>
                                </div>
                                <div class="flex items-center">
                                    <span class="font-bold">Total : ${{ ex.price*stockCounter }}</span>
                                </div>
                                <div class="flex">
                        </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
      <label class="block text-gray-700 text-sm font-bold mb-2">
        Nama Pemesan
      </label>
      <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="Nama">
      <label class="block text-gray-700 text-sm font-bold mb-2 mt-2">
        Metode Pembayaran
      </label>
      <select name="" id="" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline">
        <option>-- PILIH --</option>
        <option>Cash On Delivery (COD)</option>
        <option>Transfer</option>
      </select>
      <label class="block text-gray-700 text-sm font-bold mb-2 mt-2">
        Alamat
      </label>
      <textarea class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="Alamat" cols="15" rows="15"></textarea>
    </div>
                <div class="flex justify-center mb-2">
                        <p class="text-slate-600 font-bold">Total Yang Harus Dibayar : ${{ ex.price*stockCounter }}</p>
                </div>
                <div class="flex justify-end">
                    <button class="bg-blue-500 hover:bg-blue-700 text-white text-xs font-bold py-2 px-4" @click="Thx = true">
                        Pesan
                        </button>
                </div>
            </div>
        </div>
    </Transition>

    <Transition>
        <div class="flex fixed top-0 right-0 justify-center items-center w-screen h-screen z-[999]"
            v-show="Thx === true">
            <NuxtLink to="/list">
            <div class="flex absolute h-screen w-screen top-0 right-0 bg-slate-800 opacity-50 z-[1]"
                @click="Thx = false"></div></NuxtLink>
            <div class="flex flex-col justify-between w-[400px] h-32 rounded-lg p-4 bg-white z-[2]">
                <div class="flex justify-end">
                    <NuxtLink to="/list">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="black" class="w-6 h-6 hover:cursor-pointer mt-1" @click="Thx = false, Sum = false, deleteAll()">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M9.75 9.75l4.5 4.5m0-4.5l-4.5 4.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                        </NuxtLink>
                </div>
                <div class="flex flex-col justify-center items-center text-lg mb-8">
                    <div class="flex flex-col mx-8">
                        Terimakasih Telah Berbelanja!
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
            stockCounter: 1,
            toggleAddcartStatus: false,
            Sum: false,
            Thx: false
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

            if (!localStorage.getItem("products")) {
                let array = [];
                dataProduct.cartId = 1;
                array.push(dataProduct);
                localStorage.setItem("products", JSON.stringify(array));
                console.log(JSON.parse(localStorage.getItem("products")));
            } 
            else {
                let productAtCart = JSON.parse(localStorage.getItem("products"));
                let listProductId = [];
                for (let i = 0; i < productAtCart.length; i++) {
                    if (!listProductId.includes(productAtCart[i].id)) {
                        listProductId.push(productAtCart[i].id)
                    }
                }
                console.log(listProductId);
                
                if (!listProductId.includes(dataProduct.id)) {
                    dataProduct.cartId   = productAtCart.length + 1;
                    productAtCart.push(dataProduct);
                    localStorage.setItem("products", JSON.stringify(productAtCart));
                    console.log(JSON.parse(localStorage.getItem("products")));
                    console.log(listProductId);
                } else {
                    for (let j = 0; j < productAtCart.length; j++) {
                        if (productAtCart[j].id === id) {
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
    checkOut() {
            if ( localStorage.getItem('user') ) {
                this.Sum = true;
            } else {
                this.Login = true;
            }
        },
    mounted() {

    }
}
</script>