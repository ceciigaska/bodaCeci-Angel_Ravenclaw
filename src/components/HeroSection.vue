<template>
  <section id="inicio" class="hero-section">
    <!-- Plumas decorativas -->
    <div class="feathers" aria-hidden="true">
      <span v-for="n in 8" :key="n" class="feather" :style="featherStyle(n)"
        >✦</span
      >
    </div>

    <div class="hero-content fade-in">
      <p class="subtitle">Nuestra Historia Mágica Comienza</p>

      <h1 class="couple-names">
        Cecilia <span class="ampersand">&amp;</span> Ángel
      </h1>

      <!-- <div class="house-banner">
        <span class="eagle">🦅</span>
        <div class="house-text">
          <div class="house-name">Ravenclaw</div>
          <div class="house-motto">"Wit Beyond Measure is Man's Greatest Treasure"</div>
        </div>
      </div> -->

      <div class="wedding-date">30 · Octubre · 2026</div>

      <div class="divider">
        <span>✦</span>
        <span class="line"></span>
        <span class="wand-icon">
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
          </svg>
        </span>
        <span class="line"></span>
        <span>✦</span>
      </div>

      <p class="hero-description">
        Después de años compartiendo magia, ingenio y amor,<br />
        nos complace invitarte a celebrar nuestra unión
      </p>

      <a href="#rsvp" class="magic-button cta"> Confirmar Asistencia </a>
      <!-- <div class="spotify-container">
        <iframe
          data-testid="embed-iframe"
          style="border-radius: 12px"
          src="https://open.spotify.com/embed/track/1PPTlPJqKuL0fdoTmzwXJy?utm_source=generator&theme=0"
          width="100%" 
    height="80" 
    frameBorder="0" 
    allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" 
    loading="lazy"></iframe>
      </div> -->
    </div>

    <a href="#cuenta-regresiva" class="scroll-indicator" aria-label="Scroll">
      <span class="arrow">↓</span>
    </a>
    <div class="spotify-floating-player">
  <iframe 
    src="https://open.spotify.com/embed/track/1PPTlPJqKuL0fdoTmzwXJy?utm_source=generator&theme=0" 
    width="100%" 
    height="80" 
    frameBorder="0" 
    allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" 
    loading="lazy">
  </iframe>
</div>
  </section>
</template>

<script>
export default {
  name: "HeroSection",
  methods: {
    featherStyle(n) {
    return {
      left: Math.random() * 100 + '%',
      fontSize: (Math.random() * 10 + 10) + 'px',
      animationDuration: (Math.random() * 5 + 5) + 's', // Entre 5 y 10 segundos
      animationDelay: (Math.random() * 5) + 's',       // Retraso para que no salgan todas juntas
    };
    },
  },
  mounted() {
  // 1. Limpia el hash de la URL sin recargar la página
  // Esto quita el "#dress-code" de la barra de direcciones
  if (window.location.hash) {
    history.replaceState(null, null, window.location.pathname);
  }

  // 2. Fuerza el scroll al punto 0,0 (arriba a la izquierda)
  window.scrollTo(0, 0);

  // 3. Por si el navegador se pone terco, un pequeño refuerzo:
  setTimeout(() => {
    window.scrollTo({
      top: 0,
      behavior: 'instant' // Queremos que sea inmediato, no un scroll suave
    });
  }, 10);
}
};
</script>

<style scoped>
.hero-section {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-top: 80px; /* Debe coincidir con la altura del nav para no empujar de más */
  text-align: center;
}

/* Plumas de fondo */
.feathers {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  pointer-events: none;
}

.feather {
  position: absolute;
  color: var(--hp-gold);
  opacity: 0.3;
  /* Aplicamos la animación de caída */
  animation: magic-fall linear infinite;
}

@keyframes featherDrift {
  0% {
    top: -5%;
    transform: rotate(0deg) translateX(0);
  }
  50% {
    transform: rotate(180deg) translateX(30px);
  }
  100% {
    top: 105%;
    transform: rotate(360deg) translateX(0);
  }
}

/* Contenido */
.hero-content {
  max-width: 820px;
  position: relative;
  z-index: 1;
}

.subtitle {
  font-family: var(--font-body);
  font-size: 1.1rem;
  font-style: italic;
  color: var(--hp-silver);
  letter-spacing: 3px;
  margin-bottom: 24px;
}

