<script setup>
import { useRoute } from 'vue-router';
import { ref } from 'vue';

const route = useRoute();
const id = route.params.id;
/* router -> navegacion */

/* route -> name, meta, params */
const result = ref(null);
fetch(`https://dummyjson.com/products/${id}`).then(
  async (res) => (result.value = await res.json())
);
</script>

<template>
  <div class="grid grid-cols-4 col-start-2">
    <div class="col-start-2">
      <div
        v-if="result"
        class="mt-16"
      >
        <img :src="result.thumbnail" />
      </div>
      <div>
      </div>
    </div>
  </div>
</template>
