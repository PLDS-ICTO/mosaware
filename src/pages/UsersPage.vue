<template>
  <q-page>
    <div class="q-pa-md q-gutter-sm">
      <q-btn label="Add User" color="primary" @click="prompt = true" />
      <q-dialog v-model="prompt" persistent>
        <q-card style="min-width: 350px">
          <q-card-section>
            <div class="text-h6">Add Account</div>
          </q-card-section>

          <q-card-section class="q-pt-none">
            <q-input
              dense
              label="Last name"
              v-model="lname"
              autofocus
              @keyup.enter="prompt = false"
            />
          </q-card-section>

          <q-card-section class="q-pt-none">
            <q-input
              dense
              label="First name"
              v-model="fname"
              autofocus
              @keyup.enter="prompt = false"
            />
          </q-card-section>
          <q-card-section class="q-pt-none">
            <q-input
              dense
              label="username"
              v-model="username"
              autofocus
              @keyup.enter="prompt = false"
            />
          </q-card-section>
          <q-card-actions align="right" class="text-primary">
            <q-btn flat label="Cancel" v-close-popup />
            <q-btn flat label="Add" @click="addAccValue" v-close-popup />
          </q-card-actions>
        </q-card>
      </q-dialog>
    </div>

    <q-card class="q-pa-md">
      <q-table
        title="Accounts"
        :rows="rows"
        :grid="$q.screen.lt.md"
        :columns="columns"
        row-key="username"
      />
    </q-card>
  </q-page>
</template>
<script lang="ts" setup>
import { ref } from 'vue';
import { QTable } from 'quasar';

const prompt = ref(false);
var lname = ref('');
var fname = ref('');
var username = ref('');

const columns = ref<QTable['columns']>([
  {
    name: 'username',
    required: true,
    label: 'username',
    align: 'left',
    field: (row) => row.username,
    format: (val) => `${val}`,
    sortable: true,
  },
  {
    name: 'last_name',
    align: 'center',
    label: 'Last Name',
    field: 'last_name',
    sortable: true,
  },
  {
    name: 'first_name',
    label: 'First Name',
    field: 'first_name',
    sortable: true,
  },
]);

interface Row {
  last_name: string;
  first_name: string;
  username: string;
}

const rows = ref<Row[]>([]);

function addAccValue() {
  rows.value.push({
    last_name: lname.value,
    first_name: fname.value,
    username: username.value,
  });
  lname.value = '';
  fname.value = '';
  username.value = '';
}
</script>
