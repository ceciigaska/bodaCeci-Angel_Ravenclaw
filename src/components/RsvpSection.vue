<template>
  <section id="rsvp" class="rsvp-section section">
    <div class="container">
      <h2 class="section-title">Confirma tu Asistencia</h2>

      <p class="intro-text">
        Nos encantaría contar con tu presencia en este día tan especial.<br />
        Por favor confirma tu asistencia antes del
        <strong>30 de Agosto, 2026</strong>
      </p>

      <div class="rsvp-card fade-in">
        <div class="card-icon">
          <svg
            viewBox="0 0 32 32"
            fill="none"
            stroke="currentColor"
            stroke-width="1.3"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <!-- Sobre estilo Mágico HP -->
            <rect x="4" y="9" width="24" height="14" rx="0.5" />
            <path d="M4 9l12 7 12-7" />
            <!-- Sello Hogwarts simplificado -->
            <circle cx="16" cy="16" r="3.5" />
            <path d="M16 13v1M16 19v1M13 16h1M19 16h1" stroke-width="1" />
            <path
              d="M14 14l.5.5M17.5 17.5l.5.5M14 18l.5-.5M17.5 14.5l.5-.5"
              stroke-width="0.8"
            />
          </svg>
        </div>
        <h3 class="card-title">Formulario de Confirmación</h3>
        <div class="card-divider"></div>
        <p class="card-description">
          Completa nuestro formulario con tus datos y preferencias
        </p>
        <!-- <a
          href="https://docs.google.com/forms/d/e/1FAIpQLSdeQmSASpu9hYz3omzGRn-aZW4a38shi2SRPpZu1hSeAdFETw/viewform?usp=header"
          target="_blank"
          class="magic-button rsvp-button"
        >
          Confirmar Ahora
        </a> -->
        <div v-if="step === 1" class="search-box">
  <input
    v-model="busqueda"
    @input="filtrar"
    type="text"
    placeholder="Escribe tu nombre completo..."
    class="magic-input"
  />
  
  <div v-if="sugerencias.length" class="suggestions">
    <div v-for="inv in sugerencias" :key="inv.nombre" @click="seleccionar(inv)" class="suggestion-item">
      {{ inv.nombre }}
    </div>
  </div>

  <div v-if="busqueda.length >= 3 && sugerencias.length === 0" class="no-results-merodeador">
    <p class="error-text-magico">Nombre no detectado en el mapa</p>
    <p class="contact-text-magico">
      Parece que tu nombre no ha sido escrito con tinta invisible en este pergamino.<br>
      Por favor, contacta a los novios para cualquier tema.
    </p>
    <div class="merodeador-footer">I SOLEMNLY SWEAR THAT I AM UP TO NO GOOD</div>
  </div>
</div>

<div v-else-if="step === 2" class="details-box">
  <p class="permitidos-text">Tienes {{ invitadoSeleccionado.permitidos }} lugares reservados</p>
  <div class="guests-inputs">
    <div v-for="(asistente, index) in asistentes" :key="index" class="input-group">
      <label class="input-label">{{ index === 0 ? 'Invitado Principal' : 'Acompañante ' + index }}</label>
      <input
        :value="asistentes[index]"
        @input="(e) => { asistentes[index] = e.target.value }"
        :placeholder="index === 0 ? '' : 'Nombre del acompañante'"
        :readonly="index === 0"
        class="magic-input guest-input"
        :class="{ 'titular-readonly': index === 0 }"
      />
    </div>
  </div>
  <button @click="enviarConfirmacion" class="magic-button rsvp-button" :disabled="loading">
    {{ loading ? 'Enviando lechuza...' : 'Confirmar con Magia' }}
  </button>
</div>

<div v-else-if="step === 3" class="success-message">
  <div v-if="asistentes.length === 1">
    <p class="magical-quote">¡Travesura realizada!</p>
    <p class="success-detail">Tu lugar individual ha sido reservado en el Gran Comedor. ¡Nos vemos pronto!</p>
  </div>
  <div v-else>
    <p class="magical-quote">¡Hechizo de grupo completado!</p>
    <p class="success-detail">Tus {{ asistentes.length }} lugares han sido registrados. ¡Toda la familia está lista para la celebración!</p>
  </div>
