<template>
  <q-page>
    <q-card>
      <q-card-section class="text-h3">
        Login Page
      </q-card-section>
      <q-card-section>
        <q-input label="Username" v-model="username" />
        <q-input label="Password" type="password" v-model="passwrod" />
      </q-card-section>
      <q-card-actions>
        <q-btn icon="person" rounded color="primary">Login</q-btn>
        <q-btn icon="close" rounded color="primary" to="/">Cancel</q-btn>
      </q-card-actions>
    </q-card>
  </q-page>
</template>
<script lang="ts" setup>
import {ref} from 'vue';
const username = ref('');
const passwrod = ref('');
</script>
