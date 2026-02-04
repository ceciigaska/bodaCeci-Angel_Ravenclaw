<template>
  <section id="dress-code" class="dress-code-section section">
    <div class="container">
      <h2 class="section-title">Código de Vestimenta</h2>
      
      <div class="dress-code-intro">
        <p class="intro-text">
          Te invitamos a vestir con elegancia y magia.<br>
          Inspírate en los colores de Ravenclaw para esta celebración única.
        </p>
      </div>
      
      <div class="dress-grid">
        <!-- Formal/Elegante -->
        <div class="dress-card fade-in">
          <div class="dress-icon">🎩</div>
          <h3 class="dress-title">Formal / Elegante</h3>
          <div class="dress-divider"></div>
          <p class="dress-description">
            Vestido largo o traje completo.<br>
            La elegancia es la mejor magia.
          </p>
        </div>
        
        <!-- Colores Sugeridos -->
        <div class="dress-card fade-in" style="animation-delay: 0.15s;">
          <div class="dress-icon">🎨</div>
          <h3 class="dress-title">Paleta de Colores</h3>
          <div class="dress-divider"></div>
          <div class="color-palette">
            <div class="color-item">
              <div class="color-swatch" style="background: #0E1A40;"></div>
              <span class="color-name">Azul Ravenclaw</span>
            </div>
            <div class="color-item">
              <div class="color-swatch" style="background: #946B2D;"></div>
              <span class="color-name">Bronce</span>
            </div>
            <div class="color-item">
              <div class="color-swatch" style="background: #d4af37;"></div>
              <span class="color-name">Dorado</span>
            </div>
            <div class="color-item">
              <div class="color-swatch" style="background: #c4c4c4;"></div>
              <span class="color-name">Plateado</span>
            </div>
            <div class="color-item">
              <div class="color-swatch" style="background: #1a1a1a;"></div>
              <span class="color-name">Negro</span>
            </div>
          </div>
        </div>
        
        <!-- Accesorios Opcionales -->
        <div class="dress-card fade-in" style="animation-delay: 0.3s;">
          <div class="dress-icon">✨</div>
          <h3 class="dress-title">Toque Mágico (Opcional)</h3>
          <div class="dress-divider"></div>
          <p class="dress-description">
            Si deseas añadir un toque temático:<br>
            🪄 Accesorios inspirados en Harry Potter<br>
            📚 Detalles vintage o académicos<br>
            🦅 Elementos de Ravenclaw<br>
            ⚡ Cualquier detalle mágico
          </p>
        </div>
      </div>
      
      <!-- Notas importantes -->
      <div class="dress-notes">
        <div class="note-box">
          <div class="note-icon">⚠️</div>
          <h4 class="note-title">Importante</h4>
          <p class="note-text">
            Por favor evita el color blanco y tonos muy claros, reservados para la novia.
          </p>
        </div>
        
        <div class="note-box">
          <div class="note-icon">👗</div>
          <h4 class="note-title">Calzado</h4>
          <p class="note-text">
            Se recomienda calzado cómodo. Habrá mucho baile y diversión durante la celebración.
          </p>
        </div>
      </div>
      
      <!-- Inspiración visual -->
      <div class="inspiration-section">
        <h3 class="inspiration-title">Inspiración de Vestuario</h3>
        <div class="inspiration-grid">
          <div class="inspiration-item">
            <div class="inspiration-placeholder">
              <span class="placeholder-icon">👔</span>
              <p>Trajes elegantes<br>en tonos azul marino</p>
            </div>
          </div>
          <div class="inspiration-item">
            <div class="inspiration-placeholder">
              <span class="placeholder-icon">👗</span>
              <p>Vestidos largos<br>en colores Ravenclaw</p>
            </div>
          </div>
          <div class="inspiration-item">
            <div class="inspiration-placeholder">
              <span class="placeholder-icon">💎</span>
              <p>Accesorios dorados<br>o plateados</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'DressCode'
}
</script>

<style scoped>
.dress-code-section {
  background: linear-gradient(135deg, rgba(26, 47, 95, 0.9), rgba(14, 26, 64, 0.9));
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
</style>