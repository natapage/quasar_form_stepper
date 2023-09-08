<script setup>
import StepOneForm from 'src/components/StepOneForm.vue';
import StepTwoForm from 'src/components/StepTwoForm.vue';
import StepThreeForm from 'src/components/StepThreeForm.vue';
import StepFourForm from 'src/components/StepFourForm.vue';

import { ref, reactive } from 'vue';

const step = ref(1);

const formData = reactive({
  model: '',
  optionsListAdress: ['Option1', 'Option2', 'Option3', 'Option4', 'Option5'],
  optionsListTypes: ['Option1', 'Option2', 'Option3', 'Option4', 'Option5'],
  addressLine1: '',
  city: '',
  zip: null,
  vat: ref(null),
  industry: '',
  email: '',
  iban: null,
  optionsListIndusrtry: [
    'Industry1',
    'Industry2',
    'Industry3',
    'Industry4',
    'Industry5',
  ],
  Checkbox1: ref(false),
  Checkbox2: ref(false),
  Checkbox3: ref(false),
  name: ref(null),
  phone: ref(null),
  message: ref(null),
  accept: ref(false),
});
</script>

<template>
  <div class="q-pa-md absolute-center">
    <q-stepper
      v-model="step"
      ref="stepper"
      color="primary"
      animated
      style="width: 800px; min-height: 600px"
    >
      <q-step
        :name="1"
        title="Business structure"
        caption="description"
        icon="settings"
        :done="step > 1"
      >
        <component :is="StepOneForm"></component>
      </q-step>

      <q-step
        :name="2"
        title="Bank details"
        caption="description"
        icon="create_new_folder"
        :done="step > 2"
      >
        <component :is="StepTwoForm"></component>
      </q-step>

      <q-step
        :name="3"
        title="Authentication"
        caption="description"
        icon="create_new_folder"
        :done="step > 3"
      >
        <component :is="StepThreeForm"></component>
      </q-step>

      <q-step
        :name="4"
        title="Overview"
        icon="create_new_folder"
        caption="description"
      >
        <component :is="StepFourForm"></component>
      </q-step>

      <template v-slot:navigation>
        <q-stepper-navigation class="absolute-bottom-right q-ma-md">
          <q-btn
            v-if="step > 1"
            flat
            color="primary"
            @click="$refs.stepper.previous()"
            label="Back"
            class="q-mr-sm"
          />
          <q-btn
            @click="$refs.stepper.next()"
            color="primary"
            :label="step === 4 ? 'Finish' : 'Continue'"
          />
        </q-stepper-navigation>
      </template>
    </q-stepper>
  </div>
</template>

<style lang="scss" scoped></style>
