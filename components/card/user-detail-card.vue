<template>
  <v-card class="mx-auto" :class="$vuetify.display.mdAndUp ? 'w-66' : 'w-100'">
    <div class="d-flex ml-4">
      <v-avatar
        size="80"
        :image="`https://picsum.photos/200/200?random=${data.id}`"
      ></v-avatar>
      <div>
        <v-card-title class="pb-0">
          <div :class="$vuetify.display.mdAndUp ? 'text-h4' : 'text-h5'">
            {{ data.name }}
          </div>
        </v-card-title>
        <v-card-title class="pt-0">
          <div class="text-h6">{{ data.username }}</div>
        </v-card-title>
      </div>
    </div>

    <v-list lines="two">
      <v-list-item>
        <template v-slot:prepend>
          <v-avatar>
            <v-icon color="indigo" icon="mdi-phone"></v-icon>
          </v-avatar>
        </template>

        <a :href="`tel:${data.phone}`" class="text-black">{{ data.phone }}</a>
        <v-list-item-subtitle>Mobile</v-list-item-subtitle>
      </v-list-item>

      <v-divider inset></v-divider>

      <v-list-item>
        <template v-slot:prepend>
          <v-avatar>
            <v-icon color="indigo" icon="mdi-email"></v-icon>
          </v-avatar>
        </template>

        <a :href="`mailto:${data.email}`" class="text-black">{{
          data.email
        }}</a>
        <v-list-item-subtitle>Personal</v-list-item-subtitle>
      </v-list-item>
      <v-list-item>
        <template v-slot:prepend>
          <v-avatar>
            <v-icon color="indigo" icon="mdi-web"></v-icon>
          </v-avatar>
        </template>

        <a :href="`http://${data.website}`" class="text-black">{{
          data.website
        }}</a>
        <v-list-item-subtitle>Website</v-list-item-subtitle>
      </v-list-item>
      <v-list-item>
        <template v-slot:prepend>
          <v-avatar>
            <v-icon color="indigo" icon="mdi-briefcase-outline"></v-icon>
          </v-avatar>
        </template>

        <v-list-item-title>{{ data.company.name }}</v-list-item-title>
        <v-list-item-subtitle>company</v-list-item-subtitle>
      </v-list-item>

      <v-divider inset></v-divider>

      <v-list-item>
        <template v-slot:prepend>
          <v-avatar>
            <v-icon color="indigo" icon="mdi-map-marker"></v-icon>
          </v-avatar>
        </template>

        <v-list-item-title
          >{{ data.address.street }} /
          {{ data.address.suite }}</v-list-item-title
        >

        <v-list-item-subtitle
          >{{ data.address.city }} - zipcode:
          {{ data.address.zipcode }}</v-list-item-subtitle
        >

        <div style="height: 200px; width: 300px">
          <v-img
            height="100%"
            width="100%"
            :src="`https://maps.geoapify.com/v1/staticmap?style=osm-bright-grey&width=600&height=400&center=lonlat:${data.address.geo.lat},${data.address.geo.lng}&zoom=1.8713&marker=lonlat:${data.address.geo.lat},${data.address.geo.lng};type:material;color:%231f63e6;size:x-large;icon:cloud;icontype:awesome;whitecircle:no&apiKey=1f286604387540ba97d6ccb424a4b973`"
          />
        </div>
      </v-list-item>
    </v-list>
  </v-card>
</template>
<script setup>
import { useDisplay } from 'vuetify';
const props = defineProps({
  data: {
    type: Object,
    default: {},
  },
});
</script>
