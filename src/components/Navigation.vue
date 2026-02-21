<template>
  <nav class="navigation" :class="{ 'scrolled': isScrolled, 'menu-open': menuOpen }">
    <div class="nav-container">
      <div class="nav-logo" @click="scrollToTop">
        <span class="initials">C <span class="ampersand">&</span> A</span>
        <span class="emblem">⚡</span>
      </div>

      <button class="menu-toggle" @click="toggleMenu">
        <div class="hamburger">
          <span class="bar top"></span>
          <span class="bar mid"></span>
          <span class="bar bot"></span>
        </div>
      </button>

      <div class="nav-overlay" @click="closeMenu"></div>

      <ul class="nav-menu" :class="{ active: menuOpen }">
        <li v-for="link in navLinks" :key="link.href">
          <a 
            :href="link.href" 
            @click="handleNavClick($event, link.href)"
            :class="{ 'active-link': activeSection === link.href }"
          >
            <span class="link-text">{{ link.text }}</span>
            <span class="sparkle">✦</span>
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navigation",
  data() {
    return {
      isScrolled: false,
      menuOpen: false,
      activeSection: '#inicio',
      navLinks: [
        { text: 'Inicio', href: '#inicio' },
        { text: 'Evento', href: '#evento' },
        { text: 'Dress Code', href: '#dress-code' },
        { text: 'Regalos', href: '#regalos' },
        { text: 'RSVP', href: '#rsvp' }
      ]
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
    this.handleScroll();
  },
  unmounted() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 50;
      const sections = ['inicio', 'evento', 'dress-code', 'regalos', 'rsvp'];
      for (const sectionId of sections) {
        const element = document.getElementById(sectionId);
        if (element) {
          const rect = element.getBoundingClientRect();
          if (rect.top <= 150 && rect.bottom >= 150) {
            this.activeSection = `#${sectionId}`;
          }
        }
      }
    },
    toggleMenu() { this.menuOpen = !this.menuOpen; },
    closeMenu() { this.menuOpen = false; },
    handleNavClick(e, href) {
      e.preventDefault();
      this.closeMenu();
      const target = document.querySelector(href);
      if (target) {
        const navHeight = 80;
        const targetPosition = target.offsetTop - navHeight;
        window.scrollTo({ top: targetPosition, behavior: 'smooth' });
      }
    },
    scrollToTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }
  }
}
</script>

<style scoped>
.navigation {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  transition: all 0.4s ease;
  padding: 10px 0;
}

.navigation.scrolled {
  background: rgba(0, 0, 0, 0.85);
  backdrop-filter: blur(10px);
  padding: 5px 0;
  border-bottom: 1px solid rgba(201, 162, 77, 0.3);
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 25px;
  display: flex;
  justify-content: space-between; /* LOGO IZQUIERDA - HAMBURGUESA DERECHA */
  align-items: center;
  height: 60px;
}

.nav-logo {
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 10px;
}

.initials {
  font-family: var(--font-display);
  font-size: 1.5rem;
  color: var(--hp-gold);
  letter-spacing: 2px;
}

.emblem { font-size: 1.2rem; filter: drop-shadow(0 0 5px var(--hp-gold)); }

.nav-menu {
  display: flex;
  list-style: none;
  gap: 30px;
}

.nav-menu li a {
  text-decoration: none;
  color: #fff;
  font-family: var(--font-display);
  font-size: 0.9rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  position: relative;
  transition: all 0.3s ease;
}

.nav-menu li a.active-link { color: var(--hp-gold); }

/* MOBILE STYLES */
.menu-toggle {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: 10px;
  margin-right: -10px; /* Ajuste para pegar al borde derecho */
}

@media (max-width: 850px) {
  .menu-toggle { display: block; }
  .nav-menu {
    position: fixed;
    top: 0;
    right: -100%;
    width: 280px;
    height: 100vh;
    background: #0a0a0a;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transition: 0.4s;
    z-index: 1002;
  }
  .nav-menu.active { right: 0; }
  .hamburger { width: 25px; height: 18px; display: flex; flex-direction: column; justify-content: space-between; }
  .bar { width: 100%; height: 2px; background: var(--hp-gold); transition: 0.3s; }
  
  .menu-open .bar.top { transform: translateY(8px) rotate(45deg); }
  .menu-open .bar.mid { opacity: 0; }
  .menu-open .bar.bot { transform: translateY(-8px) rotate(-45deg); }
}

.nav-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.7);
  display: none;
  z-index: 1001;
}
.menu-open .nav-overlay { display: block; }
</style>