<template>
  <div id="app">
    <!-- Estrellas de fondo -->
    <div class="stars-background"></div>
    
    <!-- Navegación -->
    <Navigation />
    
    <!-- Hero Section -->
    <HeroSection />
    
    <!-- Countdown -->
    <CountdownSection :weddingDate="weddingDate" />
    
    <!-- Información del Evento -->
    <EventInfo />
    
    <!-- Dress Code -->
    <DressCode />
    
    <!-- Galería -->
    <Gallery />
    
    <!-- Mesa de Regalos -->
    <GiftTable />
    
    <!-- RSVP -->
    <RsvpSection />
    
    <!-- Footer -->
    <Footer />
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue'
import HeroSection from './components/HeroSection.vue'
import CountdownSection from './components/CountdownSection.vue'
import EventInfo from './components/EventInfo.vue'
import DressCode from './components/DressCode.vue'
import Gallery from './components/Gallery.vue'
import GiftTable from './components/GiftTable.vue'
import RsvpSection from './components/RsvpSection.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Navigation,
    HeroSection,
    CountdownSection,
    EventInfo,
    DressCode,
    Gallery,
    GiftTable,
    RsvpSection,
    Footer
  },
  data() {
    return {
      weddingDate: new Date('2026-10-30T18:00:00') // Ajusta la fecha de tu boda
    }
  }
}
</script>

<style>
#app {
  position: relative;
  min-height: 100vh;
}

.stars-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(ellipse at bottom, #1a2f5f 0%, #0a0e1f 100%);
  z-index: -2;
}

.stars-background::before,
.stars-background::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    radial-gradient(2px 2px at 20px 30px, white, transparent),
    radial-gradient(2px 2px at 60px 70px, white, transparent),
    radial-gradient(1px 1px at 50px 50px, white, transparent),
    radial-gradient(1px 1px at 130px 80px, white, transparent),
    radial-gradient(2px 2px at 90px 10px, white, transparent);
  background-repeat: repeat;
  background-size: 200px 200px;
  animation: twinkle 5s ease-in-out infinite;
  z-index: -1;
}

.stars-background::after {
  background-size: 300px 300px;
  animation-duration: 7s;
  opacity: 0.5;
}
</style>
