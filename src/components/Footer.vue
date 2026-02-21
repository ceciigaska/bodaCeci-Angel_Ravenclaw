<template>
  <footer class="footer">
    <div class="footer-glow" aria-hidden="true"></div>

    <div class="footer-content">
      <div class="footer-main">
        <h3 class="footer-title">C <span class="ampersand">&</span> A</h3>
        <p class="footer-date">30 · 10 · 2026</p>
        
        <div class="wedding-hashtag-minimal">
          <span class="hashtag-text">#BodaCeciliaYAngel</span>
        </div>
      </div>

      <div class="footer-bottom">
        <p class="copyright">Hecho con magia y amor</p>
        <div class="bottom-line"></div>
        <p class="signature">2026 — El Gran Comedor</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  position: relative;
  padding: 40px 0 20px; /* Reducimos padding */
  background: var(--bg-dark); /* Asegúrate que combine con tu fondo */
  text-align: center;
  overflow: hidden;
}

.footer-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(201, 162, 77, 0.05) 0%, transparent 70%);
  pointer-events: none;
}

.footer-title {
  font-family: var(--font-display);
  font-size: 1.5rem; /* Más pequeño */
  color: var(--star-white);
  letter-spacing: 5px;
  margin-bottom: 5px;
}

.ampersand {
  color: var(--hp-gold);
  font-family: serif; /* Un toque clásico */
  font-style: italic;
}

.footer-date {
  font-family: var(--font-display);
  font-size: 0.9rem;
  color: var(--hp-silver);
  letter-spacing: 3px;
  margin-bottom: 15px;
  opacity: 0.8;
}

.wedding-hashtag-minimal {
  display: inline-block;
  font-family: var(--font-body);
  font-size: 0.75rem;
  color: var(--hp-gold);
  letter-spacing: 1px;
  opacity: 0.7;
  border-top: 1px solid rgba(201, 162, 77, 0.2);
  padding-top: 10px;
}

.footer-bottom {
  margin-top: 30px;
}

.copyright {
  font-family: var(--font-body);
  font-size: 0.7rem;
  color: var(--hp-silver);
  opacity: 0.5;
  margin-bottom: 8px;
}

.bottom-line {
  width: 30px;
  height: 1px;
  background: var(--hp-gold);
  margin: 0 auto 8px;
  opacity: 0.3;
}

.signature {
  font-family: var(--font-display);
  font-size: 0.6rem;
  color: var(--hp-gold);
  letter-spacing: 2px;
  text-transform: uppercase;
  opacity: 0.6;
}

@media (max-width: 768px) {
  .footer { padding: 30px 0 15px; }
}
</style>