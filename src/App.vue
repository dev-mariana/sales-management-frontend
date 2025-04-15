<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-dark">
      <q-toolbar>
        <q-toolbar-title class="text-green">Rosa Personalizados</q-toolbar-title>
        <q-tabs>
          <q-tab label="Produtos" />
          <q-tab label="Pedidos" />
          <q-tab label="Configurações" />
        </q-tabs>
        <q-btn flat round>
          <q-icon name="notifications" />
        </q-btn>
        <q-avatar>RB</q-avatar>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <q-page padding>
        <div class="row q-col-gutter-md">
          <div class="text-h6 col-12">
            Gerenciar Produtos
            <q-btn
              @click="showForm = true"
              color="green"
              label="Registrar Novo Produto"
              class="float-right"
              icon="add"
            />
          </div>

          <div class="col-12 col-md-6">
            <q-dialog v-model="showForm">
              <ProductForm />
            </q-dialog>
          </div>

          <!-- <div class="col-12 col-md-6">
            <ProductDetails :product="selectedProduct" />
          </div> -->

          <div class="col-12">
            <ProductList />
          </div>
        </div>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<style>
body {
  background: #1e1e1e;
  color: white;
}
</style>

<script setup lang="ts">
import { ref } from 'vue'
import ProductForm from './components/ProductForm.vue'
// import ProductDetails from './components/ProductDetails.vue'
import ProductList from './pages/ProductList.vue'

const showForm = ref(false)

// const selectedProduct = ref({
//   id: '12345',
//   name: 'Wireless Headphones',
//   size: 'Electronics',
//   price: 129.99,
//   stock: 45,
// })
</script>
