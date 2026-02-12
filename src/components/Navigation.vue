<template>
  <nav class="navigation" :class="{ 'scrolled': isScrolled }">
    <div class="nav-container">
      <div class="nav-logo">
        <span class="initials">C & A</span>
        <span class="emblem">🦅</span>
      </div>

      <button class="menu-toggle" @click="toggleMenu" aria-label="Menu">
        <span :class="{ open: menuOpen }"></span>
        <span :class="{ open: menuOpen }"></span>
        <span :class="{ open: menuOpen }"></span>
      </button>

      <ul class="nav-menu" :class="{ 'active': menuOpen }">
        <li><a href="#inicio"            @click="closeMenu">Inicio</a></li>
        <li><a href="#cuenta-regresiva"  @click="closeMenu">Cuenta Regresiva</a></li>
        <li><a href="#evento"            @click="closeMenu">El Evento</a></li>
        <li><a href="#dress-code"        @click="closeMenu">Dress Code</a></li>
        <li><a href="#regalos"           @click="closeMenu">Regalos</a></li>
        <li><a href="#rsvp"              @click="closeMenu">Confirmar</a></li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navigation',
  data() {
    return {
      isScrolled: false,
      menuOpen: false
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() { this.isScrolled = window.scrollY > 80 },
    toggleMenu()   { this.menuOpen = !this.menuOpen },
    closeMenu()    { this.menuOpen = false }
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
  padding: 6px 0;
  transition: background 0.4s ease, padding 0.3s ease;
  background: transparent;
}

.navigation.scrolled {
  background: rgba(10, 14, 31, 0.92);
  backdrop-filter: blur(16px);
  border-bottom: 1px solid rgba(201, 162, 77, 0.2);
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 14px 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* Logo */
.nav-logo {
  display: flex;
  align-items: center;
  gap: 10px;
}

.initials {
  font-family: var(--font-display);
  font-size: 1.2rem;
  letter-spacing: 5px;
  color: var(--hp-gold);
}

.emblem {
  font-size: 1.3rem;
  animation: float 4s ease-in-out infinite;
}

/* Menú */
.nav-menu {
  list-style: none;
  display: flex;
  gap: 36px;
  margin: 0;
  padding: 0;
}

.nav-menu li a {
  font-family: var(--font-display);
  text-decoration: none;
  color: rgba(248, 249, 250, 0.8);
  letter-spacing: 2px;
  font-size: 0.8rem;
  text-transform: uppercase;
  position: relative;
  transition: color 0.3s ease;
}

.nav-menu li a::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -5px;
  width: 0;
  height: 1px;
  background: var(--hp-gold);
  transition: width 0.3s ease;
}

.nav-menu li a:hover {
  color: var(--hp-gold);
}

.nav-menu li a:hover::after {
  width: 100%;
}

/* Hamburguesa */
.menu-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 8px;
}

.menu-toggle span {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--hp-gold);
  transition: all 0.3s ease;
  transform-origin: center;
}

.menu-toggle span.open:nth-child(1) { transform: translateY(7px) rotate(45deg); }
.menu-toggle span.open:nth-child(2) { opacity: 0; transform: scaleX(0); }
.menu-toggle span.open:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }

@media (max-width: 768px) {
  .nav-container { padding: 14px 20px; }

  .menu-toggle { display: flex; z-index: 1001; }

.nav-menu {
    position: fixed;
    top: 0;
    right: -100%; /* Escondido por defecto */
    width: 80%; /* No satures toda la pantalla */
    height: 100vh;
    background: var(--ravenclaw-blue);
    flex-direction: column;
    justify-content: center;
    transition: 0.4s ease-in-out;
  }

  .nav-menu.active {
    right: 0; /* Entra suavemente */
  }

  .nav-menu li a { font-size: 1rem; letter-spacing: 3px; }
}
</style>