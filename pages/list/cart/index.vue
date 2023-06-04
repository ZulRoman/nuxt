
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
                    <h1 class="text-xl text-white bg-rose-500 rounded px-2 py-2 font-semibold cursor-pointer hover:text-rose-800 active:scale-95 duration-100" v-show="cartData.length > 0" @click="DeleteAll = true">Delete All</h1>
                </div>
                <div class="flex flex-col justify-center items-center h-80 text-xl text-gray-600 " v-show="cartData.length === 0">
                    <div>
                    Belum ada item apapun...
                    </div>
                    <div class="mt-2 hover:scale-110 hover:text-blue-900 duration-1000 text-blue-500 font-bold">
                    <NuxtLink to="/list">
                        Tambahkan
                    </NuxtLink>
                </div>
                </div>
                <div class="flex flex-col mt-6 mb-8 duration-1000">
                    <div class="flex flex-col py-2" v-for="cartProduct in cartData">
                        <div class="flex">
                            <div class="flex">
                                <NuxtLink :to="'/list/'+cartProduct.id">
                                <img :src="cartProduct.thumbnail" alt="" class="h-[128px] object-cover aspect-square mx-1">
                                </NuxtLink>
                                <div class="flex flex-col mx-6">
                                    <div class="flex w-full justify-between">
                                        <NuxtLink :to="'/list/'+cartProduct.id">
                                            <h2 class="active:scale-95 duration-300">{{ cartProduct.title }}</h2>
                                        </NuxtLink>
                                    </div>
                                    <div class="flex items-center">
                                        <span class="font-semibold">${{ cartProduct.price }}</span>
                                    </div>
                                    <div class="flex items-center">
                                        <span class="flex items-center h-8 border shadow-lg hover:scale-105 active:scale-95 cursor-pointer rounded-tl-lg text-xl text-center px-4" @click="accumulateQty(cartProduct.id, -1, cartProduct.stock)">-</span>
                                        <input type="number" id="qty" class="text-slate-800 font-semibold text-center px-4 w-20" v-model="cartProduct.qty" min="1" :max="cartProduct.stock"/>
                                        <span class="flex items-center h-8 border shadow-lg hover:scale-105 active:scale-95 cursor-pointer rounded-tr-lg text-xl text-center px-4" @click="accumulateQty(cartProduct.id, 1, cartProduct.stock)">+</span>
                                        <span class="font-semibold ml-2">Stock : {{ cartProduct.stock-cartProduct.qty }}</span>
                                    </div>
                                    <div class="flex items-center">
                                        <span class="font-semibold">Total : ${{ cartProduct.price*cartProduct.qty }}</span>
                                    </div>
                                    <div class="flex">
                                <span class="text-white bg-rose-500 rounded px-1 py-1 font-semibold cursor-pointer hover:text-rose-800 active:scale-95 duration-100" @click="Delete1 = true">Delete</span>
                            </div>
                                </div>
                            </div>
                        </div>
                        <Transition>
        <div class="flex fixed top-0 right-0 justify-center items-center w-screen h-screen z-[999]"
            v-show="Delete1 === true">
            <div class="flex absolute h-screen w-screen top-0 right-0 bg-slate-800 opacity-50 z-[1]"
                @click="Delete1 = false"></div>
            <div class="flex flex-col justify-between w-[400px] h-64 rounded-lg p-4 bg-white z-[2]">
                <div class="flex justify-end">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="black" class="w-6 h-6 hover:cursor-pointer mt-1" @click="Delete1 = false">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M9.75 9.75l4.5 4.5m0-4.5l-4.5 4.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                </div>
                <div class="flex flex-col justify-center items-center text-lg mb-8">
                    <div class="flex flex-col">
                        Apakah Anda Yakin Ingin Menghapus Item Ini?
                        <div class="flex mt-2">
                                <img :src="cartProduct.thumbnail" alt="" class="h-[64px] object-cover aspect-square mx-1">
                                <div class="flex flex-col mx-6">
                                    <div class="flex w-full justify-between">
                                            <h2 class="active:scale-95 duration-300">{{ cartProduct.title }}</h2>
                                    </div>
                                    <div class="flex items-center">
                                        <span class="font-semibold">${{ cartProduct.price }}</span>
                                    </div>
                                </div>
                            </div>
                    </div>
                </div>
                <div class="flex justify-end">
                    <div class="flex gap-6">
                        <div class="text-rose-500 hover:scale-105 active:scale-95 font-medium cursor-pointer"
                            @click="Delete1 = false">
                            No
                        </div>
                        <div class="text-slate-700 hover:scale-105 active:scale-95 font-medium cursor-pointer"
                            @click="delete1(cartProduct.id), Delete1 = false">
                            Yes
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </Transition>
                    </div>
                </div>
            </div>
        </div>
        <p class="text-slate-600 font-bold" v-show="cartData.length > 0">Total Harga : ${{ (allPrice) }}</p>
        <button class="bg-blue-500 hover:bg-blue-700 text-white text-xl font-bold py-2 px-4" v-show="cartData.length > 0" @click="Sum = true">
                Check Out
                </button>
        </section>

        <Transition>
        <div class="flex fixed top-0 right-0 justify-center items-center w-screen h-screen z-[999]"
            v-show="DeleteAll === true">
            <div class="flex absolute h-screen w-screen top-0 right-0 bg-slate-800 opacity-50 z-[1]"
                @click="DeleteAll = false"></div>
            <div class="flex flex-col justify-between w-[400px] h-64 rounded-lg p-4 bg-white z-[2]">
                <div class="flex justify-end">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="black" class="w-6 h-6 hover:cursor-pointer mt-1" @click="DeleteAll = false">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M9.75 9.75l4.5 4.5m0-4.5l-4.5 4.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                </div>
                <div class="flex flex-col justify-center items-center text-lg mb-8">
                    <div class="flex flex-col mx-8">
                        Apakah Anda Yakin Ingin Menghapus Semua Item?
                    </div>
                </div>
                <div class="flex justify-end">
                    <div class="flex gap-6">
                        <div class="text-rose-500 hover:scale-105 active:scale-95 font-medium cursor-pointer"
                            @click="DeleteAll = false">
                            No
                        </div>
                        <div class="text-slate-700 hover:scale-105 active:scale-95 font-medium cursor-pointer"
                            @click="deleteAll()">
                            Yes
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </Transition>

    <Transition>
        <div class="flex fixed top-0 right-0 justify-center items-center w-screen h-screen z-[999]"
            v-show="Sum === true">
            <div class="flex absolute h-screen w-screen top-0 right-0 bg-slate-800 opacity-50 z-[1]"
                @click="Sum = false"></div>
            <div class="flex flex-col justify-between w-[400px] h-screen rounded-lg p-4 bg-white z-[2]">
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
                                    <span class="font-semibold">Qty : <input type="number" id="qty" class="text-slate-800 font-semibold text-center px-4 w-20" v-model="cartProduct.qty" disabled/></span>
                                </div>
                                <div class="flex items-center">
                                    <span class="font-bold">Total : ${{ cartProduct.price*cartProduct.qty }}</span>
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
                        <p class="text-slate-600 font-bold">Total Yang Harus Dibayar : ${{ (allPrice) }}</p>
                </div>
                <div class="flex justify-end">
                    <button class="bg-blue-500 hover:bg-blue-700 text-white text-xs font-bold py-2 px-4">
                        Pesan
                        </button>
                </div>
            </div>
        </div>
    </Transition>
