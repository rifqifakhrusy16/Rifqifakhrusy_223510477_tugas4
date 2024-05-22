<template>
    <div class="shoe-list">
      <div v-for="shoe in shoes" :key="shoe.name" class="shoe-item">
        <img :src="shoe.imageUrl" :alt="shoe.name" class="shoe-image" />
        <h3>{{ shoe.name }}</h3>
        <p>Harga: Rp {{ formatPrice(shoe.price) }}</p>
        <p>Ukuran: {{ shoe.sizes.join(', ') }}</p>
        <button @click="selectShoe(shoe)">Pilih</button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { defineEmits } from 'vue'
  
  const emit = defineEmits(['shoeSelected'])
  
  const shoes = [
    { name: 'Sneakers', price: ' 500.000',  sizes: ['40', '41', '42'], selectedSize: '', imageUrl: 'https://i.pinimg.com/736x/16/a9/a4/16a9a4ee80092fde933b353cb064d48f.jpg' },
    { name: 'Boots', price: '700.000',  sizes: ['40', '41', '42'], selectedSize: '', imageUrl: 'https://i.pinimg.com/736x/04/df/ad/04dfad884f7646b80c9ea614b1376154.jpg' },
    { name: 'Sandals', price: ' 70.000',  sizes: ['40', '41', '42'], selectedSize: '', imageUrl: 'https://i.pinimg.com/564x/06/92/29/069229123cc444a9a025232ccab8eab3.jpg' },
    { name: 'Sneakers', price: ' 750.000', sizes: ['40', '41', '42'], selectedSize: '', imageUrl: 'https://i.pinimg.com/564x/fc/3a/80/fc3a801e44058d6a76e5129e3411d94c.jpg' },
    { name: 'Boots', price: ' 980.000',  sizes: ['40', '41', '42'], selectedSize: '', imageUrl: 'https://i.pinimg.com/564x/be/17/5a/be175a4c2e1684c4c1fdf0156c516278.jpg' },
    { name: 'Sandals', price: ' 400.000', sizes: ['40', '41', '42'], selectedSize: '', imageUrl: 'https://i.pinimg.com/736x/1d/39/fd/1d39fd4d223c7d43330c04d14a915884.jpg' },
    { name: 'Sneakers', price: ' 950.000',  sizes: ['40', '41', '42'], selectedSize: '', imageUrl: 'https://i.pinimg.com/564x/91/d8/f4/91d8f4bd99495f67da6fe4da37386bcf.jpg' },
    { name: 'Boots', price: ' 800.000', sizes: ['40', '41', '42'], selectedSize: '', imageUrl: 'https://i.pinimg.com/564x/e3/aa/97/e3aa97ac9eb5e3f5d54596acf95ea3bb.jpg' },
    { name: 'Sandals', price: ' 50.000', sizes: ['40', '41', '42'], selectedSize: '', imageUrl: 'https://i.pinimg.com/564x/95/60/5f/95605f97fcab45aee5b5270a95062f60.jpg' }
  ]
  
  
  const selectShoe = (shoe) => {
    emit('shoeSelected', shoe)
  }
  
  const formatPrice = (price) => {
    return price.toLocaleString('id-ID')
  }
  </script>
  
  <style scoped>
  .shoe-list {
    display: flex;
    flex-wrap: wrap;
  }
  
  .shoe-item {
    margin: 20px;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    text-align: center;
  }
  
  .shoe-image {
    width: 100px;
    height: 100px;
    object-fit: cover;
    margin-bottom: 10px;
  }
  </style>
  