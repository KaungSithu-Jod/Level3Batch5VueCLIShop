<template>
    <!-- Header -->
    <Header title="Shop in Style" subtitle="Testing 1 2 3" />
    <!-- Section -->
    <section class="py-5">
        <div class="container px-4 px-lg-5 mt-5">
            <div class="row gx-4 gx-lg-5 row-cols-12 justify-content-center">
                <div class="col">
                    <div class="card mb-3" >
                        <div class="row g-0">
                            <div class="col-md-4">
                                <img class="img-fluid rounded-start" :src="product.image">
                            </div>
                            <div class="col-md-8">
                                <div class="card-body">
                                    <h5 class="card-title">{{product.title}}</h5>
                                    <p class="card-text">{{product.description}}</p>
                                    <button class="btn btn-outline-dark mt-auto mx-2">Add to Cart</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

</template>

<script>
import Header from '@/components/Header.vue';
const axios = require("axios") ;


export default {
    name: 'DetailView',
    components: { Header},
    data() {
        return {
            product: Object,
        };
    },

    mounted() {
        this.getProduct();
    },

    methods: {
        getProduct() {
            let id = this.$route.params.id;
            axios.get(`https://fakestoreapi.com/products/${id}`).then((response) => {
                this.product = response.data;
            });
        }
    },
}
</script>