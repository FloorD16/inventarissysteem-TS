<script setup lang="ts">
import { useRoute, useRouter } from 'vue-router';
import { getProductByID, updateProduct, type Product } from '../store';
import ProductForm from '../components/ProductForm.vue';

const router = useRouter();

const id: number = Number(useRoute().params.id);
const selectedProduct = getProductByID(id);

const update = (product: Product) => {
    updateProduct(product);
    router.push({ name: 'inventory.overview' });
}

</script>

<template>
    <ProductForm :product="selectedProduct" nameButtonForSubmit='Aanpassen' @newProduct="update" />
</template>