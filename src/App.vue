<script setup>
import './style.css';
import { onMounted, ref } from 'vue';
import { fakeStoreAPI } from '../api/fakestore_api';

const products = ref(null);

onMounted(async () => {
  try {
    products.value = await fakeStoreAPI.get('/products')
    console.log(products)
  } catch(error) {
    throw new Error(error)
  }
})


</script>

<template>
  <h1>tere</h1>
  <div>
    <article v-for="product in products?.data" :key="product.id">
      <img :src="product.image" alt="">
      <h4>{{ product.title }}</h4>
      <p>{{ product.description }}</p>
    </article>
  </div>
</template>