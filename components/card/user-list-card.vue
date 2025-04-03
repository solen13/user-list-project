<template>
  <v-card class="mx-auto d-flex align-center pa-2" max-width="650">
    <v-avatar
      size="50"
      :image="`https://picsum.photos/200/200?random=${data.id}`"
    ></v-avatar>

    <div class="ml-3">
      <h2 :class="$vuetify.display.mdAndUp ? 'text-h5' : 'text-h6'">
        {{ data.name }}
      </h2>

      <div>
        <span class="mr-2">{{ data.address.city }}</span>
        -
        <span>{{ data.company.name }}</span>
      </div>
    </div>

    <nuxt-link
      :to="`/person-detail/${data.id}`"
      class="ma-2 ml-auto text-black"
    >
      <v-icon size="x-large"> mdi-chevron-right-circle-outline </v-icon>
    </nuxt-link>
  </v-card>
</template>
<script setup>
const props = defineProps({
  data: {
    type: Object,
    default: {},
  },
});
</script>
