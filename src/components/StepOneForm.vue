<template>
  <div class="q-pa-md">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
      <q-input
        filled
        v-model="name"
        label="Username"
        hint="Name and surname"
        :rules="[(val) => (val && val.length > 0) || 'Please type something']"
      />

      <q-input
        filled
        type="number"
        v-model="phone"
        label="E-mail"
        lazy-rules
        :rules="[
          (val) => (val !== null && val !== '') || 'Please type your age',
          (val) => (val > 0 && val < 100) || 'Please type a real age',
        ]"
      />
      <q-input
        filled
        type="textarea"
        v-model="age"
        label="Message"
        lazy-rules
        :rules="[]"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />
    </q-form>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.fixed-step-size {
  width: 700px;
  height: 500px;
}
</style>
