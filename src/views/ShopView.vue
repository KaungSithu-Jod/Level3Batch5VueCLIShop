<template>
    <!-- Header -->
    <Header title="Shop in Style" subtitle="Testing 1 2 3" />
    <!-- Section -->
    <section class="py-5">
        <div class="container px-4 px-lg-5 mt-5">
            <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4 justify-content-center">
                <div class="col mb-5" v-for="(row,index) in products" :key="index">
                    <Card :product="row"></Card>
                </div>
            </div>
        </div>
    </section>

</template>

<script>
    import Header from '@/components/Header.vue';
    import axios from "axios";

    import Card from '@/components/Card.vue';

export default {
    name: 'ShopView',
    components: { Header, Card },
    data() {
        return {
            products: [],
        }
    },
    mounted() {
        axios.get('https://fakestoreapi.com/products')
            .then(response => {
                // console.log(response)
                this.products = response.data
            })
    }
}
</script>