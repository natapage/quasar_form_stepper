<script setup>
import StepOne from '../components/StepOne.vue';
import StepTwo from '../components/StepTwo.vue';
import StepThree from '../components/StepThree.vue';
import StepFour from '../components/StepFour.vue';
import { stepsMap } from '../constants/constants';
import { ref, reactive } from 'vue';
import { provide } from 'vue';

const step = ref(1);

const initialFormState = {
  type: '',
  address: '',
  addressLine: '',
  city: '',
  zip: null,
  vat: null,
  industry: '',
  email: '',
  iban: null,
  checkbox1: false,
  checkbox2: false,
  checkbox3: false,
  name: null,
  phone: null,
  message: null,
  accept: false,
};

const data = reactive({ ...initialFormState });

const resetForm = () => {
  Object.assign(data, initialFormState);
  step.value = 1;
};

provide('data', data);
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
        <component :is="StepOne" />
      </q-step>

      <q-step
        :name="2"
        title="Bank details"
        caption="description"
        icon="create_new_folder"
        :done="step > 2"
      >
        <component :is="StepTwo" />
      </q-step>

      <q-step
        :name="3"
        title="Authentication"
        caption="description"
        icon="create_new_folder"
        :done="step > 3"
      >
        <component :is="StepThree" />
      </q-step>

      <q-step
        :name="4"
        title="Overview"
        icon="create_new_folder"
        caption="description"
      >
        <component :is="StepFour" />
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
            @click="() => (step < 4 ? $refs.stepper.next() : resetForm())"
            color="primary"
            :disable="
              stepsMap[step]?.some((el) => {
                if (step === 4) return true;
                return !data[el];
              })
            "
            :label="step === 4 ? 'Finish' : 'Continue'"
          />
        </q-stepper-navigation>
      </template>
    </q-stepper>
  </div>
</template>

<style lang="scss" scoped></style>
