<template>
  <section id="regalos" class="gift-section section">
    <div class="container">
      <h2 class="section-title">Mesa de Regalos & Lluvia de Sobres</h2>

      <p class="intro-text">
        Tu presencia es nuestro mejor regalo, pero si deseas contribuir a nuestro futuro juntos,
        aquí te compartimos algunas opciones
      </p>

      <div class="gift-options">

        <!-- Lluvia de sobres -->
        <div class="gift-card fade-in">
          <div class="gift-icon">
            <svg viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">
              <rect x="4" y="9" width="24" height="14" rx="0.5"/>
              <path d="M4 9l12 7 12-7"/>
              <circle cx="16" cy="16" r="3.5"/>
              <path d="M16 13v1M16 19v1M13 16h1M19 16h1" stroke-width="1"/>
              <path d="M14 14l.5.5M17.5 17.5l.5.5M14 18l.5-.5M17.5 14.5l.5-.5" stroke-width="0.8"/>
            </svg>
          </div>
          <h3 class="gift-title">Lluvia de Sobres</h3>
          <div class="gift-divider"></div>
          <p class="gift-description">
            Si deseas hacer un regalo monetario, habrá un buzón especial durante la recepción
            para que deposites tu sobre con buenos deseos.
          </p>
        </div>

        <!-- Transferencia bancaria -->
        <div class="gift-card fade-in" style="animation-delay:0.12s">
          <div class="gift-icon">
            <svg viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">
              <!-- Cofre/banco -->
              <rect x="4" y="18" width="24" height="10" rx="0.5"/>
              <path d="M4 18 Q4 12 16 12 Q28 12 28 18"/>
              <circle cx="10" cy="18" r="1" fill="currentColor" stroke="none" opacity="0.5"/>
              <circle cx="22" cy="18" r="1" fill="currentColor" stroke="none" opacity="0.5"/>
              <rect x="13" y="20" width="6" height="4" rx="0.5"/>
              <circle cx="16" cy="22" r="0.8" fill="currentColor" stroke="none" opacity="0.7"/>
              <!-- Monedas flotantes -->
              <circle cx="10" cy="8" r="2" opacity="0.6"/>
              <circle cx="22" cy="10" r="1.5" opacity="0.5"/>
              <path d="M10 8l-.5-.5M22 10l.5-.5" stroke-width="0.8" opacity="0.4"/>
            </svg>
          </div>
          <h3 class="gift-title">Transferencia Bancaria</h3>
          <div class="gift-divider"></div>
          <p class="gift-description">También puedes hacer una transferencia directa:</p>
          <div class="bank-details">
            <div class="bank-item">
              <span class="bank-label">Banco</span>
              <span class="bank-value">Mercado Pago W</span>
            </div>
            <div class="bank-item">
              <span class="bank-label">Titular</span>
              <span class="bank-value">Lorena Cecilia Gasca Cortés</span>
            </div>
            <!-- <div class="bank-item">
              <span class="bank-label">Cuenta</span>
              <span class="bank-value copy-text" @click="copyAccount" title="Copiar">
                1234567890 <span class="copy-icon">📋</span>
              </span>
            </div> -->
            <div class="bank-item">
              <span class="bank-label">CLABE</span>
              <span class="bank-value copy-text" @click="copyClabe" title="Copiar">
                722969010532478496 <span class="copy-icon">📋</span>
              </span>
            </div>
          </div>
        </div>

        <!-- Mesa de regalos -->
        <div class="gift-card fade-in" style="animation-delay:0.24s">
          <div class="gift-icon">
            <svg viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">
              <!-- Bolsa de compras mágica -->
              <path d="M6 12h20l-2 16H8z"/>
              <path d="M12 12v-2a4 4 0 0 1 8 0v2"/>
              <!-- Detalle mágico -->
              <path d="M16 18l.4 1.2 1.2.4-1.2.4-.4 1.2-.4-1.2-1.2-.4 1.2-.4z" fill="currentColor" stroke="none" opacity="0.6"/>
              <path d="M11 14l.3.9.9.3-.9.3-.3.9-.3-.9-.9-.3.9-.3z" fill="currentColor" stroke="none" opacity="0.4"/>
              <path d="M21 14l.3.9.9.3-.9.3-.3.9-.3-.9-.9-.3.9-.3z" fill="currentColor" stroke="none" opacity="0.4"/>
            </svg>
          </div>
          <h3 class="gift-title">Mesa de Regalos</h3>
          <div class="gift-divider"></div>
          <p class="gift-description">Hemos creado mesas de regalos en las siguientes tiendas:</p>
          <div class="store-links">
            <a href="https://mesaderegalos.liverpool.com.mx/milistaderegalos/51839730" target="_blank" class="magic-button store-button">
              🛒 Liverpool
            </a>
            <a href="https://www.amazon.com.mx/wedding/share/AngelyCeci" target="_blank" class="magic-button store-button">
              📦 Amazon
            </a>
          </div>
        </div>

      </div>

      <!-- Mensaje de cierre -->
      <div class="thank-you">
        <div class="thank-icon">
          <svg viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">
            <!-- Corazón con lazo de regalo -->
            <path d="M16 28s-8-5-8-12a5 5 0 0 1 10-2 5 5 0 0 1 10 2c0 7-8 12-8 12z"/>
            <!-- Lazo en el corazón -->
            <path d="M13 12 Q11 10 9 12 Q11 14 13 12" fill="currentColor" stroke="none" opacity="0.5"/>
            <path d="M19 12 Q21 10 23 12 Q21 14 19 12" fill="currentColor" stroke="none" opacity="0.5"/>
            <circle cx="16" cy="12" r="1.5" fill="currentColor" stroke="none" opacity="0.6"/>
          </svg>
        </div>
        <p class="thank-text">
          Agradecemos infinitamente tu generosidad y cariño.<br>
          Lo más importante para nosotros es compartir este día especial contigo.
        </p>
        <div class="signature">— Ceci & Ángel —</div>
      </div>

    </div>
  </section>
