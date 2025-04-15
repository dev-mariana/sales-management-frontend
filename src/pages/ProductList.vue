<template>
  <q-card flat bordered class="bg-dark">
    <q-card-section>
      <div class="text-h6 text-green">Lista de Produtos</div>
      <div class="row items-center q-gutter-x-sm">
        <q-input dark filled placeholder="Procurar produtos..." class="col">
          <template v-slot:prepend>
            <q-icon name="search" />
          </template>
        </q-input>
        <q-btn flat round icon="filter_list" />
        <q-btn flat round icon="view_module" />
      </div>
    </q-card-section>

    <q-card-section>
      <q-table
        :rows="products"
        :columns="[
          { name: 'name', label: 'NOME', field: 'name', align: 'left' },
          { name: 'size', label: 'TAMANHO', field: 'size', align: 'left' },
          {
            name: 'price',
            label: 'PREÇO',
            field: 'price',
            format: (val) => `$${val}`,
            align: 'left',
          },
          { name: 'stock', label: 'ESTOQUE', field: 'stock', align: 'left' },
          { name: 'actions', label: 'ACTIONS', field: 'actions', align: 'left' },
        ]"
        dark
        flat
        bordered
      >
        <template v-slot:body-cell-stock="props">
          <q-td :props="props">
            <q-chip
              :color="props.row.stock > 0 ? 'green' : 'red'"
              text-color="white"
              :label="props.row.stock > 0 ? `In Stock (${props.row.stock})` : 'Out of Stock'"
              size="sm"
            />
          </q-td>
        </template>

        <template v-slot:body-cell-actions="props">
          <q-td :props="props">
            <q-btn flat round size="sm" color="blue" icon="visibility" />
            <q-btn flat round size="sm" color="amber" icon="edit" />
            <q-btn flat round size="sm" color="red" icon="delete" />
          </q-td>
        </template>
      </q-table>

      <div class="row justify-between items-center q-mt-md">
        <div>Showing 1 to 5 of 25 entries</div>
        <q-pagination
          v-model="currentPage"
          :max="3"
          direction-links
          boundary-links
          color="green"
          :model-value="1"
        />
      </div>
    </q-card-section>
  </q-card>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const currentPage = ref(1)

const products = ref([
  { name: 'Wireless Headphones 0', size: '37/38', price: 89.99, stock: 45 },
  { name: 'Wireless Headphones 1', size: '34/35', price: 109.99, stock: 0 },
  { name: 'Wireless Headphones 2', size: '39/40', price: 119.99, stock: 35 },
  { name: 'Wireless Headphones 3', size: '35/36', price: 129.99, stock: 0 },
  { name: 'Wireless Headphones 4', size: '40/41', price: 139.99, stock: 25 },
])
</script>
