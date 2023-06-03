
<template>
        <section class="my-[88px]">
            <NuxtLink to="/list">
                <button class="bg-blue-500 hover:bg-blue-700 text-white text-xs font-bold py-2 px-4">
                Kembali
                </button>
            </NuxtLink>
        <div class="flex sm:justify-between gap-10 justify-center h-fit w-full mt-4 px-2 duration-1000 ">
            <div class="flex flex-col w-full h-fit duration-1000">
                <div class="flex justify-between items-center duration-1000">
                    <h1 class="text-2xl font-semibold">Keranjang Saya</h1>
                    <h1 class="text-xl text-white bg-rose-500 rounded px-2 py-2 font-semibold cursor-pointer hover:text-rose-800 active:scale-95 duration-100" @click="deleteall()">Delete All</h1>
                </div>
                <div class="flex flex-col justify-center items-center h-80 text-xl text-gray-600" v-show="cartData.length === 0">
                    <div>
                    Belum ada item apapun...
                    </div>
                    <div class="mt-2">
                    <NuxtLink to="/list" class="text-blue-900 font-bold">
                        Tambahkan
                    </NuxtLink>
                </div>
                </div>
                <div class="flex flex-col mt-6 mb-8 duration-1000">
                    <div class="flex flex-col py-2" v-for="cartProduct in cartData">
                        <div class="flex">
                            <div class="flex">
                                <img :src="cartProduct.thumbnail" alt="" class="h-[128px] object-cover aspect-square mx-1">
                                <div class="flex flex-col mx-6">
                                    <div class="flex w-full justify-between">
                                        <NuxtLink :to="'/detail/'+cartProduct.id">
                                            <h2 class="active:scale-95 duration-300">{{ cartProduct.title }}</h2>
                                        </NuxtLink>
                                    </div>
                                    <div class="flex items-center">
                                        <span class="font-semibold">${{ cartProduct.price }}</span>
                                    </div>
                                    <div class="flex items-center">
                                        <!-- <span class="flex items-center h-8 border shadow-lg hover:scale-105 active:scale-95 cursor-pointer rounded-tl-lg text-xl text-center px-4" @click="accumulateStock(1, stock)">-</span> -->
                                        <input type="number" id="qty" class="text-slate-800 font-semibold text-center px-4 w-20" v-model="cartProduct.qty"/>
                                        <!-- <span class="flex items-center h-8 border shadow-lg hover:scale-105 active:scale-95 cursor-pointer rounded-tr-lg text-xl text-center px-4" @click="accumulateStock(-1, stock)">+</span> -->
                                    </div>
                                    <div class="flex items-center">
                                        <span class="font-semibold">Total : ${{ cartProduct.price*cartProduct.qty }}</span>
                                    </div>
                                    <div class="flex">
                                <span class="text-white bg-rose-500 rounded px-1 py-1 font-semibold cursor-pointer hover:text-rose-800 active:scale-95 duration-100" @click="delete1(cartProduct.id)">Delete</span>
                            </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <button class="bg-blue-500 hover:bg-blue-700 text-white text-xl font-bold py-2 px-4" v-show="cartData.length > 0" @click="toggleAddcartStatus = true">
                Check Out
                </button>
        </section>

        <!-- <div class="flex fixed top-0 right-0 justify-center items-center w-screen h-screen"
                v-show="toggleAddcartStatus">
                <div class="flex absolute h-screen w-screen top-0 right-0 bg-slate-800 opacity-50 z-[10]"
                    @click="toggleAddcartStatus = false"></div>
                <div class="flex flex-col justify-between w-[400px] h-64 rounded-lg p-4 bg-white z-[20] shadow-lg">
                    <div class="flex justify-end">
                        <img src="/svg/close.svg" alt="" class="h-6 cursor-pointer hover:scale-105 active:scale-95"
                            @click="toggleAddcartStatus = false">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="black" class="w-6 h-6 hover:cursor-pointer" @click="toggleAddcartStatus = false">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M9.75 9.75l4.5 4.5m0-4.5l-4.5 4.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                    </div>
                    <div class="flex justify-center text-lg">
                        <div class="flex items-center flex-col">
                            Product Berhasil Ditambahkan
                        </div>
                    </div>
                    <div class="flex justify-end">
                        <div class="flex">
                            <div class="text-rose-500 hover:scale-105 active:scale-95 font-medium cursor-pointer">
                                <NuxtLink to="/list/cart">
                                    Go to cart
                                </NuxtLink>
                            </div>
                        </div>
                    </div>
                </div>
            </div> -->
</template>

<script>
export default {
    data() {
        return {
            layouts: {
                header: "header",
                container: "container"
            },
            noteStatus: false,
            cartData: [],
            allSubTotal: 0,
            toggleAddcartStatus: false
        }
    },
    methods: {
        accumulateStock(n, stock) {
            if (n == 1) {
                if (this.cartProduct.qty < stock) {
                    this.cartProduct.qty += n;
                } else if (this.cartProduct.qty >= stock) {
                    this.cartProduct.qty = stock;
                }
            } else if (n == -1) {
                if (this.cartProduct.qty < 1) {
                    this.cartProduct.qty = 1;
                } else if (this.cartProduct.qty > 1) {
                    this.cartProduct.qty += n;
                }
            } else if (this.cartProduct.qty > stock) {
                this.cartProduct.qty = stock;
            } else if (this.cartProduct.qty < 1) {
                this.cartProduct.qty = 1;
            }
            console.log(this.cartProduct.qty, stock);
        },
        cartp() {
            let rawData = JSON.parse(localStorage.getItem("products"));
            this.cartData = rawData;
            console.log(this.cartData)
        },
        deleteall() {
            localStorage.removeItem("products");
            this.cartp();
        },
        delete1(id) {
            for (let i=0; i<this.cartData.length; i++) {
                if ( this.cartData[i].id === id ) {
                    this.cartData.splice(i,1);
                    localStorage.setItem("products",JSON.stringify(this.cartData));
                    this.cartp;
                }
            }
        }
    },
    mounted() {
        this.cartp()
    }
}
</script>