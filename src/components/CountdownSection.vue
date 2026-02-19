<template>
  <section id="cuenta-regresiva" class="countdown-section section">
    <div class="container">
      <h2 class="section-title">La Magia Está Por Comenzar</h2>

      <div class="countdown-container">
        <div
          class="time-unit"
          v-for="(unit, index) in timeUnits"
          :key="index"
          :style="{ animationDelay: (index * 0.12) + 's' }"
        >
          <div class="time-box">
            <span class="sparkle">✦</span>
            <div class="time-value">{{ unit.value }}</div>
          </div>
          <div class="time-label">{{ unit.label }}</div>
        </div>
      </div>

      <div class="magical-message">
  <p v-if="timeRemaining.total > 0" class="vow-text">
    <span class="sparkle-vow">✦</span>
    {{ daysUntilWedding }} días para sellar nuestro 
    <span class="unbreakable-vow">Juramento Inquebrantable</span>
    <span class="sparkle-vow">✦</span>
  </p>
  <p v-else class="wedding-day-message">
    ¡El Juramento se ha sellado! ✨🎉
  </p>
</div>  

      <div class="hourglass-decoration" aria-hidden="true">⌛</div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'CountdownSection',
  props: {
    weddingDate: { type: Date, required: true }
  },
  data() {
    return {
      timeRemaining: { days: 0, hours: 0, minutes: 0, seconds: 0, total: 0 },
      interval: null
    }
  },
  computed: {
    timeUnits() {
      return [
        { value: String(this.timeRemaining.days).padStart(2, '0'),    label: 'Días' },
        { value: String(this.timeRemaining.hours).padStart(2, '0'),   label: 'Horas' },
        { value: String(this.timeRemaining.minutes).padStart(2, '0'), label: 'Minutos' },
        { value: String(this.timeRemaining.seconds).padStart(2, '0'), label: 'Segundos' }
      ]
    },
    daysUntilWedding() { return this.timeRemaining.days }
  },
  mounted() {
    this.updateCountdown()
    this.interval = setInterval(this.updateCountdown, 1000)
  },
  beforeUnmount() {
    if (this.interval) clearInterval(this.interval)
  },
  methods: {
    updateCountdown() {
      const distance = this.weddingDate.getTime() - Date.now()
      this.timeRemaining.total = distance
      if (distance > 0) {
        this.timeRemaining.days    = Math.floor(distance / 86400000)
        this.timeRemaining.hours   = Math.floor((distance % 86400000) / 3600000)
        this.timeRemaining.minutes = Math.floor((distance % 3600000) / 60000)
        this.timeRemaining.seconds = Math.floor((distance % 60000) / 1000)
      } else {
        this.timeRemaining = { days: 0, hours: 0, minutes: 0, seconds: 0, total: 0 }
      }
    }
  }
}
</script>

<style scoped>
.countdown-section {
  background: linear-gradient(160deg, rgba(14,26,64,0.5) 0%, rgba(10,14,31,0.3) 100%);
}

.countdown-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
  max-width: 820px;
  margin: 0 auto 48px;
}

/* Caja individual */
.time-unit {
  text-align: center;
  animation: fadeIn 0.7s ease-out both;
}

.time-box {
  position: relative;
  border: 1px solid rgba(201, 162, 77, 0.35);
  padding: 32px 16px 24px;
  margin-bottom: 12px;
  backdrop-filter: blur(6px);
  transition: border-color 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
}

.time-box:hover {
  border-color: var(--hp-gold);
  transform: translateY(-6px);
  box-shadow: 0 12px 32px rgba(201, 162, 77, 0.18);
}

.sparkle {
  position: absolute;
  top: 10px;
  right: 12px;
  font-size: 0.85rem;
  color: var(--hp-gold);
  animation: sparkle 2.5s ease-in-out infinite;
}

.time-value {
  font-family: var(--font-display);
  font-size: clamp(2.4rem, 5vw, 3.8rem);
  font-weight: 700;
  color: var(--hp-gold);
  line-height: 1;
  text-shadow: 0 0 20px rgba(201, 162, 77, 0.4);
}

.time-label {
  font-family: var(--font-display);
  font-size: 0.75rem;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--hp-silver);
}

/* Mensaje */
.magical-message {
  text-align: center;
  margin-top: 40px;
}

.magical-message p {
  font-family: var(--font-body);
  font-size: 1.3rem;
  color: var(--hp-silver);
  font-style: italic;
}

.wedding-day-message {
  font-size: 1.8rem !important;
  color: var(--hp-gold) !important;
  animation: sparkle 1.5s ease-in-out infinite;
}

/* Reloj de arena decorativo */
.hourglass-decoration {
  position: absolute;
  bottom: 28px;
  left: 50%;
  font-size: 2rem;
  opacity: 0.2;
  animation: flipHourglass 4s linear infinite;
  transform-origin: center;
}

@keyframes flipHourglass {
  0%, 49%  { transform: translateX(-50%) rotate(0deg); }
  50%, 100% { transform: translateX(-50%) rotate(180deg); }
}

@media (max-width: 640px) {
  .countdown-container {
    grid-template-columns: repeat(2, 1fr);
    gap: 16px;
  }
}

/* Estilo general del contenedor de la frase */
.vow-text {
  font-family: var(--font-body);
  font-size: 1.2rem;
  color: var(--hp-silver);
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

/* El texto dorado con "resplandor de juramento" */
.unbreakable-vow {
  color: var(--hp-gold);
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 2px;
  position: relative;
  /* Brillo constante */
  text-shadow: 0 0 10px rgba(201, 162, 77, 0.5), 0 0 20px rgba(201, 162, 77, 0.2);
  /* Animación de latido mágico */
  animation: vow-glow 4s infinite alternate ease-in-out;
}

/* Destellos que rodean el texto */
.sparkle-vow {
  color: var(--hp-gold);
  font-size: 0.9rem;
  animation: sparkle-float 2.5s infinite alternate ease-in-out;
}

/* Animación: El texto brilla como hilos de oro */
@keyframes vow-glow {
  0% {
    text-shadow: 0 0 5px rgba(201, 162, 77, 0.4);
    filter: brightness(1);
  }
  100% {
    text-shadow: 0 0 15px rgba(201, 162, 77, 0.9), 0 0 30px rgba(201, 162, 77, 0.4);
    filter: brightness(1.2);
  }
}

/* Animación: Las estrellas flotan y parpadean */
@keyframes sparkle-float {
  0% { transform: translateY(0) scale(0.8); opacity: 0.4; }
  100% { transform: translateY(-5px) scale(1.2); opacity: 1; }
}
</style>