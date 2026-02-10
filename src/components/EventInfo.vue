<template>
  <section id="evento" class="event-section section">
    <div class="container">
      <h2 class="section-title">Detalles del Gran Día</h2>
      
      <div class="event-grid">
        <!-- Ceremonia -->
        <div class="event-card fade-in">
          <div class="card-icon">💍</div>
          <h3 class="card-title">Ceremonia</h3>
          <div class="card-divider"></div>
          <div class="card-content">
            <p class="info-item">
              <span class="info-icon">📅</span>
              <span class="info-text">30 de Octubre, 2026</span>
            </p>
            <p class="info-item">
              <span class="info-icon">🕐</span>
              <span class="info-text">5:30 PM</span>
            </p>
            <p class="info-item">
              <span class="info-icon">📍</span>
              <span class="info-text">Cristo de la Colina<br>Calz De Los Corceles S/N, Colina del Sur, Álvaro Obregón, 01430 Ciudad de México, CDMX</span>
            </p>
          </div>
          <button class="location-button magic-button" @click="openLocation('ceremony')">
            Ver Ubicación
          </button>
        </div>
        
        <!-- Recepción -->
        <div class="event-card fade-in" style="animation-delay: 0.2s;">
          <div class="card-icon">🎉</div>
          <h3 class="card-title">Recepción</h3>
          <div class="card-divider"></div>
          <div class="card-content">
            <p class="info-item">
              <span class="info-icon">🕗</span>
              <span class="info-text">7:30 PM - 12:30 AM</span>
            </p>
            <p class="info-item">
              <span class="info-icon">🍽️</span>
              <span class="info-text">Cena de tres tiempos</span>
            </p>
            <p class="info-item">
              <span class="info-icon">💃</span>
              <span class="info-text">Baile hasta el amanecer</span>
            </p>
            <p class="info-item">
              <span class="info-icon">🎵</span>
              <span class="info-text">Música en vivo</span>
            </p>
          </div>
          <button class="location-button magic-button" @click="openLocation('reception')">
            Ver Ubicación
          </button>
        </div>
        
        <!-- Información Adicional -->
        <div class="event-card fade-in" style="animation-delay: 0.4s;">
          <div class="card-icon">ℹ️</div>
          <h3 class="card-title">Información Importante</h3>
          <div class="card-divider"></div>
          <div class="card-content">
            <p class="info-item">
              <span class="info-icon">🎭</span>
              <span class="info-text">Evento temático de Harry Potter</span>
            </p>
            <p class="info-item">
              <span class="info-icon">🦅</span>
              <span class="info-text">Colores: Azul y Bronce</span>
            </p>
            <p class="info-item">
              <span class="info-icon">🪄</span>
              <span class="info-text">Sorpresas mágicas durante la noche</span>
            </p>
            <p class="info-item">
              <span class="info-icon">📸</span>
              <span class="info-text">Fotógrafo profesional</span>
            </p>
          </div>
        </div>
      </div>
      
      <!-- Mapa o nota adicional -->
      <div class="additional-info">
        <p class="note">
          <span class="wand-icon">🪄</span>
          Por favor confirma tu asistencia antes del 30 de Agosto para que podamos preparar la mejor celebración mágica
          <span class="wand-icon">🪄</span>
        </p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'EventInfo',
  methods: {
    openLocation(type) {
      // Aquí puedes agregar las coordenadas reales de tu evento
      const locations = {
        ceremony: 'https://maps.app.goo.gl/6PBxWpzrpPpYFRsD6',
        reception: 'https://maps.app.goo.gl/KBhj64QpVLFujFQHA'
      }
      window.open(locations[type], '_blank')
    }
  }
}
</script>

<style scoped>
.event-section {
  background: linear-gradient(180deg, rgba(10, 14, 31, 0.9), rgba(14, 26, 64, 0.9));
  position: relative;
}

.event-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M30 30l15-15M30 30l-15 15' stroke='%23946B2D' stroke-opacity='0.1' stroke-width='1' fill='none'/%3E%3C/svg%3E");
  pointer-events: none;
  opacity: 0.3;
}

.event-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 40px;
  max-width: 1200px;
  margin: 0 auto 60px;
}

.event-card {
  background: rgba(14, 26, 64, 0.6);
  backdrop-filter: blur(10px);
  border: 2px solid var(--ravenclaw-bronze);
  padding: 40px 30px;
  text-align: center;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.event-card::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle, rgba(148, 107, 45, 0.1) 0%, transparent 70%);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.event-card:hover::before {
  opacity: 1;
}

.event-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 60px rgba(148, 107, 45, 0.4);
  border-color: var(--ravenclaw-gold);
}

.card-icon {
  font-size: 4rem;
  margin-bottom: 20px;
  animation: float 3s ease-in-out infinite;
}

.card-title {
   
  font-size: 2rem;
  color: var(--ravenclaw-bronze);
  margin-bottom: 20px;
  letter-spacing: 2px;
  font-weight: 700;
}

.card-divider {
  width: 80px;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--ravenclaw-bronze), transparent);
  margin: 20px auto;
}

.card-content {
  margin: 30px 0;
}

.info-item {
  display: flex;
  align-items: flex-start;
  gap: 15px;
  margin: 20px 0;
  /* /*font-family: var(--font-body);*/ 
  color: var(--star-white);
  font-size: 1.1rem;
  text-align: left;
}

.info-icon {
  font-size: 1.5rem;
  flex-shrink: 0;
}

.info-text {
  flex: 1;
  line-height: 1.6;
}

.location-button {
  margin-top: 20px;
  font-size: 0.9rem;
  padding: 12px 30px;
}

.additional-info {
  max-width: 900px;
  margin: 60px auto 0;
  text-align: center;
}

.note {
  /* /*font-family: var(--font-body);*/ 
  font-size: 1.3rem;
  color: var(--ravenclaw-silver);
  font-style: italic;
  line-height: 1.8;
  padding: 30px;
  background: rgba(14, 26, 64, 0.4);
  border-left: 4px solid var(--ravenclaw-bronze);
  border-right: 4px solid var(--ravenclaw-bronze);
}

.wand-icon {
  display: inline-block;
  margin: 0 10px;
  animation: sparkle 2s ease-in-out infinite;
}

@media (max-width: 768px) {
  .event-grid {
    grid-template-columns: 1fr;
    gap: 30px;
  }
  
  .event-card {
    padding: 30px 20px;
  }
  
  .card-title {
    font-size: 1.5rem;
  }
  
  .note {
    font-size: 1.1rem;
    padding: 20px;
  }
}
</style>