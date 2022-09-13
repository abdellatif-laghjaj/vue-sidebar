<template>
  <aside :class="`${is_expanded ? 'is_expanded' : ''}`">
    <!-- Logo -->
    <div class="logo">
      <img src="../assets/vue.svg" />
    </div>

    <!-- Menu Toggle -->
    <div class="menu-toggle-wrap" :style="`${is_expanded ? 'justify-content: flex-end' : 'justify-content: center;' }`">
      <button class="menu-toggle" @click="toggleMenu">
        <i class='bx bx-menu-alt-left'></i>
      </button>
    </div>

    <!-- Menu -->
    <h3>Menu</h3>

    <div class="menu">
      <router-link class="nav-link" to="/">
        <i class='bx bxs-home-smile'></i>
        <span class="nav-text">Home</span>
      </router-link>

      <router-link class="nav-link" to="/about">
        <i class='bx bx-message-dots'></i>
        <span class="nav-text">About</span>
      </router-link>

      <router-link class="nav-link" to="/products">
        <i class='bx bxs-package'></i>
        <span class="nav-text">Products</span>
      </router-link>

      <router-link class="nav-link" to="/services">
        <i class='bx bxs-briefcase-alt-2'></i>
        <span class="nav-text">Services</span>
      </router-link>
    </div>

    <div class="flex"></div>

    <div class="menu">
      <router-link class="nav-link" to="/theme">
        <i class='bx bxs-palette'></i>
        <span class="nav-text">Theme</span>
      </router-link>
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
aside {
  display: flex;
  flex-direction: column;
  background-color: var(--dark);
  color: var(--light);
  width: calc(2rem + 32px);
  overflow: hidden;
  min-height: 100vh;
  padding: 1rem;
  transition: 0.3s ease-out;

  .flex{
    flex: 1 1 0;
  }

  .logo {
    margin-bottom: 1rem;

    img {
      width: 2rem;
    }
  }

  .menu-toggle-wrap {
    display: flex;
    align-items: center;
    margin-bottom: 1rem;
    position: relative;
    top: 0;
    transition: 0.3s ease-out;

    .menu-toggle {
      transition: 0.3s ease-out;
      display: flex;
      align-items: center;
      justify-content: center;

      .bx {
        font-size: 1.6rem;
        transition: 0.2s ease-out;
        color: var(--light);

        &:hover {
          color: var(--primary);
          transform: translateX(0.3rem);
        }
      }
    }
  }

  h3{
    color: var(--grey);
    font-size: 0.8rem;
    margin-bottom: 0.5rem;
    text-transform: uppercase;
  }

  h3,
  .nav-link .nav-text {
    opacity: 0;
    transition: 0.3s ease-out;
  }

  .menu {
    margin: 0 -1rem;

    .nav-link {
      display: flex;
      align-items: center;
      text-decoration: none;
      padding: 0.5rem 1rem;
      transition: 0.3s ease-out;

      .bx {
        font-size: 2rem;
        color: var(--light);
        transition: 0.2s ease-out;
      }

      .nav-text {
        color: var(--light);
        font-size: 1.2rem;
        transition: 0.2s ease-out;
      }

      &:hover, &.router-link-exact-active {
        background-color: var(--dark-alt);
        border-right: 5px solid var(--primary);

        .bx,
        .nav-text {
          color: var(--primary);
        }
      }
    }
  }

  &.is_expanded {
    width: var(--sidebar-width);

    .menu-toggle-wrap {
      top: -3rem;

      .menu-toggle {
        transform: rotate(180deg);
      }
    }

    h3,
    .nav-link .nav-text {
      opacity: 1;
    }

    .nav-link {
      .bx {
        margin-right: 0.8rem;
      }
    }
  }

  @media (max-width: 768px) {
    position: fixed;
    z-index: 99;
  }
}
</style>
