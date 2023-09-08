<script setup>
import StepOneForm from 'src/components/StepOneForm.vue';
import StepTwoForm from 'src/components/StepTwoForm.vue';
import StepThreeForm from 'src/components/StepThreeForm.vue';
import { ref } from 'vue';

const step = ref(1);
</script>

<template>
  <div class="q-pa-md absolute-center">
    <q-stepper
      v-model="step"
      ref="stepper"
      color="primary"
      animated
      class="fixed-step-size"
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
        <component :is="StepTwoForm"></component>
      </q-step>

      <q-step
        :name="4"
        title="Overview"
        icon="create_new_folder"
        caption="description"
      >
        <component :is="StepThreeForm"></component>
      </q-step>

      <template v-slot:navigation>
        <q-stepper-navigation>
          <q-btn
            v-if="step > 1"
            flat
            color="primary"
            @click="$refs.stepper.previous()"
            label="Back"
            class="q-ml-sm"
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

<style lang="scss" scoped>
.fixed-step-size {
  width: 800px;
  min-height: 600px;
}
</style>
