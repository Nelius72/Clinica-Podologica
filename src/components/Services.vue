<template>
  <section id="services" class="py-32 px-6 md:px-12 bg-cream">
    <div class="max-w-7xl mx-auto text-center mb-16">
      <h2 class="font-serif text-3xl md:text-5xl text-slate-900 mb-4">
        Nuestros <em class="text-teal-700 italic">Servicios</em>
      </h2>
      <p class="text-slate-600 max-w-2xl mx-auto text-base md:text-lg leading-relaxed">
        Ofrecemos un cuidado integral del pie con tratamientos especializados y
        tecnología avanzada para tu salud podológica.
      </p>
    </div>

    <!-- Grid de servicios -->
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-5 justify-items-center gap-y-8">
      <div
        v-for="(service, index) in services"
        :key="index"
        class="service-card reveal"
        :style="{ transitionDelay: `${index * 0.1}s` }"
      >
        <div
          class="icon text-4xl mb-2 rounded-full w-14 h-14 flex items-center justify-center text-teal-700"
        >
          {{ service.icon }}
        </div>
        <h3 class="text-lg font-semibold mb-1">{{ service.title }}</h3>
        <p class="text-gray-600 text-sm">{{ service.description }}</p>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'

const services = [
  { icon: "🦶", title: "Podología", description: "Cuidado integral del pie, tratamiento de uñas encarnadas y hongos." },
  { icon: "🩺", title: "Estudio Biomecánico", description: "Análisis de la pisada y postura para prevenir lesiones." },
  { icon: "💉", title: "Tratamientos Avanzados", description: "Tecnología moderna para uñas y piel del pie." },
  { icon: "👣", title: "Ortopodología", description: "Plantillas personalizadas y apoyo para la movilidad." },
  { icon: "🧴", title: "Cuidado Preventivo", description: "Higiene, hidratación y prevención de patologías." },
  { icon: "📈", title: "Seguimiento Profesional", description: "Control y seguimiento del progreso de cada paciente." },
  { icon: "🏃‍♂️", title: "Rehabilitación", description: "Tratamientos para mejorar la función y aliviar dolor." },
]

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible')
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.15 }
  )

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el))
})
</script>

<style scoped>
.bg-cream {
  background-color: #fdfaf6;
}

/* Cards visibles con borde y sombra ligera */
.service-card {
  background: white;
  border: 1px solid rgba(0,0,0,0.08);
  border-radius: 16px;
  padding: 16px;
  max-width: 260px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  text-align: center;
}

/* Animación de subida suave */
.reveal {
  transform: translateY(20px);
  opacity: 0.9;
  transition: transform 0.6s ease, opacity 0.6s ease;
}
.reveal.visible {
  transform: translateY(0);
  opacity: 1;
}

/* Hover */
.service-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15);
}
.service-card:hover .icon {
  background: linear-gradient(135deg, #34d399, #06b6d4);
  color: white;
}

/* Iconos */
.icon {
  display: flex;                
  align-items: center;          
  justify-content: center;      
  width: 56px;                 
  height: 56px;                 
  border-radius: 50%;           
  font-size: 1.5rem;            
  background: linear-gradient(135deg, #a0f0e5, #06b6d4);
  color: #fff;                  
  margin: 0 auto 12px auto;     
}

/* Grid responsivo */
@media (max-width: 900px) {
  .grid { grid-template-columns: 1fr !important; gap: 24px; }
}
</style>