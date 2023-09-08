<script setup lang="ts">
import { ref } from 'vue';

// const date = ref('2019/02/01');
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
    </q-form>
  </div>
</template>

<style scoped></style>
