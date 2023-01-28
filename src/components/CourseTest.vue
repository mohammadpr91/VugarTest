<template>
  <div class="q-col-gutter-y-xl">
    <div class="q-gutter-x-md">
      <q-btn
        no-caps
        :icon="outlinedCollectionsBookmark"
        label="Təlimə aid materiallar"
        class="border-radius-6"
        color="positive"
        padding="10px 32px"
        unelevated
      />
      <q-btn
        no-caps
        :icon="outlinedRule"
        label="Testlər"
        color="secondary"
        class="border-radius-6"
        padding="10px 32px"
        unelevated
      />
    </div>
    <div class="text-h5 text-secondary">
      {{ data?.title }}
    </div>
    <div class="q-col-gutter-y-md">
      <div
        v-for="(option, index) in data?.options"
        :key="index"
      >
        <q-card
          flat
          bordered
          :class="['border-radius-6 cursor-pointer', option === optionSelected && 'text-white bg-primary']"
          @click="optionSelected = option"
        >
          <q-card-section class="q-px-2xl q-py-lg">
            {{ option }}
          </q-card-section>
        </q-card>
      </div>
    </div>
    <div class="row justify-between items-center">
      <q-btn
        label="Əvvəlki sual"
        outline
        class="border-radius-6"
        padding="10px 32px"
        :icon="roundWest"
        no-caps
        text-color="grey-1"
        unelevated
      />
      <q-btn
        label="Növbəti sual"
        class="border-radius-6"
        padding="10px 32px"
        no-caps
        :icon-right="roundEast"
        color="positive"
        unelevated
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

import { roundEast, roundWest } from '@quasar/extras/material-icons-round'
import { outlinedRule, outlinedCollectionsBookmark } from '@quasar/extras/material-icons-outlined'

defineProps({
  data: {
    type: Object,
    default: () => {}
  }
})

const optionSelected = ref(null)
</script>
