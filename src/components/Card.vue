<template>
    <div class="card h-100">
        <!-- Product image-->
        <img class="card-img-top" :src="product.image" height="300" />
        <!-- Product details-->
        <div class="card-body p-4">
            <div class="text-center">
                <!-- Product name-->
                <h5 class="fw-bolder">{{product.title}}</h5>
                <!-- Product price-->
                {{product.price}}
            </div>
        </div>
        <!-- Product actions-->
        <div class="card-footer p-4 pt-0 border-top-0 bg-transparent">
            <button class="btn btn-outline-dark mt-auto mx-2" @click="AddToCart()">Add to Cart</button>
            <router-link class="btn btn-outline-dark mt-auto" :to="{ name: 'DetailView', params: {id:product.id}}">
                Detail</router-link>
        </div>
    </div>
</template>

<script>

export default {
    name: 'ProductCard',
    props: {
        product: Object,
    },
    methods: {
        addToCart() {
            let status = true
            let product = this.product
            product['qty'] = 1;
            let productArray;
            let cart = localStorage.getItem('cart');
            if (cart) {
                productArray = JSON.parse(cart);
            } else {
                productArray = new Array;
            }
            for (const p of productArray) {
                if (p.id == product.id) {
                    p.qty++;
                    status = false
                    break;
                }
            }
            if (status) {
                productArray.push(product);
            }
            localStorage.setItem('cart', JSON.stringify(productArray));
            this.$store.dispatch('getData')
        }
    }
};
</script>
