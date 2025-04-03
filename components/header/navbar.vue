<template>
  <v-app-bar app color="primary" dark>
    <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

    <v-spacer></v-spacer>
    <v-btn
      text
      v-for="item in menuItems"
      :key="item.title"
      :to="item.link"
      class="d-none d-md-flex"
    >
      <v-icon left>{{ item.icon }}</v-icon> {{ item.title }}
    </v-btn>
    <nuxt-link to="/" class="d-flex d-md-none bg-transparent">
      <v-img
        src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ24XBy0xEPeMw9HR3L26ahY2t5UVjW1vXi3Q&s"
        width="50"
      />
    </nuxt-link>
  </v-app-bar>

  <v-navigation-drawer v-model="drawer" app temporary>
    <v-list>
      <v-list-item v-for="item in menuItems" :key="item.title" :to="item.link">
        <span class="d-flex item-center ga-2">
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </span>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script setup>
import { ref } from 'vue';

const menuItems = ref([
  { title: 'Home', icon: 'mdi-home', link: '/' },
  { title: 'About', icon: 'mdi-information' },
  { title: 'Services', icon: 'mdi-cog' },
  { title: 'Contact', icon: 'mdi-phone' },
]);

const drawer = ref(false);
</script>
