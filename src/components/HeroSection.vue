<template>
  <section id="inicio" class="hero-section">
    <!-- Plumas decorativas -->
    <div class="feathers" aria-hidden="true">
      <span v-for="n in 8" :key="n" class="feather" :style="featherStyle(n)">✦</span>
    </div>

    <div class="hero-content fade-in">
      <p class="subtitle">Nuestra Historia Mágica Comienza</p>

      <h1 class="couple-names">
        Ceci <span class="ampersand">&amp;</span> Ángel
      </h1>

      <div class="house-banner">
        <span class="eagle">🦅</span>
        <div class="house-text">
          <div class="house-name">Ravenclaw</div>
          <div class="house-motto">"Wit Beyond Measure is Man's Greatest Treasure"</div>
        </div>
      </div>

      <div class="wedding-date">30 · Octubre · 2026</div>

      <div class="divider">
        <span>✦</span>
        <span class="line"></span>
        <span>🪄</span>
        <span class="line"></span>
        <span>✦</span>
      </div>

      <p class="hero-description">
        Después de años compartiendo magia, ingenio y amor,<br>
        nos complace invitarte a celebrar nuestra unión
      </p>

      <a href="#rsvp" class="magic-button cta">
        Confirmar Asistencia
      </a>
    </div>

    <a href="#cuenta-regresiva" class="scroll-indicator" aria-label="Scroll">
      <span class="arrow">↓</span>
    </a>
  </section>
</template>

<script>
export default {
  name: 'HeroSection',
  methods: {
    featherStyle(n) {
      const positions = [8,18,30,42,55,68,78,90]
      const delays    = [0, 2, 4, 1, 3, 5, 1.5, 3.5]
      return {
        left: positions[n - 1] + '%',
        animationDelay: delays[n - 1] + 's',
        animationDuration: (12 + n) + 's',
        fontSize: (0.6 + Math.random() * 0.8) + 'rem',
        opacity: 0.08 + (n % 3) * 0.04
      }
    }
  }
}
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
  0%   { top: -5%;  transform: rotate(0deg) translateX(0); }
  50%  { transform: rotate(180deg) translateX(30px); }
  100% { top: 105%; transform: rotate(360deg) translateX(0); }
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
  font-family: 'Cinzel', serif;
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

.house-text { text-align: left; }

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
  0%, 100% { transform: translateY(0); }
  50%       { transform: translateY(8px); }
}

@media (max-width: 768px) {
  .hero-section { padding: 100px 16px 80px; }
  .house-banner { flex-direction: column; text-align: center; }
  .house-text { text-align: center; }
  .couple-names { letter-spacing: 3px; }
}
</style>