<template>
  <div class="q-col-gutter-y-lg">
    <div>
      <q-card
        flat
        class="border-radius-6"
        bordered
      >
        <q-card-section>
          <div class="text-center text-primary text-subtitle1">
            Dərsi bitirməyiniz üçün son tarix {{ data.time }}
          </div>
        </q-card-section>
      </q-card>
    </div>
    <div>
      <video
        :src="data.video"
        class="bg-grey-1 fit rounded-borders-8"
        muted
        width="587px"
        height="331px"
        preload="metadata"
        loading="lazy"
        controls
        playsinline="false"
      />
    </div>
    <div class="text-secondary text-subtitle1">
      {{ data.descriptions }}
    </div>
    <course-test :data="data.test" />
  </div>
</template>

<script setup>
import { defineAsyncComponent } from 'vue'

defineProps({
  data: {
    type: Object,
    default: () => {}
  }
})

const CourseTest = defineAsyncComponent(() => import('components/CourseTest.vue'))
</script>
