<template>
  <section id="galeria" class="gallery-section section">
    <div class="container">
      <h2 class="section-title">Nuestra Historia en Imágenes</h2>
      
      <div class="gallery-intro">
        <p class="intro-text">
          Cada fotografía cuenta un capítulo de nuestra historia mágica juntos
        </p>
      </div>
      
      <div class="gallery-grid">
        <div 
          v-for="(photo, index) in photos" 
          :key="index"
          class="gallery-item fade-in"
          :style="{ animationDelay: `${index * 0.1}s` }"
          @click="openPhoto(index)"
        >
          <div class="photo-placeholder">
            <div class="photo-icon">{{ photo.icon }}</div>
            <div class="photo-caption">{{ photo.caption }}</div>
          </div>
          <div class="photo-overlay">
            <span class="view-text">Ver foto</span>
          </div>
        </div>
      </div>
      
      <!-- Modal de foto (opcional) -->
      <div v-if="selectedPhoto !== null" class="photo-modal" @click="closePhoto">
        <div class="modal-content">
          <button class="close-button" @click.stop="closePhoto">✕</button>
          <div class="modal-photo">
            <div class="photo-icon large">{{ photos[selectedPhoto].icon }}</div>
            <p class="modal-caption">{{ photos[selectedPhoto].caption }}</p>
          </div>
        </div>
      </div>
      
      <div class="gallery-note">
        <p>
          📸 Aquí puedes agregar tus fotos reales. Simplemente reemplaza los placeholders con las URL de tus imágenes.
        </p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Gallery',
  data() {
    return {
      selectedPhoto: null,
      photos: [
        { icon: '📚', caption: 'Nuestro primer encuentro en la biblioteca' },
        { icon: '☕', caption: 'Primera cita mágica' },
        { icon: '🌟', caption: 'Una noche bajo las estrellas' },
        { icon: '🎄', caption: 'Nuestra primera navidad juntos' },
        { icon: '✈️', caption: 'Aventuras alrededor del mundo' },
        { icon: '🎓', caption: 'Graduación y nuevos comienzos' },
        { icon: '🏔️', caption: 'Escalando montañas juntos' },
        { icon: '💍', caption: 'El día que dijo sí' },
        { icon: '🎉', caption: 'Celebrando cada momento' }
      ]
    }
  },
  methods: {
    openPhoto(index) {
      this.selectedPhoto = index
      document.body.style.overflow = 'hidden'
    },
    closePhoto() {
      this.selectedPhoto = null
      document.body.style.overflow = 'auto'
    }
  },
  beforeUnmount() {
    document.body.style.overflow = 'auto'
  }
}
</script>

<style scoped>
.gallery-section {
  background: linear-gradient(180deg, rgba(14, 26, 64, 0.9), rgba(10, 14, 31, 0.9));
  position: relative;
}

.gallery-intro {
  text-align: center;
  max-width: 700px;
  margin: 0 auto 60px;
}

.intro-text {
  /*font-family: var(--font-body);*/
  font-size: 1.3rem;
  color: var(--ravenclaw-silver);
  font-style: italic;
  line-height: 1.8;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 30px;
  max-width: 1200px;
  margin: 0 auto 60px;
}

.gallery-item {
  position: relative;
  aspect-ratio: 1;
  cursor: pointer;
  overflow: hidden;
  border: 3px solid var(--ravenclaw-bronze);
  transition: all 0.3s ease;
}

.gallery-item:hover {
  transform: scale(1.05);
  box-shadow: 0 20px 50px rgba(148, 107, 45, 0.4);
  border-color: var(--ravenclaw-gold);
}

.photo-placeholder {
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, var(--ravenclaw-blue), var(--ravenclaw-blue-light));
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 20px;
  padding: 30px;
  position: relative;
}

.photo-placeholder::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    repeating-linear-gradient(45deg, transparent, transparent 10px, rgba(148, 107, 45, 0.1) 10px, rgba(148, 107, 45, 0.1) 20px);
  pointer-events: none;
}

.photo-icon {
  font-size: 5rem;
  z-index: 1;
  animation: float 3s ease-in-out infinite;
}

.photo-caption {
  /*font-family: var(--font-body);*/
  font-size: 1.1rem;
  color: var(--star-white);
  text-align: center;
  z-index: 1;
  font-weight: 500;
}

.photo-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(14, 26, 64, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.gallery-item:hover .photo-overlay {
  opacity: 1;
}

.view-text {
  /*font-family: var(--font-display);*/
  font-size: 1.2rem;
  color: var(--ravenclaw-bronze);
  letter-spacing: 2px;
  text-transform: uppercase;
}

/* Modal */
.photo-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.95);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
  padding: 20px;
  animation: fadeIn 0.3s ease;
}

.modal-content {
  position: relative;
  max-width: 800px;
  width: 100%;
}

.close-button {
  position: absolute;
  top: -40px;
  right: 0;
  background: none;
  border: none;
  color: var(--star-white);
  font-size: 2rem;
  cursor: pointer;
  transition: color 0.3s ease;
  padding: 10px;
}

.close-button:hover {
  color: var(--ravenclaw-bronze);
}

.modal-photo {
  background: linear-gradient(135deg, var(--ravenclaw-blue), var(--ravenclaw-blue-light));
  border: 4px solid var(--ravenclaw-bronze);
  padding: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 30px;
  min-height: 400px;
}

.photo-icon.large {
  font-size: 8rem;
}

.modal-caption {
  /*font-family: var(--font-body);*/
  font-size: 1.5rem;
  color: var(--star-white);
  text-align: center;
}

.gallery-note {
  max-width: 800px;
  margin: 60px auto 0;
  text-align: center;
  padding: 30px;
  background: rgba(148, 107, 45, 0.1);
  border: 2px dashed var(--ravenclaw-bronze);
}

.gallery-note p {
  /*font-family: var(--font-body);*/
  font-size: 1.1rem;
  color: var(--ravenclaw-silver);
  line-height: 1.6;
}

@media (max-width: 768px) {
  .gallery-grid {
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 20px;
  }
  
  .photo-icon {
    font-size: 4rem;
  }
  
  .photo-caption {
    font-size: 1rem;
  }
  
  .modal-photo {
    padding: 40px 20px;
    min-height: 300px;
  }
  
  .photo-icon.large {
    font-size: 6rem;
  }
}

@media (max-width: 480px) {
  .gallery-grid {
    grid-template-columns: 1fr;
  }
}
</style>