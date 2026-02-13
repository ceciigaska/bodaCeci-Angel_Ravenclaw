<template>

  <!-- Intro tipo Mapa del Merodeador -->
  <IntroMap
    v-if="showIntro"
    @close="handleCloseIntro"
  />

  <div id="app">
    <!-- Fondo estrellado fijo -->
    <div class="stars-background"></div>

    <div class="app-background">
      <Navigation />
      <HeroSection />
      <CountdownSection :weddingDate="weddingDate" />
      <EventInfo />
      <DressCode />
      <GiftTable />
      <RsvpSection />
      <Footer />
    </div>
  </div>
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
      this.showIntro = false
    }
  }
}
</script>
