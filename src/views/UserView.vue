<script setup>
import { ref } from 'vue';
import { user } from '@/utils/users';

let people = ref(user);

const delUser = (id) => people.value.filter((product) => product.id !== id);
</script>
<template>
  <div
    class="bg-blue-100 title w-screen md:mx-auto grid grid-rows-2 grid-flow-col gap-2 justify-center py-5"
  >
    <h1 class="text-2xl">Pagina de Usuarios</h1>
    <h2>#: {{ people.length }}</h2>
  </div>
  <div>
    <ul class="divide-y divide-gray-200">
      <li
        v-for="person in people"
        :key="person.email"
        class="py-4 flex bg-blue-200 md:mx m-auto w-1/3 shadow-lg my-3"
      >
        <div class="ml-3">
          <p class="text-sm font-medium text-gray-950">{{ person.name }}</p>
          <p class="text-sm text-gray-950">{{ person.email }}</p>
          <p class="text-sm text-gray-950">
            {{
              `Calle ${person.address.street}, ${person.address.suite}, ${person.address.city}, ${person.address.zipcode} Lang ${person.address.geo.lat},
                                            ${person.address.geo.lng}`
            }}
          </p>
          <p class="text-sm text-gray-950">{{ ` ${person.phone}` }}</p>
          <p class="text-sm text-gray-950">{{ ` ${person.website}` }}</p>
          <div>
            <button
              class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center"
              @click="delUser(person.id)"
            >
              <svg
                class="fill-current w-4 h-4 mr-2"
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 20 20"
              >
                <path
                  d="M 14.984375 2.4863281 A 1.0001 1.0001 0 0 0 14 3.5 L 14 4 L 8.5 4 A 1.0001 1.0001 0 0 0 7.4863281 5 L 6 5 A 1.0001 1.0001 0 1 0 6 7 L 24 7 A 1.0001 1.0001 0 1 0 24 5 L 22.513672 5 A 1.0001 1.0001 0 0 0 21.5 4 L 16 4 L 16 3.5 A 1.0001 1.0001 0 0 0 14.984375 2.4863281 z M 6 9 L 7.7929688 24.234375 C 7.9109687 25.241375 8.7633438 26 9.7773438 26 L 20.222656 26 C 21.236656 26 22.088031 25.241375 22.207031 24.234375 L 24 9 L 6 9 z"
                />
              </svg>
            </button>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>
<style scoped>
.title {
  height: 100px;
}
</style>
