<template>
  <section id="contact" class="relative bg-[#f0faf9] overflow-hidden py-24 px-6 md:px-16">

    <!-- Burbujas decorativas -->
    <div class="absolute -top-24 -right-24 w-96 h-96 bg-teal-100 rounded-full opacity-50 blur-3xl pointer-events-none" />
    <div class="absolute -bottom-24 -left-24 w-80 h-80 bg-teal-200 rounded-full opacity-30 blur-3xl pointer-events-none" />

    <div class="relative w-full px-0 lg:px-24">

      <!-- Header -->
      <div class="mb-14">
        <span
          class="inline-block text-xs font-semibold tracking-[2px] uppercase text-teal-600 mb-4"
          :class="visible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-4'"
          style="transition: opacity .6s ease, transform .6s ease;"
        >
          Contacto y ubicación
        </span>
        <h2
          class="font-serif text-4xl md:text-5xl text-slate-800 leading-tight"
          :class="visible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-4'"
          style="transition: opacity .6s ease .1s, transform .6s ease .1s;"
        >
          Visítanos o <em class="not-italic text-teal-600">contáctanos</em>
        </h2>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-start">

        <!-- Información Contacto -->
        <div class="flex flex-col gap-4">
          <div
            v-for="(item, i) in contactItems"
            :key="item.label"
            class="flex items-start gap-4 p-5 bg-white rounded-2xl border border-slate-100 shadow-sm
                   transition-all duration-300 hover:border-teal-200 hover:shadow-md hover:-translate-y-0.5"
            :class="visible ? 'opacity-100 translate-x-0' : 'opacity-0 -translate-x-6'"
            :style="`transition: opacity .6s ease ${i * 0.1}s, transform .6s ease ${i * 0.1}s, border-color .3s, box-shadow .3s;`"
          >
            <div class="shrink-0 w-11 h-11 rounded-xl bg-teal-50 border border-teal-100 flex items-center justify-center text-xl">
              {{ item.icon }}
            </div>
            <div>
              <p class="text-xs font-semibold uppercase tracking-wider text-slate-400 mb-1">{{ item.label }}</p>
              <p class="text-slate-700 font-medium text-sm leading-relaxed" v-html="item.value" />
            </div>
          </div>

          <!-- Horario -->
          <div
            class="p-5 bg-white rounded-2xl border border-slate-100 shadow-sm"
            :class="visible ? 'opacity-100 translate-x-0' : 'opacity-0 -translate-x-6'"
            style="transition: opacity .6s ease .5s, transform .6s ease .5s;"
          >
            <div class="flex items-center gap-3 mb-4">
              <div class="w-11 h-11 rounded-xl bg-teal-50 border border-teal-100 flex items-center justify-center text-xl shrink-0">
                ⏰
              </div>
              <p class="text-xs font-semibold uppercase tracking-wider text-slate-400">Horario</p>
            </div>
            <ul class="flex flex-col gap-2">
              <li
                v-for="h in hours"
                :key="h.day"
                class="flex justify-between items-center text-sm py-1.5 border-b border-slate-50 last:border-0"
              >
                <span class="font-medium text-slate-700">{{ h.day }}</span>
                <span
                  class="text-xs font-semibold px-3 py-1 rounded-full"
                  :class="h.open ? 'bg-teal-50 text-teal-700' : 'bg-slate-100 text-slate-400'"
                >
                  {{ h.time }}
                </span>
              </li>
            </ul>
          </div>
        </div>

        <!-- Mapa y Formulario Contacto -->
        <div
          class="flex flex-col gap-6 -mt-10 lg:-mt-49"
          :class="visible ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-6'"
          style="transition: opacity .7s ease .2s, transform .7s ease .2s;"
        >
          <!-- Map placeholder -->
          <div class="relative rounded-3xl overflow-hidden h-56 bg-linear-to-br from-teal-100 to-teal-200 border border-teal-200 flex flex-col items-center justify-center gap-2 shadow-sm">
            <div class="absolute inset-0"
              style="background-image: repeating-linear-gradient(0deg,rgba(13,148,136,.06) 0,rgba(13,148,136,.06) 1px,transparent 1px,transparent 32px),repeating-linear-gradient(90deg,rgba(13,148,136,.06) 0,rgba(13,148,136,.06) 1px,transparent 1px,transparent 32px);"
            />
            <span class="text-4xl animate-bounce">📍</span>
            <p class="text-teal-700 font-semibold text-sm">Calle de la Salud, 12 · Madrid</p>
            
            <iframe
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d5387.856693901735!2d-5.969573418734005!3d37.32012841394!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd126e1c635c1859%3A0xb7532eee4a787f6!2sC.%20de%20la%20Salud%2C%2041014%20Sevilla!5e0!3m2!1ses!2ses!4v1775646625195!5m2!1ses!2ses"
              class="absolute inset-0 w-full h-full border-0"
              allowfullscreen loading="lazy"
            /> 
          </div>

          <!-- Formulario de contacto -->
          <div class="bg-white rounded-3xl border border-slate-100 shadow-sm p-7">
            <h3 class="font-serif text-xl text-slate-800 mb-1">Envíanos un mensaje</h3>
            <p class="text-slate-400 text-sm mb-6">Te respondemos en menos de 24 horas.</p>

            <div class="flex flex-col gap-4">
              <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                <div>
                  <label class="text-xs font-semibold text-slate-500 uppercase tracking-wider mb-1.5 block">Nombre</label>
                  <input
                    v-model="form.name"
                    type="text"
                    placeholder="Tu nombre"
                    class="w-full px-4 py-3 rounded-xl border border-slate-200 text-sm text-slate-700 placeholder-slate-300
                           focus:outline-none focus:border-teal-400 focus:ring-2 focus:ring-teal-100 transition-all"
                  />
                </div>
                <div>
                  <label class="text-xs font-semibold text-slate-500 uppercase tracking-wider mb-1.5 block">Teléfono</label>
                  <input
                    v-model="form.phone"
                    type="tel"
                    placeholder="+34 600 000 000"
                    class="w-full px-4 py-3 rounded-xl border border-slate-200 text-sm text-slate-700 placeholder-slate-300
                           focus:outline-none focus:border-teal-400 focus:ring-2 focus:ring-teal-100 transition-all"
                  />
                </div>
              </div>

              <div>
                <label class="text-xs font-semibold text-slate-500 uppercase tracking-wider mb-1.5 block">Motivo de consulta</label>
                <select
                  v-model="form.reason"
                  class="w-full px-4 py-3 rounded-xl border border-slate-200 text-sm text-slate-700
                         focus:outline-none focus:border-teal-400 focus:ring-2 focus:ring-teal-100 transition-all bg-white"
                >
                  <option value="" disabled>Selecciona un servicio...</option>
                  <option v-for="s in services" :key="s" :value="s">{{ s }}</option>
                </select>
              </div>

              <div>
                <label class="text-xs font-semibold text-slate-500 uppercase tracking-wider mb-1.5 block">Mensaje (opcional)</label>
                <textarea
                  v-model="form.message"
                  rows="3"
                  placeholder="Cuéntanos brevemente tu caso..."
                  class="w-full px-4 py-3 rounded-xl border border-slate-200 text-sm text-slate-700 placeholder-slate-300
                         focus:outline-none focus:border-teal-400 focus:ring-2 focus:ring-teal-100 transition-all resize-none"
                />
              </div>

              <button
                @click="submitForm"
                :disabled="sending || sent"
                class="w-full py-4 rounded-xl font-semibold text-sm transition-all duration-200 flex items-center justify-center gap-2"
                :class="sent
                  ? 'bg-green-500 text-white cursor-default'
                  : 'bg-teal-600 hover:bg-teal-500 text-white hover:-translate-y-0.5 hover:shadow-lg hover:shadow-teal-200 disabled:opacity-60'"
              >
                <span v-if="sent">✅ Mensaje enviado</span>
                <span v-else-if="sending">⏳ Enviando...</span>
                <span v-else>📩 Enviar mensaje</span>
              </button>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue'

