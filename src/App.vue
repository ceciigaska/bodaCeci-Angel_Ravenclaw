<template>
  <IntroMap v-if="showIntro" @close="handleCloseIntro" />

  <transition name="fade-invitation">
    <div v-if="!showIntro" id="app">
      <div class="stars-background"></div>

      <div class="app-background">
        <Navigation />
        <HeroSection id="inicio" />
        <CountdownSection id="cuenta-regresiva" :weddingDate="weddingDate" />
        <EventInfo id="evento" />
        <DressCode id="dress-code" />
        <GiftTable id="regalos" />
        <RsvpSection id="rsvp" />
        <Footer />
      </div>
    </div>
  </transition>
</template>

<script>
import Navigation       from './components/Navigation.vue'
import HeroSection      from './components/HeroSection.vue'
import CountdownSection from './components/CountdownSection.vue'
import EventInfo        from './components/EventInfo.vue'
import DressCode        from './components/DressCode.vue'
import GiftTable        from './components/GiftTable.vue'
import RsvpSection      from './components/RsvpSection.vue'
import Footer           from './components/Footer.vue'
import IntroMap         from './components/IntroMap.vue'

export default {
  name: 'App',
  components: {
    Navigation,
    HeroSection,
    CountdownSection,
    EventInfo,
    DressCode,
    GiftTable,
    RsvpSection,
    Footer,
    IntroMap
  },
  data() {
    return {
      weddingDate: new Date('2026-10-30T17:30:00'),
      showIntro: true
    }
  },
  methods: {
    handleCloseIntro() {
      this.showIntro = false;
      localStorage.setItem('introSeen', 'true');
      
      this.$nextTick(() => {
        window.scrollTo(0, 0);
      });
    },
  },
  mounted() {
    if ('scrollRestoration' in history) {
      history.scrollRestoration = 'manual';
    }
    if (window.location.hash) {
      history.replaceState(null, null, window.location.pathname);
    }
    window.scrollTo(0, 0);
  }
}
</script>

<style>
/* TRANSICIÓN MÁGICA DE ENTRADA */
.fade-invitation-enter-active {
  transition: opacity 2s ease-in-out;
}
.fade-invitation-enter-from {
  opacity: 0;
}
.fade-invitation-enter-to {
  opacity: 1;
}
</style>
