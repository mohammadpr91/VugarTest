<template>
  <q-layout
    class="container window-height"
    view="hhh lpR fFf"
  >
    <q-header class="bg-white container">
      <q-toolbar>
        <q-toolbar-title class="container-body">
          <div class="row items-center justify-between q-py-xl">
            <div class="row items-center q-gutter-x-sm">
              <q-img
                :src="Vector"
                width="36px"
                height="36px"
              />
              <div class="text-h5 text-primary">
                MyLearning
              </div>
            </div>
            <div class="text-secondary text-subtitle1">
              <q-badge
                color="positive"
                rounded
              /> Əli M.
            </div>
          </div>
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <div class="container-body">
        <router-view />
      </div>
    </q-page-container>

    <div class="container bg-primary">
      <q-toolbar>
        <q-toolbar-title class="container-body">
          <div class="q-my-4xl">
            <div class="row items-center q-gutter-x-sm">
              <q-img
                :src="Vector"
                width="36px"
                height="36px"
              />
              <div class="text-h5 text-white">
                MyLearning
              </div>
            </div>
          </div>
          <div class="row items-center justify-between text-subtitle1">
            <div class="text-white">
              Bütün hüquqlar qorunur | © Prosper
            </div>
            <div class="link">
              Created by <a
                href="#"
                class="link"
                target="_blank"
              >
                Prosper
              </a>
            </div>
          </div>
        </q-toolbar-title>
      </q-toolbar>
    </div>
  </q-layout>
</template>

<script setup>
import Vector from 'assets/Vector.svg'
</script>

<style lang="sass" scoped>
.link
  color: #BAD6FF

</style>
