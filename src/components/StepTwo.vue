<script setup lang="ts">
import { optionsListIndusrtry } from '../constants/constants';
import { inject } from 'vue';
import DataType from '../types/types';

const data = inject('data') as DataType;
</script>
<template>
  <div class="q-pa-md" style="max-width: 70%">
    <q-form class="q-gutter-md">
      <div>VAT</div>
      <q-input
        type="number"
        dense
        outlined
        v-model.trim="data.vat"
        label="VAT number"
        :rules="[
          (val) =>
            (val && val.length >= 8 && val.length <= 12) ||
            'Please type a 8-12 digits number',
        ]"
      />

      <div>Indusrty</div>
      <q-select
        dense
        size="sm"
        outlined
        v-model="data.industry"
        :options="optionsListIndusrtry"
        label="Please select your industry"
      />

      <div>Organization e-meil</div>
      <q-input
        dense
        outlined
        v-model.trim="data.email"
        label="e-mail"
        :rules="[
          (val) =>
            (val && val.length > 6 && val.includes('@') && val.includes('.')) ||
            'Please type an email',
        ]"
      />
      <div>IBAN</div>
      <q-input
        dense
        outlined
        v-model.trim="data.iban"
        label="IBAN"
        placeholder="Please enter your IBAN"
        :rules="[
          (val) => (val && val.length === 12) || 'Please type a 12 chars code',
        ]"
      />
      <div class="row">
        <q-checkbox v-model="data.checkbox1" label="Something 1" />
        <q-checkbox v-model="data.checkbox2" label="Something 2" />
        <q-checkbox v-model="data.checkbox3" label="Something 3" />
      </div>
    </q-form>
  </div>
</template>

<style scoped></style>
