<template>
  <section id="rsvp" class="rsvp-section section">
    <div class="container">
      <h2 class="section-title">Confirma tu Asistencia</h2>
      
      <div class="rsvp-intro">
        <p class="intro-text">
          Nos encantaría contar con tu presencia en este día tan especial.<br>
          Por favor confirma tu asistencia antes del <strong>30 de Agosto, 2026</strong>
        </p>
      </div>
      
      <div class="rsvp-container">
        <!-- Opción 1: Formulario embebido de Google Forms -->
        <div class="rsvp-card">
          <div class="card-icon">✉️</div>
          <h3 class="card-title">Formulario de Confirmación</h3>
          <div class="card-divider"></div>
          <p class="card-description">
            Completa nuestro formulario de confirmación con tus datos y preferencias
          </p>
          <a 
            href="https://docs.google.com/forms/d/e/1FAIpQLSdeQmSASpu9hYz3omzGRn-aZW4a38shi2SRPpZu1hSeAdFETw/viewform?usp=header" 
            target="_blank" 
            class="rsvp-button magic-button"
          >
            Confirmar Ahora
          </a>
        </div>
        
        
      </div>
      
      
      
      <!-- Mensaje final -->
      <div class="final-message">
        <p class="magical-quote">
          "La felicidad se puede encontrar hasta en los momentos más oscuros,<br>
          si somos capaces de usar bien la luz"<br>
          <span class="quote-author">- Albus Dumbledore</span>
        </p>
        <p class="closing-text">
          ¡Esperamos celebrar contigo este día mágico!
        </p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'RsvpSection'
}
</script>

<style scoped>
.rsvp-section {
  background: linear-gradient(180deg, rgba(14, 26, 64, 0.95), rgba(10, 14, 31, 0.95));
  position: relative;
}

.rsvp-intro {
  text-align: center;
  max-width: 800px;
  margin: 0 auto 60px;
}

.intro-text {
  /*font-family: var(--font-body);*/
  font-size: 1.3rem;
  color: var(--ravenclaw-silver);
  line-height: 1.8;
}

.intro-text strong {
  color: var(--ravenclaw-bronze);
  font-weight: 600;
}

.rsvp-container {
  display: flex;             /* Cambiamos de grid a flex */
  justify-content: center;    /* Centra el contenido horizontalmente */
  align-items: center;        /* Centra el contenido verticalmente si fuera necesario */
  gap: 40px;
  max-width: 1200px;
  margin: 0 auto 80px;
}

.rsvp-card {
  /* ... tus otras propiedades ... */
  max-width: 500px;           /* Añade un ancho máximo para que no se estire demasiado */
  width: 100%;                /* Permite que sea responsivo */
  background: rgba(14, 26, 64, 0.6);
  backdrop-filter: blur(10px);
  border: 3px solid var(--ravenclaw-bronze);
  padding: 50px 40px;
  text-align: center;
}

.card-icon {
  font-size: 5rem;
  margin-bottom: 25px;
  animation: float 3s ease-in-out infinite;
}

.card-title {
  /*font-family: var(--font-display);*/
  font-size: 2rem;
  color: var(--ravenclaw-bronze);
  margin-bottom: 20px;
  letter-spacing: 2px;
  font-weight: 700;
}

.card-divider {
  width: 100px;
  height: 3px;
  background: linear-gradient(90deg, transparent, var(--ravenclaw-bronze), transparent);
  margin: 25px auto;
}

.card-description {
  /*font-family: var(--font-body);*/
  font-size: 1.2rem;
  color: var(--star-white);
  line-height: 1.8;
  margin-bottom: 35px;
}

.rsvp-button {
  font-size: 1.2rem;
  padding: 18px 50px;
  text-decoration: none;
  display: inline-block;
  margin-bottom: 30px;
}

.embed-note {
  margin-top: 30px;
  padding: 20px;
  background: rgba(148, 107, 45, 0.1);
  border-left: 3px solid var(--ravenclaw-bronze);
  text-align: left;
}

.embed-note p {
  /*font-family: var(--font-body);*/
  font-size: 0.95rem;
  color: var(--ravenclaw-silver);
  line-height: 1.6;
}

/* Info de RSVP */
.rsvp-info {
  background: rgba(26, 47, 95, 0.4);
  border: 2px solid var(--ravenclaw-bronze);
  padding: 40px 30px;
}

