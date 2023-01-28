<template>
  <q-page :class="['q-py-lg',responsive && 'q-pa-md']">
    <div :class="['q-col-gutter-y-lg text-secondary', responsive && 'q-mb-md']">
      <div>
        <q-btn
          flat
          dense
          class="q-pl-none"
          label="Geri"
          :icon="outlinedArrowLeft"
          color="secondary"
          no-caps
        />
      </div>
      <div class="text-subtitle2">
        {{ courseSelected.part }} {{ courseSelected.subtitle }}
      </div>
      <div class="text-h6">
        {{ courseSelected.title }}
      </div>
    </div>

    <div class="row items-center justify-end q-gutter-x-sm">
      <q-btn
        :icon="outlinedLeaderboard"
        label="Dərs cədvəli və nəticələriniz"
        outline
        class="border-radius-6"
        padding="10px 32px"
        no-caps
        text-color="grey-1"
      />
      <q-btn
        :icon="roundVisibilityOff"
        outline
        class="border-radius-6 bg-grey-2"
        padding="10px 13px"
        no-caps
        text-color="grey-1"
      />
    </div>
    <div :class="['row q-mt-xs q-mb-12xl', responsive && 'q-col-gutter-x-md' ]">
      <play-course
        :class="['col-sm-6 col-xs-12', responsive && 'q-mb-md']"
        :data="courseSelected"
      />
      <div class="col-sm-6 col-xs-12 q-col-gutter-y-md">
        <course-schedule
          v-for="(item, index) in schdules"
          :key="index"
          v-model:selected="courseSelected"
          :data="item"
          class="column items-end"
        />
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { computed, defineAsyncComponent, ref } from 'vue'
import { useQuasar } from 'quasar'

import { roundVisibilityOff } from '@quasar/extras/material-icons-round'
import { outlinedArrowLeft, outlinedLeaderboard } from '@quasar/extras/material-icons-outlined'

const PlayCourse = defineAsyncComponent(() => import('components/PlayCourse.vue'))
const CourseSchedule = defineAsyncComponent(() => import('components/CourseSchedule.vue'))

const schdules = [
  {
    title: 'Bölmə 1:',
    subtitle: 'Giriş',
    id: 1,
    schedule: [
      {
        title: '1. Kursla tanışlıq',
        time: '12 aprel, 18:00-dək',
        type: 'Video dərs',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə1',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '2. Dizayn proqramları ilə tanışlıq',
        time: '12 aprel, 18:00-20:00',
        type: 'Canlı dərs',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə2',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '3. Dizaynın əsasları üzrə aralıq imtahanı',
        time: '12 aprel, 20:00 - 13 aprel, 17:30',
        type: 'Aralıq imtahan',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə3',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '4. Dizaynın əsasları üzrə oxu materialı',
        time: '13 aprel, 18:00-dək',
        type: 'Oxu materialı',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə4',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      }
    ]
  },
  {
    title: 'Bölmə 2:',
    subtitle: 'Dizaynın əsasları',
    id: 2,
    schedule: [
      {
        title: '1. Kursla tanışlıq',
        time: '12 aprel, 18:00-dək',
        type: 'Video dərs',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə5',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '2. Dizayn proqramları ilə tanışlıq',
        time: '12 aprel, 18:00-20:00',
        type: 'Canlı dərs',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə6',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '3. Dizaynın əsasları üzrə aralıq imtahanı',
        time: '12 aprel, 20:00 - 13 aprel, 17:30',
        type: 'Aralıq imtahan',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə7',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '4. Dizaynın əsasları üzrə oxu materialı',
        time: '13 aprel, 18:00-dək',
        type: 'Oxu materialı',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə8',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      }
    ]
  },
  {
    title: 'Bölmə 3:',
    subtitle: 'Figmadan istifadə',
    id: 3,
    schedule: [
      {
        title: '1. Abobe Photoshop-da işləmə üzrə praktiki məşğələ',
        time: '20 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə9',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '2. Abobe İllustrator-da işləmə üzrə praktiki məşğələ',
        time: '21 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə10',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '3. Figma-da səhifənin hazırlanması',
        time: '22 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə11',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '4. Çapa materialların hazırlığı',
        time: '23 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə12',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      }
    ]
  },
  {
    title: 'Bölmə 4:',
    subtitle: 'Bravo marketdə 4 günlük təcrübə məşğələsi',
    id: 4,
    schedule: [
      {
        title: '1. Abobe Photoshop-da işləmə üzrə praktiki məşğələ',
        time: '20 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə13',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '2. Abobe İllustrator-da işləmə üzrə praktiki məşğələ',
        time: '21 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə14',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '3. Figma-da səhifənin hazırlanması',
        time: '22 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə15',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '4. Çapa materialların hazırlığı',
        time: '23 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə16',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      }
    ]
  },
  {
    title: 'Bölmə 5:',
    subtitle: 'İmtahan',
    id: 5,
    schedule: [
      {
        title: '1. Abobe Photoshop-da işləmə üzrə praktiki məşğələ',
        time: '20 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə17',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '2. Abobe İllustrator-da işləmə üzrə praktiki məşğələ',
        time: '21 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə18',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '3. Figma-da səhifənin hazırlanması',
        time: '22 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə19',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      },
      {
        title: '4. Çapa materialların hazırlığı',
        time: '23 aprel, 18:00-20:00',
        type: 'Təcrübə',
        video: '',
        descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
        test: {
          title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
          options: [
            'a) Müəyyən etmə20',
            'b) Dizayn vermə',
            'c) Dəyişmə',
            'd) Araşdırma'
          ]
        }
      }
    ]
  }
]

const $q = useQuasar()

const responsive = computed(() => $q.screen.name !== 'lg')

const courseSelected = ref({
  id: 1,
  descriptions: 'Salam, hörmətli təlim iştirakçısı. Kursa tanışlıq videosuna baxmağınız xahiş olunur.',
  part: 'Bölmə 1:',
  subtitle: 'Giriş',
  test: {
    title: 'Müştərini və layihəni başa düşmək üçün dizayner_______ mərhələsini başlamalıdır',
    options: [
      'a) Müəyyən etmə1',
      'b) Dizayn vermə',
      'c) Dəyişmə',
      'd) Araşdırma'
    ]
  },
  time: '12 aprel, 18:00-dək',
  title: '1. Kursla tanışlıq',
  type: 'Video dərs',
  video: ''

})

</script>
