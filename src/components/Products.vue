<template>
    <div :key="product.id" v-for="product in products">
        <Product @delete-product="$emit('delete-product', product.id)" :product="product" />
    </div>
</template>

<script>
import Product from './Product.vue'

    export default {
        name: 'Products',
        props: {
            products: Array
        },
        components: {
            Product
        },
        emits: ['delete-product'],

    }
</script>