<template>
  <div>
    <v-list>
      <user-list-card v-for="item in visibleUsers" :data="item" class="mt-4" />
    </v-list>
    <div class="d-flex justify-center mt-10">
      <v-btn
        v-if="visibleUsers.length < responseData.length"
        @click="loadMore"
        class="mx-auto"
      >
        Daha Fazla Göster
      </v-btn>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const responseData = ref([]);
const visibleCount = ref(4); // Başlangıçta 4 öğe göster

const { data } = await useAsyncData('products', () =>
  $fetch('https://jsonplaceholder.typicode.com/users')
);

responseData.value = data.value;

// Gösterilecek kullanıcıları hesaplayan computed property
const visibleUsers = computed(() =>
  responseData.value.slice(0, visibleCount.value)
);

// Butona basıldığında 4 tane daha ekler
const loadMore = () => {
  visibleCount.value += 4;
};
</script>
