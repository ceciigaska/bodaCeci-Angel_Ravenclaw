<template>
  <section id="regalos" class="gift-section section">
    <div class="container">
      <h2 class="section-title">Mesa de Regalos & Lluvia de Sobres</h2>
      
      <div class="gift-intro">
        <p class="intro-text">
          Tu presencia es nuestro mejor regalo, pero si deseas contribuir a nuestro futuro juntos,
          aquí te compartimos algunas opciones
        </p>
      </div>
      
      <div class="gift-options">
        <!-- Lluvia de Sobres -->
        <div class="gift-card fade-in">
          <div class="card-header">
            <div class="gift-icon">💌</div>
            <h3 class="gift-title">Lluvia de Sobres</h3>
          </div>
          <div class="gift-divider"></div>
          <div class="gift-content">
            <p class="gift-description">
              Si deseas hacer un regalo monetario, habrá un buzón especial durante la recepción
              para que deposites tu sobre con buenos deseos.
            </p>
            <div class="gift-details">
              <div class="detail-item">
                <span class="detail-icon">📮</span>
                <span class="detail-text">Buzón disponible en la recepción</span>
              </div>
              <div class="detail-item">
                <span class="detail-icon">🎁</span>
                <span class="detail-text">Con tus mejores deseos</span>
              </div>
            </div>
          </div>
        </div>
        
        <!-- Transferencia Bancaria -->
        <div class="gift-card fade-in" style="animation-delay: 0.15s;">
          <div class="card-header">
            <div class="gift-icon">🏦</div>
            <h3 class="gift-title">Transferencia Bancaria</h3>
          </div>
          <div class="gift-divider"></div>
          <div class="gift-content">
            <p class="gift-description">
              También puedes hacer una transferencia directa a nuestra cuenta:
            </p>
            <div class="bank-details">
              <div class="bank-item">
                <span class="bank-label">Banco:</span>
                <span class="bank-value">Nombre del Banco</span>
              </div>
              <div class="bank-item">
                <span class="bank-label">Titular:</span>
                <span class="bank-value">Ceci & Ángel</span>
              </div>
              <div class="bank-item">
                <span class="bank-label">Cuenta:</span>
                <span class="bank-value copy-text" @click="copyAccount">
                  1234567890
                  <span class="copy-icon">📋</span>
                </span>
              </div>
              <div class="bank-item">
                <span class="bank-label">CLABE:</span>
                <span class="bank-value copy-text" @click="copyClabe">
                  012345678901234567
                  <span class="copy-icon">📋</span>
                </span>
              </div>
            </div>
          </div>
        </div>
        
        <!-- Mesa de Regalos Liverpool/Amazon -->
        <div class="gift-card fade-in" style="animation-delay: 0.3s;">
          <div class="card-header">
            <div class="gift-icon">🛍️</div>
            <h3 class="gift-title">Mesa de Regalos</h3>
          </div>
          <div class="gift-divider"></div>
          <div class="gift-content">
            <p class="gift-description">
              Hemos creado mesas de regalos en las siguientes tiendas:
            </p>
            <div class="store-links">
              <a href="#" target="_blank" class="store-button magic-button">
                <span class="store-icon">🛒</span>
                Liverpool
              </a>
              <a href="#" target="_blank" class="store-button magic-button">
                <span class="store-icon">📦</span>
                Amazon
              </a>
            </div>
            <div class="event-codes">
              <div class="code-item">
                <span class="code-label">Código de evento Liverpool:</span>
                <span class="code-value">123456</span>
              </div>
              <div class="code-item">
                <span class="code-label">Código de evento Amazon:</span>
                <span class="code-value">ABCD1234</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Mensaje de agradecimiento -->
      <div class="thank-you-message">
        <div class="message-icon">💝</div>
        <p class="message-text">
          Agradecemos infinitamente tu generosidad y cariño.<br>
          Lo más importante para nosotros es compartir este día especial contigo.
        </p>
        <div class="signature">- Ceci & Ángel -</div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'GiftTable',
  methods: {
    copyAccount() {
      navigator.clipboard.writeText('1234567890')
      this.showCopyMessage('Número de cuenta copiado')
    },
    copyClabe() {
      navigator.clipboard.writeText('012345678901234567')
      this.showCopyMessage('CLABE copiada')
    },
    showCopyMessage(message) {
      // Simple alert - puedes mejorarlo con un toast notification
      alert(message)
    }
  }
}
</script>

<style scoped>
.gift-section {
  background: linear-gradient(135deg, rgba(10, 14, 31, 0.95), rgba(14, 26, 64, 0.95));
  position: relative;
}

.gift-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    radial-gradient(circle at 30% 40%, rgba(148, 107, 45, 0.05) 0%, transparent 50%),
    radial-gradient(circle at 70% 70%, rgba(212, 175, 55, 0.05) 0%, transparent 50%);
  pointer-events: none;
}

.gift-intro {
  text-align: center;
  max-width: 800px;
  margin: 0 auto 60px;
}

