<template>
  <section id="rsvp" class="rsvp-section section">
    <div class="container">
      <h2 class="section-title">Confirma tu Asistencia</h2>

      <p class="intro-text">
        Nos encantaría contar con tu presencia en este día tan especial.<br>
        Por favor confirma tu asistencia antes del
        <strong>30 de Agosto, 2026</strong>
      </p>

      <div class="rsvp-card fade-in">
        <div class="card-icon">✉️</div>
        <h3 class="card-title">Formulario de Confirmación</h3>
        <div class="card-divider"></div>
        <p class="card-description">
          Completa nuestro formulario con tus datos y preferencias
        </p>
        <a
          href="https://docs.google.com/forms/d/e/1FAIpQLSdeQmSASpu9hYz3omzGRn-aZW4a38shi2SRPpZu1hSeAdFETw/viewform?usp=header"
          target="_blank"
          class="magic-button rsvp-button"
        >
          Confirmar Ahora
        </a>
      </div>

      <!-- Cita de Dumbledore -->
      <div class="final-message">
        <div class="quote-marks">"</div>
        <p class="magical-quote">
          La felicidad se puede encontrar hasta en los momentos más oscuros,
          si somos capaces de usar bien la luz
        </p>
        <span class="quote-author">— Albus Dumbledore</span>
        <p class="closing-text">¡Esperamos celebrar contigo este día mágico!</p>
      </div>

    </div>
  </section>
</template>

<script>
export default { name: 'RsvpSection' }
</script>

<style scoped>
.rsvp-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  /* Asegúrate de que no tenga un height fijo que corte la sección */
  min-height: auto; 
  padding: 80px 20px;
}

.intro-text {
  font-family: var(--font-body);
  font-size: 1.2rem;
  color: var(--hp-silver);
  line-height: 1.9;
  text-align: center;
  max-width: 640px;
  margin: 0 auto 56px;
  font-style: italic;
}

.intro-text strong {
  color: var(--star-white);
  font-style: normal;
}

/* Tarjeta */
.rsvp-card {
  max-width: 520px;
  margin: 0 auto 80px;
  border: 1px solid rgba(201, 162, 77, 0.28);
  padding: 52px 44px;
  text-align: center;
  backdrop-filter: blur(10px);
  transition: border-color 0.3s ease;
}

.rsvp-container {
  display: flex;
  justify-content: center;
  width: 100%;
  margin-top: 40px; /* Separa el título del formulario */
}

.rsvp-card:hover {
  border-color: var(--hp-gold);
}

.card-icon {
  font-size: 2.8rem;
  margin-bottom: 16px;
  animation: float 4s ease-in-out infinite;
}

.card-title {
  font-family: var(--font-display);
  font-size: 1.4rem;
  color: var(--hp-gold);
  letter-spacing: 2px;
}

.card-divider {
  width: 60px;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--hp-gold), transparent);
  margin: 18px auto;
}

.card-description {
  font-family: var(--font-body);
  font-size: 1.1rem;
  color: var(--hp-silver);
  line-height: 1.8;
  margin-bottom: 32px;
}

.rsvp-button {
  font-size: 0.9rem;
  padding: 16px 44px;
}

/* Cita final */
.final-message {
  text-align: center;
  max-width: 620px;
  margin: 0 auto;
}

.quote-marks {
  font-family: var(--font-display);
  font-size: 5rem;
  color: var(--hp-gold);
  opacity: 0.25;
  line-height: 0.6;
  margin-bottom: 20px;
}

.magical-quote {
  font-family: var(--font-body);
  font-size: 1.2rem;
  color: var(--hp-silver);
  font-style: italic;
  line-height: 1.9;
  margin-bottom: 12px;
}

.quote-author {
  display: block;
  font-family: var(--font-display);
  font-size: 0.9rem;
  color: var(--hp-gold);
  letter-spacing: 3px;
  margin-bottom: 36px;
}

.closing-text {
  font-family: var(--font-display);
  font-size: 1.5rem;
  color: var(--star-white);
  letter-spacing: 2px;
}

@media (max-width: 600px) {
  .rsvp-card { padding: 36px 24px; }
  .closing-text { font-size: 1.2rem; }
}
</style>