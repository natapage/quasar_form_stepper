<script setup lang="ts">
import { ref } from 'vue';
const props = defineProps({
  model: String,
  optionsListAdress: Array,
  optionsListTypes: Array,
  addressLine1: String,
  city: String,
  zip: Number,
});
</script>

<template>
  <div class="q-pa-md" style="max-width: 70%">
    <q-form class="q-gutter-md">
      <div>Buisness adress</div>
      <q-select
        dense
        size="sm"
        outlined
        v-model="model"
        :options="optionsListAdress"
        label="Outlined"
      />
      <div>Buisness adress</div>
      <q-select
        dense
        size="sm"
        outlined
        v-model="model"
        :options="optionsListTypes"
        label="Outlined"
      />
      <div>Address</div>
      <q-input dense outlined v-model="addressLine1" label="AddressLine1" />
      <!-- <q-input dense outlined v-model="addressLine2" label="AddressLine2" /> -->
      <q-input dense outlined v-model="city" label="City" />
      <q-input dense outlined v-model="zip" label="Zip code" type="number" />
    </q-form>
  </div>
</template>

<style scoped></style>
