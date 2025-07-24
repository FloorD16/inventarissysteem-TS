<script setup lang="ts">

import { ref } from 'vue';
import ProductForm from '../components/ProductForm.vue';
import { addProduct, getAllProducts, type Product } from '../store';
import { useRouter } from 'vue-router';

const router = useRouter();

const newID = getAllProducts.value.length === 0 ? 1 : Math.max(...getAllProducts.value.map(product => product.id)) + 1;

const product = ref<Product>({ id: newID, name: '', actualAmount: 0, minimumAmount: 0 });

const addNewProduct = (product: Product) => {
    addProduct(product);
    router.push({ name: 'inventory.overview' });
}
</script>

<template>
    <ProductForm :product="product" nameButtonForSubmit="Toevoegen" @newProduct="addNewProduct" />    
</template>