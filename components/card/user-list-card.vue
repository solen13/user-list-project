<template>
  <v-card class="mx-auto d-flex align-center pa-2" max-width="650">
    <v-avatar
      size="50"
      image="https://cdn.vuetifyjs.com/images/lists/1.jpg"
    ></v-avatar>

    <div class="ml-3">
      <h2 :class="$vuetify.display.mdAndUp ? 'text-h4' : 'text-h6'">jack</h2>

      <div>
        <span class="mr-2">Gwenborough</span>
        <span>Romaguera-Crona</span>
      </div>
    </div>

    <v-btn
      class="ma-2 ml-auto"
      icon="mdi-chevron-right-circle-outline"
      variant="text"
    ></v-btn>
  </v-card>
</template>
<script setup></script>
