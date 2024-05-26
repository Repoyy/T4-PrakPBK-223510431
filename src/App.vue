<template>
  <div id="app">
    <div class="custom-container">
      <ParentComponent />
    </div>
  </div>
</template>

<script>
import ParentComponent from './components/ParentComponent.vue';

export default {
  name: 'App',
  components: {
    ParentComponent,
  },
};
</script>

<style>
body {
  background: linear-gradient(270deg, #a8e6cf, #dcedc1, #ffd3b6);
  background-size: 600% 600%;
  animation: GradientAnimation 15s ease infinite;
}

@keyframes GradientAnimation {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

#app {
  font-family: 'Helvetica Neue', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #333;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.custom-container {
  width: 80%;
  max-width: 800px;
  height: auto; 
  background-color: #dcedc1;
  border-radius: 25px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
  padding: 30px;
  box-sizing: border-box;
  text-align: center;
  justify-content: center;
  display: flex;
  flex-direction: column; 
  align-items: center; 
}

</style>
