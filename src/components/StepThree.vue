<script setup lang="ts">
import { inject } from 'vue';
import DataType from '../types/types';

const data = inject('data') as DataType;
</script>

<template>
  <div class="q-pa-md" style="max-width: 70%">
    <q-form class="q-gutter-md">
      <div>User info</div>
      <q-input
        dense
        outlined
        v-model.trim="data.name"
        label="Username"
        :rules="[(val) => (val && val.length > 0) || 'Please type something']"
      />

      <q-input
        dense
        outlined
        v-model.trim="data.phone"
        label="Phone number"
        hint="Your phone number"
        mask="+# (###) ### - ##-##"
        :rules="[(val) => (val && val.length > 19) || 'Invalid phone number']"
      />

      <q-input
        dense
        outlined
        type="textarea"
        autogrow
        label="Message"
        v-model.trim="data.message"
      />

      <q-toggle v-model="data.accept" label="I accept the license and terms" />
    </q-form>
  </div>
</template>

<style scoped></style>
