<template>
  <div class="popup-overlay">
    <div class="popup-container">
      <!-- Başlık -->
      <div class="popup-header">
        <h3>Ürün Başarıyla Sepete Eklendi</h3>
        <span class="success-icon">✔</span>
      </div>

      <!-- Ürün Bilgisi -->
      <div class="popup-content">
        <div class="product-wrapper">
          <img
            src="https://www.kitapsepeti.com/siyam-545196-37-K.jpg"
            alt="Siyam Kitap Resmi"
            class="product-image"
          />
          <div class="product-info-wrapper">
            <div class="product-info">
              <p class="product-brand fw-bold">Epsilon Yayınevi</p>
              <p class="product-title">Siyam IV Mare</p>
              <div class="price-wrapper">
                <del class="text-gray text-delete price-old">305,00 TL</del>
                <div class="current-price fw-black text-primary">252,80 TL</div>
              </div>
              <div class="count-info text-black">1 Adet</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Düğmeler -->
      <div class="popup-buttons">
        <button @click="goToCart" class="btn btn-primary">SEPETE GİT</button>
        <button @click="proceedToCheckout" class="btn btn-secondary">SATIN AL</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Genel Popup Stil */
.popup-overlay {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  pointer-events: none; /* Arka plan tıklamalarını pasif yapar */
}

.popup-container {
  background: #fff;
  width: 570px; /* Ana container genişliği */
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  pointer-events: auto
}

/* Başlık */
.popup-header {
  display: flex;
  justify-content: flex-start; /* Elemanları sola hizala */
  align-items: center;
  margin-bottom: 16px;
}

.popup-header h3 {
  font-size: 18px;
  font-weight: bold;
  margin-right: 8px; /* Başlık ile tik arasına biraz mesafe ekleyelim */
}

.success-icon {
  color: #43B54C;
  font-size: 20px;
}

/* İçerik */
.popup-content {
  border-top: 1px solid #ddd;
  padding-top: 16px;
}

.product-wrapper {
  display: flex;
  align-items: center;
  gap: 16px; /* Resim ve yazı arasındaki mesafeyi ayarladım */
  padding: 8px; /* İç boşlukları biraz daha arttırdım */
  border: 1px solid #ddd; /* Kitap resmi ve yazılar için çerçeve */
  border-radius: 4px;
}

.product-image {
  width: 86px;
  height: 129px;
  border-radius: 4px;
  object-fit: cover;
}

/* Yazılar için wrapper */
.product-info-wrapper {
  display: flex;
  flex-direction: column;
  align-items: flex-start; /* Yazıları sola hizaladım */
  gap: 6px; /* Yazılar arasındaki mesafe */
}

.product-info {
  flex: 1;
}

/* Yazılar */
.product-brand {
  font-size: 14px;
  font-weight: bold;
}

.product-title {
  font-size: 16px;
}

/* Fiyat düzeni */
.price-wrapper {
  display: flex;
  flex-direction: column; /* Fiyatları alt alta yerleştiriyorum */
  gap: 4px; /* Fiyatlar arasındaki mesafe */
  color: #56008E;
}

.price-old {
  font-size: 12px;
  color: #888;
  text-decoration: line-through;
}

.current-price {
  font-size: 16px;
  font-weight: bold;
  color: #56008E; /* Mor renk */
}

/* Adet bilgisi */
.count-info {
  font-size: 14px;
  color: #0000;
}

/* Düğmeler */
.popup-buttons {
  display: flex;
  justify-content: space-between;
  margin-top: 16px;
}

.btn {
  width: 48%;
  padding: 8px;
  font-size: 14px;
  font-weight: bold;
  text-align: center;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.btn-primary {
  background-color: #56008E;
  color: #fff;
}

.btn-primary:hover {
  background-color: #4d00cc;
}

.btn-secondary {
  background-color: #333;
  color: #fff;
}

.btn-secondary:hover {
  background-color: #111;
}
</style>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ProductAddedModal',
  methods: {
    goToCart() {
      // Sepet sayfasına yönlendirme
      this.$router.push('/cart');
    },
    proceedToCheckout() {
      // Satın alma sayfasına yönlendirme
      this.$router.push('/checkout');
    },
    goBack() {
    this.$router.go(-1); // Kullanıcıyı önceki sayfaya yönlendirme
  },
  },
});
</script>








  