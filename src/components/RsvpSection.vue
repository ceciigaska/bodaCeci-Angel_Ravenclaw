<template>
  <section id="rsvp" class="rsvp-section section">
    <div class="container">

      <div class="rsvp-header-full fade-in">
        <div class="ministry-seal">
          <h2 class="section-title">Decreto de Asistencia</h2>
        </div>
      </div>

      <div class="rsvp-split-layout fade-in">

        <div class="rsvp-info-side">
          <div class="info-content">
            <p class="magic-paragraph">
              Tu nombre ha sido expulsado por el <span class="gold-text">Cáliz de Fuego</span>.
              Has sido seleccionado como campeón para la unión de
              <span class="couple-names">Cecilia & Ángel</span>.
            </p>

            <div class="sorting-hat-box">
              <div class="hat-inline-icon">
                <svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="1">
                  <path d="M25 75c10-2 40-2 50 0-5-5-12-35-12-45 0-12-8-20-13-20s-13 8-13 20c0 10-7 40-12 45z" />
                  <path d="M42 50c2 3 14 3 16 0" />
                </svg>
              </div>
              <p class="hat-text">
                "Para que el <span class="hat-link">Sombrero Seleccionador</span> pueda ubicar tu lugar en el Gran Comedor, debes registrar tu presencia."
              </p>
            </div>

            <div class="owl-post-note">
              <div class="owl-inline-icon">
                <svg viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="1.2">
                  <path d="M35 35c0-10 10-15 15-15s15 5 15 15v30c0 8-7 12-15 12s-15-4-15-12V35z" />
                  <circle cx="43" cy="38" r="3" /><circle cx="57" cy="38" r="3" />
                  <path d="M48 43l2 3 2-3z" />
                </svg>
              </div>
              <p>Esperamos tu lechuza antes del <strong>30 de Agosto, 2026</strong></p>
            </div>
          </div>
        </div>

        <div class="rsvp-form-side">
          <div class="rsvp-card-wrapper">
            <div class="card-corner top-left"></div>
            <div class="card-corner bottom-right"></div>

            <!-- ref="card" para el scroll automático en móvil -->
            <div ref="card" class="rsvp-card-compact" :class="{ 'magic-glow': animating }">

              <!-- STEP 1: Buscar nombre -->
              <div v-if="step === 1" class="rsvp-step">
                <div class="card-header">
                  <div class="magic-envelope">
                    <svg viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.2">
                      <rect x="4" y="9" width="24" height="14" rx="0.5" />
                      <path d="M4 9l12 7 12-7" />
                      <circle cx="16" cy="16" r="3" fill="rgba(201, 162, 77, 0.1)" />
                    </svg>
                  </div>
                  <p class="map-label">Tu nombre aguarda en el Libro de las Admisiones</p>
                </div>

                <div v-if="errorCarga" class="error-banner">
                  No se pudo conectar con el Libro de Admisiones. Intenta recargar la página.
                </div>

                <div v-if="cargandoInvitados" class="loading-invitados">
                  <span class="spinner"></span>
                  <span class="loading-text">Consultando el Libro...</span>
                </div>

                <template v-else>
                  <div class="input-magic-group">
                    <input
                      v-model="busqueda"
                      type="text"
                      placeholder="Escribe tu nombre para buscarte en el Libro..."
                      @input="filtrar"
                      class="input-magic"
                      autocomplete="off"
                    />
                    <div class="btn-magic-icon">✦</div>
                  </div>

                  <transition-group name="fade" tag="div" class="suggestions-list">
                    <div
                      v-for="invitado in sugerencias"
                      :key="invitado.nombre"
                      class="suggestion-item"
                      :class="{ 'ya-confirmado': invitado.confirmado }"
                      @click="seleccionar(invitado)"
                    >
                      <span>{{ invitado.nombre }}</span>
                      <span v-if="invitado.confirmado" class="badge-confirmado">✓ Ya confirmado</span>
                    </div>
                  </transition-group>

                  <p v-if="busqueda.length >= 3 && sugerencias.length === 0" class="no-results">
                    No encontramos ese nombre en el Libro. Verifica la ortografía o contacta a los novios.
                  </p>
                </template>
              </div>

              <!-- STEP 2: Confirmar acompañantes -->
              <div v-if="step === 2" class="rsvp-step fade-in">
                <h3 class="invitado-name">{{ invitadoSeleccionado.nombre }}</h3>
                <p class="pases-count">
                  Asientos en el Gran Comedor: {{ invitadoSeleccionado.permitidos }}
                </p>

                <div class="acompanantes-form">

                  <!-- Nota para invitados con boleto individual -->
                  <div v-if="invitadoSeleccionado.permitidos === 1" class="solo-notice">
                    <div class="solo-notice-icon">✦</div>
                    <p class="solo-notice-text">
                      El <span class="solo-gold">Sombrero Seleccionador</span> ha asignado un lugar para ti. Cada asiento en nuestro Gran Comedor es para alguien que lleva un lugar especial en nuestros corazones.
                    </p>
                    <p class="solo-notice-firma">— Con mucho amor, Cecilia & Ángel</p>
                  </div>

                  <!-- Invitado principal (solo lectura) -->
                  <div class="input-magic-group mini">
                    <span class="input-label-inline">Tú</span>
                    <input
                      :value="invitadoSeleccionado.nombre"
                      type="text"
                      class="input-magic small readonly"
                      readonly
                    />
                  </div>

                  <!-- Acompañantes -->
                  <div
                    v-for="(nombre, index) in asistentes"
                    :key="index"
                    class="input-magic-group mini"
                  >
                    <span class="input-label-inline">{{ index + 1 }}</span>
                    <input
                      v-model="asistentes[index]"
                      type="text"
                      :placeholder="'Nombre del acompañante ' + (index + 1)"
                      class="input-magic small"
                      :class="{ 'input-error': camposConError[index] }"
                      maxlength="60"
                    />
                  </div>

                  <!-- Teléfono con validación mejorada -->
                  <div class="input-magic-group mini" :class="{ 'group-error': telefonoError }">
                    <span class="input-label-inline">📱</span>
                    <input
                      v-model="telefono"
                      type="tel"
                      placeholder="Tu número de teléfono (10 dígitos)"
                      class="input-magic small"
                      :class="{ 'input-error': telefonoError }"
                      @input="validarTelefonoEnVivo"
                      maxlength="15"
                    />
                  </div>
                  <p v-if="telefonoError" class="field-error-msg">✦ Ingresa un número de teléfono válido</p>

                  <!-- Comentarios -->
                  <div class="comentarios-group">
                    <textarea
                      v-model="comentarios"
                      placeholder="¿Restricciones alimentarias, alergias o mensaje para los novios? (opcional)"
                      class="input-magic textarea-magic"
                      rows="2"
                      maxlength="300"
                    ></textarea>
                  </div>

                  <!-- Aviso de timeout -->
                  <div v-if="timeoutWarning" class="timeout-banner">
                    ⏳ La conexión está tardando más de lo usual. Si el problema persiste, intenta de nuevo.
                  </div>

                  <div class="confirmation-actions">
                    <button
                      @click="enviarConfirmacion('Confirmado')"
                      class="btn-confirm ok"
                      :disabled="loading || enviado"
                    >
                      <span v-if="!loading">⚡ Confirmar Asistencia</span>
                      <span v-else class="spinner"></span>
                    </button>
                    <button
                      @click="enviarConfirmacion('Declinado')"
                      class="btn-confirm decline"
                      :disabled="loading || enviado"
                    >
                      No podré asistir
                    </button>
                    <button @click="resetStep" class="btn-confirm no" :disabled="loading">
                      Volver
                    </button>
                  </div>
                </div>
              </div>

              <!-- STEP 3: Confirmación exitosa -->
              <div v-if="step === 3" class="rsvp-step success-view fade-in">
                <div class="wax-seal-wrapper">
                  <div class="wax-seal">
                    <div class="seal-inner"><span class="seal-letter">H</span></div>
                  </div>
                </div>
                <h3 class="success-title">¡Mesa Asignada!</h3>
                <p class="success-text">
                  El Sombrero Seleccionador ha hablado. Tu lugar en el Gran Comedor está asegurado.
                </p>
                <div class="success-summary">
                  <p><strong>{{ invitadoSeleccionado.nombre }}</strong></p>
                  <p v-if="asistentes.length > 0" class="summary-acomp">
                    + {{ asistentes.filter(n => n.trim()).join(', ') }}
                  </p>
                </div>

                <!-- Mensaje para boleto individual -->
                <div v-if="invitadoSeleccionado.permitidos === 1" class="solo-success-msg">
                  <div class="solo-success-divider">
                    <span class="ssm-line"></span>
                    <span class="ssm-star">🕊️</span>
                    <span class="ssm-line"></span>
                  </div>
                  <p class="solo-success-text">
                    Tu lugar en el Gran Comedor es <span class="solo-gold">único e irrepetible</span>,
                    tal como tú lo eres para nosotros. Gracias por ser parte de este capítulo tan especial de nuestra historia.
                  </p>
                  <p class="solo-success-firma">— Con todo nuestro amor, Cecilia & Ángel</p>
                </div>

                <!-- Compartir / guardar comprobante -->
                <div class="share-comprobante">
                  <button @click="compartirComprobante" class="btn-share">
                    <span class="share-icon">{{ shareSupported ? '↗' : '📋' }}</span>
                    {{ shareSupported ? 'Compartir confirmación' : 'Copiar comprobante' }}
                  </button>
                  <p v-if="shareCopied" class="share-copied">✓ ¡Copiado al portapapeles!</p>
                  <p class="share-hint">Guarda tu confirmación como comprobante</p>
                </div>

                <button @click="resetStep" class="btn-confirm ok mt-20">Cerrar</button>
              </div>

              <!-- STEP 4: Declinación -->
              <div v-if="step === 4" class="rsvp-step decline-view fade-in">
                <div class="decline-icon">🕯️</div>
                <h3 class="decline-title">Nos dará tristeza no verte</h3>
                <p class="decline-text">
                  Tu ausencia ha sido registrada. Estarás en nuestros corazones ese día.
                </p>
                <button @click="resetStep" class="btn-confirm no mt-20">Cerrar</button>
              </div>

              <!-- STEP 5: Ya confirmado - Ravenclaw -->
              <div v-if="step === 5" class="rsvp-step ravenclaw-view fade-in">
                <div class="ravenclaw-crest">
                  <svg viewBox="0 0 100 120" fill="none" stroke="currentColor" stroke-width="0.8">
                    <path d="M10 10 L90 10 L90 80 L50 115 L10 80 Z" stroke="rgba(0,120,180,0.5)" fill="rgba(0,50,110,0.12)" />
                    <path d="M50 30 L35 50 L42 48 L40 65 L50 60 L60 65 L58 48 L65 50 Z" stroke="rgba(180,150,80,0.8)" fill="rgba(180,150,80,0.08)" stroke-width="0.7"/>
                    <circle cx="50" cy="26" r="5" stroke="rgba(180,150,80,0.8)" fill="none" />
                    <path d="M42 48 Q25 38 18 42 Q28 52 35 50" stroke="rgba(180,150,80,0.5)" fill="none" stroke-width="0.6"/>
                    <path d="M58 48 Q75 38 82 42 Q72 52 65 50" stroke="rgba(180,150,80,0.5)" fill="none" stroke-width="0.6"/>
                    <text x="22" y="75" font-size="6" fill="rgba(180,150,80,0.4)" font-family="serif">✦</text>
                    <text x="72" y="75" font-size="6" fill="rgba(180,150,80,0.4)" font-family="serif">✦</text>
                  </svg>
                </div>
                <div class="ravenclaw-scroll">
                  <p class="scroll-label">— Registro del Gran Libro —</p>
                  <h3 class="ravenclaw-name">{{ invitadoSeleccionado ? invitadoSeleccionado.nombre : '' }}</h3>
                  <div class="ravenclaw-divider">
                    <span class="rv-line"></span>
                    <span class="rv-star">⚡</span>
                    <span class="rv-line"></span>
                  </div>
                  <p class="ravenclaw-message">
                    Tu confirmación ya fue registrada en el
                    <span class="rv-gold">Gran Libro de Admisiones</span>.
                    El Sombrero Seleccionador no olvida ningún nombre.
                  </p>
                  <p class="ravenclaw-submsg">
                    Si necesitas modificar tu registro, contacta a los novios directamente.
                  </p>
                </div>
                <button @click="resetStep" class="btn-confirm rv-btn mt-20">Entendido</button>
              </div>

            </div>
          </div>
        </div>
      </div>

      <div class="dumbledore-container fade-in">
        <div class="quote-decoration">
          <span class="line"></span>
          <span class="star">✦</span>
          <span class="line"></span>
        </div>
        <p class="quote-text">
          "La felicidad se puede hallar hasta en los más oscuros momentos, si
          somos capaces de usar bien la luz."
        </p>
        <cite class="quote-author">— Albus Dumbledore</cite>
      </div>

    </div>
  </section>
