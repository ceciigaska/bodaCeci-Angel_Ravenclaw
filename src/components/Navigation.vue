<template>
  <nav class="navigation" :class="{ 'scrolled': isScrolled }">
    <div class="nav-container">
      <div class="nav-logo">
        <span class="initials">C & A</span>
        <div class="ravenclaw-emblem">⚡</div>
      </div>
      
      <button class="menu-toggle" @click="toggleMenu" aria-label="Menu">
        <span></span>
        <span></span>
        <span></span>
      </button>
      
      <ul class="nav-menu" :class="{ 'active': menuOpen }">
        <li><a href="#inicio" @click="closeMenu">Inicio</a></li>
        <li><a href="#cuenta-regresiva" @click="closeMenu">Cuenta Regresiva</a></li>
        <li><a href="#evento" @click="closeMenu">El Evento</a></li>
        <li><a href="#dress-code" @click="closeMenu">Dress Code</a></li>
        <li><a href="#galeria" @click="closeMenu">Galería</a></li>
        <li><a href="#regalos" @click="closeMenu">Regalos</a></li>
        <li><a href="#rsvp" @click="closeMenu">Confirmar</a></li>
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
    handleScroll() {
      this.isScrolled = window.scrollY > 100
    },
    toggleMenu() {
      this.menuOpen = !this.menuOpen
    },
    closeMenu() {
      this.menuOpen = false
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
  padding: 20px 0;
  z-index: 1000;
  transition: all 0.3s ease;
  background: transparent;
}

.navigation.scrolled {
  background: rgba(14, 26, 64, 0.95);
  backdrop-filter: blur(10px);
  padding: 15px 0;
  box-shadow: 0 5px 30px rgba(148, 107, 45, 0.2);
}

.nav-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav-logo {
  display: flex;
  align-items: center;
  gap: 15px;
}

.initials {
  /*font-family: var(--font-display);*/
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--ravenclaw-bronze);
  letter-spacing: 3px;
}

.ravenclaw-emblem {
  font-size: 1.5rem;
  animation: float 3s ease-in-out infinite;
}

.menu-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 10px;
}

.menu-toggle span {
  width: 25px;
  height: 3px;
  background: var(--ravenclaw-bronze);
  transition: all 0.3s ease;
}

.nav-menu {
  display: flex;
  list-style: none;
  gap: 40px;
  align-items: center;
}

.nav-menu li a {
  /*font-family: var(--font-display);*/
  color: var(--star-white);
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 600;
  letter-spacing: 1px;
  text-transform: uppercase;
  position: relative;
  transition: color 0.3s ease;
}

.nav-menu li a::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--ravenclaw-bronze);
  transition: width 0.3s ease;
}

.nav-menu li a:hover {
  color: var(--ravenclaw-bronze);
}

.nav-menu li a:hover::after {
  width: 100%;
}

@media (max-width: 768px) {
  .nav-container {
    padding: 0 20px;
  }
  
  .menu-toggle {
    display: flex;
    z-index: 1001;
  }
  
  .nav-menu {
    position: fixed;
    top: 0;
    right: -100%;
    width: 70%;
    height: 100vh;
    background: rgba(14, 26, 64, 0.98);
    backdrop-filter: blur(10px);
    flex-direction: column;
    justify-content: center;
    gap: 30px;
    transition: right 0.3s ease;
    padding: 40px;
  }
  
  .nav-menu.active {
    right: 0;
  }
  
  .nav-menu li a {
    font-size: 1.2rem;
  }
}
</style>