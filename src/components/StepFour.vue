<script setup lang="ts">
import { inject } from 'vue';
import DataType from '../types/types';

const data = inject('data') as DataType;
</script>

<template>
  <div class="text-weight-bold">Please check the information</div>
  <div class="q-mt-lg" style="max-height: 350px">
    <q-list bordered separator>
      <q-item v-ripple v-for="item in Object.entries(data)" :key="item[0]">
        <q-item-section>
          <q-item-label>{{ item[0] }}</q-item-label>
          <q-item-label> {{ item[1] }} </q-item-label>
        </q-item-section>
      </q-item>
    </q-list>
  </div>
</template>

<style scoped></style>