</template>

<script>
export default {
  name: "RsvpSection",
  data() {
    return {
      apiUrl:
        "https://script.google.com/macros/s/AKfycbyqE4-ODPZ9tetY2VqFyhQQg8SJo8D5E6X7QrZuS-VbNyDsWxcpW0O8qYAN7ALvVhctCw/exec",
      step: 1,
      busqueda: "",
      invitadosData: [],
      sugerencias: [],
      invitadoSeleccionado: null,
      asistentes: [],
      comentarios: "",
      telefono: "",
      telefonoError: false,
      loading: false,
      enviado: false,          // bloqueo anti doble clic
      animating: false,
      cargandoInvitados: true,
      errorCarga: false,
      camposConError: [],
      timeoutWarning: false,   // aviso de lentitud
      timeoutTimer: null,
      shareSupported: false,   // Web Share API
      shareCopied: false,
      // ── SOLO PARA PRUEBAS: cambia a true para saltar bloqueo de confirmados ──
      debugMode: false,
    };
  },

  async mounted() {
    // Detectar si el navegador soporta Web Share API (principalmente móviles)
    this.shareSupported = !!navigator.share;

    try {
      // ?t= evita que el navegador o Google cacheen la respuesta
      const response = await fetch(`${this.apiUrl}?t=${Date.now()}`);
      this.invitadosData = await response.json();
    } catch (e) {
      console.error("Error cargando invitados", e);
      this.errorCarga = true;
    } finally {
      this.cargandoInvitados = false;
    }
  },

  methods: {
    filtrar() {
      if (this.busqueda.length < 3) {
        this.sugerencias = [];
        return;
      }
      this.sugerencias = this.invitadosData
        .filter((i) =>
          i.nombre.toLowerCase().includes(this.busqueda.toLowerCase())
        )
        .slice(0, 5);
    },

    seleccionar(invitado) {
      // En debugMode se ignora el bloqueo de "ya confirmado"
      if (invitado.confirmado && !this.debugMode) {
        this.invitadoSeleccionado = invitado;
        this.triggerMagic();
        this.step = 5;
        this.scrollToCard();
        return;
      }

      this.triggerMagic();
      this.invitadoSeleccionado = invitado;
      this.busqueda = invitado.nombre;
      this.sugerencias = [];
      this.comentarios = "";
      this.telefono = "";
      this.telefonoError = false;
      this.enviado = false;

      const totalAcompanantes = Math.max((Number(invitado.permitidos) || 1) - 1, 0);
      this.asistentes = Array(totalAcompanantes).fill("");
      this.camposConError = Array(totalAcompanantes).fill(false);

      this.step = 2;
      this.scrollToCard(); // scroll automático en móvil
    },

    // Scroll suave hacia la card al cambiar de step
    scrollToCard() {
      this.$nextTick(() => {
        if (this.$refs.card) {
          this.$refs.card.scrollIntoView({ behavior: "smooth", block: "start" });
        }
      });
    },

    triggerMagic() {
      this.animating = true;
      setTimeout(() => { this.animating = false; }, 1500);
    },

    resetStep() {
      this.step = 1;
      this.busqueda = "";
      this.asistentes = [];
      this.camposConError = [];
      this.comentarios = "";
      this.telefono = "";
      this.telefonoError = false;
      this.invitadoSeleccionado = null;
      this.sugerencias = [];
      this.enviado = false;
      this.timeoutWarning = false;
      this.shareCopied = false;
      if (this.timeoutTimer) clearTimeout(this.timeoutTimer);
    },

    // Validación en vivo: solo corrige el error si ya existía, no interrumpe mientras escribe
    validarTelefonoEnVivo() {
      if (this.telefonoError) {
        this.telefonoError = !this.telefonoValido();
      }
    },

    // Validación con regex: acepta dígitos, espacios, guiones, paréntesis y +
    telefonoValido() {
      const soloDigitos = this.telefono.trim().replace(/[\s\-\(\)\+]/g, "");
      return /^\d{7,15}$/.test(soloDigitos);
    },

    async enviarConfirmacion(tipoAsistencia) {
      // Bloqueo inmediato anti doble clic
      if (this.loading || this.enviado) return;

      // Validar teléfono con regex
      this.telefonoError = !this.telefonoValido();
      if (this.telefonoError) return;

      // Validar acompañantes si confirma
      if (tipoAsistencia === "Confirmado") {
        this.camposConError = this.asistentes.map(
          (nombre) => !nombre || nombre.trim().length < 2
        );
        if (this.camposConError.some(Boolean)) {
          alert("Por favor, escribe el nombre completo de todos tus acompañantes mágicos.");
          return;
        }
      }

      // Bloquear botones inmediatamente
      this.loading = true;
      this.enviado = true;
      this.timeoutWarning = false;

      // Aviso de lentitud a los 8 segundos
      this.timeoutTimer = setTimeout(() => {
        if (this.loading) this.timeoutWarning = true;
      }, 8000);

      try {
        const data = {
          nombrePrincipal: this.invitadoSeleccionado.nombre,
          asistencia: tipoAsistencia,
          telefono: this.telefono.trim(),
          totalAsistentes: tipoAsistencia === "Confirmado"
            ? this.asistentes.length + 1
            : 0,
          nombresAsistentes: tipoAsistencia === "Confirmado"
            ? this.asistentes.filter(n => n.trim()).join(", ")
            : "",
          comentarios: this.comentarios.trim(),
        };

        // Race entre el fetch real y un timeout de 15 segundos
        const fetchPromise = fetch(this.apiUrl, {
          method: "POST",
          mode: "no-cors",
          body: JSON.stringify(data),
        });
        const timeoutPromise = new Promise((_, reject) =>
          setTimeout(() => reject(new Error("timeout")), 15000)
        );
        await Promise.race([fetchPromise, timeoutPromise]);

        clearTimeout(this.timeoutTimer);
        this.timeoutWarning = false;
        this.triggerMagic();

        // Marcar localmente para evitar doble registro en esta sesión
        // (en debugMode no se marca para poder probar de nuevo)
        if (!this.debugMode) {
          const idx = this.invitadosData.findIndex(
            (i) => i.nombre === this.invitadoSeleccionado.nombre
          );
          if (idx !== -1) this.invitadosData[idx].confirmado = true;
        }

        this.step = tipoAsistencia === "Confirmado" ? 3 : 4;
        this.scrollToCard();

      } catch (e) {
        clearTimeout(this.timeoutTimer);
        this.timeoutWarning = false;
        this.enviado = false; // permitir reintentar si falló

        if (e.message === "timeout") {
          alert("La Red Flu no respondió a tiempo. Por favor intenta de nuevo.");
        } else {
          alert("Hubo un error con la conexión de la Red Flu. Intenta de nuevo.");
        }
      } finally {
        this.loading = false;
      }
    },

    // Compartir o copiar comprobante de confirmación
    async compartirComprobante() {
      const acomp = this.asistentes.filter(n => n.trim());
      const texto =
        `✦ Confirmación de Asistencia ✦\n` +
        `Boda de Cecilia & Ángel\n\n` +
        `Invitado: ${this.invitadoSeleccionado.nombre}\n` +
        (acomp.length > 0 ? `Acompañantes: ${acomp.join(", ")}\n` : "") +
        `Total: ${this.invitadoSeleccionado.permitidos} lugar(es)\n\n` +
        `"El Sombrero Seleccionador ha asignado tu mesa."`;

      if (this.shareSupported) {
        try {
          await navigator.share({ title: "Confirmación Boda Cecilia & Ángel", text: texto });
        } catch {
          // El usuario canceló el share, no hacer nada
        }
      } else {
        try {
          await navigator.clipboard.writeText(texto);
          this.shareCopied = true;
          setTimeout(() => { this.shareCopied = false; }, 3000);
        } catch {
          alert("No se pudo copiar. Toma una captura de pantalla como comprobante.");
        }
      }
    },
  },
};
</script>

