<script setup>
import mapBg from '../assets/hogwarts-lineart.png'
import { ref, onMounted } from 'vue'

const emit = defineEmits(['close'])

// Tres líneas, mismo tamaño, se escriben en secuencia
const lines = [
  'Juro Solemnemente Que Mis Intenciones Son Buenas',
  '— ✦ —',
  'Ceci & Ángel',
]

const displayed  = ref(['', '', ''])
const cursors    = ref([false, false, false])
const writeDone  = ref(false)
const showHint   = ref(false)
const mapIn      = ref(false)
const lumos      = ref(false)
const closing    = ref(false)

function typeLine(lineIdx, delay = 0) {
  return new Promise(resolve => {
    const text = lines[lineIdx]
    setTimeout(() => {
      cursors.value[lineIdx] = true
      let i = 0
      const next = () => {
        if (i < text.length) {
          displayed.value[lineIdx] += text[i]
          i++
          const ch = text[i - 1]
          // ornamento y nombres van más lento para efecto dramático
          const speed = lineIdx === 1 ? 120
            : lineIdx === 2 ? 95 + Math.random() * 55
            : ch === ' ' ? 65 : 48 + Math.random() * 38
          setTimeout(next, speed)
        } else {
          cursors.value[lineIdx] = false
          resolve()
        }
      }
      next()
    }, delay)
  })
}

onMounted(async () => {
  setTimeout(() => { mapIn.value = true }, 300)

  await typeLine(0, 1200)          // "Juro solemnemente..."
  await new Promise(r => setTimeout(r, 300))
  await typeLine(1)                 // "— ✦ —"
  await new Promise(r => setTimeout(r, 280))
  await typeLine(2)                 // "Ceci & Ángel"

  writeDone.value = true
  setTimeout(() => { showHint.value = true }, 700)
})

function handleClick() {
  if (!writeDone.value) return
  lumos.value = true
  setTimeout(() => {
    closing.value = true
    setTimeout(() => emit('close'), 1400)
  }, 850)
}
</script>

<template>
  <div class="im-root" :class="{ 'im-closing': closing }" @click="handleClick">

    <div class="im-sky">
  <div class="stars s1"></div>
  <div class="stars s2"></div>
  <div class="stars s3"></div>
  <div class="nebula n1"></div>
  <div class="nebula n2"></div>
  </div>

    <!-- ── FLASH LUMOS ── -->
    <div class="lumos-flash" :class="{ active: lumos }"></div>

    <!-- ── CARTA DEL MAPA ── -->
    <div class="im-card" :class="{ 'card-in': mapIn, 'card-lumos': lumos }">

      <div class="im-map-img" :style="{ backgroundImage: `url(${mapBg})` }"></div>

      <!-- Gradiente sutil para leer el texto -->
      <div class="read-veil"></div>

      <!-- TEXTO: 3 líneas mismo tamaño, centradas sobre el castillo -->
      <div class="im-oath">

        <div class="oath-row">
          <span class="oath-text t-italic">{{ displayed[0] }}</span>
          <span v-if="cursors[0]" class="quill">✒</span>
        </div>

        <div class="oath-row oath-row--ornament">
          <span class="oath-text t-ornament">{{ displayed[1] }}</span>
          <span v-if="cursors[1]" class="quill">✒</span>
        </div>

        <div class="oath-row">
          <span class="oath-text t-names">{{ displayed[2] }}</span>
          <span v-if="cursors[2]" class="quill">✒</span>
        </div>

      </div>

      <!-- Polvo de tinta dorada -->
      <div class="dust-wrap" v-if="displayed[0].length > 5 && !closing">
        <span v-for="n in 16" :key="n" class="dust" :style="{'--di': n}"></span>
      </div>

      <!-- Hint -->
      <transition name="hint-fade">
        <p v-if="showHint" class="im-hint">✦ toca para revelar la invitación ✦</p>
      </transition>

    </div>

  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=IM+Fell+English:ital@0;1&family=Cinzel+Decorative:wght@400;700&display=swap');

/* ══════════════════════════════════════════
   RAÍZ
══════════════════════════════════════════ */
.im-root {
  position: fixed;
  inset: 0;
  z-index: 9999;
  display: flex;
  align-items: center;
  justify-content: center;
  animation: rootIn .7s ease forwards;
}
.im-root.im-closing {
  /* Eliminamos el efecto de brillo extra aquí para que no choque con el flash */
  animation: rootOut 0.8s ease forwards;
}
@keyframes rootIn  { from{opacity:0} to{opacity:1} }
@keyframes rootOut {
  from { opacity: 1; }
  to   { opacity: 0; }
}

