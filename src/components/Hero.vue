<script setup lang="ts"></script>

<template>
  <section
    id="hero"
    class="min-h-[65vh] grid md:grid-cols-2 items-center px-6 md:px-12 py-8 md:py-6 bg-linear-to-br from-cream via-[#e8f5f4] to-teal-pale relative overflow-hidden"
  >
    <!-- Fondo radial -->
    <div
      class="absolute -top-32 -right-32 w-150 h-150 rounded-full bg-gradient-radial from-teal-100 to-transparent"
    ></div>

    <!-- Texto Hero -->
    <div class="relative z-10 space-y-6 -mt-2 md:-mt-4">
      <div
        class="inline-flex items-center gap-2 bg-teal-pale text-teal-700 border border-teal-200 rounded-full px-4 py-1 text-xs font-semibold uppercase animate-pulse"
      >
        🦶 Especialistas en salud podológica
      </div>

      <h1 class="font-serif text-3xl md:text-5xl text-slate-900 leading-tight">
        Clínica Podológica especializada en el
        <em class="text-teal-700 italic">cuidado integral</em> del pie
      </h1>

      <p class="text-slate-600 max-w-lg text-base md:text-lg leading-relaxed">
        Tratamientos avanzados para uñas encarnadas, hongos, papilomas y estudio
        biomecánico. Tu salud, en las mejores manos.
      </p>

      <div class="flex flex-wrap gap-4">
        <a
          href="#contact"
          class="inline-flex items-center gap-2 bg-teal-700 text-white px-6 py-4 rounded-full font-semibold shadow-lg hover:bg-teal-500 hover:-translate-y-1 transition-all"
        >
          📅 Reservar cita
        </a>
        <a
          href="tel:+34900000000"
          class="inline-flex items-center gap-2 border-2 border-gray-200 px-6 py-4 rounded-full font-semibold text-teal-700 hover:border-teal-700 hover:-translate-y-1 transition-all"
        >
          📞 Llamar ahora
        </a>
      </div>

      <!-- Stats -->
      <div class="flex flex-wrap gap-10 mt-10 pt-6 border-t border-gray-200">
        <div>
          <div class="font-serif text-3xl text-teal-700">10+</div>
          <div class="text-sm text-slate-400 mt-1">Años de experiencia</div>
        </div>
        <div>
          <div class="font-serif text-3xl text-teal-700">3.500+</div>
          <div class="text-sm text-slate-400 mt-1">Pacientes tratados</div>
        </div>
        <div>
          <div class="font-serif text-3xl text-teal-700">98%</div>
          <div class="text-sm text-slate-400 mt-1">Satisfacción</div>
        </div>
      </div>
    </div>

    <!-- Visual Hero -->
    <div
      class="hero-visual relative flex justify-center md:justify-end mt-6 md:mt-0"
    >
      <div
        class="w-full max-w-md h-130 md:h-130 rounded-2xl bg-linear-to-br from-[#c5ece9] to-[#8dd4cf] shadow-lg overflow-hidden relative flex items-center justify-center translate-x-0 md:-translate-x-46"
      >
        <div class="flex flex-col items-center justify-center gap-4">
          <img
            src="https://img.freepik.com/free-photo/front-view-male-osteopathic-therapist-checking-female-patient-s-toes_23-2148846626.jpg?semt=ais_incoming&w=740&q=80"
            alt="Imagen profesional"
            class="w-120 h-132 object-cover"
          />
        </div>
        
      </div>
    </div>
  </section>
</template>

<script setup></script>

<style>
@keyframes bounce-slow {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-8px);
  }
}
@keyframes bounce-fast {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(10px);
  }
}
.animate-bounce-slow {
  animation: bounce-slow 5s ease-in-out infinite;
}
.animate-bounce-fast {
  animation: bounce-fast 6s ease-in-out infinite;
}
</style>
