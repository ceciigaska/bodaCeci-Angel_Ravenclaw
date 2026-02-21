<template>
  <section id="evento" class="event-section section">
    <div class="container">
      <h2 class="section-title">Itinerario del Gran Día</h2>

      <div class="timeline-container">
        <div class="timeline-item left fade-in">
          <div class="timeline-card">
            <div class="card-icon floating-icon">
              <svg viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">
                <path d="M12 16m-6,0a6,6 0 1,0 12,0a6,6 0 1,0 -12,0" />
                <path d="M20 16m-6,0a6,6 0 1,0 12,0a6,6 0 1,0 -12,0" />
                <path d="M12 10l1 1M20 10l-1 1" stroke-width="0.9" opacity="0.5" />
                <circle cx="16" cy="16" r="0.8" fill="currentColor" stroke="none" opacity="0.6" />
              </svg>
            </div>
            <div class="timeline-text-content">
              <h3 class="event-time">17:30 HRS</h3>
              <h4 class="event-name">Ceremonia Religiosa</h4>
              <p class="event-location">Cristo de la Colina</p>
              
              <div class="parking-note">
                <span class="magic-star">✦</span>
                <p>Estacionamiento <strong>muy pequeño</strong>; sugerimos llegar con anticipación.</p>
              </div>

              <div class="action-buttons">
                <a href="https://maps.app.goo.gl/6PBxWpzrpPpYFRsD6" target="_blank" class="magic-button mini">📍 Aparecer en la Ceremonia</a>
                <a :href="calendarLinkCeremonia" target="_blank" class="magic-button mini gold">📅 Guardar en el Pensadero</a>
              </div>
            </div>
          </div>
        </div>

        <div class="timeline-travel fade-in">
          <span class="travel-info">⚡ 10 min de trayecto aproximado</span>
        </div>

        <div class="timeline-item right fade-in">
          <div class="timeline-card">
            <div class="card-icon floating-icon">
              <svg viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">
                <path d="M8 24l8-16 8 16z" />
                <line x1="6" y1="24" x2="26" y2="24" />
                <path d="M11 16h10M13 20h6" stroke-width="0.9" opacity="0.4" />
                <circle cx="16" cy="7" r="1" fill="currentColor" stroke="none" />
                <path d="M14 4l.3 1 1 .3-1 .3-.3 1-.3-1-1-.3 1-.3z" fill="currentColor" stroke="none" opacity="0.7" />
                <path d="M18 4l.3 1 1 .3-1 .3-.3 1-.3-1-1-.3 1-.3z" fill="currentColor" stroke="none" opacity="0.7" />
              </svg>
            </div>
            <div class="timeline-text-content">
              <h3 class="event-time">19:30 HRS</h3>
              <h4 class="event-name">Recepción y Banquete</h4>
              <p class="event-location">Salón de Eventos "SAARA"</p>
              
              <div class="parking-note alert">
                <span class="magic-star">✦</span>
                <p><strong>Sin estacionamiento propio</strong>. Recomendamos buscar lugar a la redonda.</p>
              </div>

              <div class="action-buttons">
                <a href="https://maps.app.goo.gl/KBhj64QpVLFujFQHA" target="_blank" class="magic-button mini">📍 Traslador al Evento</a>
                <a :href="calendarLinkRecepcion" target="_blank" class="magic-button mini gold">📅 Asegurar mi Lugar</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "EventInfo",
  computed: {
    calendarLinkCeremonia() {
      const title = "Boda Ceci & Ángel - Ceremonia";
      const details = "Favor de llegar temprano, estacionamiento limitado.";
      return `https://www.google.com/calendar/render?action=TEMPLATE&text=${encodeURIComponent(title)}&details=${encodeURIComponent(details)}&location=Cristo+de+la+Colina&dates=20261030T173000/20261030T183000`;
    },
    calendarLinkRecepcion() {
      const title = "Boda Ceci & Ángel - Recepción";
      const details = "Salón SAARA. No cuenta con estacionamiento propio.";
      return `https://www.google.com/calendar/render?action=TEMPLATE&text=${encodeURIComponent(title)}&details=${encodeURIComponent(details)}&location=Salón+de+Eventos+SAARA&dates=20261030T193000/20261031T020000`;
    }
  }
};
</script>

