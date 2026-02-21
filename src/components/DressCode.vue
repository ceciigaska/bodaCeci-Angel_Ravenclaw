<template>
  <section id="dress-code" class="dress-code-section section">
    <div class="container">
      <h2 class="section-title">Protocolo de Vestimenta</h2>

      <p class="dress-intro fade-in">
        Deseamos que nuestra boda sea una noche llena de elegancia y magia. 
        <br>El código de vestimenta es <strong>Formal de Noche</strong>.
      </p>

      <div class="color-palette fade-in">
        <h3 class="palette-subtitle">Paleta Inspirada en las Casas</h3>
        <div class="palette-grid">
          <div class="swatch-wrapper" v-for="color in paleta" :key="color.name">
            <div class="swatch" :style="{ background: color.hex }">
              <div class="swatch-glint"></div>
            </div>
            <span class="swatch-label">{{ color.name }}</span>
          </div>
        </div>
      </div>

      <div class="notes-grid">
        <div class="note-box fade-in">
          <div class="card-icon floating-icon small">
             <svg viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.3">
                <path d="M16 4L9 28h14L16 4z" />
                <path d="M12 12h8" opacity="0.5"/>
             </svg>
          </div>
          <div class="note-content">
            <h3 class="note-title">Damas</h3>
            <p class="note-text">
              Solicitamos <strong>vestido midi o largo de gala</strong>. Siéntanse libres de elegir texturas y cortes que las hagan sentir mágicas, respetando la formalidad de la noche.
            </p>
          </div>
        </div>

        <div class="note-box fade-in">
          <div class="card-icon floating-icon small">
             <svg viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.3">
                <path d="M10 8h12v18H10z" />
                <path d="M10 8l6 4 6-4" />
             </svg>
          </div>
          <div class="note-content">
            <h3 class="note-title">Caballeros</h3>
            <p class="note-text">
              Los esperamos con <strong>traje de 2 o 3 piezas oscuro</strong> (Negro, Azul Medianoche o Gris Carbón). 
              Si desean mostrar su lealtad, pueden portar los colores de su casa en la corbata, pañuelo o gemelos.
            </p>
          </div>
        </div>

        <div class="note-box fade-in">
          <div class="card-icon floating-icon small">
             <svg viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.3">
                <circle cx="16" cy="16" r="6" />
                <path d="M16 6v2M16 24v2M26 16h-2M8 16h-2" />
             </svg>
          </div>
          <div class="note-content">
            <h3 class="note-title">Comodidad y Clima</h3>
            <p class="note-text">
              Octubre es fresco; un abrigo será su mejor aliado. 
              Para el baile, <strong>pueden cambiar sus zapatos por tennis</strong>.
            </p>
          </div>
        </div>
      </div>

      <div class="faq-container fade-in">
        <h3 class="faq-section-title-mini">Dudas del Gran Comedor</h3>

        <div class="faq-accordion-list">
          <div 
            v-for="(item, index) in faqs" 
            :key="index" 
            class="faq-item-compact"
            :class="{ active: activeFaq === index }"
          >
            <button class="faq-button-mini" @click="toggleFaq(index)">
              <span class="faq-question-text-mini">{{ item.q }}</span>
              <span class="faq-chevron-mini">{{ activeFaq === index ? '−' : '+' }}</span>
            </button>
            
            <div class="faq-panel-mini" :style="faqStyle(index)">
              <p class="faq-answer-text-mini" v-html="item.a"></p>
            </div>
          </div>
        </div>
      </div>

      <div class="no-white-banner fade-in">
        <span class="magic-star">✦</span>
        <p>Rogamos dejar el color <strong>blanco y marfil</strong> para el uso exclusivo de la novia.</p>
        <span class="magic-star">✦</span>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "DressCode",
  data() {
    return {
      activeFaq: null,
      paleta: [
        { name: "Negro", hex: "#0b0b0f" },
        { name: "Vino", hex: "#4b0f1a" },
        { name: "Esmeralda", hex: "#0f3d2e" },
        { name: "Azul", hex: "#0e1a2b" },
        { name: "Dorado", hex: "#c9a24d" },
        { name: "Plata", hex: "#8b8e98" },
      ],
      faqs: [
        { q: "¿Puedo llevar disfraz o túnica?", a: "Rogamos <strong>no asistir con disfraces o túnicas</strong>. Buscamos una estética de Gala Nocturna." },
        { q: "¿Se permiten trajes claros?", a: "Solicitamos tonos oscuros (Gris Carbón, Azul Marino o Negro) para mantener la elegancia." },
        { q: "¿El vestido debe ser largo?", a: "No, solicitamos vestido midi o largo para todas nuestras invitadas." },
        { q: "¿Colores prohibidos?", a: "Solo el blanco y marfil. Cualquier otro color es bienvenido." },
        { q: "¿Accesorios temáticos?", a: "¡Sí! Joyería o broches de casa son detalles perfectos." },
        { q: "¿Y los niños?", a: "Agradecemos que también asistan con vestimenta formal." }
      ]
    };
  },
  methods: {
    toggleFaq(index) {
      this.activeFaq = this.activeFaq === index ? null : index;
    },
    faqStyle(index) {
      const isOpened = this.activeFaq === index;
      return {
        maxHeight: isOpened ? '100px' : '0',
        opacity: isOpened ? '1' : '0',
        paddingBottom: isOpened ? '15px' : '0'
      };
    }
  }
};
</script>