.couple-names {
  font-family: var(--font-display);
  color: var(--hp-gold);
  
  /* Esto es vital para móviles */
  display: block;
  width: 100%;
  white-space: nowrap; /* Evita el salto de línea */
  text-align: center;
  
  /* Tamaño fluido: en pantallas grandes es 5rem, en pequeñas se encoge */
  font-size: clamp(1.8rem, 8vw, 5rem) !important; 
  line-height: 1.2;
}

.ampersand {
  color: var(--hp-gold);
  font-family: "Cinzel", serif;
  margin: 0 15px;
}

/* Banner Ravenclaw */
.house-banner {
  display: inline-flex;
  align-items: center;
  gap: 16px;
  border: 1px solid rgba(201, 162, 77, 0.35);
  padding: 14px 32px;
  margin: 28px auto;
  backdrop-filter: blur(4px);
}

.eagle {
  font-size: 2rem;
  animation: float 4s ease-in-out infinite;
}

.house-text {
  text-align: left;
}

.house-name {
  font-family: var(--font-display);
  font-size: 1.3rem;
  color: var(--hp-gold);
  letter-spacing: 4px;
  text-transform: uppercase;
}

.house-motto {
  font-family: var(--font-body);
  font-size: 0.85rem;
  color: var(--hp-silver);
  font-style: italic;
  letter-spacing: 1px;
  margin-top: 2px;
}

/* Fecha */
.wedding-date {
  font-family: var(--font-display);
  font-size: 1.4rem;
  color: var(--hp-gold);
  letter-spacing: 6px;
  margin: 20px 0;
}

/* Divisor */
.divider {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  margin: 20px 0 28px;
  color: var(--hp-gold);
  font-size: 1rem;
  opacity: 0.7;
}

.divider .line {
  width: 60px;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--hp-gold), transparent);
}

.divider .wand-icon {
  display: inline-flex;
  align-items: center;
  color: var(--hp-gold);
}

/* Descripción */
.hero-description {
  font-family: var(--font-body);
  font-size: 1.2rem;
  color: var(--hp-silver);
  line-height: 1.9;
  margin-bottom: 40px;
  font-style: italic;
}

/* CTA */
.cta {
  font-size: 0.95rem;
  padding: 16px 48px;
}

/* Scroll indicator */
.scroll-indicator {
  position: absolute;
  bottom: 36px;
  left: 50%;
  transform: translateX(-50%);
  text-decoration: none;
}

.arrow {
  display: block;
  font-size: 1.6rem;
  color: var(--hp-gold);
  opacity: 0.6;
  animation: bounce 2.5s ease-in-out infinite;
}

@keyframes bounce {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(8px);
  }
}

@media (max-width: 768px) {
  .hero-section {
    padding-top: 60px; /* Reducimos el espacio superior en móvil */
    padding-left: 20px;
    padding-right: 20px;
  }
  .house-banner {
    flex-direction: column;
    text-align: center;
  }
  .house-text {
    text-align: center;
  }
  .couple-names {
    font-size: 2.8rem; /* Aumentamos el tamaño de los nombres */
    line-height: 1.1;
    margin: 15px 0;
  }
  .wedding-date {
    font-size: 1.2rem;
    margin-top: 10px;
  }
  .subtitle {
    font-size: 1rem; /* Un poco más legible */
    margin-bottom: 10px;
    letter-spacing: 2px;
  }
}

.spotify-floating-player {
  position: fixed;
  bottom: 20px;
  right: 20px;
  width: 300px;
  z-index: 1000;
  border-radius: 12px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.5);
  background: #000; /* Fondo negro para que no brille de más */
  border: 1px solid var(--hp-gold);
  overflow: hidden;
  transition: transform 0.3s ease;
}

/* En celulares pequeños lo ocultamos o lo hacemos miniatura */
@media (max-width: 480px) {
  .spotify-floating-player {
    width: 80px;
    height: 80px;
    right: 10px;
  }
}

.spotify-floating-player:hover {
  opacity: 1;
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(201, 162, 77, 0.2);
}

/* Ajuste para móviles: se mueve al centro inferior o se oculta */
@media (max-width: 768px) {
  .spotify-floating-player {
    width: 250px;
    bottom: 10px;
    right: 10px;
    opacity: 0.8;
  }
}



@keyframes magic-fall {
  0% {
    transform: translateY(-10vh) translateX(0) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 0.4;
  }
  50% {
    /* Movimiento de vaivén hacia la derecha */
    transform: translateY(50vh) translateX(20px) rotate(180deg);
  }
  90% {
    opacity: 0.4;
  }
  100% {
    /* Cae hasta el fondo con vaivén hacia la izquierda */
    transform: translateY(100vh) translateX(-20px) rotate(360deg);
    opacity: 0;
  }
}
</style>
