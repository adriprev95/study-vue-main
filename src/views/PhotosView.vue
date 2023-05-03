<script setup>
import { ref } from 'vue';
import { photo } from '@/utils/photos';

const photos = ref(photo);
</script>

<template>
  <div
    class="title w-screen md:mx-auto grid grid-rows-2 grid-flow-col gap-2 justify-center py-5"
  >
    <h1 class="text-2xl">Pagina photos</h1>
    <h2>#: {{ photos.length }}</h2>
  </div>
  <div>
    <div class="flex flex-wrap justify-center mx-5">
      <div
        v-for="photo in photos"
        :key="photo.id"
      >
        <div v-if="photo.id !== 43">
          <div v-if="!photo.title.endsWith('s')">
            <div class="flex flex-wrap md:w-80 mx-5">
              <img
                :src="photo.url"
                alt=""
                class="photo"
              />
              <div class="flex flex-wrap justify-center content-around mx-2">
                <span
                  v-if="photo.title.startsWith('v')"
                  class="text-justify"
                >
                  {{
                    `${photo.title.replace('accusamus', 'soy un crack')}
                    wtf creo que ya entendi como funciona el v-if`
                  }}
                </span>
                <span
                  v-else
                  class="text-justify"
                >
                  {{ photo.title.replace('accusamus', 'soy un crack') }}
                </span>
                <span class="text-justify">{{ photo.id }}</span>
                <span class="text-justify">
                  {{ photo.id % 2 === 0 ? ' Es par' : ' Es impar' }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.title {
  background-color: aliceblue;
  height: 100px;
}

.algo {
  width: 250px;
}
</style>