/* ══════════════════════════════════════════
   FONDO — azul noche mágico, no tan oscuro
══════════════════════════════════════════ */
/* Modifica estos estilos en IntroMap.vue */
.im-sky {
  position: absolute;
  inset: 0;
  /* Fondo más cálido y terroso para que el mapa se sienta integrado */
  background: radial-gradient(circle at 50% 50%,
    #3b2a1a 0%,   /* Tono pergamino oscuro */
    #1a120b 50%, 
    #05070a 100%
  );
}
/* Luna */
.moon {
  position: absolute;
  top: 6%;
  right: 12%;
  width: clamp(50px, 7vw, 90px);
  height: clamp(50px, 7vw, 90px);
  border-radius: 50%;
  background: radial-gradient(circle at 40% 38%,
    rgba(255,252,235,.95) 0%,
    rgba(240,232,200,.80) 40%,
    rgba(220,210,175,.55) 70%,
    transparent 100%
  );
  box-shadow:
    0 0 clamp(20px,4vw,55px) clamp(8px,2vw,20px) rgba(220,210,170,.22),
    0 0 clamp(40px,8vw,110px) clamp(16px,4vw,40px) rgba(200,190,140,.12);
  animation: moonGlow 6s ease-in-out infinite;
}
@keyframes moonGlow {
  0%,100%{ filter:brightness(1); }
  50%    { filter:brightness(1.08); }
}

/* Nebulosas */
.nebula {
  position: absolute;
  border-radius: 50%;
  filter: blur(clamp(30px,6vw,80px));
  pointer-events: none;
}
.n1 {
  width: 45%; height: 35%;
  top: 5%; left: 5%;
  background: rgba(55, 90, 180, .22);
}
.n2 {
  width: 40%; height: 30%;
  bottom: 10%; right: 8%;
  background: rgba(90, 45, 130, .18);
}

/* ── ESTRELLAS ── */
.stars { position:absolute; inset:0; }

.s1 {
  background-image:
    radial-gradient(1px 1px at  4%  7%,  rgba(255,255,255,.85) 0%,transparent 100%),
    radial-gradient(1px 1px at 11% 19%,  rgba(255,255,255,.70) 0%,transparent 100%),
    radial-gradient(1px 1px at 19%  3%,  rgba(255,255,255,.78) 0%,transparent 100%),
    radial-gradient(1px 1px at 27% 31%,  rgba(255,255,255,.60) 0%,transparent 100%),
    radial-gradient(1px 1px at 35%  9%,  rgba(255,255,255,.72) 0%,transparent 100%),
    radial-gradient(1px 1px at 43% 23%,  rgba(255,255,255,.65) 0%,transparent 100%),
    radial-gradient(1px 1px at 52%  5%,  rgba(255,255,255,.80) 0%,transparent 100%),
    radial-gradient(1px 1px at 60% 16%,  rgba(255,255,255,.68) 0%,transparent 100%),
    radial-gradient(1px 1px at 68%  2%,  rgba(255,255,255,.75) 0%,transparent 100%),
    radial-gradient(1px 1px at 76% 28%,  rgba(255,255,255,.62) 0%,transparent 100%),
    radial-gradient(1px 1px at 84% 11%,  rgba(255,255,255,.78) 0%,transparent 100%),
    radial-gradient(1px 1px at 92%  6%,  rgba(255,255,255,.70) 0%,transparent 100%),
    radial-gradient(1px 1px at  7% 52%,  rgba(255,255,255,.55) 0%,transparent 100%),
    radial-gradient(1px 1px at 15% 68%,  rgba(255,255,255,.62) 0%,transparent 100%),
    radial-gradient(1px 1px at 23% 85%,  rgba(255,255,255,.58) 0%,transparent 100%),
    radial-gradient(1px 1px at 31% 74%,  rgba(255,255,255,.65) 0%,transparent 100%),
    radial-gradient(1px 1px at 39% 91%,  rgba(255,255,255,.52) 0%,transparent 100%),
    radial-gradient(1px 1px at 48% 61%,  rgba(255,255,255,.68) 0%,transparent 100%),
    radial-gradient(1px 1px at 57% 78%,  rgba(255,255,255,.60) 0%,transparent 100%),
    radial-gradient(1px 1px at 65% 95%,  rgba(255,255,255,.55) 0%,transparent 100%),
    radial-gradient(1px 1px at 73% 55%,  rgba(255,255,255,.70) 0%,transparent 100%),
    radial-gradient(1px 1px at 81% 88%,  rgba(255,255,255,.58) 0%,transparent 100%),
    radial-gradient(1px 1px at 89% 72%,  rgba(255,255,255,.65) 0%,transparent 100%),
    radial-gradient(1px 1px at 97% 42%,  rgba(255,255,255,.72) 0%,transparent 100%);
  animation: tw1 7s ease-in-out infinite;
}
.s2 {
  background-image:
    radial-gradient(1.5px 1.5px at  9% 13%, rgba(220,235,255,.82) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 24%  8%, rgba(220,235,255,.75) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 40% 20%, rgba(220,235,255,.80) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 56% 14%, rgba(220,235,255,.72) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 71%  4%, rgba(220,235,255,.78) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 87% 22%, rgba(220,235,255,.70) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at  5% 80%, rgba(220,235,255,.65) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 33% 92%, rgba(220,235,255,.72) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 62% 83%, rgba(220,235,255,.68) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 79% 70%, rgba(220,235,255,.75) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 95% 88%, rgba(220,235,255,.62) 0%,transparent 100%);
  animation: tw2 9s ease-in-out infinite 2s;
}
.s3 {
  background-image:
    radial-gradient(2px 2px at 16%  9%, rgba(255,252,230,.92) 0%,transparent 100%),
    radial-gradient(2px 2px at 38%  4%, rgba(255,252,230,.88) 0%,transparent 100%),
    radial-gradient(2px 2px at 63% 12%, rgba(255,252,230,.90) 0%,transparent 100%),
    radial-gradient(2px 2px at 82%  7%, rgba(255,252,230,.85) 0%,transparent 100%),
    radial-gradient(2px 2px at  3% 42%, rgba(255,252,230,.80) 0%,transparent 100%),
    radial-gradient(2px 2px at 94% 35%, rgba(255,252,230,.84) 0%,transparent 100%),
    radial-gradient(2px 2px at 28% 88%, rgba(255,252,230,.82) 0%,transparent 100%),
    radial-gradient(2px 2px at 72% 90%, rgba(255,252,230,.86) 0%,transparent 100%);
  animation: tw3 5.5s ease-in-out infinite 1s;
}
@keyframes tw1 { 0%,100%{opacity:.75} 50%{opacity:.35} }
@keyframes tw2 { 0%,100%{opacity:.85} 40%{opacity:.45} 70%{opacity:.80} }
@keyframes tw3 { 0%,100%{opacity:1}   35%{opacity:.50} 65%{opacity:.90} }

