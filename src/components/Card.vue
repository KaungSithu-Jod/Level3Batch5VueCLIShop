<template>
    <div class="card h-100">
        <!-- Product image-->
        <img class="card-img-top" :src="product.image" height="300"/>
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
            <button class="btn btn-outline-dark mt-auto mx-2"  >Add to Cart</button>
            <router-link class="btn btn-outline-dark mt-auto" :to="{ name: 'DetailView', params: {id:product.id}}">Detail</router-link>
        </div>
    </div>
</template>

<script>
    
    export default {
        name: 'ProductCard',
        props: {
            product: Object,
        },
    };
</script>
