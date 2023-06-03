
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
                    <h1 class="text-2xl font-semibold">My cart</h1>
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
                                <img :src="cartProduct.thumbnail" alt="" class="h-20 object-cover aspect-square mx-1">
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
                                        <div class="flex">
                                <span class="text-rose-900 font-semibold cursor-pointer hover:text-rose-700 active:scale-95 duration-100 ml-2" @click="delete1(cartProduct.id)">Delete</span>
                            </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <button class="bg-blue-500 hover:bg-blue-700 text-white text-xl font-bold py-2 px-4 mb-[40px]" v-show="cartData.length > 0">
                Check Out
                </button>
        </section>
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
            allSubTotal: 0
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