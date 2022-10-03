<template>
    <!-- Header -->
    <Header title="Shop in Style" subtitle="Testing 1 2 3"/>
    <!-- Dropdown -->
    <section class="py-5">
        <div class="container ms-5">
            <div class="dropdown">
                <a class="btn btn-light btn-outline-dark dropdown-toggle" role="button" data-bs-toggle="dropdown"
                    aria-expanded="false">
                    Categories
                </a>
                <ul class="dropdown-menu">
                    <li><a class="dropdown-item" @click="reloadPage()">All Products</a></li>
                    <li v-for="(cat,index) in Categories" :key="index">
                        <a class="dropdown-item text-capitalize" @click="ItemsInCat(cat)">
                            {{cat}}
                        </a>
                    </li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Section -->
    <section>
        <div class="container">
            <div class="row row-cols-2 row-cols-md-3 row-cols-xl-4 justify-content-center">
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
            Categories: [],

        }
    },
    mounted() {
        axios.get('https://fakestoreapi.com/products').then(response => {
            // console.log(response)
            this.products = response.data
            });
        axios.get('https://fakestoreapi.com/products/categories').then(response => {
            this.Categories = response.data
        })
    },
    methods: {
        ItemsInCat(cat) {
            axios.get(`https://fakestoreapi.com/products/category/${cat}`).then(response => {
                this.products = response.data
            })
        },
        reloadPage(){
            window.location.reload();
        }
    },
}
</script>