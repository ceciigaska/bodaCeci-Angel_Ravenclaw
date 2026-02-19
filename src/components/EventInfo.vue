<template>
  <section id="evento" class="event-section section">
    <div class="container">
      <h2 class="section-title">Detalles del Gran Día</h2>

      <div class="event-grid">
        <!-- Ceremonia -->
        <div class="event-card fade-in">
          <div class="card-icon">
            <!-- Anillos estilo Mágico HP -->
            <svg
              viewBox="0 0 32 32"
              fill="none"
              stroke="currentColor"
              stroke-width="1.3"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <path d="M12 16m-6,0a6,6 0 1,0 12,0a6,6 0 1,0 -12,0" />
              <path d="M20 16m-6,0a6,6 0 1,0 12,0a6,6 0 1,0 -12,0" />
              <path
                d="M12 10l1 1M20 10l-1 1"
                stroke-width="0.9"
                opacity="0.5"
              />
              <circle
                cx="16"
                cy="16"
                r="0.8"
                fill="currentColor"
                stroke="none"
                opacity="0.6"
              />
            </svg>
          </div>
          <h3 class="card-title">Ceremonia</h3>
          <div class="card-divider"></div>
          <div class="card-content">
            <div class="info-item">
              <span class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  width="20"
                  height="20"
                >
                  <rect x="3" y="4" width="18" height="17" rx="1" />
                  <line x1="3" y1="9" x2="21" y2="9" />
                  <line x1="8" y1="2" x2="8" y2="6" />
                  <line x1="16" y1="2" x2="16" y2="6" />
                  <path
                    d="M7 13h2v2H7zM11 13h2v2h-2zM15 13h2v2h-2zM7 17h2v2H7zM11 17h2v2h-2z"
                    stroke-width="0.8"
                  />
                </svg>
              </span>
              <span class="info-text">30 de Octubre, 2026</span>
            </div>
            <div class="info-item">
              <span class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  width="20"
                  height="20"
                >
                  <circle cx="12" cy="12" r="9" />
                  <path d="M12 7v5l3 3" />
                  <path
                    d="M12 3v1M12 20v1M3 12h1M20 12h1"
                    stroke-width="0.9"
                    opacity="0.5"
                  />
                </svg>
              </span>
              <span class="info-text">5:30 PM</span>
            </div>
            <div class="info-item">
              <span class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  width="20"
                  height="20"
                >
                  <path
                    d="M12 2C8.7 2 6 4.7 6 8c0 5 6 13 6 13s6-8 6-13c0-3.3-2.7-6-6-6z"
                  />
                  <circle cx="12" cy="8" r="2.5" />
                  <path
                    d="M8 19 Q12 22 16 19"
                    stroke-width="0.8"
                    opacity="0.4"
                  />
                </svg>
              </span>
              <span class="info-text">
                Cristo de la Colina<br />
                Calz De Los Corceles S/N, Colina del Sur,<br />
                Álvaro Obregón, 01430 CDMX
              </span>
            </div>
            <div class="info-item">
              <div class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                >
                  <path
                    d="M19 17h2c.6 0 1-.4 1-1v-3c0-.9-.7-1.7-1.5-1.9C18.7 10.6 16 10 16 10s-1.3-1.4-2.2-2.3c-.5-.4-1.1-.7-1.8-.7H5c-1.1 0-2 .9-2 2v7c0 1.1.9 2 2 2h2"
                  />
                  <circle cx="7" cy="17" r="2" />
                  <circle cx="17" cy="17" r="2" />
                </svg>
              </div>
              <div class="parking-note">
    <span class="magic-star">✦</span>
    <p>La iglesia cuenta con estacionamiento <strong>muy pequeño</strong>; sugerimos llegar con anticipación para asegurar lugar.</p>
  </div>
            </div>
          </div>
          <button
            class="magic-button location-button"
            @click="openLocation('ceremony')"
          >
            <span>📍 Explorar los alrededores</span>
          </button>
        </div>

        <!-- Recepción -->
        <div class="event-card fade-in" style="animation-delay: 0.15s">
          <div class="card-icon">
            <!-- Sombrero de fiesta estilo Mágico HP -->
            <svg
              viewBox="0 0 32 32"
              fill="none"
              stroke="currentColor"
              stroke-width="1.3"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <path d="M8 24l8-16 8 16z" />
              <line x1="6" y1="24" x2="26" y2="24" />
              <path d="M11 16h10M13 20h6" stroke-width="0.9" opacity="0.4" />
              <circle cx="16" cy="7" r="1" fill="currentColor" stroke="none" />
              <path
                d="M14 4l.3 1 1 .3-1 .3-.3 1-.3-1-1-.3 1-.3z"
                fill="currentColor"
                stroke="none"
                opacity="0.7"
              />
              <path
                d="M18 4l.3 1 1 .3-1 .3-.3 1-.3-1-1-.3 1-.3z"
                fill="currentColor"
                stroke="none"
                opacity="0.7"
              />
            </svg>
          </div>
          <h3 class="card-title">Recepción</h3>
          <div class="card-divider"></div>
          <div class="card-content">
            <div class="info-item">
              <span class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  width="20"
                  height="20"
                >
                  <circle cx="12" cy="12" r="9" />
                  <path d="M12 7v5l3 3" />
                  <path
                    d="M12 3v1M12 20v1M3 12h1M20 12h1"
                    stroke-width="0.9"
                    opacity="0.5"
                  />
                </svg>
              </span>
              <span class="info-text">7:30 PM – 12:30 AM</span>
            </div>
            <div class="info-item">
              <span class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  width="20"
                  height="20"
                >
                  <!-- Tenedor -->
                  <line x1="7" y1="3" x2="7" y2="10" />
                  <path d="M5 3v4a2 2 0 0 0 4 0V3" />
                  <line x1="7" y1="10" x2="7" y2="21" />
                  <!-- Cuchillo -->
                  <path d="M17 3 Q19 6 19 10H15V3z" />
                  <line x1="17" y1="10" x2="17" y2="21" />
                </svg>
              </span>
              <span class="info-text">Cena de tres tiempos</span>
            </div>
            <div class="info-item">
              <span class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  width="20"
                  height="20"
                >
                  <circle cx="12" cy="4" r="2" />
                  <path d="M10 8 Q8 12 9 16l-3 5" />
                  <path d="M10 8 Q13 10 15 8l2 5" />
                  <path d="M9 16 Q12 18 14 15l1 6" />
                  <path d="M6 18 Q9 20 9 16" stroke-width="0.8" opacity="0.5" />
                </svg>
              </span>
              <span class="info-text">Baile hasta el amanecer</span>
            </div>
            <div class="info-item">
              <div class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                >
                  <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z" />
                  <path d="M12 8v4" />
                  <path d="M12 16h.01" />
                </svg>
              </div>
              <div class="parking-note alert">
    <span class="magic-star">✦</span>
    <p>El salón <strong>no cuenta con estacionamiento propio</strong>. Recomendamos llegar temprano para localizar lugar en las calles aledañas.</p>
  </div>
            </div>
          </div>
          <button
            class="magic-button location-button"
            @click="openLocation('reception')"
          >
           <span>📍 Revelar ubicación del Salón</span>
          </button>
        </div>

        <!-- Info adicional -->
        <div class="event-card fade-in" style="animation-delay: 0.3s">
          <div class="card-icon">
            <!-- Águila Ravenclaw -->
            <svg
              viewBox="0 0 48 48"
              fill="none"
              stroke="currentColor"
              stroke-width="1.3"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <!-- Cuerpo -->
              <ellipse cx="24" cy="28" rx="7" ry="9" />
              <!-- Cabeza -->
              <circle cx="24" cy="16" r="5" />
              <!-- Pico -->
              <path
                d="M22 17l-3 3 5-1z"
                fill="currentColor"
                stroke="none"
                opacity="0.7"
              />
              <!-- Alas extendidas -->
              <path d="M17 26 Q10 20 6 22 Q10 28 17 28" />
              <path d="M31 26 Q38 20 42 22 Q38 28 31 28" />
              <!-- Plumas ala izquierda -->
              <path d="M12 21 Q10 24 12 26" stroke-width="0.8" opacity="0.5" />
              <path d="M9 22 Q7 25 9 27" stroke-width="0.8" opacity="0.4" />
              <!-- Plumas ala derecha -->
              <path d="M36 21 Q38 24 36 26" stroke-width="0.8" opacity="0.5" />
              <path d="M39 22 Q41 25 39 27" stroke-width="0.8" opacity="0.4" />
              <!-- Cola -->
              <path d="M20 37 Q24 42 28 37" />
              <!-- Garras -->
              <path d="M21 37l-2 4M24 37v4M27 37l2 4" stroke-width="1" />
              <!-- Ojo -->
              <circle cx="22" cy="15" r="1" fill="currentColor" stroke="none" />
            </svg>
          </div>
          <h3 class="card-title">Información Importante</h3>
          <div class="card-divider"></div>
          <div class="card-content">
            <div class="info-item">
              <span class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  width="20"
                  height="20"
                >
                  <!-- Sombrero de mago -->
                  <path d="M4 18h16l-8-14z" />
                  <line x1="2" y1="18" x2="22" y2="18" />
                  <!-- Estrella en el sombrero -->
                  <path
                    d="M12 8l.4 1.2 1.2.4-1.2.4-.4 1.2-.4-1.2-1.2-.4 1.2-.4z"
                    fill="currentColor"
                    stroke="none"
                    opacity="0.6"
                  />
                </svg>
              </span>
              <span class="info-text">Temática Harry Potter</span>
            </div>
            <div class="info-item">
              <span class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  width="20"
                  height="20"
                >
                  <ellipse cx="12" cy="14" rx="4" ry="5" />
                  <circle cx="12" cy="7" r="3" />
                  <path
                    d="M11 8l-2 2 3-.5z"
                    fill="currentColor"
                    stroke="none"
                    opacity="0.7"
                  />
                  <path d="M8 13 Q4 10 2 11 Q4 14 8 14" />
                  <path d="M16 13 Q20 10 22 11 Q20 14 16 14" />
                  <path d="M10 19 Q12 22 14 19" />
                </svg>
              </span>
              <span class="info-text">Colores Ravenclaw: Azul & Bronce</span>
            </div>
            <div class="info-item">
              <span class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.3"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  width="20"
                  height="20"
                >
                  <line x1="5" y1="21" x2="18" y2="8" stroke-width="2" />
                  <circle cx="19" cy="7" r="2" />
                  <line x1="6" y1="20" x2="7.5" y2="18.5" stroke-width="1.5" />
                  <path
                    d="M21 3l.5 1.5 1.5.5-1.5.5-.5 1.5-.5-1.5-1.5-.5 1.5-.5z"
                    fill="currentColor"
                    stroke="none"
                    opacity="0.7"
                  />
                  <path
                    d="M22 11l.3.9.9.3-.9.3-.3.9-.3-.9-.9-.3.9-.3z"
                    fill="currentColor"
                    stroke="none"
                    opacity="0.5"
                  />
                  <path
                    d="M9 14l.2.6.6.2-.6.2-.2.6-.2-.6-.6-.2.6-.2z"
                    fill="currentColor"
                    stroke="none"
                    opacity="0.4"
                  />
                </svg>
              </span>
              <span class="info-text">Sorpresas mágicas durante la noche</span>
            </div>
            <div class="info-item">
              <span class="info-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  width="20"
                  height="20"
                >
                  <path
                    d="M23 19a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h4l2-3h6l2 3h4a2 2 0 0 1 2 2z"
                  />
                  <circle cx="12" cy="13" r="4" />
                  <circle
                    cx="12"
                    cy="13"
                    r="1.5"
                    fill="currentColor"
                    stroke="none"
                    opacity="0.4"
                  />
                </svg>
              </span>
              <span class="info-text">Fotógrafo profesional</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Nota -->
      <div class="additional-info">
        <p class="note">
          <span class="wand-icon">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="1.3"
              stroke-linecap="round"
              stroke-linejoin="round"
              width="18"
              height="18"
            >
              <line x1="5" y1="21" x2="18" y2="8" stroke-width="2" />
              <circle cx="19" cy="7" r="2" />
              <line x1="6" y1="20" x2="7.5" y2="18.5" stroke-width="1.5" />
              <path
                d="M21 3l.5 1.5 1.5.5-1.5.5-.5 1.5-.5-1.5-1.5-.5 1.5-.5z"
                fill="currentColor"
                stroke="none"
                opacity="0.7"
              />
            </svg>
          </span>
          Por favor confirma tu asistencia antes del 30 de Agosto para que
          podamos preparar la mejor celebración mágica
          <span class="wand-icon">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="1.3"
              stroke-linecap="round"
              stroke-linejoin="round"
              width="18"
              height="18"
            >
              <line x1="5" y1="21" x2="18" y2="8" stroke-width="2" />
              <circle cx="19" cy="7" r="2" />
              <line x1="6" y1="20" x2="7.5" y2="18.5" stroke-width="1.5" />
              <path
                d="M21 3l.5 1.5 1.5.5-1.5.5-.5 1.5-.5-1.5-1.5-.5 1.5-.5z"
                fill="currentColor"
                stroke="none"
                opacity="0.7"
              />
            </svg>
          </span>
        </p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "EventInfo",
  methods: {
    openLocation(type) {
      const locations = {
        ceremony: "https://maps.app.goo.gl/6PBxWpzrpPpYFRsD6",
        reception: "https://maps.app.goo.gl/KBhj64QpVLFujFQHA",
      };
      window.open(locations[type], "_blank");
    },
  },
};
</script>

