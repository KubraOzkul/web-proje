<template>
    <div class="component-three">
      <!-- Üstteki Başlık -->
      <div class="title-block">
        <h2>POPÜLER YAYINEVLERİ</h2>
      </div>
  
      <!-- Slider Alanı -->
      <div class="slider-container">
        <!-- Sol Ok -->
        <button class="slider-button left" @click="scrollLeft">
          <span>&lt;</span>
        </button>
  
        <!-- Görseller -->
        <div class="slider" ref="slider">
          <div
            v-for="(item, index) in items"
            :key="index"
            class="circle"
          >
            <img :src="item.image" :alt="item.name" />
          </div>
        </div>
  
        <!-- Sağ Ok -->
        <button class="slider-button right" @click="scrollRight">
          <span>&gt;</span>
        </button>
      </div>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { ref } from 'vue';
  
  // Görsel Verilerinin Tipini Tanımlıyoruz
  interface SliderItem {
    image: string;
    name: string;
  }
  
  // Görsel verileri
  const items = ref<SliderItem[]>([
    { image: '/items/marti-yayinlari-1-tr.jpg', name: 'Martı Yayınları' },
    { image: '/items/dokuz-yayinlari-3-tr.jpg', name: 'Dokuz Yayınları' },
    { image: '/items/domingo-yayinevi-5-tr.jpg', name: 'Domingo Yayınları' },
    { image: 'path_to_image4.jpg', name: 'Yayınevi 4' },
    { image: 'path_to_image5.jpg', name: 'Yayınevi 5' },
    { image: 'path_to_image6.jpg', name: 'Yayınevi 6' },
    { image: 'path_to_image7.jpg', name: 'Yayınevi 7' },
    { image: 'path_to_image8.jpg', name: 'Yayınevi 8' },
    { image: 'path_to_image9.jpg', name: 'Yayınevi 9' },
  ]);
  
  const slider = ref<HTMLElement | null>(null);
  
  // Kaydırma İşlemleri
  const scrollLeft = () => {
    if (slider.value) {
      slider.value.scrollBy({
        left: -150, // Sol yönde kaydırma miktarı
        behavior: 'smooth',
      });
    }
  };
  
  const scrollRight = () => {
    if (slider.value) {
      slider.value.scrollBy({
        left: 150, // Sağ yönde kaydırma miktarı
        behavior: 'smooth',
      });
    }
  };
  </script>
  
  <style scoped>
  /* Başlık Alanı */
  .title-block {
    text-align: center;
    margin-bottom: 8px;
  }
  
  .title-block h2 {
    box-sizing: border-box;
    font-size: 1rem;
    color: #58008E;
    font-weight: 700;
    line-height: 1.3;
    background-color: transparent;
    display: block;
    unicode-bidi: isolate;
    --custom-text-color1: #575756;
    padding: 10px 20px;
    border-radius: 5px;
    margin-block-start: 0.83em;
    margin-block-end: 0.83em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
  }
  
  /* Slider Alanı */
  .slider-container {
    position: relative;
    display: flex;
    align-items: center;
    width: 100%;
    overflow: hidden; /* Kaydırılabilir alan dışında kalan kısımları gizler */
  }
  
  .slider {
    display: flex;
    gap: 20px; /* Daireler arasındaki boşluk */
    overflow-x: auto;
    scroll-behavior: smooth;
    padding: 10px 0;
    width: calc(8 * 114.25px + 7 * 20px); /* 8 daire ve aralarındaki 7 boşluk */
  }

  .slider::-webkit-scrollbar {
  display: none;  /* Chrome, Safari, Opera için */
    }
  
  .circle {
    width: 114.25px;
    height: 114.25px;
    background-color: transparent;
    color: inherit;
    text-decoration: none;
    outline: 0;
    box-sizing: border-box;
    border: 4px solid orange;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }
  
  .circle img {
    width: 106.25px;
    height: 106.25px;
    border-radius: 50%;
    object-fit: cover;
  }
  
  /* Slider Butonları */
  .slider-button {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: white;
    border: 2px solid gray;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    z-index: 10;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
  
  .slider-button.left {
    left: 10px;
  }
  
  .slider-button.right {
    right: 10px;
  }
  
  .slider-button span {
    font-size: 18px;
    font-weight: bold;
    color: gray;
  }
  
  .slider-button:hover {
    background-color: lightgray;
  }
  </style>
  