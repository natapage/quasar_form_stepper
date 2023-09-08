<script setup lang="ts">
import { useQuasar } from 'quasar';
import { ref } from 'vue';

// const $q = useQuasar();

const name = ref(null);
const phone = ref(null);
const message = ref(null);
const accept = ref(false);

// function onSubmit() {
//   if (accept.value !== true) {
//     $q.notify({
//       color: 'red-5',
//       textColor: 'white',
//       icon: 'warning',
//       message: 'You need to accept the license and terms first',
//     });
//   } else {
//     $q.notify({
//       color: 'green-4',
//       textColor: 'white',
//       icon: 'cloud_done',
//       message: 'Submitted',
//     });
//   }
// }

// function onReset() {
//   name.value = null;
//   phone.value = null;
//   accept.value = false;
// }
</script>
<template>
  <div class="q-pa-md">
    <q-form class="q-gutter-md">
      <q-input
        filled
        v-model.trim="name"
        hint="Name and surname"
        label="Username"
        :rules="[(val) => (val && val.length > 0) || 'Please type something']"
      />

      <q-input
        filled
        v-model.trim="phone"
        label="Phone number"
        hint="Your phone number"
        :rules="[
          (val) =>
            /^((8|\+7)[\- ]?)?(\(?\d{3}\)?[\- ]?)?[\d\- ]{7,10}$/.test(val) ||
            'Invalid phone number',
        ]"
      />

      <q-input
        v-model.trim="message"
        filled
        type="textarea"
        hint="Message for order pickers"
        autogrow
        label="Message"
        :rules="[(val) => val.length <= 550 || 'Message is too long']"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />
    </q-form>
  </div>
</template>

<style scoped></style>
