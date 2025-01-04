<template>
     <div class="container">
      <h1>Component Viewer</h1>
      <div class="button-container">
        <button v-for="n in 10" :key="n" @click="navigateToComponent(n)">
          Go to Component {{ n }}
        </button>
      </div>
    </div>
   
    <HeaderComponent></HeaderComponent>


    
   
    <CourselComponent></CourselComponent>
    
    <CompComponents></CompComponents>


    <FooterComponents></FooterComponents>
</template>

<style>
.bosluk{
    padding: 50px;
}

</style>
  
  <script setup>
  import { useRouter } from 'vue-router';
  
  const router = useRouter();
  
  const navigateToComponent = (componentId) => {
    router.push(`/component/${componentId}`);
  };

  const goToComponentTwo = () => {
  // ComponentTwo'ya yönlendir yeni ekledim
  router.push({ path: '/component/2' });
}

  </script>
  
  <style scoped>
  .container {
    text-align: center;
    margin: 20px;
  }
  .button-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
  }
  button {
    padding: 10px 20px;
    cursor: pointer;
  }
  </style>
  
