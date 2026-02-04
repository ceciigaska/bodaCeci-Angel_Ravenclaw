<template>
  <section id="inicio" class="hero-section">
    <div class="hero-content">
      <!-- Pergamino decorativo -->
      <div class="scroll-decoration top"></div>
      
      <div class="hero-text fade-in">
        <div class="subtitle">Nuestra Historia Mágica Comienza</div>
        
        <h1 class="couple-names">
          <span class="name">Ceci</span>
          <span class="ampersand">&</span>
          <span class="name">Ángel</span>
        </h1>
        
        <div class="house-banner">
          <div class="eagle-icon">🦅</div>
          <div class="house-name">Ravenclaw</div>
          <div class="house-motto">"Wit Beyond Measure is Man's Greatest Treasure"</div>
        </div>
        
        <div class="wedding-date">
          30 de Octubre 2026
        </div>
        
        <div class="magical-divider">
          <span class="star">✦</span>
          <span class="wand">────</span>
          <span class="star">✦</span>
        </div>
        
        <p class="hero-description">
          Después de años compartiendo magia, ingenio y amor,<br>
          nos complace invitarte a celebrar nuestra unión
        </p>
        
        <a href="#rsvp" class="cta-button magic-button">
          Confirmar Asistencia
        </a>
      </div>
      
      <div class="scroll-decoration bottom"></div>
      
      <!-- Plumas flotantes -->
      <div class="floating-feathers">
        <div class="feather" style="--delay: 0s; --x: 10%;"></div>
        <div class="feather" style="--delay: 2s; --x: 30%;"></div>
        <div class="feather" style="--delay: 4s; --x: 70%;"></div>
        <div class="feather" style="--delay: 1s; --x: 85%;"></div>
      </div>
    </div>
    
    <!-- Flecha para scroll -->
    <a href="#cuenta-regresiva" class="scroll-indicator">
      <div class="arrow-down"></div>
    </a>
  </section>
</template>

<script>
export default {
  name: 'HeroSection'
}
</script>

<style scoped>
.hero-section {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 100px 20px;
  overflow: hidden;
}

.hero-content {
  max-width: 900px;
  text-align: center;
  position: relative;
  z-index: 1;
}

.scroll-decoration {
  width: 100%;
  height: 30px;
  background: repeating-linear-gradient(
    90deg,
    var(--ravenclaw-bronze) 0px,
    var(--ravenclaw-bronze) 10px,
    transparent 10px,
    transparent 20px
  );
  opacity: 0.3;
  margin: 20px 0;
}

.hero-text {
  padding: 40px 0;
}

.subtitle {
  /*font-family: var(--font-body);*/
  font-size: 1.3rem;
  color: var(--ravenclaw-silver);
  font-style: italic;
  margin-bottom: 20px;
  letter-spacing: 2px;
}

.couple-names {
  /*font-family: var(--font-display);*/
  font-size: clamp(3rem, 10vw, 6rem);
  font-weight: 700;
  color: var(--star-white);
  margin: 20px 0;
  line-height: 1.2;
  letter-spacing: 5px;
  text-shadow: 0 0 30px rgba(148, 107, 45, 0.5);
}

.name {
  display: inline-block;
  background: linear-gradient(135deg, var(--ravenclaw-bronze), var(--ravenclaw-gold));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: shimmer 3s ease-in-out infinite;
  background-size: 200% 200%;
}

.ampersand {
  display: inline-block;
  margin: 0 20px;
  color: var(--ravenclaw-bronze);
  font-size: 0.8em;
  animation: float 3s ease-in-out infinite;
}

.house-banner {
  margin: 40px auto;
  padding: 30px;
  border: 3px solid var(--ravenclaw-bronze);
  border-radius: 0;
  background: rgba(14, 26, 64, 0.6);
  backdrop-filter: blur(5px);
  max-width: 500px;
}

.eagle-icon {
  font-size: 3rem;
  margin-bottom: 10px;
  animation: float 4s ease-in-out infinite;
}

.house-name {
  /*font-family: var(--font-display);*/
  font-size: 2rem;
  color: var(--ravenclaw-bronze);
  font-weight: 700;
  letter-spacing: 4px;
  margin-bottom: 10px;
}

.house-motto {
  /*font-family: var(--font-body);*/
  font-size: 1rem;
  color: var(--ravenclaw-silver);
  font-style: italic;
  letter-spacing: 1px;
}

.wedding-date {
  /*font-family: var(--font-display);*/
  font-size: 1.5rem;
  color: var(--ravenclaw-bronze);
  margin: 30px 0;
  letter-spacing: 3px;
  font-weight: 600;
}

.magical-divider {
  margin: 30px 0;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
}

.star {
  color: var(--ravenclaw-gold);
  font-size: 1.5rem;
  animation: sparkle 2s ease-in-out infinite;
}

.wand {
  color: var(--ravenclaw-bronze);
  letter-spacing: -5px;
}

.hero-description {
  /*font-family: var(--font-body);*/
  font-size: 1.2rem;
  color: var(--ravenclaw-silver);
  line-height: 1.8;
  margin: 30px auto;
  max-width: 600px;
}

.cta-button {
  margin-top: 40px;
  font-size: 1.1rem;
  padding: 18px 50px;
}

/* Plumas flotantes */
.floating-feathers {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  overflow: hidden;
}

.feather {
  position: absolute;
  width: 20px;
  height: 60px;
  background: linear-gradient(135deg, var(--ravenclaw-bronze), transparent);
  opacity: 0.3;
  left: var(--x);
  animation: featherFall 15s var(--delay) infinite ease-in;
  filter: blur(1px);
}

@keyframes featherFall {
  0% {
    top: -10%;
    transform: rotate(0deg) translateX(0);
  }
  50% {
    transform: rotate(180deg) translateX(50px);
  }
  100% {
    top: 110%;
    transform: rotate(360deg) translateX(0);
  }
}

/* Indicador de scroll */
.scroll-indicator {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  text-decoration: none;
}

.arrow-down {
  width: 30px;
  height: 30px;
  border-right: 3px solid var(--ravenclaw-bronze);
  border-bottom: 3px solid var(--ravenclaw-bronze);
  transform: rotate(45deg);
  animation: bounce 2s infinite;
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% {
    transform: translateY(0) rotate(45deg);
  }
  40% {
    transform: translateY(-20px) rotate(45deg);
  }
  60% {
    transform: translateY(-10px) rotate(45deg);
  }
}

@media (max-width: 768px) {
  .hero-section {
    padding: 80px 15px;
  }
  
  .couple-names {
    font-size: clamp(2.5rem, 8vw, 4rem);
  }
  
  .house-banner {
    padding: 20px;
  }
  
  .house-name {
    font-size: 1.5rem;
  }
  
  .hero-description {
    font-size: 1rem;
  }
}
</style>