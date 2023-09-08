<script setup lang="ts">
import { ref } from 'vue';

const props = defineProps({
  vat: {
    type: null,
    default: null,
  },
  industry: String,
  email: String,
  iban: {
    type: null,
    default: null,
  },
  optionsListIndustry: Array,
  Checkbox1: Boolean,
  Checkbox2: Boolean,
  Checkbox3: Boolean,
});
</script>
<template>
  <div class="q-pa-md" style="max-width: 70%">
    <q-form class="q-gutter-md">
      <div>VAT</div>
      <q-input dense outlined v-model="props.vat" label="VAT number" />

      <div>Indusrty</div>
      <q-select
        dense
        size="sm"
        outlined
        v-model="industry"
        :options="optionsListIndusrtry"
        label="Please select your industry"
      />

      <div>Organization website</div>
      <q-input dense outlined v-model="email" label="www.example.com" />
      <div>IBAN</div>
      <q-input
        dense
        outlined
        v-model="iban"
        label="IBAN"
        placeholder="Please enter your IBAN"
      />
      <div class="row">
        <q-checkbox v-model="Checkbox1" label="Label 1" />
        <q-checkbox v-model="Checkbox2" label="Label 2" />
        <q-checkbox v-model="Checkbox3" label="Label 3" />
      </div>
    </q-form>
  </div>
</template>

<style scoped></style>
