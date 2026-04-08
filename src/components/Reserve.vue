<template>
  <section class="relative overflow-hidden bg-teal-700 py-24 px-6 md:px-16">

    <!-- Texturas -->
    <div class="absolute inset-0 pointer-events-none">
      <div class="absolute -top-32 -left-32 w-125 h-125 rounded-full border border-white/10" />
      <div class="absolute -top-20 -left-20 w-90 h-90 rounded-full border border-white/10" />
      <div class="absolute -bottom-32 -right-32 w-120 h-120 rounded-full border border-white/10" />
      <div class="absolute -bottom-16 -right-16 w-[320px] h-80 rounded-full border border-white/10" />
      <div class="absolute inset-0 bg-linear-to-br from-teal-600/50 via-transparent to-teal-900/60" />
    </div>

    <div class="relative max-w-4xl mx-auto text-center">

      <!-- Animación Icono -->
      <div
        class="inline-flex items-center justify-center w-16 h-16 rounded-full bg-white/15 mb-6 text-3xl
               ring-4 ring-white/10"
        :class="visible ? 'scale-100 opacity-100' : 'scale-75 opacity-0'"
        style="transition: transform .6s cubic-bezier(.34,1.56,.64,1), opacity .5s ease;"
      >
        📅
      </div>

      <!-- Cabecera -->
      <h2
        class="font-serif text-4xl md:text-5xl lg:text-6xl text-white leading-tight mb-5"
        :class="visible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'"
        style="transition: opacity .7s ease .1s, transform .7s ease .1s;"
      >
        ¿Listo para cuidar
        <em class="not-italic text-teal-200">tus pies?</em>
      </h2>

      <!-- Subtext -->
      <p
        class="text-teal-100 text-lg leading-relaxed max-w-xl mx-auto mb-10"
        :class="visible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'"
        style="transition: opacity .7s ease .2s, transform .7s ease .2s;"
      >
        Reserva tu cita hoy mismo. Atención personalizada y resultados
        visibles desde la primera visita.
      </p>

      <!-- Botones -->
      <div
        class="flex flex-col sm:flex-row items-center justify-center gap-4"
        :class="visible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'"
        style="transition: opacity .7s ease .3s, transform .7s ease .3s;"
      >
        <a
          href="#contact"
          class="inline-flex items-center gap-2 bg-white text-teal-700 font-bold text-base
                 px-10 py-5 rounded-full shadow-xl shadow-black/20
                 transition-all duration-200 hover:-translate-y-1 hover:shadow-2xl hover:bg-teal-50"
        >
          📅 Reservar mi cita ahora
        </a>
        
      </div>

      

    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const visible = ref(false)



onMounted(() => {
  const el = document.querySelector('#cta-band-section') ?? document.currentScript?.closest('section')

  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) visible.value = true },
    { threshold: 0.25 }
  )

  
  const section = document.querySelector('section.bg-teal-700')
  if (section) observer.observe(section)

  setTimeout(() => { visible.value = true }, 500)
})
</script>