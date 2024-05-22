<template>
  <div class="modal-overlay" @click="closeModal">
    <div class="modal-content" @click.stop>
      <h3>Detail Sepatu</h3>
      <img :src="shoe.imageUrl" :alt="shoe.name" class="shoe-image" />
      <p>Nama: {{ shoe.name }}</p>
      <p>Harga: Rp {{ formatPrice(shoe.price) }}</p>
      <p>Ukuran:</p>
      <select v-model="selectedSize">
        <option v-for="size in shoe.sizes" :key="size" :value="size">{{ size }}</option>
      </select>
      <p>Jumlah:</p>
      <input type="number" v-model.number="quantity" min="1" />
      <p>Total Harga: Rp {{ formatPrice(totalPrice) }}</p>
      <button @click="buyShoe">Beli</button>
      <button @click="closeModal">Tutup</button>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, defineProps, defineEmits } from 'vue'

const props = defineProps({
  shoe: Object
})

const emit = defineEmits(['close'])

const selectedSize = ref(props.shoe.sizes[0])
const quantity = ref(1)

const totalPrice = ref(props.shoe.price)

watch([quantity, () => props.shoe.price], () => {
  totalPrice.value = props.shoe.price * quantity.value
})

const formatPrice = (price) => {
  return price.toLocaleString('id-ID')
}

const closeModal = () => {
  emit('close')
}

const buyShoe = () => {
  alert(`Anda telah membeli sepatu ${props.shoe.name} ukuran ${selectedSize.value} dengan jumlah ${quantity.value} dengan total harga Rp ${formatPrice(totalPrice.value)}`)
  closeModal()
}
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal-content {
  background: white;
  color: black;
  padding: 20px;
  border-radius: 10px;
  text-align: center;
  position: relative;
}

.shoe-image {
  width: 150px;
  height: 150px;
  object-fit: cover;
  margin-bottom: 10px;
}

button {
  margin: 5px;
  padding: 10px 20px;
  border: none;
  background: #007bff;
  color: white;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background: #0056b3;
}
</style>
