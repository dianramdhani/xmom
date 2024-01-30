<template>
  <q-page>
    <q-form>
      <q-input label="Username" name="username" v-model="username" />
      <q-input label="Password" name="password" type="password" v-model="password" />
      <q-btn type="submit">Login</q-btn>
      <q-btn flat></q-btn>
    </q-form>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const username = ref('')
const password = ref('')
</script>
