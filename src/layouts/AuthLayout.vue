<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toggle v-model="darkModeSwitch" aria-label="dark mode switch" class="toggle" />
        <q-select class="language-selector" :options="languageOptions" v-model="languageValue" map-options />
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const darkModeSwitch = ref(false)
const languageOptions = [
  {
    label: 'IND',
    value: 'id'
  },
  {
    label: 'ENG',
    value: 'en'
  }
]
const languageValue = ref('id')
</script>

<style scoped lang="scss">
.language-selector {
  background-color: #fff;
}
</style>

<style lang="scss">
.toggle {
  transform: rotate(90deg);
  $component: ".q-toggle";
  $dimension: (
    width: 34px,
    height: 18px,
    thumb-size: 14px,
  );


&:not(.disabled):hover #{$component}__thumb:before {
  transform: scale3d(1.5, 1.5, 1) !important;
}

#{$component} {
  &__inner {
    width: map-get($dimension, width);
    height: map-get($dimension, height);
    min-width: unset;
    padding: 0;

    &--truthy {
      #{$component}__thumb {
        left: calc(100% - map-get($dimension, thumb-size) - 2px);
      }

      #{$component}__track {
        opacity: 1;
      }
    }
  }

  &__track {
    width: 100%;
    height: 100%;
    background-color: unset;
    outline: 2px solid #FFC202;
    border-radius: calc(map-get($dimension, height) / 2);
    transition: opacity 0.22s cubic-bezier(0.4, 0, 0.2, 1);
  }

  &__thumb {
    top: 50%;
    left: 2px;
    transform: translateY(-50%);
    width: map-get($dimension, thumb-size);
    height: map-get($dimension, thumb-size);

    &::after {
      background: linear-gradient(16deg, #DD5D00 -9.02%, #FFC202 87.77%);
      box-shadow: 0px 5px 10px 0px rgba(222, 200, 4, 0.40);
    }
  }
}
}
</style>
