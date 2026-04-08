<script setup lang="ts">
import podologoImg from '../assets/podologo.png'
import { onMounted } from "vue";


interface AboutItem {
  icon: string;
  title: string;
  desc: string;
}
const props = defineProps({
  aboutItems: {
    type: Array<AboutItem>,
    default: () => [
      {
        icon: "🎓",
        title: "Formación especializada",
        desc: "Máster universitario en podología clínica y biomecánica del movimiento.",
      },
      {
        icon: "🔬",
        title: "Tecnología avanzada",
        desc: "Sistemas digitales de análisis de pisada, podoscopio y ecógrafo podológico.",
      },
      {
        icon: "🧼",
        title: "Esterilización certificada",
        desc: "Protocolo de higiene nivel hospitalario con autoclave de vapor a 134°C.",
      },
      {
        icon: "⚡",
        title: "Atención urgente",
        desc: "Disponemos de huecos para urgencias podológicas el mismo día.",
      },
    ],
  },
});

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((e) => {
        if (e.isIntersecting) e.target.classList.add("visible");
      });
    },
    { threshold: 0.12 },
  );

  document.querySelectorAll(".reveal").forEach((el) => observer.observe(el));
});
</script>

<template>
  <section id="about">
    <div class="about-grid">
      <div class="about-img-wrap reveal">
  <img
    :src="podologoImg"
    alt="Podólogo profesional"
    class="w-full h-full object-cover"
  />

  <div class="about-badge">
    <div class="badge-num">Col. 1234</div>
    <div class="badge-txt">Número de colegiado</div>
  </div>
</div>

      <div>
        <span class="font-serif text-3xl md:text-5xl text-slate-900 mb-4"
          >Sobre <em class="text-teal-700 italic">la Clínica</em></span
        >
        <h2 class="section-title reveal reveal-delay-1">
          Más de 10 años cuidando<br />la salud del pie
        </h2>
        <p class="section-sub reveal reveal-delay-2">
          Con tecnología de última generación y una formación especializada
          continua, ofrecemos el mejor diagnóstico y tratamiento para cada
          paciente.
        </p>

        <div class="about-items">
          <div
            v-for="(item, i) in aboutItems"
            :key="item.title"
            class="about-item reveal"
            :class="'reveal-delay-' + Math.min(i + 1, 5)"
          >
            <div class="about-item-icon">{{ item.icon }}</div>
            <div>
              <div class="about-item-title">{{ item.title }}</div>
              <div class="about-item-desc">{{ item.desc }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Animaciones de revelado */
.reveal {
  opacity: 0;
  transform: translateY(32px);
  transition:
    opacity 0.7s cubic-bezier(0.4, 0, 0.2, 1),
    transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}
.reveal.visible {
  opacity: 1;
  transform: none;
}
.reveal-delay-1 {
  transition-delay: 0.08s;
}
.reveal-delay-2 {
  transition-delay: 0.16s;
}
.reveal-delay-3 {
  transition-delay: 0.24s;
}
.reveal-delay-4 {
  transition-delay: 0.32s;
}
.reveal-delay-5 {
  transition-delay: 0.4s;
}


#about {
  background: #bde2f596;
  padding: 80px 24px; /* móvil */
}
.about-grid {
  display: grid;
  grid-template-columns: 1fr; 
  gap: 40px;
  align-items: center;
  width: 100%;
}
.about-img-wrap {
  border-radius: 28px;
  background: linear-gradient(145deg, #1e3a4a, #2d5468);
  aspect-ratio: 4/5;
  display: flex;
  align-items: center;
  
  justify-self: start;
  position: relative;
  overflow: hidden;
}
.about-img-wrap::after {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to top,
    rgba(13, 125, 120, 0.35),
    transparent 60%
  );
}
.about-placeholder {
  font-size: 5rem;
  opacity: 0.28;
}
.about-badge {
  position: absolute;
  bottom: 28px;
  left: 28px;
  z-index: 2;
  background: #0d7d78;
  color: #fff;
  border-radius: 16px;
  padding: 14px 18px;
}
.badge-num {
  font-family: "DM Serif Display", serif;
  font-size: 1.6rem;
}
.badge-txt {
  font-size: 0.78rem;
  opacity: 0.95;
}

.section-label {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  color: #12a89e;
  margin-bottom: 10px;
}
.section-title {
  font-family: "DM Serif Display", serif;
  font-size: clamp(1.6rem, 3vw, 2rem);
  line-height: 1.18;
  color: #122;
  margin: 6px 0 12px;
}
.section-sub {
  color: rgba(0, 0, 0, 0.68);
  max-width: 560px;
  margin-bottom: 18px;
}

.about-items {
  display: flex;
  flex-direction: column;
  gap: 16px;
  margin-top: 18px;
}
.about-item {
  display: flex;
  align-items: flex-start;
  gap: 14px;
  padding: 14px;
  border-radius: 16px;
  background: azure;
  border: 1px solid rgba(0, 0, 0, 0.04);
  transition: background 0.25s;
}
.about-item:hover {
  background: rgba(13, 125, 120, 0.06);
}
.about-item-icon {
  width: 44px;
  height: 44px;
  flex-shrink: 0;
  background: rgba(13, 125, 120, 0.18);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
}
.about-item-title {
  font-weight: 600;
  font-size: 0.95rem;
  margin-bottom: 4px;
}
.about-item-desc {
  font-size: 0.86rem;
  color: rgba(0, 0, 0, 0.6);
  line-height: 1.5;
}

@media (min-width: 1024px) {
  .about-grid {
    grid-template-columns: 0.9fr 1.1fr;
    gap: 40px; /* antes 100px */
  }

  .about-img-wrap {
    justify-self: center;
    max-width: 420px;
    transform: translateX(-20px); /* antes -30px */
  }
}
</style>
