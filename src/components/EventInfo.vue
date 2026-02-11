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
            <div class="info-item">
              <span class="info-icon">📅</span>
              <span class="info-text">30 de Octubre, 2026</span>
            </div>
            <div class="info-item">
              <span class="info-icon">🕐</span>
              <span class="info-text">5:30 PM</span>
            </div>
            <div class="info-item">
              <span class="info-icon">📍</span>
              <span class="info-text">
                Cristo de la Colina<br>
                Calz De Los Corceles S/N, Colina del Sur,<br>
                Álvaro Obregón, 01430 CDMX
              </span>
            </div>
          </div>
          <button class="magic-button location-button" @click="openLocation('ceremony')">
            Ver Ubicación
          </button>
        </div>

        <!-- Recepción -->
        <div class="event-card fade-in" style="animation-delay: 0.15s">
          <div class="card-icon">🎉</div>
          <h3 class="card-title">Recepción</h3>
          <div class="card-divider"></div>
          <div class="card-content">
            <div class="info-item">
              <span class="info-icon">🕗</span>
              <span class="info-text">7:30 PM – 12:30 AM</span>
            </div>
            <div class="info-item">
              <span class="info-icon">🍽️</span>
              <span class="info-text">Cena de tres tiempos</span>
            </div>
            <div class="info-item">
              <span class="info-icon">💃</span>
              <span class="info-text">Baile hasta el amanecer</span>
            </div>
            <div class="info-item">
              <span class="info-icon">🎵</span>
              <span class="info-text">Música en vivo</span>
            </div>
          </div>
          <button class="magic-button location-button" @click="openLocation('reception')">
            Ver Ubicación
          </button>
        </div>

        <!-- Info adicional -->
        <div class="event-card fade-in" style="animation-delay: 0.3s">
          <div class="card-icon">🦅</div>
          <h3 class="card-title">Información Importante</h3>
          <div class="card-divider"></div>
          <div class="card-content">
            <div class="info-item">
              <span class="info-icon">🎭</span>
              <span class="info-text">Temática Harry Potter</span>
            </div>
            <div class="info-item">
              <span class="info-icon">🦅</span>
              <span class="info-text">Colores Ravenclaw: Azul & Bronce</span>
            </div>
            <div class="info-item">
              <span class="info-icon">🪄</span>
              <span class="info-text">Sorpresas mágicas durante la noche</span>
            </div>
            <div class="info-item">
              <span class="info-icon">📸</span>
              <span class="info-text">Fotógrafo profesional</span>
            </div>
          </div>
        </div>

      </div>

      <!-- Nota -->
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
      const locations = {
        ceremony:  'https://maps.app.goo.gl/6PBxWpzrpPpYFRsD6',
        reception: 'https://maps.app.goo.gl/KBhj64QpVLFujFQHA'
      }
      window.open(locations[type], '_blank')
    }
  }
}
</script>

<style scoped>
.event-section {
  background: linear-gradient(180deg, rgba(10,14,31,0.4) 0%, rgba(14,26,64,0.4) 100%);
}

.event-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(290px, 1fr));
  gap: 32px;
  max-width: 1100px;
  margin: 0 auto 60px;
}

/* Tarjeta */
.event-card {
  border: 1px solid rgba(201, 162, 77, 0.22);
  border-radius: 2px;
  padding: 36px 28px;
  backdrop-filter: blur(8px);
  transition: border-color 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
}

.event-card:hover {
  border-color: var(--hp-gold);
  transform: translateY(-6px);
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.4);
}

.card-icon {
  font-size: 2.2rem;
  margin-bottom: 12px;
  animation: float 4s ease-in-out infinite;
}

.card-title {
  font-family: var(--font-display);
  font-size: 1.25rem;
  color: var(--hp-gold);
  letter-spacing: 2px;
  margin-bottom: 4px;
}

.card-divider {
  width: 48px;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--hp-gold), transparent);
  margin: 16px 0;
}

.card-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 14px;
  margin-bottom: 28px;
}

.info-item {
  display: flex;
  align-items: flex-start;
  gap: 12px;
}

.info-icon {
  font-size: 1.2rem;
  flex-shrink: 0;
  margin-top: 1px;
}

.info-text {
  font-family: var(--font-body);
  font-size: 1.05rem;
  color: var(--hp-silver);
  line-height: 1.6;
}

.location-button {
  align-self: flex-start;
  font-size: 0.78rem;
  padding: 10px 24px;
}

/* Nota */
.additional-info {
  max-width: 800px;
  margin: 0 auto;
}

.note {
  font-family: var(--font-body);
  font-size: 1.15rem;
  color: var(--hp-silver);
  font-style: italic;
  line-height: 1.9;
  text-align: center;
  padding: 28px 36px;
  border-left: 2px solid rgba(201, 162, 77, 0.4);
  border-right: 2px solid rgba(201, 162, 77, 0.4);
}

.wand-icon {
  display: inline-block;
  margin: 0 8px;
  animation: sparkle 2s ease-in-out infinite;
}

@media (max-width: 768px) {
  .event-grid { grid-template-columns: 1fr; }
  .note { padding: 20px; font-size: 1rem; }
}
</style>