const visible = ref(false)
const sending = ref(false)
const sent = ref(false)

const form = reactive({
  name: '',
  phone: '',
  reason: '',
  message: '',
})

const contactItems = [
  {
    icon: '📍',
    label: 'Dirección',
    value: 'Calle de la Salud, 15 · 41014 Sevilla',
  },
  {
    icon: '📞',
    label: 'Teléfono',
    value: '<a href="tel:+34900000000" class="text-teal-600 hover:underline">+34 900 000 000</a>',
  },
  {
    icon: '📧',
    label: 'Email',
    value: '<a href="mailto:info@clinicapodologica.es" class="text-teal-600 hover:underline">info@clinicapodologica.es</a>',
  },
]

const hours = [
  { day: 'Lunes – Viernes', time: '9:00 – 20:00', open: true },
  { day: 'Sábado',          time: '9:00 – 14:00', open: true },
  { day: 'Domingo',         time: 'Cerrado',       open: false },
]

const services = [
  'Quiropodia',
  'Tratamiento de hongos',
  'Podología infantil',
  'Estudio de la pisada',
  'Pie diabético',
  'Uñas encarnadas',
  'Otra consulta',
]

function submitForm() {
  if (!form.name || !form.phone) return
  sending.value = true
  // Aquí iría la lógica real de envío (API, email, etc). Simulamos con timeout:
  setTimeout(() => {
    sending.value = false
    sent.value = true
  }, 1400)
}

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) visible.value = true },
    { threshold: 0.1 }
  )
  const section = document.querySelector('section.bg-\\[\\#f0faf9\\]')
  if (section) observer.observe(section)
  setTimeout(() => { visible.value = true }, 500)
})
</script>