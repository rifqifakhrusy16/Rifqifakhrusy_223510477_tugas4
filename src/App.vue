<template>
  <div>
    <h2>Halaman Penjualan Sepatu</h2>
    <SlotComponent>
      <template #shoe>
        <ShoeComponent @shoeSelected="handleShoeSelection" />
      </template>
    </SlotComponent>
    <p v-if="selectedShoe">Sepatu yang dipilih: {{ selectedShoe.name }} ({{ selectedShoe.price }})</p>
    <Modal v-if="selectedShoe" :shoe="selectedShoe" @close="selectedShoe = null" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import SlotComponent from './components/SlotComponent.vue'
import ShoeComponent from './components/ShoeComponent.vue'
import Modal from './components/Modal.vue'

const selectedShoe = ref(null)

const handleShoeSelection = (shoe) => {
  selectedShoe.value = shoe
}
</script>

<style scoped>
/* Styling sesuai kebutuhan */
</style>
