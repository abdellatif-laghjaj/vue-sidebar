<template>
  <aside :class="`${is_expanded ? 'is_expanded' : ''}`">
    <!-- Logo -->
    <div class="logo">
      <img src="../assets/vue.svg" /> 
    </div>

    <!-- Menu -->
    <div class="menu-toggle-wrap" :style="`${is_expanded ? 'justify-content: flex-end' : 'justify-content: center;' }`">
      <button class="menu-toggle" @click="toggleMenu">
        <box-icon name='right-arrow-square' type='solid' color='#fffefe' ></box-icon>
      </button>
    </div>
  </aside>
</template>

<script setup>
  import { ref } from 'vue'

  const is_expanded = ref(false)

  const toggleMenu = () => {
    is_expanded.value = !is_expanded.value
  }
</script>

<style lang="scss">
aside{
  display: flex;
  flex-direction: column;
  background-color: var(--dark);
  color: var(--light);
  width: calc(2rem + 32px);
  overflow: hidden;
  min-height: 100vh;
  padding: 1rem;
  transition: 0.3s ease-out;

  &.is_expanded{
    width: var(--sidebar-width);

    .menu-toggle-wrap{
      top: -3rem;
    }
  }

  .logo{
    margin-bottom: 1rem;

    img{
      width: 2rem;
    }
  }

  .menu-toggle-wrap{
    display: flex;
    align-items: center;
    margin-bottom: 1rem;
    position: relative;
    top: 0;
    transition: 0.3s ease-out;

    .menu-toggle{
      transition: 0.3s ease-out;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }

  @media (max-width: 768px){
    position: fixed;
    z-index: 99;
  }
}
</style>