/* ══════════════════════════════════════════
   EFECTO LUMOS
══════════════════════════════════════════ */
.lumos-flash {
  position: absolute;
  inset: 0;
  z-index: 10;
  pointer-events: none;
  opacity: 0;
  background: radial-gradient(ellipse at 50% 50%,
    rgba(255,252,225,1) 0%,
    rgba(255,242,190,.85) 28%,
    rgba(255,225,140,.45) 58%,
    transparent 100%
  );
}
.lumos-flash.active {
  animation: lumosBurst 1.1s cubic-bezier(.2,0,.8,1) forwards;
}
@keyframes lumosBurst {
  0%  { opacity:0;   transform:scale(.25); }
  14% { opacity:1;   transform:scale(1); }
  42% { opacity:.90; transform:scale(1.5); }
  100%{ opacity:0;   transform:scale(2.8); }
}

/* ══════════════════════════════════════════
   CARTA DEL MAPA
══════════════════════════════════════════ */
.im-card {
  position: relative;
  width: min(90vw, 48vh);
  aspect-ratio: 2 / 3;
  border-radius: 2px;
  overflow: hidden;
  opacity: 0;
  transform: scale(.93) translateY(22px);
  transition:
    opacity   1.4s cubic-bezier(.22,1,.36,1),
    transform 1.4s cubic-bezier(.22,1,.36,1),
    box-shadow .5s ease;
  box-shadow: 
    0 0 20px rgba(0,0,0,0.5),
    inset 0 0 100px rgba(139, 69, 19, 0.15); 
  border: 1px solid rgba(180, 150, 80, 0.3);
  z-index: 2;
  background-color: #e4d1b9; /* Color base de pergamino */
  background-image: 
    url("https://www.transparenttextures.com/patterns/paper-fibers.png"); /* Textura sutil */
  filter: sepia(0.2) contrast(1.1); /* Envejecido digital */
}
.im-card.card-in {
  opacity: 1;
  transform: scale(1) translateY(0);
}
.im-card.card-lumos {
  box-shadow:
    0 0 50px  rgba(255,240,160,.65),
    0 0 110px rgba(255,220,100,.40),
    0 0 200px rgba(255,200,80,.22),
    inset 0 0 0 1px rgba(255,245,190,.55);
  transition: box-shadow .18s ease;
}

