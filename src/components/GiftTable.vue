<template>
  <section id="regalos" class="gift-section section">
    <div class="container">
      <h2 class="section-title">Mesa de Regalos & Lluvia de Sobres</h2>
      <p class="intro-text">
        Tu presencia es nuestro mejor regalo, pero si deseas contribuir a
        nuestro futuro juntos, aquí te compartimos algunas opciones.
      </p>

      <div class="gift-options">
        <div class="gift-card" @click="toggleCard('sobres')">
          <div class="gift-icon">
            <svg
              viewBox="0 0 32 32"
              fill="none"
              stroke="currentColor"
              stroke-width="1.3"
            >
              <rect x="4" y="9" width="24" height="14" rx="0.5" />
              <path d="M4 9l12 7 12-7" />
              <circle cx="16" cy="16" r="3.5" />
            </svg>
          </div>
          <h3 class="gift-title">
            Lluvia de Sobres {{ activeCard === "sobres" ? "−" : "+" }}
          </h3>

          <div
            v-if="activeCard === 'sobres'"
            class="collapsible-content fade-in"
          >
            <div class="gift-divider"></div>
            <p class="gift-description">
              Si deseas hacer un regalo monetario, habrá un buzón especial
              durante la recepción para que deposites tu sobre.
            </p>
          </div>
        </div>

        <div class="gift-card" @click="toggleCard('clabe')">
          <div class="gift-icon">
            <svg
              viewBox="0 0 32 32"
              fill="none"
              stroke="currentColor"
              stroke-width="1.3"
            >
              <rect x="4" y="18" width="24" height="10" rx="0.5" />
            </svg>
          </div>
          <h3 class="gift-title">
            Transferencia {{ activeCard === "clabe" ? "−" : "+" }}
          </h3>

          <div
            v-if="activeCard === 'clabe'"
            class="collapsible-content fade-in"
          >
            <div class="gift-divider"></div>
            <div class="bank-details">
              <div class="bank-item">
                <span class="bank-label">Titular</span>
                <span class="bank-value">Lorena Cecilia Gasca Cortés</span>
              </div>
              <div class="bank-item">
                <span class="bank-label">CLABE</span>
                <span class="bank-value copy-text" @click.stop="copyClabe">
                  722969010532478496
                  <span class="copy-icon">{{ copied ? "✅" : "📋" }}</span>
                </span>
              </div>
              <div class="bank-item">
                <span class="bank-label">Banco</span>

                <span class="bank-value">Mercado Pago W</span>
              </div>
            </div>
          </div>
        </div>

        <div class="gift-card" @click="toggleCard('mesa')">
          <div class="gift-icon"></div>
          <h3 class="gift-title">
            Ver Tiendas {{ activeCard === "mesa" ? "−" : "+" }}
          </h3>

          <div v-if="activeCard === 'mesa'" class="collapsible-content fade-in">
            <div class="gift-divider"></div>
            <div class="store-links">
              <a
                href="https://mesaderegalos.liverpool.com.mx/milistaderegalos/51839730"
                target="_blank"
                class="magic-button store-button"
                @click.stop
                >🛒 Liverpool</a
              >
              <a
                href="https://www.amazon.com.mx/wedding/share/AngelyCeci"
                target="_blank"
                class="magic-button store-button"
                @click.stop
                >📦 Amazon</a
              >
              <a
                href="https://meli.uniko.co/E7519/boda/ceciliayangel"
                target="_blank"
                class="magic-button store-button"
              >
                📦 Mercado Libre
              </a>
              <a
                href="https://www.sears.com.mx/Mesa-de-Regalos/210182/te-invito-a-mi-boda-lorena-cecilia-angel"
                target="_blank"
                class="magic-button store-button"
              >
                🛒 Sears
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "GiftTable",
  data() {
    return {
      // Usamos 'clabe' como default o null si quieres que todas empiecen cerradas
      activeCard: null,
      copied: false,
    };
  },
  methods: {
    copyToClipboard(text, label) {
      navigator.clipboard.writeText(text).then(() => {
        this.copied = true;
        alert(label + " ¡Hechizo copiado! ✨");
        setTimeout(() => {
          this.copied = false;
        }, 2000);
      });
    },
    // AQUÍ CORREGIMOS TU NÚMERO
    copyAccount() {
      this.copyToClipboard("722969010532478496", "Número de cuenta");
    },
    copyClabe() {
      this.copyToClipboard("722969010532478496", "CLABE");
    },

    // Método para abrir/cerrar tarjetas
    toggleCard(cardName) {
      this.activeCard = this.activeCard === cardName ? null : cardName;
    },
  },
};
</script>

<style scoped>
.gift-section {
  background: linear-gradient(
    135deg,
    rgba(10, 14, 31, 0.45) 0%,
    rgba(14, 26, 64, 0.45) 100%
  );
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
  transition:
    border-color 0.3s ease,
    transform 0.3s ease,
    box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
  cursor: pointer;
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
  filter: drop-shadow(0 0 6px rgba(201, 162, 77, 0.3));
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

/* Evita que el clic en el botón de copiar cierre la tarjeta */
.copy-text,
.store-button {
  pointer-events: auto;
}

.copy-text:hover {
  color: var(--hp-gold);
}

.copy-icon {
  margin-left: 4px;
}

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
  filter: drop-shadow(0 0 8px rgba(201, 162, 77, 0.3));
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
  .gift-options {
    grid-template-columns: 1fr;
  }
  .bank-item {
    flex-direction: column;
    align-items: flex-start;
  }
}

.collapsible-content {
  overflow: hidden;
  animation: slideDown 0.3s ease-out;
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
