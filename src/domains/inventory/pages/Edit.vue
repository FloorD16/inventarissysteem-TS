<script setup lang="ts">
import { useRoute } from 'vue-router';
import { getProductByID, updateProduct, type Product } from '../store';
import ProductForm from '../components/ProductForm.vue';

const id: number = Number(useRoute().params.id);
const selectedProduct = getProductByID(id);
</script>

<template>
    <ProductForm :product="selectedProduct" nameButtonForSubmit='Aanpassen' @newProduct="updateProduct" />
</template>