</template>

<script>
export default {
    data() {
        return {
            cartData: [],
            allPrice: 0,
            allQty: 0,
            Delete1: false,
            DeleteAll: false,
            Sum : false
        }
    },
    methods: {
        getCartData() {
            let rawData = JSON.parse(localStorage.getItem("products"));
            if (rawData) {
                this.cartData = rawData;
                console.log(this.cartData)
            } else {
                this.cartData = [];
                console.log(this.cartData)
            }
            this.setTotal();
        },
        deleteAll() {
            this.cartData = [];
            localStorage.removeItem("products");
            this.DeleteAll = false;
            this.getCartData();
        },
        delete1(id) {
            for (let i = 0; i < this.cartData.length; i++) {
                if (this.cartData[i].id === id) {
                    this.cartData.splice(i, 1);
                    localStorage.setItem("products", JSON.stringify(this.cartData));
                    this.DeleteAll = false;
                }
            }
            this.getCartData();
        },
        accumulateQty(id, qty, stock) {
            //get data with the same id
            for (let i = 0; i < this.cartData.length; i++) {
                if (this.cartData[i].id === id) {
                    if (qty == 1) {
                        if (this.cartData[i].qty < stock) {
                            this.cartData[i].qty += qty;
                        } else if (this.cartData[i].qty >= stock) {
                            this.cartData[i].qty = stock;
                        }
                    } else if (qty == -1) {
                        if (this.cartData[i].qty < 1) {
                            this.cartData[i].qty = 1;
                        } else if (this.cartData[i].qty > 1) {
                            this.cartData[i].qty += qty;
                        }
                    } else if (this.cartData[i].qty > stock) {
                        this.cartData[i].qty = stock;
                    } else if (this.cartData[i].qty < 1) {
                        this.cartData[i].qty = 1;
                    }
                    this.cartData[i].subTotal = this.cartData[i].qty * this.cartData[i].netPrice
                }
            }
            localStorage.setItem("products", JSON.stringify(this.cartData));
            this.getCartData();
        },
        setTotal() {
            if (!this.cartData.length == 0) {
                //set to 0
                this.allPrice = 0;
                this.allQty = 0;
                for (let i = 0; i < this.cartData.length; i++) {
                    //accumulate
                    this.allPrice += this.cartData[i].price * this.cartData[i].qty;
                    this.allQty += this.cartData[i].qty;
                    console.log(this.allPrice);
                }
            } else {
                this.allPrice = 0;
                this.allQty = 0;
                console.log(this.allPrice);
                console.log(this.allQty);
            }
        },
    },
    mounted() {
        this.getCartData()
    }
}
</script>