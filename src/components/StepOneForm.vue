<script setup lang="ts">
import { ref } from 'vue';

const model = ref(null);
const optionsListAdress = [
  'Option1',
  'Option2',
  'Option3',
  'Option4',
  'Option5',
];
const optionsListTypes = [
  'Option1',
  'Option2',
  'Option3',
  'Option4',
  'Option5',
];
const addressLine1 = ref('');
const addressLine2 = ref('');
const city = ref('');
const zip = ref(null);
</script>

<template>
  <div class="q-pa-md">
    <q-form class="q-gutter-md">
      <div>Buisness adress</div>
      <q-select
        size="sm"
        outlined
        v-model="model"
        :options="optionsListAdress"
        label="Outlined"
      />
      <div>Buisness adress</div>
      <q-select
        size="sm"
        outlined
        v-model="model"
        :options="optionsListTypes"
        label="Outlined"
      />
      <div>Address</div>
      <q-input outlined v-model="addressLine1" label="AddressLine1" />
      <q-input outlined v-model="addressLine2" label="AddressLine2" />
      <q-input outlined v-model="city" label="City" />
      <q-input outlined v-model="zip" label="Zip code" type="number" />
    </q-form>
  </div>
</template>

<style scoped></style>
