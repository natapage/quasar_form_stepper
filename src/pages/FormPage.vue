<script setup>
import { ref, reactive } from 'vue';
import {
  optionsListTypes,
  optionsListAddress,
  optionsListIndusrtry,
  stepsMap,
} from '../constants/constants';

const step = ref(1);

const data = reactive({
  type: '',
  address: '',
  addressLine: '',
  city: '',
  zip: null,
  vat: ref(null),
  industry: '',
  email: '',
  iban: null,
  checkbox1: ref(false),
  checkbox2: ref(false),
  checkbox3: ref(false),
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
        <div class="q-pa-md" style="max-width: 70%">
          <q-form class="q-gutter-md">
            <div>Buisness adress</div>
            <q-select
              dense
              size="sm"
              outlined
              v-model="data.address"
              :options="optionsListAddress"
              label="Select an address"
              :rules="[
                (val) => (val && val.length > 0) || 'Please select an address',
              ]"
            />

            <div>Types</div>
            <q-select
              dense
              size="sm"
              outlined
              v-model="data.type"
              :options="optionsListTypes"
              label="Select a type"
              :rules="[
                (val) => (val && val.length > 0) || 'Please select a type',
              ]"
            />

            <div>Address</div>
            <q-input
              dense
              outlined
              v-model.trim="data.addressLine"
              label="Address"
              :rules="[
                (val) => (val && val.length > 0) || 'Please type an address',
              ]"
            />
            <q-input
              dense
              outlined
              v-model="data.city"
              label="City"
              :rules="[
                (val) => (val && val.length > 0) || 'Please type a city',
              ]"
            />
            <q-input
              dense
              outlined
              v-model.trim="data.zip"
              label="Zip code"
              type="number"
              :rules="[
                (val) =>
                  (val && val.length === 6) || 'Please type a 6 digit zip code',
              ]"
            />
          </q-form>
        </div>
      </q-step>

      <q-step
        :name="2"
        title="Bank details"
        caption="description"
        icon="create_new_folder"
        :done="step > 2"
      >
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
                  (val &&
                    val.length > 6 &&
                    val.includes('@') &&
                    val.includes('.')) ||
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
                (val) =>
                  (val && val.length === 12) || 'Please type a 12 chars code',
              ]"
            />
            <div class="row">
              <q-checkbox v-model="data.checkbox1" label="Something 1" />
              <q-checkbox v-model="data.checkbox2" label="Something 2" />
              <q-checkbox v-model="data.checkbox3" label="Something 3" />
            </div>
          </q-form>
        </div>
      </q-step>

      <q-step
        :name="3"
        title="Authentication"
        caption="description"
        icon="create_new_folder"
        :done="step > 3"
      >
        <div class="q-pa-md" style="max-width: 70%">
          <q-form class="q-gutter-md">
            <div>User info</div>
            <q-input
              dense
              outlined
              v-model.trim="data.name"
              label="Username"
              :rules="[
                (val) => (val && val.length > 0) || 'Please type something',
              ]"
            />

            <q-input
              dense
              outlined
              v-model.trim="data.phone"
              label="Phone number"
              hint="Your phone number"
              :rules="[
                (val) =>
                  /^((8|\+7)[\- ]?)?(\(?\d{3}\)?[\- ]?)?[\d\- ]{7,10}$/.test(
                    val
                  ) || 'Invalid phone number',
              ]"
            />

            <q-input
              dense
              outlined
              type="textarea"
              autogrow
              label="Message"
              v-model.trim="data.message"
            />

            <q-toggle
              v-model="data.accept"
              label="I accept the license and terms"
            />
          </q-form>
        </div>
      </q-step>

      <q-step
        :name="4"
        title="Overview"
        icon="create_new_folder"
        caption="description"
      >
        <div>Please check the information</div>
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