.intro-text {
  /*font-family: var(--font-body);*/
  font-size: 1.3rem;
  color: var(--ravenclaw-silver);
  line-height: 1.8;
  font-style: italic;
}

.gift-options {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 40px;
  max-width: 1200px;
  margin: 0 auto 80px;
}

.gift-card {
  background: rgba(14, 26, 64, 0.6);
  backdrop-filter: blur(10px);
  border: 2px solid var(--ravenclaw-bronze);
  padding: 40px 30px;
  transition: all 0.3s ease;
}

.gift-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 60px rgba(148, 107, 45, 0.4);
  border-color: var(--ravenclaw-gold);
}

.card-header {
  text-align: center;
  margin-bottom: 25px;
}

.gift-icon {
  font-size: 4rem;
  margin-bottom: 15px;
  animation: float 3s ease-in-out infinite;
}

.gift-title {
  /*font-family: var(--font-display);*/
  font-size: 1.8rem;
  color: var(--ravenclaw-bronze);
  letter-spacing: 2px;
  font-weight: 700;
}

.gift-divider {
  width: 80px;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--ravenclaw-bronze), transparent);
  margin: 25px auto;
}

.gift-content {
  text-align: center;
}

.gift-description {
  /*font-family: var(--font-body);*/
  font-size: 1.1rem;
  color: var(--star-white);
  line-height: 1.8;
  margin-bottom: 25px;
}

.gift-details {
  margin-top: 25px;
}

.detail-item {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  margin: 15px 0;
  /*font-family: var(--font-body);*/
  color: var(--ravenclaw-silver);
  font-size: 1rem;
}

.detail-icon {
  font-size: 1.5rem;
}

/* Detalles bancarios */
.bank-details {
  background: rgba(26, 47, 95, 0.4);
  padding: 25px;
  border-left: 3px solid var(--ravenclaw-bronze);
  margin-top: 20px;
  text-align: left;
}

.bank-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 15px 0;
  gap: 15px;
}

.bank-label {
  /*font-family: var(--font-display);*/
  color: var(--ravenclaw-bronze);
  font-size: 1rem;
  font-weight: 600;
}

.bank-value {
  /*font-family: var(--font-body);*/
  color: var(--star-white);
  font-size: 1rem;
}

.copy-text {
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 8px;
  transition: color 0.3s ease;
}

.copy-text:hover {
  color: var(--ravenclaw-gold);
}

.copy-icon {
  font-size: 1.2rem;
}

/* Enlaces de tiendas */
.store-links {
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin: 25px 0;
}

.store-button {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  text-decoration: none;
  font-size: 1rem;
  padding: 15px 30px;
}

.store-icon {
  font-size: 1.5rem;
}

.event-codes {
  margin-top: 25px;
  padding: 20px;
  background: rgba(26, 47, 95, 0.3);
  border: 1px solid var(--ravenclaw-bronze);
}

.code-item {
  display: flex;
  flex-direction: column;
  gap: 5px;
  margin: 10px 0;
  text-align: left;
}

.code-label {
  /*font-family: var(--font-body);*/
  color: var(--ravenclaw-silver);
  font-size: 0.9rem;
}

.code-value {
  /*font-family: var(--font-display);*/
  color: var(--ravenclaw-bronze);
  font-size: 1.3rem;
  font-weight: 700;
  letter-spacing: 2px;
}

/* Mensaje de agradecimiento */
.thank-you-message {
  max-width: 700px;
  margin: 80px auto 0;
  text-align: center;
  padding: 50px 40px;
  background: rgba(14, 26, 64, 0.5);
  border: 3px solid var(--ravenclaw-bronze);
  position: relative;
}

.thank-you-message::before,
.thank-you-message::after {
  content: '✨';
  position: absolute;
  font-size: 2rem;
  color: var(--ravenclaw-gold);
  animation: sparkle 2s ease-in-out infinite;
}

.thank-you-message::before {
  top: 20px;
  left: 20px;
}

.thank-you-message::after {
  bottom: 20px;
  right: 20px;
  animation-delay: 1s;
}

.message-icon {
  font-size: 4rem;
  margin-bottom: 20px;
  animation: float 3s ease-in-out infinite;
}

.message-text {
  /*font-family: var(--font-body);*/
  font-size: 1.3rem;
  color: var(--star-white);
  line-height: 1.8;
  margin-bottom: 25px;
}

.signature {
  /*font-family: var(--font-display);*/
  font-size: 1.5rem;
  color: var(--ravenclaw-bronze);
  letter-spacing: 3px;
  font-weight: 600;
}

@media (max-width: 768px) {
  .gift-options {
    grid-template-columns: 1fr;
    gap: 30px;
  }
  
  .gift-card {
    padding: 30px 20px;
  }
  
  .bank-item {
    flex-direction: column;
    align-items: flex-start;
    gap: 5px;
  }
  
  .thank-you-message {
    padding: 40px 25px;
  }
  
  .message-text {
    font-size: 1.1rem;
  }
}
</style>