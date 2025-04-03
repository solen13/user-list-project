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
        show more
      </v-btn>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const responseData = ref([]);
const visibleCount = ref(4);

const { data } = await useAsyncData('products', () =>
  $fetch('https://jsonplaceholder.typicode.com/users')
);

responseData.value = data.value;

const visibleUsers = computed(() =>
  responseData.value.slice(0, visibleCount.value)
);

const loadMore = () => {
  // Aşırı derecede veri yüklememek için dom a kısım kısım alıyoruz
  visibleCount.value += 4;
};
</script>