<style scoped>
.rsvp-section {
  padding: 80px 0;
  background: radial-gradient(circle at center, rgba(201, 162, 77, 0.05) 0%, transparent 80%);
}

/* HEADER */
.rsvp-header-full { text-align: center; margin-bottom: 60px; }
.ministry-seal { display: flex; align-items: center; justify-content: center; gap: 15px; }

/* LAYOUT */
.rsvp-split-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  max-width: 1000px;
  margin: 0 auto 60px;
  align-items: center;
}

/* INFO SIDE */
.hat-inline-icon { float: left; margin-right: 15px; color: var(--hp-gold); }
.hat-inline-icon svg { width: 45px; height: 45px; }
.owl-inline-icon { color: var(--hp-gold); width: 28px; height: 28px; }
.owl-inline-icon svg { width: 100%; height: 100%; }
.magic-paragraph { font-family: var(--font-body); color: var(--hp-silver); font-size: 1.1rem; line-height: 1.6; margin-bottom: 25px; }
.gold-text { color: var(--hp-gold); font-weight: bold; }
.couple-names { color: var(--star-white); font-family: var(--font-display); }
.sorting-hat-box { background-color: rgba(201, 162, 77, 0.03); border-left: 1px solid var(--hp-gold); padding: 20px; margin: 25px 0; overflow: hidden; }
.hat-text { font-family: var(--font-body); color: var(--hp-silver); font-style: italic; font-size: 1rem; margin: 0; }
.owl-post-note { display: flex; align-items: center; gap: 12px; color: var(--hp-gold); font-family: var(--font-display); font-size: 0.8rem; letter-spacing: 1px; }

