<script setup lang="ts">
import informeIMG from "../assets/informe.png";
import { ref, onMounted } from "vue";

const visible = ref(false);

const benefits = [
  { icon: "🤝", text: "Atención completamente personalizada" },
  { icon: "💉", text: "Tratamientos indoloros y mínimamente invasivos" },
  { icon: "🧼", text: "Higiene y esterilización certificada" },
  { icon: "🎁", text: "Primera valoración sin compromiso" },
  { icon: "⚡", text: "Atención urgente disponible" },
];

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) visible.value = true;
    },
    { threshold: 0.2 },
  );
  const el = document.querySelector("#benefits-section");
  if (el) observer.observe(el);

  // Fallback: trigger after short delay if observer misses
  setTimeout(() => {
    visible.value = true;
  }, 400);
});
</script>
<template>
  <section
    id="benefits"
    class="relative bg-[#f0faf9] overflow-hidden py-24 px-6 md:px-16"
  >
    <!-- Background decorative blobs -->
    <div
      class="absolute -top-24 -left-24 w-96 h-96 bg-teal-100 rounded-full opacity-40 blur-3xl pointer-events-none"
    />
    <div
      class="absolute -bottom-24 -right-24 w-80 h-80 bg-teal-200 rounded-full opacity-30 blur-3xl pointer-events-none"
    />

    <div
      class="relative w-full grid grid-cols-1 lg:grid-cols-2 gap-16 items-center px-0 lg:px-24"
    >
      <!-- Lista Beneficios -->
      <div>
        <span
          class="inline-block font-serif text-3xl md:text-5xl text-teal-600 mb-4"
        >
          ¿Por qué elegirnos?
        </span>
        <h2
          class="font-serif text-4xl md:text-5xl leading-tight text-slate-800 mb-4"
        >
          Tu bienestar,<br />
          <em class="not-italic text-teal-600">nuestra prioridad</em>
        </h2>
        <p class="text-slate-500 text-base leading-relaxed mb-10 max-w-md">
          Nos diferenciamos por un trato cercano, tecnología avanzada y
          resultados visibles desde la primera visita.
        </p>

        <ul class="flex flex-col gap-4">
          <li
            v-for="(benefit, i) in benefits"
            :key="benefit.text"
            class="benefit-item flex items-center gap-4 bg-white rounded-2xl px-5 py-4 border border-slate-100 shadow-sm transition-all duration-300 hover:translate-x-2 hover:border-teal-200 hover:shadow-md"
            :style="{ transitionDelay: `${i * 60}ms` }"
            :class="
              visible ? 'opacity-100 translate-x-0' : 'opacity-0 -translate-x-6'
            "
            ref="itemRefs"
          >
            <div
              class="shrink-0 w-9 h-9 rounded-full bg-teal-600 flex items-center justify-center text-white text-sm font-bold shadow-md shadow-teal-200"
            >
              ✓
            </div>
            <div class="flex items-center gap-3">
              <span class="text-xl">{{ benefit.icon }}</span>
              <span class="text-slate-700 font-medium text-[0.95rem]">{{
                benefit.text
              }}</span>
            </div>
          </li>
        </ul>
      </div>

      <!-- CTA -->
      <div class="flex flex-col items-center text-center">
        <!-- Círculo de llamada a la acción -->
        <div
          class="relative w-72 h-72 md:w-80 md:h-80 rounded-full mb-10 flex flex-col items-center justify-center gap-3 bg-linear-to-br from-teal-500 to-teal-700 shadow-[0_24px_80px_rgba(13,148,136,0.45)] overflow-hidden"
          :class="visible ? 'scale-100 opacity-100' : 'scale-90 opacity-0'"
          style="
            transition:
              transform 0.8s cubic-bezier(0.34, 1.56, 0.64, 1),
              opacity 0.6s ease;
          "
        >
          <!-- Imagen de perfil -->
          <img
            :src="informeIMG"
            alt="Mi foto"
            class="absolute inset-0 w-full h-full object-cover rounded-full"
          />

          <!-- Animación de pulso -->
          <span
            class="absolute inset-0 rounded-full animate-ping bg-teal-400 opacity-10"
          />

          
        </div>

        <!-- CTA Botón -->
        <a
          href="#contact"
          class="inline-flex items-center gap-2 bg-teal-600 hover:bg-teal-500 text-white font-semibold text-base px-10 py-5 rounded-full shadow-lg shadow-teal-300/50 transition-all duration-200 hover:-translate-y-1 hover:shadow-xl hover:shadow-teal-300/60"
        >
          📅 Reservar valoración gratuita
        </a>

        <!-- Valoraciones -->
        <div class="flex items-center gap-6 mt-8">
          <div class="flex flex-col items-center">
            <span class="text-teal-600 font-serif text-2xl font-bold">98%</span>
            <span class="text-slate-400 text-xs mt-0.5">Satisfacción</span>
          </div>
          <div class="w-px h-10 bg-slate-200" />
          <div class="flex flex-col items-center">
            <span class="text-teal-600 font-serif text-2xl font-bold"
              >3.500+</span
            >
            <span class="text-slate-400 text-xs mt-0.5">Pacientes</span>
          </div>
          <div class="w-px h-10 bg-slate-200" />
          <div class="flex flex-col items-center">
            <span class="text-teal-600 font-serif text-2xl font-bold"
              >10 años</span
            >
            <span class="text-slate-400 text-xs mt-0.5">Experiencia</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