<style scoped>
/* Contenedor Principal */
.timeline-container {
  position: relative;
  max-width: 1100px;
  margin: 40px auto;
  display: flex;
  flex-direction: column;
}

/* Línea central solo para pantallas grandes */
@media (min-width: 992px) {
  .timeline-container::after {
    content: '';
    position: absolute;
    width: 2px;
    background: linear-gradient(to bottom, transparent, var(--hp-gold), transparent);
    top: 0; bottom: 0; left: 50%;
    margin-left: -1px;
  }

  .timeline-item {
    width: 50%;
    position: relative;
    margin-bottom: 20px;
  }

  .timeline-item.left { align-self: flex-start; padding-right: 60px; text-align: right; }
  .timeline-item.right { align-self: flex-end; padding-left: 60px; text-align: left; }

  /* Ajuste de botones según el lado */
  .timeline-item.left .action-buttons, 
  .timeline-item.left .parking-note { justify-content: flex-end; }
}

/* Tarjeta Estilo HP */
.timeline-card {
  border: 1px solid rgba(201, 162, 77, 0.22);
  padding: 35px;
  background: rgba(10, 14, 31, 0.3);
  backdrop-filter: blur(8px);
  border-radius: 4px;
  transition: all 0.3s ease;
}

.timeline-card:hover {
  border-color: var(--hp-gold);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
}

/* Iconos Flotantes (He reintegrado tu animación) */
.card-icon.floating-icon {
  width: 52px;
  height: 52px;
  color: var(--hp-gold);
  margin-bottom: 20px;
  display: inline-block;
  animation: float 4s ease-in-out infinite;
  filter: drop-shadow(0 0 6px rgba(201, 162, 77, 0.3));
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

/* Textos */
.event-time { font-family: var(--font-display); color: var(--hp-gold); font-size: 1.5rem; margin-bottom: 8px; letter-spacing: 2px; }
.event-name { font-family: var(--font-display); color: var(--star-white); letter-spacing: 3px; text-transform: uppercase; margin-bottom: 12px; }
.event-location { color: var(--hp-silver); font-style: italic; margin-bottom: 20px; font-size: 1.1rem; }

/* El Lugar y Notas de Estacionamiento */
.event-location, 
.parking-note p { 
  font-family: var(--font-body); /* La fuente legible pero estilizada */
  color: var(--hp-silver); 
  line-height: 1.6;
}

/* Parking Notes */
.parking-note {
  display: flex;
  gap: 10px;
  background: rgba(201, 162, 77, 0.08);
  padding: 8px 12px;
  border-radius: 4px;
  border-left: 2px solid var(--hp-gold);
  margin: 20px 0;
  font-size: 0.9rem;
  align-items: center;
}

.parking-note p {
  font-size: 0.82rem; /* Tamaño más pequeño que el resto del texto */
  margin: 0;
  opacity: 0.9;
}

.parking-note strong {
  color: var(--hp-gold);
  font-weight: 600;
}

.parking-note.alert { border-left-color: #b42828; background: rgba(180, 40, 40, 0.05); }

/* Botones */
.action-buttons { display: flex; gap: 12px; }
.magic-button.mini { padding: 10px 20px; font-size: 0.8rem; text-decoration: none; display: inline-flex; align-items: center; }

.timeline-travel {
  text-align: center;
  margin: 40px 0;
  color: var(--hp-gold);
  font-family: var(--font-display);
  font-size: 1rem;
  letter-spacing: 3px;
  z-index: 2;
}

/* Mobile Responsive */
@media (max-width: 991px) {
  .timeline-item { width: 100%; padding: 0 15px 30px; text-align: center; }
  .timeline-item.left .action-buttons, .timeline-item.right .action-buttons,
  .timeline-item.left .parking-note, .timeline-item.right .parking-note { justify-content: center; }
}

.magic-button.mini:hover {
  box-shadow: 0 0 15px rgba(201, 162, 77, 0.4);
  letter-spacing: 1px;
  transition: all 0.4s ease;
}

/* Los Botones */
.magic-button {
  font-family: var(--font-display);
  letter-spacing: 1px;
  text-transform: uppercase;
}

.magic-star {
  font-size: 0.7rem; /* Estrella más discreta */
  opacity: 0.8;
}
</style>