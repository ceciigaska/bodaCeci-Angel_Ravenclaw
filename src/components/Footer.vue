<template>
  <footer class="footer">
    <div class="footer-glow" aria-hidden="true"></div>

    <div class="footer-content">

      <!-- Separador superior -->
      <!-- <div class="footer-top-deco" aria-hidden="true">
        <span class="deco-star">✦</span>
        <span class="deco-line"></span>
        <span class="deco-eagle">🦅</span>
        <span class="deco-line"></span>
        <span class="deco-star">✦</span>
      </div> -->

      <!-- Iniciales y nombre -->
      <div class="footer-main">
        <!-- <div class="couple-initials">
          <span class="initial">C</span>
          <span class="ampersand">&</span>
          <span class="initial">A</span>
        </div> -->

        <h3 class="footer-title">Ceci & Ángel</h3>
        <p class="footer-date">30 · 10 · 2026</p>
        <p class="footer-tagline">Donde el amor y la magia se encuentran</p>

        <div class="wedding-hashtag">
          <span class="hashtag-symbol">#</span>
          <span class="hashtag-text">BodaCeci&Angel</span>
        </div>
      </div>

      <!-- Créditos -->
      <div class="footer-bottom">
        <p class="copyright">Hecho con 💙 y magia</p>
        <p class="credits">© 2026 Ceci & Ángel · Todos los derechos reservados</p>
      </div>

      <!-- Separador inferior -->
      <div class="footer-bottom-deco" aria-hidden="true">
        <span class="wand-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round" width="20" height="20">
            <line x1="5" y1="21" x2="18" y2="8" stroke-width="2"/>
            <circle cx="19" cy="7" r="2"/>
            <line x1="6" y1="20" x2="7.5" y2="18.5" stroke-width="1.5"/>
            <path d="M21 3l.5 1.5 1.5.5-1.5.5-.5 1.5-.5-1.5-1.5-.5 1.5-.5z" fill="currentColor" stroke="none" opacity="0.7"/>
          </svg>
        </span>
        <span class="deco-sparkles">✨ ✨ ✨</span>
        <span class="wand-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round" width="20" height="20">
            <line x1="5" y1="21" x2="18" y2="8" stroke-width="2"/>
            <circle cx="19" cy="7" r="2"/>
            <line x1="6" y1="20" x2="7.5" y2="18.5" stroke-width="1.5"/>
            <path d="M21 3l.5 1.5 1.5.5-1.5.5-.5 1.5-.5-1.5-1.5-.5 1.5-.5z" fill="currentColor" stroke="none" opacity="0.7"/>
          </svg>
        </span>
      </div>

    </div>
  </footer>
</template>

<script>
export default { name: 'Footer' }
</script>

<style scoped>
.footer {
  position: relative;
  overflow: hidden;
  border-top: 1px solid rgba(201, 162, 77, 0.25);
  padding: 72px 24px 40px;
  text-align: center;
}

.footer-glow {
  position: absolute;
  top: -60%;
  left: 50%;
  transform: translateX(-50%);
  width: 70%;
  height: 200%;
  background: radial-gradient(ellipse at center, rgba(201, 162, 77, 0.06) 0%, transparent 70%);
  pointer-events: none;
}

.footer-content {
  max-width: 700px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

/* Decoraciones */
.footer-top-deco,
.footer-bottom-deco {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 16px;
  margin: 0 auto 40px;
  color: var(--hp-gold);
  opacity: 0.6;
}

.footer-bottom-deco { margin: 40px auto 0; }

.deco-line {
  width: 80px;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--hp-gold), transparent);
  opacity: 0.5;
}

.deco-star    { animation: sparkle 2.5s ease-in-out infinite; font-size: 0.9rem; }
.deco-eagle   { font-size: 1.6rem; animation: float 4s ease-in-out infinite; }
.deco-sparkles { letter-spacing: 4px; animation: sparkle 2s ease-in-out infinite; }

.footer-bottom-deco .wand-icon {
  display: inline-flex;
  align-items: center;
  color: var(--hp-gold);
}

/* Iniciales */
.footer-main { margin: 0 auto 40px; }

.couple-initials {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 16px;
  margin-bottom: 16px;
}

.initial {
  font-family: var(--font-display);
  font-size: 3.5rem;
  font-weight: 700;
  color: var(--ravenclaw-bronze);
  text-shadow: 0 0 24px rgba(148, 107, 45, 0.35);
}

.ampersand {
  font-family: var(--font-display);
  font-size: 2.8rem;
  color: var(--hp-gold);
  animation: float 4s ease-in-out infinite;
  font-style: italic;
}

.footer-title {
  font-family: var(--font-display);
  font-size: 2rem;
  color: var(--star-white);
  letter-spacing: 4px;
  margin-bottom: 8px;
}

.footer-date {
  font-family: var(--font-display);
  font-size: 1.3rem;
  color: var(--ravenclaw-bronze);
  letter-spacing: 6px;
  margin-bottom: 8px;
}

.footer-tagline {
  font-family: var(--font-body);
  font-size: 1.05rem;
  color: var(--hp-silver);
  font-style: italic;
  margin-bottom: 24px;
}

/* Hashtag */
.wedding-hashtag {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  border: 1px solid rgba(201, 162, 77, 0.35);
  padding: 10px 28px;
}

.hashtag-symbol {
  font-family: var(--font-display);
  font-size: 1.2rem;
  color: var(--hp-gold);
}

.hashtag-text {
  font-family: var(--font-display);
  font-size: 1.1rem;
  color: var(--star-white);
  letter-spacing: 2px;
}

/* Créditos */
.footer-bottom {
  padding-top: 28px;
  border-top: 1px solid rgba(201, 162, 77, 0.15);
  margin-bottom: 0;
}

.copyright {
  font-family: var(--font-body);
  font-size: 1rem;
  color: var(--hp-silver);
  margin-bottom: 4px;
}

.credits {
  font-family: var(--font-body);
  font-size: 0.82rem;
  color: var(--hp-silver);
  opacity: 0.55;
}

@media (max-width: 600px) {
  .footer { padding: 56px 16px 32px; }
  .initial { font-size: 2.8rem; }
  .footer-title { font-size: 1.6rem; }
  .deco-line { width: 40px; }
}
</style>