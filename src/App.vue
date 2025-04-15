<script setup>
import HeaderComponent from './components/header.vue';
import PageBody from './components/body.vue';
import PageFooter from './components/footer.vue';
</script>

<template>  
  <div class="app-wrapper">
    
    <div class="app-container">
      <HeaderComponent/>
      <main>
        <PageBody />
      </main>
      <PageFooter />
    </div>
  </div>
</template>


<style scoped>
.app-wrapper {
  min-height: 100vh; 
    flex-direction: column;
    justify-content: space-between; 
    align-items: center;
    padding: 0;
    margin: 0;
}

.app-container {
  min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between; 
    align-items: center; 
    padding: 0;
    margin: 0;
}
</style>
