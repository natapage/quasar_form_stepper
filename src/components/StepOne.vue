<script setup lang="ts">
import { optionsListTypes, optionsListAddress } from '../constants/constants';
import { inject } from 'vue';
import DataType from '../types/types';

const data = inject('data') as DataType;
</script>
<template>
  <div class="q-pa-md" style="max-width: 70%">
    <q-form class="q-gutter-md">
      <div>Buisness address</div>
      <q-select
        dense
        size="sm"
        outlined
        v-model="data.address"
        :options="optionsListAddress"
        label="Select an address"
        :rules="[
          (val) => (val && val.length > 0) || 'Please select an address',
        ]"
      />
      <div>Types</div>
      <q-select
        dense
        size="sm"
        outlined
        v-model="data.type"
        :options="optionsListTypes"
        label="Select a type"
        :rules="[(val) => (val && val.length > 0) || 'Please select a type']"
      />
      <div>Address</div>
      <q-input
        dense
        outlined
        v-model.trim="data.addressLine"
        label="Address"
        :rules="[(val) => (val && val.length > 0) || 'Please type an address']"
      />
      <q-input
        dense
        outlined
        v-model="data.city"
        label="City"
        :rules="[(val) => (val && val.length > 0) || 'Please type a city']"
      />
      <q-input
        dense
        outlined
        v-model.trim="data.zip"
        label="Zip code"
        type="number"
        :rules="[
          (val) =>
            (val && val.length === 6) || 'Please type a 6 digit zip code',
        ]"
      />
    </q-form>
  </div>
</template>

<style scoped></style>
