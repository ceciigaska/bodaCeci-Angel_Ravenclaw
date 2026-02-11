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
        <p v-if="timeRemaining.total > 0">
          {{ daysUntilWedding }} días hasta que unamos nuestras varitas mágicas
        </p>
        <p v-else class="wedding-day-message">
          ¡Hoy es nuestro día mágico! ✨🎉
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
</style>