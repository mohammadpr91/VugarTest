<template>
  <div>
    <q-list
      bordered
      class="expansion-width"
    >
      <q-expansion-item
        v-model="expanded"
        expand-separator
        :header-class="['q-py-lg q-px-xl text-h6', (expanded || checkId) ? 'bg-primary text-white' : 'bg-grey-3']"
        hide-expand-icon
      >
        <template #header>
          <div class="row q-col-gutter-x-xs justify-between fit ">
            <div :class="['col-auto',(expanded|| checkId) ? 'text-white': 'text-secondary']">
              {{ data.title }}
            </div>
            <div :class="['col',(expanded|| checkId) ? 'text-white': 'text-primary']">
              {{ data.subtitle }}
            </div>
            <div class="col-auto items-center">
              <q-icon
                :name="(expanded|| checkId)?roundArrowDropUp:roundArrowDropDown"
                size="30px"
                :class="(expanded|| checkId) ? 'text-white': 'text-secondary'"
              />
            </div>
          </div>
        </template>
        <q-list separator>
          <q-item
            v-for="(sch, index) in data.schedule"
            :key="index"
            clickable
            active-class="bg-grey-4"
            :active="sch.title === selected.title"
            @click="emit('update:selected', {...sch, part: data.title, subtitle:data.subtitle, id: data.id })"
          >
            <q-item-label class="q-py-sm q-px-md">
              <div class="q-col-gutter-y-xs">
                <div :class="['text-subtitle1', sch.title === selected.title && 'text-accent']">
                  {{ sch.title }}
                </div>
                <div class="row items-center q-gutter-x-sm">
                  <q-chip
                    :label="sch.type"
                    text-color="secondary"
                    :class="sch.title === selected.title && 'bg-white'"
                  />

                  <q-icon
                    size="20px"
                    color="grey-5"
                    :name="roundWatchLater"
                  />
                  <div class="text-secondary">
                    {{ sch.time }}
                  </div>
                </div>
              </div>
            </q-item-label>
          </q-item>
        </q-list>
      </q-expansion-item>
    </q-list>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue'

import { roundArrowDropDown, roundArrowDropUp, roundWatchLater } from '@quasar/extras/material-icons-round'

const props = defineProps({
  data: {
    type: Object,
    default: () => {}
  },
  selected: {
    type: Object,
    default: () => {}
  }
})

const emit = defineEmits(['update:selected'])

const expanded = ref(props.data.id === props.selected.id)

const checkId = computed(() => props.data.id === props.selected.id)

</script>

<style lang="sass" scoped>
.expansion-width
  width: 100%
  max-width:487px

@media (max-width: $breakpoint-sm)
  .expansion-width
    max-width:100%

</style>
