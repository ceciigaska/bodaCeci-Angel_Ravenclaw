<template>
  <footer class="footer">
    <div class="footer-content">
      <!-- Decoración superior -->
      <div class="footer-decoration top">
        <span class="star">✦</span>
        <span class="line">────────</span>
        <span class="eagle">🦅</span>
        <span class="line">────────</span>
        <span class="star">✦</span>
      </div>
      
      <!-- Contenido principal -->
      <div class="footer-main">
        <div class="couple-initials">
          <span class="initial">C</span>
          <span class="ampersand">&</span>
          <span class="initial">A</span>
        </div>
        
        <h3 class="footer-title">Ceci & Ángel</h3>
        <p class="footer-date">30.10.2026</p>
        <p class="footer-tagline">Donde el amor y la magia se encuentran</p>
        
        <!-- Hashtag de la boda -->
        <div class="wedding-hashtag">
          <span class="hashtag-icon">#</span>
          <span class="hashtag-text">CeciYAngelForever</span>
        </div>
      </div>
      
      <!-- Enlaces rápidos -->
      <div class="footer-links">
        <a href="#inicio" class="footer-link">Inicio</a>
        <span class="separator">•</span>
        <a href="#cuenta-regresiva" class="footer-link">Cuenta Regresiva</a>
        <span class="separator">•</span>
        <a href="#evento" class="footer-link">Evento</a>
        <span class="separator">•</span>
        <a href="#galeria" class="footer-link">Galería</a>
        <span class="separator">•</span>
        <a href="#rsvp" class="footer-link">RSVP</a>
      </div>
      
      <!-- Casa de Hogwarts -->
      <div class="house-badge">
        <div class="badge-content">
          <div class="house-crest">🦅</div>
          <div class="house-info">
            <div class="house-name">Ravenclaw</div>
            <div class="house-values">Ingenio • Sabiduría • Creatividad</div>
          </div>
        </div>
      </div>
      
      <!-- Copyright y créditos -->
      <div class="footer-bottom">
        <p class="copyright">
          Hecho con 💙 y magia
        </p>
        <p class="credits">
          © 2025 Ceci & Ángel • Todos los derechos reservados
        </p>
        <p class="tech-credit">
          Desarrollado con Vue.js 3
        </p>
      </div>
      
      <!-- Decoración inferior -->
      <div class="footer-decoration bottom">
        <span class="wand">🪄</span>
        <span class="sparkles">✨ ✨ ✨</span>
        <span class="wand">🪄</span>
      </div>
    </div>
    
    <!-- Efecto de brillo -->
    <div class="footer-glow"></div>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style scoped>
.footer {
  background: linear-gradient(180deg, rgba(14, 26, 64, 0.95), rgba(10, 14, 31, 1));
  border-top: 3px solid var(--ravenclaw-bronze);
  padding: 80px 20px 40px;
  position: relative;
  overflow: hidden;
}

