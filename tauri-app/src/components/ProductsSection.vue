<script setup>
import carData from '../data/carData.json';
import { useRouter } from 'vue-router';

// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue';

// Import Swiper styles
import 'swiper/css';

const router = useRouter();
const carDataHome = carData;
</script>

<template>
  <section id="urunler" class="flex w-full flex-wrap items-center justify-center gap-4 pt-12">
    <div class="w-full py-4 text-center">
      <h2 class="text-3xl font-bold">Ürünler</h2>
    </div>
    <div
      class="my-4 min-h-[32rem] w-80 max-w-sm overflow-hidden rounded-lg bg-white shadow-lg sm:w-auto"
      v-for="data in carDataHome.cars"
      :key="data.id"
    >
      <swiper :rewind="true" class="mySwiper">
        <swiper-slide v-for="imageCar in data.resimler" :key="imageCar">
          <img :src="imageCar" class="h-56 w-full object-cover object-center" alt="car image" />
        </swiper-slide>
      </swiper>
      <div class="px-6 py-4">
        <h2 class="text-xl font-bold text-gray-800">{{ data.isim }}</h2>
        <p class="py-2 text-lg text-gray-700">
          {{ data['kisa-aciklama'] }}
        </p>
        <div class="mt-4 flex w-full items-center justify-end text-gray-700">
          <button
            class="cursor-pointer rounded-lg bg-gray-800 px-4 py-4 text-sm text-white/90 shadow-md shadow-blue-400 transition-all duration-200 hover:text-white hover:shadow-md hover:shadow-blue-900"
            @click="router.push('/car/' + data.id)"
          >
            Detay gör
          </button>
        </div>
      </div>
    </div>
  </section>
</template>