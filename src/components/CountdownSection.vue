<template>
  <section id="cuenta-regresiva" class="countdown-section section">
    <div class="container">
      <h2 class="section-title">La Magia Está Por Comenzar</h2>
      
      <div class="countdown-container">
        <div class="time-unit" v-for="(unit, index) in timeUnits" :key="index">
          <div class="time-box">
            <div class="time-value">{{ unit.value }}</div>
            <div class="time-sparkle">✨</div>
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
      
      <!-- Relojes de arena decorativos -->
      <div class="hourglass-decoration">⌛</div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'CountdownSection',
  props: {
    weddingDate: {
      type: Date,
      required: true
    }
  },
  data() {
    return {
      timeRemaining: {
        days: 0,
        hours: 0,
        minutes: 0,
        seconds: 0,
        total: 0
      },
      interval: null
    }
  },
  computed: {
    timeUnits() {
      return [
        { value: String(this.timeRemaining.days).padStart(2, '0'), label: 'Días' },
        { value: String(this.timeRemaining.hours).padStart(2, '0'), label: 'Horas' },
        { value: String(this.timeRemaining.minutes).padStart(2, '0'), label: 'Minutos' },
        { value: String(this.timeRemaining.seconds).padStart(2, '0'), label: 'Segundos' }
      ]
    },
    daysUntilWedding() {
      return this.timeRemaining.days
    }
  },
  mounted() {
    this.updateCountdown()
    this.interval = setInterval(this.updateCountdown, 1000)
  },
  beforeUnmount() {
    if (this.interval) {
      clearInterval(this.interval)
    }
  },
  methods: {
    updateCountdown() {
      const now = new Date().getTime()
      const distance = this.weddingDate.getTime() - now
      
      this.timeRemaining.total = distance
      
      if (distance > 0) {
        this.timeRemaining.days = Math.floor(distance / (1000 * 60 * 60 * 24))
        this.timeRemaining.hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
        this.timeRemaining.minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60))
        this.timeRemaining.seconds = Math.floor((distance % (1000 * 60)) / 1000)
      } else {
        this.timeRemaining = { days: 0, hours: 0, minutes: 0, seconds: 0, total: 0 }
      }
    }
  }
}
</script>

<style scoped>
.countdown-section {
  background: linear-gradient(135deg, rgba(14, 26, 64, 0.8), rgba(26, 47, 95, 0.8));
  position: relative;
  overflow: hidden;
}

.countdown-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    radial-gradient(circle at 20% 50%, rgba(148, 107, 45, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 80% 80%, rgba(212, 175, 55, 0.1) 0%, transparent 50%);
  pointer-events: none;
}

.countdown-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 30px;
  max-width: 900px;
  margin: 0 auto 50px;
  padding: 0 20px;
}

.time-unit {
  text-align: center;
  animation: fadeIn 0.8s ease-out forwards;
}

.time-unit:nth-child(1) { animation-delay: 0.1s; }
.time-unit:nth-child(2) { animation-delay: 0.2s; }
.time-unit:nth-child(3) { animation-delay: 0.3s; }
.time-unit:nth-child(4) { animation-delay: 0.4s; }

.time-box {
  position: relative;
  background: linear-gradient(135deg, var(--ravenclaw-blue), var(--ravenclaw-blue-light));
  border: 3px solid var(--ravenclaw-bronze);
  padding: 30px 20px;
  margin-bottom: 15px;
  box-shadow: 0 10px 40px rgba(148, 107, 45, 0.3);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.time-box:hover {
  transform: translateY(-10px);
  box-shadow: 0 15px 50px rgba(148, 107, 45, 0.5);
}

.time-value {
   
  font-size: 4rem;
  font-weight: 700;
  color: var(--ravenclaw-bronze);
  line-height: 1;
  text-shadow: 0 0 20px rgba(148, 107, 45, 0.5);
}

.time-sparkle {
  position: absolute;
  top: 10px;
  right: 10px;
  font-size: 1.5rem;
  animation: sparkle 2s ease-in-out infinite;
}

.time-label {
   
  font-size: 1.2rem;
  color: var(--ravenclaw-silver);
  text-transform: uppercase;
  letter-spacing: 2px;
  font-weight: 600;
}

.magical-message {
  text-align: center;
  margin-top: 50px;
}

.magical-message p {
  /* /*font-family: var(--font-body);*/ 
  font-size: 1.5rem;
  color: var(--star-white);
  font-style: italic;
  line-height: 1.8;
}

.wedding-day-message {
  font-size: 2rem !important;
  color: var(--ravenclaw-gold) !important;
  font-weight: 600;
  animation: sparkle 1.5s ease-in-out infinite;
}

.hourglass-decoration {
  position: absolute;
  bottom: 30px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 3rem;
  opacity: 0.3;
  animation: rotate 4s linear infinite;
}

@keyframes rotate {
  0%, 50% {
    transform: translateX(-50%) rotate(0deg);
  }
  51%, 100% {
    transform: translateX(-50%) rotate(180deg);
  }
}

@media (max-width: 768px) {
  .countdown-container {
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }
  
  .time-value {
    font-size: 3rem;
  }
  
  .time-box {
    padding: 20px 15px;
  }
  
  .magical-message p {
    font-size: 1.2rem;
  }
}

@media (max-width: 480px) {
  .countdown-container {
    grid-template-columns: repeat(2, 1fr);
    gap: 15px;
  }
  
  .time-value {
    font-size: 2.5rem;
  }
  
  .time-label {
    font-size: 1rem;
  }
}
</style>