<style scoped>
.event-section {
  background: linear-gradient(
    180deg,
    rgba(10, 14, 31, 0.4) 0%,
    rgba(14, 26, 64, 0.4) 100%
  );
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
  transition:
    border-color 0.3s ease,
    transform 0.3s ease,
    box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
}

.event-card:hover {
  border-color: var(--hp-gold);
  transform: translateY(-6px);
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.4);
}

.card-icon {
  width: 52px;
  height: 52px;
  margin-bottom: 12px;
  color: var(--hp-gold);
  animation: float 4s ease-in-out infinite;
  filter: drop-shadow(0 0 6px rgba(201, 162, 77, 0.3));
}

.card-icon svg {
  width: 100%;
  height: 100%;
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
  width: 20px;
  height: 20px;
  flex-shrink: 0;
  margin-top: 2px;
  color: var(--hp-gold);
  opacity: 0.75;
  display: flex;
  align-items: flex-start;
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
  display: inline-flex;
  vertical-align: middle;
  margin: 0 8px;
  color: var(--hp-gold);
  animation: sparkle 2s ease-in-out infinite;
}

@media (max-width: 768px) {
  .event-grid {
    grid-template-columns: 1fr;
  }
  .note {
    padding: 20px;
    font-size: 1rem;
  }
}

/* Estilo para las notas de estacionamiento */
.parking-note {
  display: flex;
  gap: 10px;
  background: rgba(201, 162, 77, 0.08); /* Fondo dorado muy tenue */
  padding: 12px 15px;
  border-radius: 4px;
  border-left: 3px solid var(--hp-gold);
  margin: 10px 0 15px 0;
}

.parking-note.alert {
  border-left-color: #b42828; /* Rojo sutil para el salón que no tiene estacionamiento */
  background: rgba(180, 40, 40, 0.05);
}

.parking-note p {
  font-family: var(--font-body);
  font-size: 0.9rem;
  color: var(--hp-silver);
  line-height: 1.4;
  margin: 0;
}

.parking-note strong {
  color: var(--hp-gold);
}

.magic-star {
  color: var(--hp-gold);
  font-size: 0.8rem;
  margin-top: 2px;
}
</style>
