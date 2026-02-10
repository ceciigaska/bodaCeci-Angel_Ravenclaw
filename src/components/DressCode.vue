<template>
  <section id="dress-code" class="dress-code-section section">
    <div class="container">
      <h2 class="section-title">Código de Vestimenta</h2>

      <div class="dress-code-intro">
        <!-- Paleta de colores sugeridos -->
        <div class="color-palette">
          <h3 class="palette-title">Paleta sugerida para la noche</h3>
          <div class="palette-grid">
            <div class="color-item" style="background: #0b0b0f"></div>
            <div class="color-item" style="background: #4b0f1a"></div>
            <div class="color-item" style="background: #0f3d2e"></div>
            <div class="color-item" style="background: #0e1a2b"></div>
            <div class="color-item" style="background: #c9a24d"></div>
            <div class="color-item" style="background: #8b8e98"></div>
          </div>
          <p class="palette-caption">
            Negro • Vino • Verde esmeralda • Azul profundo • Dorado • Plateado
          </p>
        </div>

        <p class="intro-text">
          Nuestro evento será por la noche en un salón cerrado, inspirado en la
          elegancia y magia del mundo de Harry Potter.<br />
          Viste formal, elegante y con un sutil toque mágico para esta
          celebración especial.
        </p>
      </div>

      <div class="dress-grid">
        <!-- Formal/Elegante -->
        <!-- <div class="dress-card fade-in">
          <div class="dress-icon">🪄</div>
          <h3 class="dress-title">Elegancia Mágica Nocturna</h3>
          <div class="dress-divider"></div>
          <p class="dress-description">
            Evento nocturno en salón cerrado.<br /><br />
            Opta por atuendos formales, sofisticados y con personalidad.<br />
            La elegancia es la mejor forma de honrar la magia de la noche.
          </p>
        </div> -->

        <!-- Para Ellas -->
        <div class="dress-card fade-in" style="animation-delay: 0.15s">
          <div class="dress-icon">👗</div>
          <h3 class="dress-title">Para Ellas</h3>
          <div class="dress-divider"></div>
          <p class="dress-description">
            Vestidos midi o largos, telas con caída elegante.<br /><br />
            <strong>Colores sugeridos:</strong> negro, vino, verde esmeralda,
            azul profundo, dorado, plateado, ciruela.<br /><br />
            <strong>Evitar:</strong> blanco, ivory, beige muy claro y colores
            neón.<br /><br />
            Tacón cómodo, block heel o flats elegantes.
          </p>
        </div>

        <!-- Para Ellos -->
        <div class="dress-card fade-in" style="animation-delay: 0.3s">
          <div class="dress-icon">🎩</div>
          <h3 class="dress-title">Para Ellos</h3>
          <div class="dress-divider"></div>
          <p class="dress-description">
            Traje formal de dos o tres piezas.<br /><br />
            <strong>Colores sugeridos:</strong> negro, gris oscuro, azul marino,
            verde oscuro, vino.<br /><br />
            Camisa blanca, negra o tonos oscuros.<br />
            Corbata o moño recomendado.<br />
            Zapatos de vestir negros o café oscuro.
          </p>
        </div>

        <!-- Toque Mágico -->
        <div class="dress-card fade-in" style="animation-delay: 0.45s">
          <div class="dress-icon">✨</div>
          <h3 class="dress-title">Toque Mágico (Opcional)</h3>
          <div class="dress-divider"></div>
          <p class="dress-description">
            Puedes añadir un detalle inspirado en la temática:<br /><br />
            🪄 Accesorios dorados o vintage<br />
            📚 Texturas como terciopelo, satín o telas con carácter<br />
            🕯️ Detalles elegantes que combinen con la atmósfera mágica<br /><br />
            (No es disfraz — es elegancia con un guiño a Hogwarts)
          </p>
        </div>
      </div>

      <!-- Notas importantes -->
      <div class="dress-notes">
        <div class="note-box">
          <div class="note-icon">⚠️</div>
          <h4 class="note-title">Importante</h4>
          <p class="note-text">
            Por favor evita el color blanco y tonos muy claros, reservados para
            la novia.
          </p>
        </div>

        <div class="note-box">
          <div class="note-icon">👞</div>
          <h4 class="note-title">Calzado</h4>
          <p class="note-text">
            Habrá mucho baile y celebración toda la noche.<br /><br />
            Puedes usar tacones cómodos, flats elegantes o
            <strong>tenis blancos, negros o minimalistas</strong>.<br />
            La comodidad también puede ser elegante ✨
          </p>
        </div>
      </div>

      <!-- Inspiración visual -->
      <!-- <div class="inspiration-section">
        <h3 class="inspiration-title">Inspiración de Vestuario</h3>
        <div class="inspiration-grid">
          <div class="inspiration-item">
            <div class="inspiration-placeholder">
              <span class="placeholder-icon">🎩</span>
              <p>Trajes formales<br />en tonos oscuros elegantes</p>
            </div>
          </div>
          <div class="inspiration-item">
            <div class="inspiration-placeholder">
              <span class="placeholder-icon">👗</span>
              <p>Vestidos largos<br />en colores profundos</p>
            </div>
          </div>
          <div class="inspiration-item">
            <div class="inspiration-placeholder">
              <span class="placeholder-icon">💎</span>
              <p>Accesorios dorados<br />y detalles mágicos</p>
            </div>
          </div>
        </div>
      </div> -->
    </div>
  </section>
