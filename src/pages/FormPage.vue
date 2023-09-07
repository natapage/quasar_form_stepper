<script setup>
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
        title="First step"
        icon="settings"
        :done="step > 1"
        caption="description"
      >
        <component :is="StepOneForm"></component>
      </q-step>

      <q-step
        :name="2"
        title="Second step"
        caption="description"
        icon="create_new_folder"
        :done="step > 2"
      >
      <component :is="StepTwoForm"></component>

      </q-step>

      <q-step
        :name="4"
        title="Third step"
        icon="add_comment"
        caption="description"
      >
      <component :is="StepThreeForm"></component>

      </q-step>

      <template v-slot:navigation>
        <q-stepper-navigation class="absolute-bottom-right q-ma-lg">
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
  width: 700px;
  height: 500px;
}
</style>