</div>
        <div v-if="animating" class="magic-particles">
          <div v-for="n in 12" :key="n" class="particle"></div>
        </div>
      </div>

      <!-- Cita de Dumbledore -->
      <div class="final-message">
        <div class="quote-marks">"</div>
        <p class="magical-quote">
          La felicidad se puede encontrar hasta en los momentos más oscuros, si
          somos capaces de usar bien la luz
        </p>
        <span class="quote-author">— Albus Dumbledore</span>
        <p class="closing-text">¡Esperamos celebrar contigo este día mágico!</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "RsvpSection",
  data() {
    return {
      apiUrl:
        "https://script.google.com/macros/s/AKfycbwxoZMb02xSPA0PDl2hcnDWj42-gSHq5yVqZW73COtIk1SXyfs4SgXz013swlZnnibJ8g/exec", // Reemplaza con tu URL implementada
      step: 1, // 1: Buscador, 2: Formulario de acompañantes, 3: Éxito
      busqueda: "",
      invitadosData: [], // Se llenará desde tu Sheet
      sugerencias: [],
      invitadoSeleccionado: null,
      asistentes: [],
      loading: false,
      animating: false,
    };
  },
  async mounted() {
    // Cargamos los invitados al inicio para que el buscador sea instantáneo
    try {
      const response = await fetch(this.apiUrl);
      this.invitadosData = await response.json();
    } catch (e) {
      console.error("Error cargando invitados", e);
    }
  },
  methods: {
    filtrar() {
      if (this.busqueda.length < 3) {
        this.sugerencias = [];
        return;
      }
      this.sugerencias = this.invitadosData
        .filter((i) =>
          i.nombre.toLowerCase().includes(this.busqueda.toLowerCase()),
        )
        .slice(0, 5); // Limitamos a 5 sugerencias por estética
    },
    seleccionar(invitado) {
  this.triggerMagic(); // Polvo de estrellas
  this.invitadoSeleccionado = invitado;
  this.busqueda = invitado.nombre;
  this.sugerencias = [];
  
  // Forzamos conversión robusta a número
  const totalLugares = Number(invitado.permitidos) > 0 ? Number(invitado.permitidos) : 1;
  
  // Construimos el array completo de una vez (evita mutar por índice para mantener reactividad en Vue 2)
  this.asistentes = Array.from({ length: totalLugares }, (_, i) => i === 0 ? invitado.nombre : "");
  
  this.step = 2; // Avanzamos al formulario de acompañantes
},

    triggerMagic() {
      this.animating = true;
      setTimeout(() => {
        this.animating = false;
      }, 1500);
    },
   async enviarConfirmacion() {
  // VALIDACIÓN: Evita que envíen acompañantes vacíos
  const hayCamposVacios = this.asistentes.some(nombre => !nombre || nombre.trim() === "");
  if (hayCamposVacios) {
    alert("Por favor, escribe los nombres de todos tus acompañantes mágicos.");
    return;
  }

  this.loading = true;
  try {
    const data = {
      nombrePrincipal: this.invitadoSeleccionado.nombre,
      asistencia: "Confirmado",
      totalAsistentes: this.asistentes.length,
      nombresAsistentes: this.asistentes.join(", ")
    };

    await fetch(this.apiUrl, {
      method: 'POST',
      mode: 'no-cors', 
      body: JSON.stringify(data)
    });

    this.triggerMagic();
    this.step = 3;
  } catch (e) {
    alert("Hubo un error con la conexión de la Red Flu.");
  } finally {
    this.loading = false;
  }
}
  },
};
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
  width: 64px;
  height: 64px;
  margin: 0 auto 16px;
  color: var(--hp-gold);
  animation: float 4s ease-in-out infinite;
  filter: drop-shadow(0 0 8px rgba(201, 162, 77, 0.3));
}

.card-icon svg {
  width: 100%;
  height: 100%;
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
  .rsvp-card {
    width: 100%;
    padding: 30px 20px; /* Reduce paddings internos */
  }
  .closing-text {
    font-size: 1.2rem;
  }
}
.magic-input {
  width: 100%;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid var(--hp-gold);
  padding: 12px;
  color: var(--star-white);
  font-family: var(--font-body);
  margin-bottom: 10px;
  text-align: center;
}

.suggestions {
  background: #1a1a1a;
  border: 1px solid var(--hp-gold);
  position: absolute;
  width: 100%;
  z-index: 10;
  max-width: 432px; /* Alineado con el padding de la card */
}

.suggestion-item {
  padding: 10px;
  cursor: pointer;
  color: var(--hp-silver);
}

.suggestion-item:hover {
  background: var(--hp-gold);
  color: #000;
}

.permitidos-text {
  color: var(--hp-gold);
  margin-bottom: 20px;
  font-family: var(--font-display);
}

