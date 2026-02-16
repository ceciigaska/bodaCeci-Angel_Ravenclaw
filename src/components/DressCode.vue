<template>
  <section id="dress-code" class="dress-code-section section">
    <div class="container">
      <h2 class="section-title">Código de Vestimenta</h2>

      <!-- Paleta de colores -->
      <div class="color-palette">
        <p class="palette-title">Paleta sugerida para la noche</p>
        <div class="palette-grid">
          <div class="swatch" style="background:#0b0b0f" title="Negro"></div>
          <div class="swatch" style="background:#4b0f1a" title="Vino"></div>
          <div class="swatch" style="background:#0f3d2e" title="Verde esmeralda"></div>
          <div class="swatch" style="background:#0e1a2b" title="Azul profundo"></div>
          <div class="swatch" style="background:#c9a24d" title="Dorado"></div>
          <div class="swatch" style="background:#8b8e98" title="Plateado"></div>
        </div>
        <p class="palette-caption">Negro · Vino · Verde Esmeralda · Azul Profundo · Dorado · Plateado</p>
      </div>

      <p class="intro-text">
        Nuestro evento será por la noche en un salón cerrado, inspirado en la elegancia y magia
        del mundo de Harry Potter.<br>
        Viste <strong>formal y elegante</strong> con un sutil toque mágico para esta celebración especial.
      </p>

      <!-- Tarjetas -->
      <div class="dress-grid">

        <div class="dress-card fade-in" style="animation-delay:0.1s">
          <div class="dress-icon">
            <svg viewBox="0 0 48 48" fill="none" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">
              <!-- Vestido largo -->
              <path d="M18 4 Q24 8 30 4"/>
              <path d="M18 4 Q14 10 12 16l-6 28h36l-6-28Q34 10 30 4"/>
              <path d="M15 18 Q24 22 33 18" stroke-width="0.9" opacity="0.5"/>
              <!-- Cintura -->
              <path d="M16 20 Q24 24 32 20" stroke-width="0.8" opacity="0.4"/>
              <!-- Escote -->
              <path d="M18 4 Q24 10 30 4" stroke-width="0.9" opacity="0.5"/>
              <!-- Detalle falda -->
              <path d="M10 36 Q24 40 38 36" stroke-width="0.7" opacity="0.3"/>
            </svg>
          </div>
          <h3 class="dress-title">Para Ellas</h3>
          <div class="dress-divider"></div>
          <p class="dress-description">
            Vestidos midi o largos, telas con caída elegante.<br><br>
            <strong>Sugeridos:</strong> negro, vino, verde esmeralda, azul profundo, dorado, plateado, ciruela.<br><br>
            <strong>Evitar:</strong> blanco, ivory, beige muy claro y colores neón.<br><br>
            Tacón cómodo, block heel o flats elegantes.
          </p>
        </div>

        <div class="dress-card fade-in" style="animation-delay:0.22s">
          <div class="dress-icon">
            <svg viewBox="0 0 48 48" fill="none" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">
              <!-- Sombrero de copa -->
              <rect x="16" y="10" width="16" height="22" rx="1"/>
              <!-- Ala -->
              <path d="M8 32 Q16 36 32 36 Q40 36 40 32"/>
              <line x1="8" y1="32" x2="40" y2="32"/>
              <!-- Cinta decorativa -->
              <line x1="16" y1="26" x2="32" y2="26" stroke-width="2.5" opacity="0.4"/>
              <!-- Detalle superior -->
              <line x1="16" y1="10" x2="32" y2="10" stroke-width="0.8" opacity="0.5"/>
              <!-- Destello mágico -->
              <path d="M36 8l.5 1.5 1.5.5-1.5.5-.5 1.5-.5-1.5-1.5-.5 1.5-.5z" fill="currentColor" stroke="none" opacity="0.6"/>
            </svg>
          </div>
          <h3 class="dress-title">Para Ellos</h3>
          <div class="dress-divider"></div>
          <p class="dress-description">
            Traje formal de dos o tres piezas.<br><br>
            <strong>Sugeridos:</strong> negro, gris oscuro, azul marino, verde oscuro, vino.<br><br>
            Camisa blanca, negra o tonos oscuros.<br>
            Corbata o moño recomendado.<br>
            Zapatos de vestir negros o café oscuro.
          </p>
        </div>

        <div class="dress-card fade-in" style="animation-delay:0.34s">
          <div class="dress-icon">
            <svg viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">
              <!-- Varita Mágica HP -->
              <line x1="5" y1="27" x2="23" y2="9" stroke-width="2"/>
              <circle cx="24" cy="8" r="2.5"/>
              <line x1="6" y1="26" x2="8" y2="24" stroke-width="1.5"/>
              <!-- Lumos effect -->
              <path d="M27 4l.6 1.8 1.8.6-1.8.6-.6 1.8-.6-1.8-1.8-.6 1.8-.6z" fill="currentColor" stroke="none" opacity="0.7"/>
              <path d="M28 12l.4 1.2 1.2.4-1.2.4-.4 1.2-.4-1.2-1.2-.4 1.2-.4z" fill="currentColor" stroke="none" opacity="0.5"/>
              <path d="M11 16l.3.9.9.3-.9.3-.3.9-.3-.9-.9-.3.9-.3z" fill="currentColor" stroke="none" opacity="0.4"/>
            </svg>
          </div>
          <h3 class="dress-title">Toque Mágico</h3>
          <div class="dress-divider"></div>
          <p class="dress-description">
            Puedes añadir un detalle inspirado en la temática:<br><br>
            🪄 Accesorios dorados o vintage<br>
            📚 Terciopelo, satín o telas con carácter<br>
            🕯️ Detalles elegantes con atmósfera mágica<br><br>
            <em>No es disfraz — es elegancia con un guiño a Hogwarts</em>
          </p>
        </div>

      </div>

      <!-- Notas -->
      <div class="dress-notes">
        <div class="note-box">
          <span class="note-icon">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round" width="28" height="28">
              <path d="M10.3 3.5L2 20h20L13.7 3.5a2 2 0 0 0-3.4 0z"/>
              <line x1="12" y1="10" x2="12" y2="14"/>
              <circle cx="12" cy="17" r="0.8" fill="currentColor" stroke="none"/>
            </svg>
          </span>
          <div>
            <h4 class="note-title">Importante</h4>
            <p class="note-text">Por favor evita el color blanco y tonos muy claros, reservados para la novia.</p>
          </div>
        </div>
        <div class="note-box">
          <span class="note-icon">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round" width="28" height="28">
              <!-- Zapato de vestir -->
              <path d="M2 17 Q6 10 12 12 Q17 13 20 10 Q22 8 22 10 Q22 14 18 16 Q14 18 8 18 Q4 18 2 17z"/>
              <path d="M2 17 Q2 19 8 19 Q14 19 18 17"/>
              <path d="M12 12 Q11 15 10 17" stroke-width="0.8" opacity="0.4"/>
              <!-- Tacón -->
              <path d="M18 16 Q20 16 20 18 Q18 18 16 17"/>
            </svg>
          </span>
          <div>
            <h4 class="note-title">Calzado</h4>
            <p class="note-text">
              Habrá mucho baile. Puedes usar tacones cómodos, flats elegantes o
              <strong>tenis blancos, negros o minimalistas</strong>.
              La comodidad también puede ser elegante ✨
            </p>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script>