.footer-glow {
  position: absolute;
  top: -50%;
  left: 50%;
  transform: translateX(-50%);
  width: 80%;
  height: 200%;
  background: radial-gradient(ellipse at center, rgba(148, 107, 45, 0.1) 0%, transparent 70%);
  pointer-events: none;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

/* Decoraciones */
.footer-decoration {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  margin: 30px 0;
  font-size: 1.2rem;
  color: var(--ravenclaw-bronze);
}

.footer-decoration .star {
  animation: sparkle 2s ease-in-out infinite;
}

.footer-decoration .eagle {
  font-size: 2rem;
  animation: float 3s ease-in-out infinite;
}

.footer-decoration .line {
  color: var(--ravenclaw-bronze);
  opacity: 0.5;
}

.footer-decoration .wand {
  animation: float 3s ease-in-out infinite;
}

.footer-decoration .sparkles {
  animation: sparkle 2s ease-in-out infinite;
  animation-delay: 0.5s;
}

/* Contenido principal */
.footer-main {
  text-align: center;
  margin: 50px 0;
}

.couple-initials {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  margin-bottom: 25px;
}

.initial {
   
  font-size: 4rem;
  font-weight: 700;
  color: var(--ravenclaw-bronze);
  text-shadow: 0 0 20px rgba(148, 107, 45, 0.5);
}

.ampersand {
  /*font-family: var(--font-display);*/
  font-size: 3rem;
  color: var(--ravenclaw-gold);
  animation: float 3s ease-in-out infinite;
}

.footer-title {
  /*font-family: var(--font-display);*/
  font-size: 2.5rem;
  color: var(--star-white);
  margin-bottom: 15px;
  letter-spacing: 3px;
  font-weight: 600;
}

.footer-date {
  /*font-family: var(--font-display);*/
  font-size: 1.5rem;
  color: var(--ravenclaw-bronze);
  margin-bottom: 15px;
  letter-spacing: 5px;
}

.footer-tagline {
  /*font-family: var(--font-body);*/
  font-size: 1.2rem;
  color: var(--ravenclaw-silver);
  font-style: italic;
  margin-bottom: 30px;
}

/* Hashtag */
.wedding-hashtag {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 15px 30px;
  background: rgba(14, 26, 64, 0.6);
  border: 2px solid var(--ravenclaw-bronze);
  margin-top: 20px;
}

.hashtag-icon {
  /*font-family: var(--font-display);*/
  font-size: 1.5rem;
  color: var(--ravenclaw-bronze);
}

.hashtag-text {
  /*font-family: var(--font-display);*/
  font-size: 1.3rem;
  color: var(--star-white);
  letter-spacing: 2px;
}

/* Enlaces */
.footer-links {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  gap: 15px;
  margin: 50px 0;
}

.footer-link {
  /*font-family: var(--font-display);*/
  font-size: 0.95rem;
  color: var(--ravenclaw-silver);
  text-decoration: none;
  letter-spacing: 1px;
  transition: color 0.3s ease;
  text-transform: uppercase;
}

.footer-link:hover {
  color: var(--ravenclaw-bronze);
}

.separator {
  color: var(--ravenclaw-bronze);
  opacity: 0.5;
}

/* Badge de la casa */
.house-badge {
  max-width: 500px;
  margin: 50px auto;
  padding: 30px;
  background: rgba(14, 26, 64, 0.6);
  border: 2px solid var(--ravenclaw-bronze);
  backdrop-filter: blur(10px);
}

.badge-content {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 25px;
}

.house-crest {
  font-size: 4rem;
  animation: float 3s ease-in-out infinite;
}

.house-info {
  text-align: left;
}

.house-name {
  /*font-family: var(--font-display);*/
  font-size: 2rem;
  color: var(--ravenclaw-bronze);
  font-weight: 700;
  letter-spacing: 2px;
  margin-bottom: 8px;
}

.house-values {
  /*font-family: var(--font-body);*/
  font-size: 1rem;
  color: var(--ravenclaw-silver);
  letter-spacing: 1px;
}

/* Footer inferior */
.footer-bottom {
  text-align: center;
  margin-top: 60px;
  padding-top: 30px;
  border-top: 1px solid rgba(148, 107, 45, 0.3);
}

.copyright,
.credits,
.tech-credit {
  /*font-family: var(--font-body);*/
  font-size: 0.95rem;
  color: var(--ravenclaw-silver);
  margin: 8px 0;
}

.copyright {
  font-size: 1.1rem;
  margin-bottom: 15px;
}

.tech-credit {
  font-size: 0.85rem;
  opacity: 0.7;
  margin-top: 15px;
}

@media (max-width: 768px) {
  .footer {
    padding: 60px 15px 30px;
  }
  
  .couple-initials {
    gap: 15px;
  }
  
  .initial {
    font-size: 3rem;
  }
  
  .ampersand {
    font-size: 2.5rem;
  }
  
  .footer-title {
    font-size: 2rem;
  }
  
  .footer-date {
    font-size: 1.2rem;
  }
  
  .footer-links {
    flex-direction: column;
    gap: 10px;
  }
  
  .separator {
    display: none;
  }
  
  .house-badge {
    padding: 25px 20px;
  }
  
  .badge-content {
    flex-direction: column;
    text-align: center;
  }
  
  .house-info {
    text-align: center;
  }
  
  .house-name {
    font-size: 1.5rem;
  }
  
  .wedding-hashtag {
    padding: 12px 20px;
  }
  
  .hashtag-text {
    font-size: 1.1rem;
  }
}
</style>