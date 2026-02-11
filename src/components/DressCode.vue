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
          <div class="dress-icon">👗</div>
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
          <div class="dress-icon">🎩</div>
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
          <div class="dress-icon">✨</div>
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
          <span class="note-icon">⚠️</span>
          <div>
            <h4 class="note-title">Importante</h4>
            <p class="note-text">Por favor evita el color blanco y tonos muy claros, reservados para la novia.</p>
          </div>
        </div>
        <div class="note-box">
          <span class="note-icon">👞</span>
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
  font-size: 2rem;
  margin-bottom: 12px;
  animation: float 4s ease-in-out infinite;
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
  font-size: 1.6rem;
  flex-shrink: 0;
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