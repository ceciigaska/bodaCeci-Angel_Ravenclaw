<script setup>
import mapBg from '../assets/hogwarts-lineart.png'
import { ref, onMounted, onUnmounted } from 'vue'

const emit = defineEmits(['close'])

const lines = [
  'Juro Solemnemente Que Mis Intenciones Son Buenas',
  '30 ✦ Octubre ✦ 2026',
  'Cecilia & Ángel',
]

const displayed  = ref(['', '', ''])
const cursors    = ref([false, false, false])
const writeDone  = ref(false)
const showHint   = ref(false)
const mapIn      = ref(false)
const lumos      = ref(false)
const closing    = ref(false)
const lumosPos   = ref({ x: 50, y: 50 })

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
          const speed = lineIdx === 1 ? 120 
            : lineIdx === 2 ? 95 + Math.random() * 55 
            : text[i-1] === ' ' ? 65 : 48 + Math.random() * 38
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
  document.body.style.overflow = 'hidden'
  const img = new Image()
  img.src = mapBg
  img.onload = () => {
    mapIn.value = true
    startTypingSequence()
  }
})

onUnmounted(() => {
  document.body.style.overflow = ''
})

async function startTypingSequence() {
  await typeLine(0, 800)
  await typeLine(1, 300)
  await typeLine(2, 280)
  writeDone.value = true
  setTimeout(() => { showHint.value = true }, 500)
}

function handleMapClick(e) {
  if (!writeDone.value || lumos.value) return

  const x = (e.clientX / window.innerWidth) * 100
  const y = (e.clientY / window.innerHeight) * 100
  lumosPos.value = { x, y }

  lumos.value = true 
  
  // Iniciamos el desvanecimiento del mapa poco después del brillo
  setTimeout(() => {
    closing.value = true
    document.body.style.overflow = ''
    // Tiempo para que la transición de CSS termine antes de desmontar
    setTimeout(() => emit('close'), 1500)
  }, 400)
}
</script>

<template>
  <div class="im-root" :class="{ 'im-closing': closing }" @click="handleMapClick">
    
    <div class="im-sky">
      <div class="stars s1"></div>
      <div class="stars s2"></div>
      <div class="nebula n1"></div>
    </div>

    <div 
      class="lumos-flash" 
      :class="{ active: lumos }"
      :style="{ left: lumosPos.x + '%', top: lumosPos.y + '%' }"
    ></div>

    <div class="im-card" :class="{ 'card-in': mapIn, 'card-out': lumos }">
      <div class="im-map-img" :style="{ backgroundImage: `url(${mapBg})` }"></div>
      
      <div class="read-veil"></div>

      <div class="im-oath" :class="{ 'fade-out-text': lumos }">
        <div v-for="(line, idx) in displayed" :key="idx" class="oath-row">
          <span :class="['oath-text', idx === 0 ? 't-italic' : idx === 1 ? 't-ornament' : 't-names']">
            {{ line }}
          </span>
          <div v-if="cursors[idx]" class="quill-wrapper">
             <svg class="quill-svg" viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg">
                <path d="M448 0c-35.35 0-64 28.65-64 64 0 11.05 2.8 21.43 7.74 30.48l-231.1 231.1c-15.62 15.62-15.62 40.95 0 56.57 15.62 15.62 40.95 15.62 56.57 0l231.1-231.1c9.05 4.94 19.43 7.74 30.48 7.74 35.35 0 64-28.65 64-64S483.35 0 448 0zM128 448c-17.67 0-32-14.33-32-32s14.33-32 32-32 32 14.33 32 32-14.33 32-32 32zm-64 64c-35.35 0-64-28.65-64-64s28.65-64 64-64 64 28.65 64 64-28.65 64-64 64z" fill="#3b2a1a"/>
             </svg>
          </div>
        </div>
      </div>

      <transition name="hint-fade">
        <p v-if="showHint && !lumos" class="im-hint">✦ Toca el mapa para revelar el camino ✦</p>
      </transition>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=IM+Fell+English:ital@0;1&family=Cinzel+Decorative:wght@400;700&display=swap');