<style scoped>
/* Mantengo todos tus estilos de paleta, intro y notas intactos */
.dress-code-section { background: rgba(10, 14, 31, 0.2); }
.palette-grid { display: flex; justify-content: center; flex-wrap: wrap; gap: 24px; margin: 30px 0 50px; }
.swatch-wrapper { display: flex; flex-direction: column; align-items: center; gap: 10px; }
.swatch { position: relative; overflow: hidden; width: 48px; height: 48px; border-radius: 50%; border: 1px solid var(--hp-gold); cursor: pointer; transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275); }
.swatch:hover { transform: scale(1.15) rotate(10deg); box-shadow: 0 0 20px var(--hp-gold); }
.swatch-glint { position: absolute; top: -100%; left: -100%; width: 200%; height: 200%; background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1) 45%, rgba(255, 255, 255, 0.4) 50%, rgba(255, 255, 255, 0.1) 55%, transparent); transition: all 0.6s; }
.swatch:hover .swatch-glint { top: 100%; left: 100%; }
.swatch-label { font-family: var(--font-display); font-size: 0.7rem; color: var(--hp-silver); letter-spacing: 1px; text-transform: uppercase; }
.floating-icon.small { width: 35px; height: 35px; color: var(--hp-gold); flex-shrink: 0; animation: float 4s ease-in-out infinite; }
.notes-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; max-width: 900px; margin: 0 auto; }
.note-box { background: rgba(10, 14, 31, 0.3); backdrop-filter: blur(10px); border: 1px solid rgba(201, 162, 77, 0.15); border-radius: 4px; padding: 30px; display: flex; gap: 15px; min-height: 120px; }
.note-title { font-family: var(--font-display); color: var(--hp-gold); font-size: 1rem; letter-spacing: 1.5px; margin-bottom: 5px; }
.note-text { font-family: var(--font-body); font-size: 0.9rem; color: var(--hp-silver); line-height: 1.4; }
.note-text strong { color: var(--hp-gold); }
.dress-intro { text-align: center; font-family: var(--font-body); color: var(--hp-silver); margin-bottom: 40px; line-height: 1.6; font-size: 1.1rem; }
.palette-subtitle { font-family: var(--font-display); color: var(--hp-gold); text-align: center; font-size: 1rem; letter-spacing: 3px; text-transform: uppercase; margin-bottom: 25px; display: flex; align-items: center; justify-content: center; gap: 15px; }
.palette-subtitle::before, .palette-subtitle::after { content: ""; width: 40px; height: 1px; background: linear-gradient(90deg, transparent, var(--hp-gold)); }
.palette-subtitle::after { background: linear-gradient(-90deg, transparent, var(--hp-gold)); }

/* --- FAQ REDUCIDO --- */
.faq-container {
  margin-top: 50px;
  max-width: 550px; /* Más estrecho */
  margin-left: auto;
  margin-right: auto;
}

.faq-section-title-mini {
  font-family: var(--font-display);
  color: var(--hp-gold);
  text-align: center;
  font-size: 0.95rem; /* Título más pequeño */
  margin-bottom: 20px;
  letter-spacing: 2px;
  opacity: 0.8;
}

.faq-button-mini {
  width: 100%;
  background: none;
  border: none;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 5px; /* Menos relleno */
  cursor: pointer;
  text-align: left;
  border-bottom: 1px solid rgba(201, 162, 77, 0.1);
}

.faq-question-text-mini {
  font-family: var(--font-display);
  color: var(--hp-silver); /* Un poco más discreto */
  font-size: 0.75rem; /* Texto pequeño */
  text-transform: uppercase;
  letter-spacing: 1px;
}

.faq-chevron-mini {
  color: var(--hp-gold);
  font-size: 1rem;
}

.faq-panel-mini {
  overflow: hidden;
  transition: all 0.3s ease;
  padding: 0 5px;
}

.faq-answer-text-mini {
  font-family: var(--font-body);
  color: var(--hp-silver);
  font-size: 0.8rem; /* Respuesta más pequeña */
  line-height: 1.5;
  font-style: italic;
  padding-top: 10px;
}

/* Banner de no blanco */
.no-white-banner {
  margin-top: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 15px;
  padding: 20px;
  border-top: 1px solid rgba(201, 162, 77, 0.2);
  color: var(--hp-silver);
  font-style: italic;
  font-size: 0.9rem;
}

.no-white-banner strong { color: var(--hp-gold); }
.magic-star { color: var(--hp-gold); }

@media (max-width: 768px) {
  .faq-container { padding: 0 20px; }
}
</style>