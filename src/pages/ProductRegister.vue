<template>
  <div class="q-pa-md" style="max-width: 400px">
    <h2 class="text-h2">Registrar Produto</h2>

    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
      <q-input
        filled
        v-model="name"
        label="Nome *"
        hint="Name and surname"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Digite o nome']"
      />

      <q-input
        filled
        type="number"
        v-model="size"
        label="Tamanho *"
        lazy-rules
        :rules="[
          (val) => (val !== null && val !== '') || 'Digite o tamanho',
          (val) => (val > 0 && val < 42) || 'Digite um tamanho válido',
        ]"
      />

      <q-input
        filled
        type="number"
        v-model="price"
        label="Preço *"
        lazy-rules
        :rules="[
          (val) => (val !== null && val !== '') || 'Digite o preço',
          (val) => val > 0 || 'Digite um preço válido',
        ]"
      />

      <div>
        <q-btn label="Criar" type="submit" color="primary" />
      </div>
    </q-form>
  </div>
</template>

<script setup lang="ts">
import { useQuasar } from 'quasar'
import { ref } from 'vue'

const $q = useQuasar()

const name = ref(null)
const size = ref(null)
const price = ref(null)

const onSubmit = () => {
  if (name.value !== true || size.value !== true || price.value !== true) {
    $q.notify({
      color: 'red-5',
      textColor: 'white',
      icon: 'warning',
      message: 'Falha ao enviar',
    })
  } else {
    $q.notify({
      color: 'green-4',
      textColor: 'white',
      icon: 'cloud_done',
      message: 'Criado com sucesso',
    })
  }
}

// align form to center
// align title
// choose the colors
// do css for this page

const onReset = () => {
  name.value = null
  size.value = null
  price.value = null
}
</script>