</template>

<script>
export default {
  name: 'GiftTable',
  methods: {
    copyToClipboard(text, label) {
      navigator.clipboard.writeText(text).then(() => {
        alert(label + ' copiado al portapapeles')
      })
    },
    copyAccount() { this.copyToClipboard('1234567890', 'Número de cuenta') },
    copyClabe()   { this.copyToClipboard('012345678901234567', 'CLABE') }
  }
}
</script>

<style scoped>
.gift-section {
  background: linear-gradient(135deg, rgba(10,14,31,0.45) 0%, rgba(14,26,64,0.45) 100%);
}

.intro-text {
  font-family: var(--font-body);
  font-size: 1.2rem;
  color: var(--hp-silver);
  line-height: 1.8;
  font-style: italic;
  text-align: center;
  max-width: 700px;
  margin: 0 auto 60px;
}

/* Grid */
.gift-options {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 28px;
  max-width: 1100px;
  margin: 0 auto 80px;
}

/* Tarjeta */
.gift-card {
  border: 1px solid rgba(201, 162, 77, 0.22);
  border-radius: 2px;
  padding: 36px 28px;
  backdrop-filter: blur(8px);
  transition: border-color 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
}

.gift-card:hover {
  border-color: var(--hp-gold);
  transform: translateY(-6px);
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.4);
}

.gift-icon {
  width: 56px;
  height: 56px;
  margin: 0 auto 10px;
  color: var(--hp-gold);
  animation: float 4s ease-in-out infinite;
  filter: drop-shadow(0 0 6px rgba(201,162,77,0.3));
}

.gift-icon svg {
  width: 100%;
  height: 100%;
}

.gift-title {
  font-family: var(--font-display);
  font-size: 1.2rem;
  color: var(--hp-gold);
  letter-spacing: 2px;
  margin-bottom: 4px;
}

.gift-divider {
  width: 48px;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--hp-gold), transparent);
  margin: 14px 0;
}

.gift-description {
  font-family: var(--font-body);
  font-size: 1.05rem;
  color: var(--hp-silver);
  line-height: 1.8;
  margin-bottom: 20px;
}

/* Banco */
.bank-details {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 8px;
}

.bank-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 12px;
  padding-bottom: 8px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.07);
}

.bank-label {
  font-family: var(--font-display);
  font-size: 0.78rem;
  letter-spacing: 2px;
  color: var(--hp-silver);
  text-transform: uppercase;
  flex-shrink: 0;
}

.bank-value {
  font-family: var(--font-body);
  font-size: 0.98rem;
  color: var(--star-white);
  text-align: right;
}

.copy-text {
  cursor: pointer;
  transition: color 0.25s ease;
}

.copy-text:hover {
  color: var(--hp-gold);
}

.copy-icon { margin-left: 4px; }

/* Tiendas */
.store-links {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-top: 12px;
}

.store-button {
  font-size: 0.82rem;
  padding: 12px 20px;
  text-align: center;
}

/* Mensaje final */
.thank-you {
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
  padding: 48px 36px;
  border: 1px solid rgba(201, 162, 77, 0.25);
}

.thank-icon {
  width: 70px;
  height: 70px;
  margin: 0 auto 16px;
  color: var(--hp-gold);
  animation: float 4s ease-in-out infinite;
  filter: drop-shadow(0 0 8px rgba(201,162,77,0.3));
}

.thank-icon svg {
  width: 100%;
  height: 100%;
}

.thank-text {
  font-family: var(--font-body);
  font-size: 1.15rem;
  color: var(--hp-silver);
  line-height: 1.9;
  font-style: italic;
  margin-bottom: 20px;
}

.signature {
  font-family: var(--font-display);
  font-size: 1.2rem;
  color: var(--hp-gold);
  letter-spacing: 4px;
}

@media (max-width: 768px) {
  .gift-options { grid-template-columns: 1fr; }
  .bank-item    { flex-direction: column; align-items: flex-start; }
}
</style>