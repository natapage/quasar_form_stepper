<script setup lang="ts">
import { inject } from 'vue';
import DataType from '../types/types';

const data = inject('data') as DataType;
</script>

<template>
  <div>Please check the information</div>
  <div v-for="item in Object.entries(data)" :key="item[0]">
    {{ item[0] }} : {{ item[1] }}
  </div>
</template>

<style scoped></style>