.im-map-img {
  position: absolute;
  inset: 0;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

.read-veil {
  position: absolute;
  inset: 0;
  background: radial-gradient(
    ellipse 80% 42% at 50% 60%,
    rgba(12,5,1,.18) 0%, transparent 100%
  );
  pointer-events: none;
}

/* ══════════════════════════════════════════
   TEXTO — todo el mismo tamaño
══════════════════════════════════════════ */
.im-oath {
  position: absolute;
  top: 57%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 88%;
  text-align: center;
  z-index: 3;
  pointer-events: none;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: .35em;
}

.oath-row {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 1.5em;
  line-height: 1.4;
}
.oath-row--ornament {
  min-height: 1.1em;
}

/* Tamaño único para todas las líneas */
.oath-text {
  font-size: clamp(.72rem, 2.2vw, 1.05rem);
  color: #3b2a1a;
  text-shadow:
    0 1px 5px rgba(230,190,100,.65),
    0 0 14px rgba(210,165,70,.30);
  filter: blur(0.3px)
}

.t-italic {
  font-family: 'IM Fell English', serif;
  font-style: italic;
  letter-spacing: .08em;
}
.t-ornament {
  font-family: 'IM Fell English', serif;
  letter-spacing: .3em;
  color: rgba(40,18,4,.55);
  font-size: clamp(.65rem, 1.8vw, .9rem);
}
.t-names {
  font-family: 'Cinzel Decorative', serif;
  font-weight: 700;
  letter-spacing: .2em;
  /* Mismo tamaño base pero un poco más prominente */
  font-size: clamp(.85rem, 2.6vw, 1.25rem);
  color: #140802;
  text-shadow:
    0 0 16px rgba(175,110,22,.55),
    0 0 38px rgba(148,88,8,.28),
    0 1px 0  rgba(228,182,85,.50);
}

/* Cursor pluma */
.quill {
  display: inline-block;
  font-size: clamp(.72rem, 2.2vw, 1.05rem);
  color: rgba(65,28,5,.68);
  margin-left: 2px;
  animation: quillAnim .55s ease-in-out infinite;
  transform: rotate(180deg);
}
@keyframes quillAnim {
  0%   { transform: rotate(180deg) translate(0, 0); }
  25%  { transform: rotate(185deg) translate(2px, -2px); }
  50%  { transform: rotate(175deg) translate(-1px, 1px); }
  100% { transform: rotate(180deg) translate(0, 0); }
}

/* ══════════════════════════════════════════
   POLVO DE TINTA
══════════════════════════════════════════ */
.dust-wrap {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 2;
}
.dust {
  position: absolute;
  top:  calc(54% + (var(--di) * 2.2% - 16%));
  left: calc(50%  + (var(--di) * 5.5% - 44%));
  width:  clamp(1.5px, .3vw, 3px);
  height: clamp(1.5px, .3vw, 3px);
  border-radius: 50%;
  background: rgba(165,108,25,.72);
  animation: dustRise calc(3s + var(--di) * .28s) ease-in-out infinite;
  animation-delay: calc(var(--di) * .25s);
}
.dust:nth-child(odd) {
  background: rgba(212,162,50,.55);
  width:  clamp(1px, .2vw, 2px);
  height: clamp(1px, .2vw, 2px);
}
@keyframes dustRise {
  0%  { opacity:0; transform:translate(0,0) scale(0); }
  22% { opacity:.82; transform:translate(calc((var(--di)-8)*3px), -7px) scale(1); }
  70% { opacity:.28; }
  100%{ opacity:0;  transform:translate(calc((var(--di)-8)*7px), -22px) scale(.2); }
}

/* ══════════════════════════════════════════
   HINT
══════════════════════════════════════════ */
.im-hint {
  position: absolute;
  bottom: 5%;
  left: 50%;
  transform: translateX(-50%);
  font-family: 'IM Fell English', serif;
  font-style: italic;
  font-size: clamp(.52rem, 1.5vw, .75rem);
  color: rgba(38,16,3,.48);
  letter-spacing: .16em;
  white-space: nowrap;
  z-index: 4;
  pointer-events: none;
  animation: hintPulse 2.8s ease-in-out infinite;
}
.hint-fade-enter-active{ transition: opacity .9s ease; }
.hint-fade-enter-from  { opacity: 0; }
@keyframes hintPulse {
  0%,100%{ opacity:.48; }
  50%    { opacity:.16; }
}
</style>