.im-root {
  position: fixed;
  inset: 0;
  z-index: 9999;
  cursor: pointer;
  background: #000;
  overflow: hidden;
}

/* LUMOS DORADO SUTIL */
.lumos-flash {
  position: absolute;
  width: 15px;
  height: 15px;
  background: #fff8e1;
  border-radius: 50%;
  transform: translate(-50%, -50%) scale(0);
  z-index: 100;
  pointer-events: none;
  box-shadow: 0 0 100px 50px #ffecb3;
}
.lumos-flash.active {
  animation: lumosBurst 1.8s cubic-bezier(0.1, 0.8, 0.15, 1) forwards;
}
@keyframes lumosBurst {
  0% { transform: translate(-50%, -50%) scale(0); opacity: 1; }
  30% { transform: translate(-50%, -50%) scale(150); opacity: 1; }
  100% { transform: translate(-50%, -50%) scale(300); opacity: 0; }
}

/* CARTA PERGAMINO */
.im-card {
  position: absolute;
  inset: 0;
  background-color: #e4d1b9;
  opacity: 0;
  transition: opacity 1.2s ease-in-out, transform 1.5s ease-in-out, filter 1.2s ease;
  z-index: 2;
}
.im-card.card-in { opacity: 1; }

/* Efecto cuando se da click: el mapa se desvanece y se expande */
.im-card.card-out {
  opacity: 0;
  transform: scale(1.1);
  filter: brightness(1.2) blur(5px);
  pointer-events: none;
}

.im-map-img {
  position: absolute;
  inset: 0;
  background-size: cover;
  background-position: center bottom;
  background-repeat: no-repeat;
  opacity: 1;
}

/* PLUMA DE AVE REALISTA */
.quill-wrapper {
  display: inline-block;
  width: 35px;
  height: 35px;
  margin-left: 10px;
  vertical-align: middle;
  transform-origin: bottom left;
  animation: quillWrite 0.7s infinite ease-in-out;
}
.quill-svg {
  width: 100%;
  height: 100%;
  transform: rotate(200deg);
  filter: drop-shadow(0 2px 3px rgba(0,0,0,0.3));
}
@keyframes quillWrite {
  0%, 100% { transform: rotate(0deg) translateY(0); }
  50% { transform: rotate(-12deg) translateY(-4px); }
}

/* TEXTO */
.im-oath {
  position: absolute;
  top: 45%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 90%;
  text-align: center;
  transition: all 1s ease;
}
.fade-out-text {
  opacity: 0;
  filter: blur(15px);
  transform: translate(-50%, -60%) scale(0.9);
}

.oath-text {
  color: #1a0f08;
  display: inline-block;
}
.t-italic { font-family: 'IM Fell English', serif; font-style: italic; font-size: clamp(1.2rem, 3.5vw, 1.8rem); }
.t-ornament { opacity: 0.5; margin: 15px 0; font-size: 1.4rem; font-family: 'IM Fell English', serif; }
.t-names { font-family: 'Cinzel Decorative', serif; font-size: clamp(2.2rem, 6vw, 3.2rem); font-weight: bold; }

.im-hint {
  position: absolute;
  bottom: 8%;
  width: 100%;
  text-align: center;
  font-family: 'IM Fell English', serif;
  font-style: italic;
  color: #1a0f08;
  opacity: 0.4;
  letter-spacing: 2px;
}

/* FONDO CIELO (El que quedará visible al final) */
.im-sky { 
  position: absolute; 
  inset: 0; 
  background: #050505; 
  z-index: 1;
}
.stars { position: absolute; inset: 0; background-image: radial-gradient(1px 1px at 20% 30%, #fff, transparent), radial-gradient(1.5px 1.5px at 70% 60%, #fff, transparent); }
.n1 { position: absolute; inset: 0; background: radial-gradient(circle, #1a120b 0%, #000 80%); opacity: 0.7; }
</style>