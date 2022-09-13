<template>
  <div class="app">
    <SideBar />
    <router-view />
  </div>
</template>

<script setup>
import SideBar from './components/SideBar.vue'
</script>

<style lang="scss" scoped>
:root {
  --primary: #4ade80;
  --grey: #64748b;
  --dark: D #1e293b;
  --dark-alt: #334155;
  --light: #f1f5f9;
  --sidebar-width: 300px;
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Ubuntu', sans-serif;
}

body{
  background: var(--light);
}

button{
  cursor: pointer;
  appearance: none;
  border: none;
  background: none;
  outline: none;
}

.app{
  display: flex;

  main{
    flex: 1 1 0;
    padding: 2rem;

    @media (max-width: 768px){
      padding: 6rem;
    }
  }
}
</style>