.guest-input {
  font-size: 0.9rem;
  margin-bottom: 8px;
}
.magic-particles {
  position: absolute;
  top: 50%;
  left: 50%;
  pointer-events: none;
  z-index: 20;
}

.particle {
  position: absolute;
  width: 6px;
  height: 6px;
  background: var(--hp-gold);
  box-shadow:
    0 0 10px var(--hp-gold),
    0 0 20px var(--hp-silver);
  border-radius: 50%;
  opacity: 0;
  animation: explode 1.5s ease-out forwards;
}

/* Variar colores y posiciones para las 12 partículas */
.particle:nth-child(odd) {
  background: var(--hp-silver);
}
.particle:nth-child(2n) {
  animation-delay: 0.1s;
}
.particle:nth-child(3n) {
  animation-delay: 0.2s;
}

@keyframes explode {
  0% {
    transform: translate(-50%, -50%) scale(0);
    opacity: 1;
  }
  100% {
    /* Crea una explosión en diferentes direcciones */
    transform: translate(
        calc(-50% + (var(--dir-x, 100px) * 1)),
        calc(-50% + (var(--dir-y, 100px) * 1))
      )
      scale(1);
    opacity: 0;
  }
}

/* Definición manual de direcciones para que parezca una explosión circular */
.particle:nth-child(1) {
  --dir-x: 80px;
  --dir-y: -80px;
}
.particle:nth-child(2) {
  --dir-x: -80px;
  --dir-y: 80px;
}
.particle:nth-child(3) {
  --dir-x: 0px;
  --dir-y: -110px;
}
.particle:nth-child(4) {
  --dir-x: 110px;
  --dir-y: 0px;
}
.particle:nth-child(5) {
  --dir-x: -90px;
  --dir-y: -40px;
}
.particle:nth-child(6) {
  --dir-x: 40px;
  --dir-y: 90px;
}
/* ... puedes añadir más variaciones de dirección aquí ... */

.input-group {
  margin-bottom: 15px;
  text-align: left;
}

.input-label {
  display: block;
  font-family: var(--font-body);
  color: var(--hp-gold);
  font-size: 0.8rem;
  margin-bottom: 5px;
  text-transform: uppercase;
  letter-spacing: 1px;
  padding-left: 5px;
}

.titular-input {
  border-color: var(--hp-silver);
  opacity: 0.8;
  cursor: not-allowed;
  background: rgba(255, 255, 255, 0.1);
}

.guests-inputs {
  max-height: 300px; /* Por si son muchos invitados, permite scroll */
  overflow-y: auto;
  padding-right: 10px;
  margin-bottom: 20px;
}

/* Scrollbar estilo pergamino */
.guests-inputs::-webkit-scrollbar {
  width: 4px;
}
.guests-inputs::-webkit-scrollbar-thumb {
  background: var(--hp-gold);
}

.error-msg-magic {
  margin-top: 15px;
  color: #ff4d4d; /* Un rojo que resalte pero suave */
  font-family: var(--font-body);
  animation: shake 0.5s;
}

.error-msg-magic p {
  font-weight: bold;
  margin-bottom: 0;
}

.titular-readonly {
  border-color: var(--hp-silver) !important;
  opacity: 0.7;
  cursor: not-allowed;
}

@keyframes shake {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-5px); }
  75% { transform: translateX(5px); }
}

/* Estilo Mapa del Merodeador */
.no-results-merodeador {
  margin-top: 20px;
  padding: 20px;
  background: rgba(244, 228, 188, 0.05);
  border: 1px dashed var(--hp-gold);
  border-radius: 8px;
  position: relative;
  animation: shake 0.5s ease-in-out;
}

.error-text-magico {
  font-family: var(--font-display);
  color: var(--hp-gold);
  font-size: 1.1rem;
  margin-bottom: 8px;
  text-transform: uppercase;
  letter-spacing: 2px;
}

.contact-text-magico {
  font-family: var(--font-body);
  color: var(--hp-silver);
  font-size: 0.95rem;
  font-style: italic;
  line-height: 1.6;
}

.merodeador-footer {
  margin-top: 15px;
  font-size: 0.7rem;
  color: var(--hp-gold);
  opacity: 0.6;
  letter-spacing: 3px;
  text-transform: uppercase;
}

.success-detail {
  font-family: var(--font-body);
  color: var(--hp-silver);
  margin-top: 10px;
}

@keyframes shake {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-5px); }
  75% { transform: translateX(5px); }
}
</style>