.info-title {
  /*font-family: var(--font-display);*/
  font-size: 1.5rem;
  color: var(--ravenclaw-bronze);
  margin-bottom: 30px;
  text-align: center;
  letter-spacing: 2px;
}

.info-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.info-item {
  display: flex;
  align-items: center;
  gap: 15px;
  /*font-family: var(--font-body);*/
  color: var(--star-white);
  font-size: 1.1rem;
}

.info-icon {
  font-size: 1.8rem;
  flex-shrink: 0;
}

.info-text {
  line-height: 1.6;
}

/* Formulario embebido */
.embedded-form-section {
  max-width: 900px;
  margin: 80px auto;
}

.embedded-title {
  /*font-family: var(--font-display);*/
  font-size: 2rem;
  color: var(--ravenclaw-bronze);
  text-align: center;
  margin-bottom: 40px;
  letter-spacing: 2px;
}

.form-container {
  background: white;
  padding: 20px;
  border: 3px solid var(--ravenclaw-bronze);
  box-shadow: 0 10px 50px rgba(148, 107, 45, 0.3);
}

.google-form {
  display: block;
  width: 100%;
  min-height: 800px;
  border: none;
}

.form-placeholder {
  background: rgba(14, 26, 64, 0.6);
  border: 2px dashed var(--ravenclaw-bronze);
  padding: 50px 30px;
  text-align: center;
  margin-top: 30px;
}

.placeholder-icon {
  font-size: 4rem;
  margin-bottom: 20px;
}

.placeholder-text {
  /*font-family: var(--font-body);*/
  font-size: 1.1rem;
  color: var(--ravenclaw-silver);
  line-height: 1.8;
}

/* Contacto alternativo */
.alternative-contact {
  max-width: 700px;
  margin: 80px auto;
}

.contact-box {
  background: rgba(14, 26, 64, 0.6);
  border: 2px solid var(--ravenclaw-bronze);
  padding: 40px;
  text-align: center;
}

.contact-title {
  /*font-family: var(--font-display);*/
  font-size: 1.5rem;
  color: var(--ravenclaw-bronze);
  margin-bottom: 15px;
  letter-spacing: 2px;
}

.contact-text {
  /*font-family: var(--font-body);*/
  font-size: 1.1rem;
  color: var(--star-white);
  margin-bottom: 25px;
}

.contact-methods {
  display: flex;
  flex-direction: column;
  gap: 15px;
  align-items: center;
}

.contact-link {
  display: flex;
  align-items: center;
  gap: 10px;
  /*font-family: var(--font-body);*/
  font-size: 1.1rem;
  color: var(--star-white);
  text-decoration: none;
  padding: 12px 25px;
  background: rgba(26, 47, 95, 0.5);
  border: 1px solid var(--ravenclaw-bronze);
  transition: all 0.3s ease;
  min-width: 280px;
  justify-content: center;
}

.contact-link:hover {
  background: var(--ravenclaw-bronze);
  color: var(--ravenclaw-blue);
  transform: translateX(10px);
}

.contact-icon {
  font-size: 1.5rem;
}

/* Mensaje final */
.final-message {
  max-width: 800px;
  margin: 80px auto 0;
  text-align: center;
}

.magical-quote {
  /*font-family: var(--font-body);*/
  font-size: 1.4rem;
  color: var(--ravenclaw-silver);
  font-style: italic;
  line-height: 1.8;
  margin-bottom: 20px;
}

.quote-author {
  display: block;
  margin-top: 15px;
  font-size: 1.1rem;
  color: var(--ravenclaw-bronze);
}

.closing-text {
  /*font-family: var(--font-display);*/
  font-size: 1.8rem;
  color: var(--ravenclaw-bronze);
  margin-top: 40px;
  letter-spacing: 2px;
  font-weight: 600;
}

@media (max-width: 768px) {
  .rsvp-container {
    flex-direction: column;   /* Alinea las tarjetas una debajo de otra en móviles */
    gap: 30px;
  }
  
  .rsvp-card {
    padding: 40px 25px;
  }
  
  .contact-methods {
    width: 100%;
  }
  
  .contact-link {
    min-width: 100%;
  }
  
  .magical-quote {
    font-size: 1.2rem;
  }
  
  .closing-text {
    font-size: 1.5rem;
  }
}
</style>