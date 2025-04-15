<template>
  <q-card flat bordered class="bg-dark" style="width: 700px; max-width: 80vw">
    <q-card-section>
      <div class="text-h6 text-green">Registrar Novo Produto</div>
    </q-card-section>

    <q-card-section>
      <q-form @submit="saveProduct">
        <div class="q-gutter-y-md">
          <q-input v-model="productName" label="Nome do Produto" dark filled />

          <q-select
            v-model="productCategory"
            label="Tamanho"
            :options="['37/38', '38/39', '39/40']"
            dark
            filled
          />

          <q-input v-model="productPrice" label="Preço ($)" type="number" dark filled />

          <q-input
            v-model="stockQuantity"
            label="Quantidade em Estoque"
            type="number"
            dark
            filled
          />

          <div class="text-right">
            <q-btn
              v-close-popup
              label="Cancelar"
              type="reset"
              color="red"
              class="q-mr-lg"
              style="width: 150px"
            />
            <q-btn label="Salvar Produto" type="submit" color="primary" style="width: 150px" />
          </div>
        </div>
      </q-form>
    </q-card-section>
  </q-card>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const productName = ref('')
const productCategory = ref('37/38')
const productPrice = ref('')
const stockQuantity = ref('')

const saveProduct = () => {
  // Handle save logic
}
</script>
