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
      const positions = [8, 18, 30, 42, 55, 68, 78, 90];
      const delays = [0, 2, 4, 1, 3, 5, 1.5, 3.5];
      return {
        left: positions[n - 1] + "%",
        animationDelay: delays[n - 1] + "s",
        animationDuration: 12 + n + "s",
        fontSize: 0.6 + Math.random() * 0.8 + "rem",
        opacity: 0.08 + (n % 3) * 0.04,
      };
    },
  },
};
</script>

<style scoped>
.hero-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  position: relative;
  padding: 120px 24px 80px;
  overflow: hidden;
}

/* Plumas de fondo */
.feathers {
  position: absolute;
  inset: 0;
  pointer-events: none;
  overflow: hidden;
}

.feather {
  position: absolute;
  color: var(--hp-gold);
  animation: featherDrift linear infinite;
  top: -10%;
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
  font-size: 5rem; /* Ajusta según prefieras */
  color: var(--hp-gold); /* O var(--hp-gold) para que resalte */
  text-shadow: 0 0 15px rgba(212, 175, 55, 0.5); /* Brillo mágico */
  margin: 20px 0;
  display: block;
  z-index: 10;
  background: transparent !important; /* Evita el recuadro azul que mencionabas */
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
    padding: 100px 16px 80px;
  }
  .house-banner {
    flex-direction: column;
    text-align: center;
  }
  .house-text {
    text-align: center;
  }
  .couple-names {
    font-size: 3rem !important; /* Reduce el tamaño en móviles */
    line-height: 1.2;
  }
  .wedding-date {
    font-size: 1.1rem;
    letter-spacing: 3px; /* Reduce el espaciado para que no se corte */
  }
}

/*.spotify-mini-wrapper {
/*  max-width: 280px; /* Tamaño pequeño */
/*  margin: 0 auto 20px; /* Centrado y con poco margen */
/*  opacity: 0.6; /* Se vuelve sutil */
/*  transition: opacity 0.3s ease;
/*  border-radius: 12px;
/*  overflow: hidden;
/*}
/*
/*.spotify-mini-wrapper:hover {
/*  opacity: 1; /* Solo resalta si pasan el mouse */
/*}*/

.spotify-floating-player {
  position: fixed;
  bottom: 20px;
  right: 20px;
  width: 300px;
  z-index: 1000;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.6);
  border: 1px solid rgba(201, 162, 77, 0.3); /* Dorado Ravenclaw */
  opacity: 0.5; /* Muy sutil por defecto */
  transition: all 0.4s ease;
  backdrop-filter: blur(5px);
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
</style>
