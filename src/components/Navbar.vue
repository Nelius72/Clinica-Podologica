<script setup lang="ts">

</script>

<template>
  <nav
    :class="[
      'fixed top-0 left-0 right-0 z-50 flex items-center justify-between px-6 md:px-12 py-4 bg-white/85 backdrop-blur-md border-b border-teal-100 transition-shadow',
      { 'shadow-lg': scrolled }
    ]"
  >
    <!-- Logo -->
    <div class="font-serif text-xl tracking-tight text-teal-600">
      Podología<span class="text-slate-600">Clínica</span>
    </div>

    <!-- Links -->
    <ul class="hidden md:flex gap-9 list-none">
      <li><a href="#services" class="text-slate-500 text-sm font-medium hover:text-teal-600 transition-colors">Servicios</a></li>
      <li><a href="#about" class="text-slate-500 text-sm font-medium hover:text-teal-600 transition-colors">Sobre Nosotros</a></li>
      <li><a href="#benefits" class="text-slate-500 text-sm font-medium hover:text-teal-600 transition-colors">Por Qué Elegirnos</a></li>
      <li>
        <a href="#contact" class="bg-teal-600 text-white px-5 py-2.5 rounded-full text-sm font-medium transition-transform hover:bg-teal-500 hover:-translate-y-0.5">
          Reservar Cita
        </a>
      </li>
    </ul>

    <!-- Movil Hamburger -->
    <button @click="menuOpen = !menuOpen" class="md:hidden focus:outline-none">
      <span v-if="!menuOpen" class="text-2xl">☰</span>
      <span v-else class="text-2xl">✕</span>
    </button>

    <!-- Menú Movil -->
    <transition name="fade">
      <ul
        v-if="menuOpen"
        class="absolute top-full left-0 w-full bg-white/95 backdrop-blur-md flex flex-col items-center gap-6 py-6 md:hidden border-b border-teal-100 shadow-md"
      >
        <li><a href="#services" @click="menuOpen=false" class="text-slate-500 text-lg font-medium hover:text-teal-600 transition-colors">Servicios</a></li>
        <li><a href="#about" @click="menuOpen=false" class="text-slate-500 text-lg font-medium hover:text-teal-600 transition-colors">Sobre Nosotros</a></li>
        <li><a href="#benefits" @click="menuOpen=false" class="text-slate-500 text-lg font-medium hover:text-teal-600 transition-colors">Por Qué Elegirnos</a></li>
        <li>
          <a href="#contact" @click="menuOpen=false" class="bg-teal-600 text-white px-6 py-2 rounded-full text-sm font-medium transition-transform hover:bg-teal-500 hover:-translate-y-0.5">
            Reservar Cita
          </a>
        </li>
      </ul>
    </transition>
  </nav>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue';

export default {
  name: 'Navbar',
  setup() {
    const scrolled = ref(false);
    const menuOpen = ref(false);

    const handleScroll = () => {
      scrolled.value = window.scrollY > 50;
    };

    onMounted(() => {
      window.addEventListener('scroll', handleScroll);
    });

    onUnmounted(() => {
      window.removeEventListener('scroll', handleScroll);
    });

    return { scrolled, menuOpen };
  },
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>