/* CARD */
.rsvp-card-wrapper { position: relative; }
.rsvp-card-compact {
  background-color: rgba(13, 17, 33, 0.85);
  backdrop-filter: blur(8px);
  border: 1px solid rgba(201, 162, 77, 0.2);
  padding: 40px 30px;
  text-align: center;
}
.magic-glow { box-shadow: 0 0 30px rgba(201, 162, 77, 0.15); }
.magic-envelope { width: 50px; height: 50px; margin: 0 auto 15px; color: var(--hp-gold); }
.map-label { font-family: var(--font-body); color: var(--hp-gold); font-size: 0.65rem; text-transform: uppercase; margin-bottom: 20px; letter-spacing: 1px; opacity: 0.7; }

/* INPUTS */
.input-magic-group { display: flex; align-items: center; border-bottom: 1px solid rgba(201, 162, 77, 0.2); margin-bottom: 12px; }
.input-magic-group.mini { margin-bottom: 8px; }
.input-label-inline { font-family: var(--font-display); color: var(--hp-gold); font-size: 0.65rem; min-width: 28px; opacity: 0.6; text-align: left; }
.input-magic { width: 100%; background-color: transparent; border: none; padding: 10px; color: #fff; font-family: var(--font-body); outline: none; font-size: 0.95rem; }
.input-magic.readonly { opacity: 0.5; cursor: default; }
.input-magic.input-error { border-bottom: 1px solid #e05050; }
.btn-magic-icon { color: var(--hp-gold); padding: 8px; }
.comentarios-group { margin: 12px 0 20px; }
.textarea-magic { width: 100%; background-color: rgba(201, 162, 77, 0.03); border: 1px solid rgba(201, 162, 77, 0.15); border-radius: 2px; padding: 10px; color: var(--hp-silver); font-family: var(--font-body); font-size: 0.85rem; outline: none; resize: none; line-height: 1.5; }
.textarea-magic::placeholder { opacity: 0.4; }

/* SUGGESTIONS */
.suggestions-list { margin-top: 4px; }
.suggestion-item { display: flex; justify-content: space-between; align-items: center; padding: 10px 14px; cursor: pointer; border-bottom: 1px solid rgba(201, 162, 77, 0.08); font-family: var(--font-body); color: var(--hp-silver); font-size: 0.9rem; transition: background-color 0.2s; text-align: left; }
.suggestion-item:hover { background-color: rgba(201, 162, 77, 0.06); }
.suggestion-item.ya-confirmado { opacity: 0.5; cursor: not-allowed; }
.badge-confirmado { font-size: 0.65rem; color: #7abf7a; font-family: var(--font-display); letter-spacing: 0.5px; white-space: nowrap; margin-left: 8px; }
.no-results { font-size: 0.8rem; color: var(--hp-silver); opacity: 0.5; font-family: var(--font-body); margin-top: 12px; font-style: italic; }

/* LOADING / ERROR */
.loading-invitados { display: flex; align-items: center; justify-content: center; gap: 10px; padding: 20px 0; }
.loading-text { color: var(--hp-gold); font-family: var(--font-display); font-size: 0.75rem; letter-spacing: 1px; opacity: 0.7; }
.error-banner { background-color: rgba(200, 60, 60, 0.08); border: 1px solid rgba(200, 60, 60, 0.3); color: #e08080; font-family: var(--font-body); font-size: 0.82rem; padding: 10px 14px; margin-bottom: 16px; line-height: 1.4; }

/* TIMEOUT */
.timeout-banner { background-color: rgba(201, 162, 77, 0.06); border: 1px solid rgba(201, 162, 77, 0.25); color: var(--hp-gold); font-family: var(--font-body); font-size: 0.78rem; padding: 8px 12px; margin-bottom: 12px; line-height: 1.4; animation: notice-in 0.3s ease both; }

/* STEP 2 */
.invitado-name { font-family: var(--font-display); color: #fff; font-size: 1.2rem; margin-bottom: 5px; }
.pases-count { color: var(--hp-gold); font-size: 0.7rem; text-transform: uppercase; margin-bottom: 20px; }

/* BOTONES */
.confirmation-actions { margin-top: 20px; }
.btn-confirm { display: block; padding: 12px; font-family: var(--font-display); font-size: 0.75rem; cursor: pointer; background-color: transparent; border: 1px solid var(--hp-gold); color: var(--hp-gold); width: 100%; text-transform: uppercase; transition: background-color 0.3s, opacity 0.3s; margin-bottom: 8px; }
.btn-confirm:hover:not(:disabled) { background-color: rgba(201, 162, 77, 0.1); }
.btn-confirm:disabled { opacity: 0.5; cursor: not-allowed; }
.btn-confirm.no { border-color: rgba(255,255,255,0.15); color: var(--hp-silver); }
.btn-confirm.decline { border-color: rgba(255,255,255,0.2); color: rgba(255,255,255,0.4); font-size: 0.7rem; }
.btn-confirm.decline:hover:not(:disabled) { background-color: rgba(255,255,255,0.04); }
.mt-20 { margin-top: 20px; }

/* STEP 3 - Éxito */
.wax-seal-wrapper { position: relative; width: 80px; height: 80px; margin: 0 auto 20px; animation: seal-drop 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275); }
.wax-seal { width: 100%; height: 100%; background: radial-gradient(circle, #8b0000 0%, #4b0000 100%); border-radius: 50%; display: flex; align-items: center; justify-content: center; box-shadow: 0 4px 10px rgba(0,0,0,0.5); }
.seal-inner { width: 80%; height: 80%; border: 1px solid rgba(201, 162, 77, 0.5); border-radius: 50%; display: flex; align-items: center; justify-content: center; }
.seal-letter { color: var(--hp-gold); font-size: 1.8rem; font-family: 'Cinzel', serif; }
.success-title { font-family: var(--font-display); color: var(--hp-gold); font-size: 1.4rem; margin-bottom: 10px; }
.success-text { color: var(--hp-silver); font-size: 0.9rem; margin-bottom: 16px; }
.success-summary { background-color: rgba(201, 162, 77, 0.05); border: 1px solid rgba(201, 162, 77, 0.15); padding: 12px 16px; margin-bottom: 8px; font-family: var(--font-body); color: var(--hp-silver); font-size: 0.85rem; line-height: 1.6; }
.summary-acomp { opacity: 0.7; font-size: 0.8rem; }

/* COMPARTIR COMPROBANTE */
.share-comprobante { margin: 16px 0 4px; }
.btn-share { display: inline-flex; align-items: center; gap: 8px; padding: 9px 18px; font-family: var(--font-display); font-size: 0.7rem; letter-spacing: 1px; text-transform: uppercase; background-color: transparent; border: 1px solid rgba(201, 162, 77, 0.35); color: var(--hp-gold); cursor: pointer; transition: background-color 0.2s; width: 100%; justify-content: center; }
.btn-share:hover { background-color: rgba(201, 162, 77, 0.08); }
.share-icon { font-style: normal; font-size: 1rem; }
.share-hint { font-family: var(--font-body); color: var(--hp-silver); font-size: 0.7rem; opacity: 0.4; margin-top: 6px; font-style: italic; }
.share-copied { font-family: var(--font-display); color: #7abf7a; font-size: 0.7rem; letter-spacing: 1px; margin-top: 6px; animation: notice-in 0.3s ease both; }

/* BOLETO INDIVIDUAL - Step 2 */
.solo-notice { background: linear-gradient(135deg, rgba(201, 162, 77, 0.06) 0%, rgba(201, 162, 77, 0.02) 100%); border: 1px solid rgba(201, 162, 77, 0.2); border-left: 3px solid rgba(201, 162, 77, 0.5); padding: 14px 16px; margin-bottom: 16px; text-align: left; animation: notice-in 0.4s ease both; }
.solo-notice-icon { color: var(--hp-gold); font-size: 0.7rem; letter-spacing: 4px; margin-bottom: 8px; opacity: 0.6; }
.solo-notice-text { font-family: var(--font-body); color: var(--hp-silver); font-size: 0.83rem; line-height: 1.6; font-style: italic; margin: 0 0 6px; }
.solo-notice-firma { font-family: var(--font-display); color: var(--hp-gold); font-size: 0.68rem; letter-spacing: 1px; opacity: 0.75; margin: 0; }
.solo-gold { color: var(--hp-gold); font-style: normal; font-weight: 600; }

/* BOLETO INDIVIDUAL - Step 3 */
.solo-success-msg { margin: 16px 0 4px; padding: 16px; background: linear-gradient(135deg, rgba(201, 162, 77, 0.07) 0%, rgba(201, 162, 77, 0.02) 100%); border: 1px solid rgba(201, 162, 77, 0.18); animation: notice-in 0.5s 0.3s ease both; }
.solo-success-divider { display: flex; align-items: center; justify-content: center; gap: 8px; margin-bottom: 12px; }
.ssm-line { flex: 1; height: 1px; background-color: rgba(201, 162, 77, 0.25); }
.ssm-star { font-size: 0.9rem; }
.solo-success-text { font-family: var(--font-body); color: var(--hp-silver); font-size: 0.85rem; line-height: 1.65; font-style: italic; margin: 0 0 8px; }
.solo-success-firma { font-family: var(--font-display); color: var(--hp-gold); font-size: 0.68rem; letter-spacing: 1px; opacity: 0.8; margin: 0; }

/* STEP 4 - Declinación */
.decline-view { padding: 20px 0; }
.decline-icon { font-size: 2.5rem; margin-bottom: 16px; }
.decline-title { font-family: var(--font-display); color: var(--hp-silver); font-size: 1.2rem; margin-bottom: 10px; }
.decline-text { color: var(--hp-silver); font-size: 0.88rem; opacity: 0.7; line-height: 1.5; }

/* STEP 5 - Ravenclaw */
.ravenclaw-view { padding: 10px 0; }
.ravenclaw-crest { width: 90px; height: 108px; margin: 0 auto 20px; color: rgba(0, 100, 180, 0.7); animation: crest-appear 0.7s cubic-bezier(0.175, 0.885, 0.32, 1.275) both; }
@keyframes crest-appear { from { transform: scale(0.6) translateY(10px); opacity: 0; } to { transform: scale(1) translateY(0); opacity: 1; } }
.ravenclaw-scroll { background: linear-gradient(160deg, rgba(0, 40, 100, 0.25) 0%, rgba(0, 20, 60, 0.15) 100%); border: 1px solid rgba(0, 100, 200, 0.2); border-top: 2px solid rgba(0, 120, 220, 0.35); padding: 20px 18px; margin-bottom: 6px; position: relative; }
.ravenclaw-scroll::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 1px; background: linear-gradient(90deg, transparent, rgba(180,150,80,0.4), transparent); }
.scroll-label { font-family: var(--font-display); color: rgba(100, 160, 220, 0.6); font-size: 0.6rem; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 10px; }
.ravenclaw-name { font-family: var(--font-display); color: #c0d8f0; font-size: 1.15rem; margin-bottom: 12px; text-shadow: 0 0 20px rgba(0, 120, 255, 0.3); }
.ravenclaw-divider { display: flex; align-items: center; justify-content: center; gap: 8px; margin-bottom: 14px; opacity: 0.5; }
.rv-line { width: 30px; height: 1px; background-color: rgba(0,120,200,0.5); }
.rv-star { color: var(--hp-gold); font-size: 0.75rem; }
.ravenclaw-message { font-family: var(--font-body); color: rgba(180, 210, 240, 0.85); font-size: 0.88rem; line-height: 1.6; font-style: italic; margin-bottom: 10px; }
.rv-gold { color: var(--hp-gold); font-style: normal; }
.ravenclaw-submsg { font-family: var(--font-body); color: rgba(150, 180, 210, 0.5); font-size: 0.75rem; line-height: 1.4; }
.btn-confirm.rv-btn { border-color: rgba(0, 100, 200, 0.4); color: rgba(150, 200, 255, 0.8); }
.btn-confirm.rv-btn:hover:not(:disabled) { background-color: rgba(0, 80, 180, 0.1); }

/* TELÉFONO ERROR */
.group-error { border-bottom-color: rgba(224, 80, 80, 0.5) !important; }
.field-error-msg { font-family: var(--font-display); color: #e07070; font-size: 0.65rem; letter-spacing: 0.5px; text-align: left; margin: -6px 0 10px 0; opacity: 0.9; }

/* DUMBLEDORE */
.dumbledore-container { text-align: center; margin-top: 40px; }
.quote-decoration { display: flex; align-items: center; justify-content: center; gap: 10px; margin-bottom: 15px; opacity: 0.3; }
.quote-decoration .line { width: 30px; height: 1px; background: var(--hp-gold); }
.quote-text { font-family: var(--font-body); color: var(--hp-silver); font-style: italic; font-size: 1.05rem; line-height: 1.6; max-width: 500px; margin: 0 auto 8px; }
.quote-author { font-family: var(--font-display); color: var(--hp-gold); font-size: 0.75rem; letter-spacing: 2px; text-transform: uppercase; }

/* SPINNER / ANIMACIONES */
.spinner { width: 16px; height: 16px; border: 2px solid rgba(201, 162, 77, 0.2); border-top-color: var(--hp-gold); border-radius: 50%; animation: spin 0.8s linear infinite; display: inline-block; }
@keyframes spin { to { transform: rotate(360deg); } }
@keyframes seal-drop { from { transform: scale(0) rotate(-15deg); opacity: 0; } to { transform: scale(1) rotate(0deg); opacity: 1; } }
@keyframes notice-in { from { opacity: 0; transform: translateY(-6px); } to { opacity: 1; transform: translateY(0); } }

/* RESPONSIVE */
@media (max-width: 850px) {
  .rsvp-split-layout { grid-template-columns: 1fr; gap: 30px; text-align: center; }
  .hat-inline-icon { float: none; margin: 0 auto 10px; }
  .owl-post-note { justify-content: center; }
  .sorting-hat-box { border-left: none; border-top: 1px solid var(--hp-gold); }
}
</style>