</template>

<script>
export default {
  name: "DressCode",
};
</script>

<style scoped>
.dress-code-section {
  background: linear-gradient(
    135deg,
    rgba(26, 47, 95, 0.9),
    rgba(14, 26, 64, 0.9)
  );
  position: relative;
}

.dress-code-intro {
  text-align: center;
  max-width: 800px;
  margin: 0 auto 60px;
}

.intro-text {
  /* /*font-family: var(--font-body);*/
  font-size: 1.4rem;
  color: var(--ravenclaw-silver);
  line-height: 1.8;
  font-style: italic;
}

.dress-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 40px;
  max-width: 1200px;
  margin: 0 auto 60px;
}

.dress-card {
  background: rgba(14, 26, 64, 0.5);
  backdrop-filter: blur(10px);
  border: 2px solid var(--ravenclaw-bronze);
  padding: 40px 30px;
  text-align: center;
  transition: all 0.3s ease;
}

.dress-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 50px rgba(148, 107, 45, 0.3);
}

.dress-icon {
  font-size: 4rem;
  margin-bottom: 20px;
  animation: float 3s ease-in-out infinite;
}

.dress-title {
  font-size: 1.5rem;
  color: var(--ravenclaw-bronze);
  margin-bottom: 15px;
  letter-spacing: 2px;
  font-weight: 700;
}

.dress-divider {
  width: 60px;
  height: 2px;
  background: var(--ravenclaw-bronze);
  margin: 20px auto;
}

.dress-description {
  /* /*font-family: var(--font-body);*/
  font-size: 1.1rem;
  color: var(--star-white);
  line-height: 1.8;
  text-align: left;
}

/* Paleta de colores */
.color-palette {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.color-item {
  display: flex;
  align-items: center;
  gap: 15px;
}

.color-swatch {
  width: 50px;
  height: 50px;
  border: 2px solid var(--ravenclaw-bronze);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s ease;
}

.color-item:hover .color-swatch {
  transform: scale(1.1);
}

.color-name {
  /* /*font-family: var(--font-body);*/
  font-size: 1rem;
  color: var(--star-white);
}

/* Notas */
.dress-notes {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
  max-width: 900px;
  margin: 60px auto;
}

.note-box {
  background: rgba(148, 107, 45, 0.1);
  border-left: 4px solid var(--ravenclaw-bronze);
  padding: 25px;
  text-align: left;
}

.note-icon {
  font-size: 2rem;
  margin-bottom: 10px;
}

.note-title {
  font-size: 1.2rem;
  color: var(--ravenclaw-bronze);
  margin-bottom: 10px;
  font-weight: 700;
}

.note-text {
  /* /*font-family: var(--font-body);*/
  font-size: 1rem;
  color: var(--star-white);
  line-height: 1.6;
}

/* Inspiración */
.inspiration-section {
  margin-top: 80px;
  text-align: center;
}

.inspiration-title {
  font-size: 2rem;
  color: var(--ravenclaw-bronze);
  margin-bottom: 40px;
  letter-spacing: 2px;
}

.inspiration-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
  max-width: 1000px;
  margin: 0 auto;
}

.inspiration-item {
  position: relative;
}

.inspiration-placeholder {
  background: rgba(14, 26, 64, 0.6);
  border: 2px dashed var(--ravenclaw-bronze);
  padding: 60px 30px;
  min-height: 250px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
}

.inspiration-placeholder:hover {
  background: rgba(14, 26, 64, 0.8);
  border-style: solid;
  transform: scale(1.05);
}

.placeholder-icon {
  font-size: 4rem;
  margin-bottom: 20px;
}

.inspiration-placeholder p {
  /* /*font-family: var(--font-body);*/
  font-size: 1.1rem;
  color: var(--ravenclaw-silver);
  line-height: 1.6;
}

@media (max-width: 768px) {
  .dress-grid {
    grid-template-columns: 1fr;
    gap: 30px;
  }

  .dress-notes {
    grid-template-columns: 1fr;
  }

  .inspiration-grid {
    grid-template-columns: 1fr;
  }

  .intro-text {
    font-size: 1.2rem;
  }
}

/* 🎨 Paleta de colores */
.color-palette {
  margin: 2.5rem 0 1.5rem;
  text-align: center;
}

.palette-title {
  font-size: 1.2rem;
  margin-bottom: 1rem;
  letter-spacing: 1px;
}

.palette-grid {
  display: flex;
  justify-content: center;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 0.8rem;
}

.color-item {
  width: 42px;
  height: 42px;
  border-radius: 50%;
  box-shadow: 0 4px 10px rgba(0,0,0,0.25);
  border: 2px solid rgba(255,255,255,0.3);
}

.palette-caption {
  font-size: 0.9rem;
  opacity: 0.8;
}


</style>
