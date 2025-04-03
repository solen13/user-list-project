<template>
  <user-detail-card :data="filteredProducts" />
</template>
<script setup>
import { useRoute } from 'vue-router';

const route = useRoute();
const slug = Number(route.params.id);

const responseData = ref([]);

const { data } = await useAsyncData('products', () =>
  $fetch('https://jsonplaceholder.typicode.com/users')
);

responseData.value = data.value;

// api yetersizliğinden  bu şekilde yapılmıştır normal şartlarda  "/users/1" şeklinde istek atılır
const filteredProducts = computed(() => {
  const filtered = responseData.value.filter((product) => product.id === slug);

  return filtered.length > 0 ? filtered[0] : {};
});
</script>
