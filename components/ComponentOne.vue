<!-- components/ComponentOne.vue -->
<template>
  <div class="header">
    <div class="container text-center">
      <div class="row align-items-center">
        <div class="col">
          <img src="/items/kitapsepeti-logo1.png" alt="Kitapsepeti Logo">
        </div>
        <div class="col">
          <div class="search-container">
            <div class="icon-box">
              <span class="search-icon">🔍</span>
            </div>
            <input type="text" class="search-input" placeholder="Aradığınız ürünün adını yazınız.">
            <button class="search-button">ARA</button>
          </div>
        </div>
        <div class="col">
          <div class="row">
            <div class="col">
              <button class="register-button">
                <div class="col">
                  <img src="/items/user.svg" alt="User Icon">
                  <div>E-posta ile Giriş veya Kayıt Ol</div>
                </div>
              </button>
            </div>
            <div class="col-4">
              <button class="cart-button">
                <img src="/items/whitecart.png" alt="Sepetim Icon" class="cart-icon">
                Sepetim
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ComponentOne',
};
</script>

<style scoped>
.header {
  padding-top: 20px;
}
.search-container {
  display: flex;
  align-items: center;
  background-color: #56008E;
  padding: 1px;
  border-radius: 1px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}
.icon-box {
  background-color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 5px 10px;
  border-radius: 1px 0 0 1px;
}
.search-icon {
  font-size: 18px;
  color: white;
}
.search-input {
  padding: 8px;
  border: none;
  outline: none;
  font-size: 16px;
  border-radius: 0;
  flex-grow: 1;
}
.search-button {
  background-color: #56008E;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  border-radius: 0 1px 1px 0;
  transition: background-color 0.3s ease;
}
.search-button:hover {
  background-color: #505050;
}
.register-button {
  height: 42px;
  width: 134px;
  background-color: #56008E;
  color: white;
  border: none;
  padding: 12px 24px;
  font-size: 12px;
  font-weight: bold;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
}
.register-button:active {
  background-color: #56008E;
  transform: scale(0.98);
}
.cart-button {
  background-color: #FF5722;
  color: white;
  font-size: 16px;
  padding: 10px 20px;
  border: none;
  border-radius: 30px;
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
}
.cart-button:hover {
  background-color: #e64a19;
}
.cart-icon {
  width: 20px;
  height: 20px;
}
</style>

