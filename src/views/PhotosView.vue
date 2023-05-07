<script setup>
import { ref } from 'vue';

const result = ref(null);
fetch('https://dummyjson.com/products').then(
  async (res) => (result.value = await res.json())
);
</script>

<template>
  <div class="my-container">
    <div class="my-grid-system">
      <div
        v-for="product in result?.products"
        :key="product.id"
      >
        <img
          :src="product.thumbnail"
          style="width: 100%; height: 250px"
          @click="$router.push({ name: 'product', params: { cualquiercosa: product.id } })"
        />
      </div>
    </div>
    <div>
      {{ $router }}
    </div>
  </div>
</template>

<style scoped>
.my-grid-system {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  column-gap: 20px;
  row-gap: 20px;
}
.my-container {
  padding: 30px 50px 30px 50px;
}
@media only screen and (max-width: 700px) {
  .my-grid-system {
    grid-template-columns: 1fr 1fr;
  }
}
</style>