export default { name: 'DressCode' }
</script>

<style scoped>
.dress-code-section {
  background: linear-gradient(135deg, rgba(26,47,95,0.35) 0%, rgba(14,26,64,0.35) 100%);
}

/* Paleta */
.color-palette {
  text-align: center;
  margin-bottom: 36px;
}

.palette-title {
  font-family: var(--font-display);
  font-size: 0.85rem;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--hp-silver);
  margin-bottom: 16px;
}

.palette-grid {
  display: flex;
  justify-content: center;
  gap: 14px;
  flex-wrap: wrap;
  margin-bottom: 12px;
}

.swatch {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  border: 1px solid rgba(255, 255, 255, 0.2);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.4);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  cursor: default;
}

.swatch:hover {
  transform: scale(1.15);
  box-shadow: 0 6px 18px rgba(201, 162, 77, 0.25);
}

.palette-caption {
  font-family: var(--font-body);
  font-size: 0.88rem;
  color: var(--hp-silver);
  opacity: 0.75;
  letter-spacing: 1px;
}

/* Intro */
.intro-text {
  font-family: var(--font-body);
  font-size: 1.2rem;
  color: var(--hp-silver);
  line-height: 1.9;
  font-style: italic;
  text-align: center;
  max-width: 720px;
  margin: 0 auto 56px;
}

.intro-text strong {
  color: var(--star-white);
  font-style: normal;
}

/* Grid */
.dress-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 28px;
  max-width: 1100px;
  margin: 0 auto 56px;
}

.dress-card {
  border: 1px solid rgba(201, 162, 77, 0.2);
  border-radius: 2px;
  padding: 32px 26px;
  backdrop-filter: blur(8px);
  transition: border-color 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
}

.dress-card:hover {
  border-color: var(--hp-gold);
  transform: translateY(-6px);
  box-shadow: 0 14px 36px rgba(0, 0, 0, 0.35);
}

.dress-icon {
  width: 54px;
  height: 54px;
  margin-bottom: 12px;
  color: var(--hp-gold);
  animation: float 4s ease-in-out infinite;
  filter: drop-shadow(0 0 6px rgba(201,162,77,0.25));
}

.dress-icon svg {
  width: 100%;
  height: 100%;
}

.dress-title {
  font-family: var(--font-display);
  font-size: 1.15rem;
  color: var(--hp-gold);
  letter-spacing: 2px;
}

.dress-divider {
  width: 40px;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--hp-gold), transparent);
  margin: 14px 0;
}

.dress-description {
  font-family: var(--font-body);
  font-size: 1.05rem;
  color: var(--hp-silver);
  line-height: 1.8;
}

.dress-description strong { color: var(--star-white); }
.dress-description em     { color: var(--hp-gold); opacity: 0.85; }

/* Notas */
.dress-notes {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 24px;
  max-width: 900px;
  margin: 0 auto;
}

.note-box {
  display: flex;
  gap: 16px;
  align-items: flex-start;
  border: 1px solid rgba(201, 162, 77, 0.18);
  border-radius: 2px;
  padding: 22px 20px;
  backdrop-filter: blur(6px);
}

.note-icon {
  width: 28px;
  height: 28px;
  flex-shrink: 0;
  color: var(--hp-gold);
  opacity: 0.8;
  display: flex;
  align-items: flex-start;
  padding-top: 2px;
}

.note-title {
  font-family: var(--font-display);
  font-size: 0.95rem;
  color: var(--hp-gold);
  letter-spacing: 2px;
  margin-bottom: 6px;
  text-transform: uppercase;
}

.note-text {
  font-family: var(--font-body);
  font-size: 1rem;
  color: var(--hp-silver);
  line-height: 1.7;
}

.note-text strong { color: var(--star-white); }

@media (max-width: 768px) {
  .dress-grid  { grid-template-columns: 1fr; }
  .dress-notes { grid-template-columns: 1fr; }
}
</style>