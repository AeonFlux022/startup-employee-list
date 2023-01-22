<template>
  <nav>
    <NavBar></NavBar>
  </nav>
  <main>
    <div class="container-fluid">
    <router-view/>
    </div>
  </main>
  
</template>

<script setup>
import { RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue'
</script>

<style>
#addStartup, #showStartups, #home {
  margin-top: 60px;
}
</style>
