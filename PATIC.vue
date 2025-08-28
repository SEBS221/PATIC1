<template>
  <div class="app">
    <!-- Header -->
    <header class="header">
      <div class="header-content">
        <div class="logo">
          <div class="logo-icon">UPB</div>
          <div class="logo-text">
            <h1>Universidad Pontificia Bolivariana</h1>
            <p>Campus Medellín • Laureles</p>
          </div>
        </div>
        <nav class="nav">
          <a href="#" class="nav-btn" :class="{ active: currentSection === 'home' }" @click.prevent="changeSection('home')">
            <i class="fas fa-home"></i>
            Inicio
          </a>
          <a href="#" class="nav-btn" :class="{ active: currentSection === 'map' }" @click.prevent="changeSection('map')">
            <i class="fas fa-map-marked-alt"></i>
            Mapa
          </a>
        </nav>
      </div>
    </header>

    <!-- Main Content -->
    <main class="main-content">
      <!-- Home Section -->
      <section id="home" class="section" :class="{ active: currentSection === 'home' }">
        <div class="hero">
          <div class="hero-content animate-fade-in">
            <h2>Explora el Campus UPB</h2>
            <p>Descubre los espacios vibrantes, las facultades destacadas y los lugares emblemáticos de nuestra universidad en el corazón de Medellín.</p>
            <a href="#" class="cta-button" @click.prevent="changeSection('map')">
              <i class="fas fa-map-marked-alt"></i>
              Explorar Mapa Interactivo
            </a>
          </div>
          <div class="particle-effect"></div>
        </div>
      </section>

      <!-- Map Section -->
      <section id="map" class="section" :class="{ active: currentSection === 'map' }">
        <div class="container">
          <div class="map-section">
            <div class="map-header">
              <h3><i class="fas fa-map-marker-alt"></i> Campus UPB Medellín</h3>
              <p>Circular 1 #70-01, Barrio Laureles • Medellín, Antioquia</p>
            </div>
            <div class="map-container">
              <div class="map-sidebar">
                <div class="sidebar-header">
                  <i class="fas fa-list-ul"></i>
                  Lugares de Interés
                </div>
                <div class="places-list">
                  <div class="place-category">
                    <div class="category-header">
                      <i class="fas fa-graduation-cap"></i>
                      Facultades
                    </div>
                    <div class="place-item" @click="highlightLocation('engineering')">
                      <i class="fas fa-cogs"></i>
                      Facultad de Ingeniería
                    </div>
                    <div class="place-item" @click="highlightLocation('medicine')">
                      <i class="fas fa-stethoscope"></i>
                      Facultad de Medicina
                    </div>
                  </div>
                </div>
              </div>
              <iframe
                id="google-map"
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3966.528!2d-75.571234!3d6.251184!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8e4429b7f4a8b1e3%3A0x8f5d8c2b9a7e6f4c!2sUniversidad%20Pontificia%20Bolivariana%20-%20Campus%20Laureles!5e0!3m2!1ses!2sco!4v1693159999!5m2!1ses!2sco"
                allowfullscreen=""
                loading="lazy"
                referrerpolicy="no-referrer-when-downgrade"
              ></iframe>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      currentSection: 'home'
    };
  },
  methods: {
    changeSection(section) {
      this.currentSection = section;
    },
    highlightLocation(location) {
      alert(`Ubicación seleccionada: ${location}`);
      // Add logic to highlight on map (e.g., using Google Maps API)
    }
  }
};
</script>

<style scoped>
/* Updated CSS with refined red, black, and gold colors */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --upb-gold: #D4AF37;         /* Gold */
  --upb-red: #C41E3A;          /* Red */
  --upb-dark: #000000;         /* Pure Black for background */
  --upb-light-gold: #F4E192;   /* Light Gold */
  --upb-dark-red: #8B0A1E;     /* Darker Red */
  --gradient-primary: linear-gradient(135deg, var(--upb-red), var(--upb-dark-red));
  --gradient-secondary: linear-gradient(135deg, var(--upb-gold), var(--upb-light-gold));
  --shadow-soft: 0 10px 40px rgba(0, 0, 0, 0.3);
  --shadow-strong: 0 20px 60px rgba(196, 30, 58, 0.5);
  --border-radius: 24px;
  --animation-smooth: cubic-bezier(0.4, 0, 0.2, 1);
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  background: var(--upb-dark); /* Line 144 - Controls page background */
  min-height: 100vh;
  overflow-x: hidden;
  color: #ffffff;
}

/* Header */
.header {
  background: rgba(26, 26, 26, 0.95);
  backdrop-filter: blur(20px);
  border-bottom: 2px solid var(--upb-gold);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 1.5rem 0;
  transition: all 0.4s var(--animation-smooth);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
}

.header-content {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

.logo-icon {
  width: 70px;
  height: 70px;
  background: var(--gradient-secondary);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 900;
  font-size: 1.9rem;
  color: var(--upb-dark);
  box-shadow: var(--shadow-soft);
  border: 5px solid var(--upb-red);
  transition: transform 0.4s var(--animation-smooth), box-shadow 0.4s var(--animation-smooth);
}

.logo-icon:hover {
  transform: scale(1.15);
  box-shadow: 0 15px 50px rgba(212, 175, 55, 0.6);
}

.logo-text h1 {
  color: var(--upb-gold);
  font-size: 2rem;
  font-weight: 900;
  margin-bottom: 0.3rem;
  text-shadow: 0 3px 10px rgba(212, 175, 55, 0.5);
}

.logo-text p {
  color: var(--upb-light-gold);
  font-size: 1.1rem;
  font-weight: 600;
}

.nav {
  display: flex;
  gap: 1.5rem;
}

.nav-btn {
  background: transparent;
  border: 2px solid rgba(212, 175, 55, 0.3);
  color: var(--upb-light-gold);
  padding: 0.9rem 2rem;
  border-radius: 30px;
  cursor: pointer;
  transition: all 0.4s var(--animation-smooth);
  font-weight: 700;
  display: flex;
  align-items: center;
  gap: 0.8rem;
  text-decoration: none;
  position: relative;
  overflow: hidden;
}

.nav-btn::after {
  content: '';
  position: absolute;
  width: 0;
  height: 100%;
  background: rgba(212, 175, 55, 0.2);
  top: 0;
  left: 0;
  transition: width 0.4s var(--animation-smooth);
  z-index: 0;
}

.nav-btn:hover::after, .nav-btn.active::after {
  width: 100%;
}

.nav-btn:hover, .nav-btn.active {
  background: var(--gradient-primary);
  border-color: var(--upb-gold);
  color: white;
  transform: translateY(-4px);
  box-shadow: var(--shadow-strong);
}

.nav-btn i {
  font-size: 1.2rem;
}

/* Hero Section */
.hero {
  background: var(--gradient-primary);
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  padding-top: 80px;
}

.hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grid" width="15" height="15" patternUnits="userSpaceOnUse"><path d="M 15 0 L 0 0 0 15" fill="none" stroke="rgba(212,175,55,0.3)" stroke-width="0.5"/></pattern></defs><rect width="100" height="100" fill="url(%23grid)"/></svg>');
  opacity: 0.7;
  z-index: 1;
}

.particle-effect {
  position: absolute;
  width: 100%;
  height: 100%;
  overflow: hidden;
  pointer-events: none;
}

.particle-effect::before,
.particle-effect::after {
  content: '';
  position: absolute;
  background: rgba(212, 175, 55, 0.1);
  border-radius: 50%;
  animation: float 15s infinite linear;
}

.particle-effect::before {
  width: 20px;
  height: 20px;
  top: 10%;
  left: 15%;
  animation-delay: 0s;
}

.particle-effect::after {
  width: 15px;
  height: 15px;
  top: 70%;
  left: 70%;
  animation-delay: 5s;
}

@keyframes float {
  0% { transform: translateY(0) scale(1); }
  50% { transform: translateY(-50px) scale(1.2); }
  100% { transform: translateY(0) scale(1); }
}

.hero-content {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
  text-align: center;
  position: relative;
  z-index: 2;
  color: white;
}

.hero h2 {
  font-size: clamp(3.5rem, 8vw, 6.5rem);
  font-weight: 900;
  margin-bottom: 1.8rem;
  text-shadow: 0 6px 25px rgba(212, 175, 55, 0.7);
  line-height: 1.1;
  animation: fadeInUp 1s var(--animation-smooth);
  color: var(--upb-gold);
}

.hero p {
  font-size: clamp(1.3rem, 3vw, 1.7rem);
  margin-bottom: 3.5rem;
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
  line-height: 1.7;
  opacity: 0.95;
  color: white;
}

.cta-button {
  background: var(--gradient-secondary);
  color: var(--upb-dark);
  padding: 1.4rem 3.8rem;
  border: none;
  border-radius: 50px;
  font-size: 1.4rem;
  font-weight: 800;
  cursor: pointer;
  transition: all 0.4s var(--animation-smooth);
  box-shadow: var(--shadow-strong);
  display: inline-flex;
  align-items: center;
  gap: 1rem;
  text-decoration: none;
  position: relative;
  overflow: hidden;
}

.cta-button::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: all 0.6s var(--animation-smooth);
  z-index: 0;
}

.cta-button:hover::before {
  width: 300px;
  height: 300px;
}

.cta-button:hover {
  transform: translateY(-6px) scale(1.1);
  box-shadow: 0 30px 90px rgba(212, 175, 55, 0.8);
}

.cta-button i {
  font-size: 1.3rem;
}

/* Map Section */
.map-section {
  background: rgba(26, 26, 26, 0.9);
  border-radius: var(--border-radius);
  box-shadow: var(--shadow-soft);
  overflow: hidden;
  margin: 5rem auto;
  max-width: 1400px;
  border: 2px solid var(--upb-gold);
}

.map-header {
  background: var(--gradient-primary);
  color: white;
  padding: 3rem;
  text-align: center;
  border-bottom: 5px solid rgba(212, 175, 55, 0.2);
  position: relative;
  overflow: hidden;
}

.map-header::after {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(212, 175, 55, 0.2), transparent);
  animation: shine 5s infinite;
}

@keyframes shine {
  0% { left: -100%; }
  20% { left: 100%; }
  100% { left: 100%; }
}

.map-header h3 {
  font-size: 3rem;
  font-weight: 900;
  margin-bottom: 0.6rem;
  text-shadow: 0 3px 10px rgba(212, 175, 55, 0.5);
  color: var(--upb-gold);
}

.map-header p {
  opacity: 0.95;
  font-size: 1.3rem;
  color: white;
}

.map-container {
  position: relative;
  height: 70vh;
  min-height: 600px;
}

#google-map {
  width: 100%;
  height: 100%;
  border: none;
  transition: filter 0.3s var(--animation-smooth);
  filter: grayscale(20%) brightness(0.9);
}

.map-container:hover #google-map {
  filter: grayscale(0%) brightness(1.1);
}

.map-sidebar {
  position: absolute;
  top: 3rem;
  left: 3rem;
  width: 400px;
  background: rgba(26, 26, 26, 0.95);
  backdrop-filter: blur(25px);
  border-radius: var(--border-radius);
  box-shadow: var(--shadow-strong);
  overflow: hidden;
  z-index: 100;
  max-height: calc(100% - 6rem);
  border: 2px solid var(--upb-gold);
  transition: transform 0.4s var(--animation-smooth), box-shadow 0.4s var(--animation-smooth);
}

.map-sidebar:hover {
  transform: translateY(-6px);
  box-shadow: 0 25px 70px rgba(196, 30, 58, 0.6);
}

.sidebar-header {
  background: var(--gradient-secondary);
  color: var(--upb-dark);
  padding: 2rem;
  text-align: center;
  font-weight: 800;
  font-size: 1.4rem;
  border-bottom: 3px solid rgba(212, 175, 55, 0.3);
  text-transform: uppercase;
}

.places-list {
  max-height: 550px;
  overflow-y: auto;
  padding: 1.5rem 0;
  scrollbar-width: thin;
  scrollbar-color: var(--upb-gold) rgba(0, 0, 0, 0.5);
}

.places-list::-webkit-scrollbar {
  width: 8px;
}

.places-list::-webkit-scrollbar-thumb {
  background-color: var(--upb-gold);
  border-radius: 4px;
}

.place-category {
  margin-bottom: 1.5rem;
}

.category-header {
  background: var(--upb-red);
  color: white;
  padding: 1.5rem 2rem;
  font-weight: 700;
  margin-bottom: 0.6rem;
  cursor: pointer;
  transition: all 0.4s var(--animation-smooth);
  display: flex;
  align-items: center;
  gap: 1rem;
  border-radius: 8px;
}

.category-header:hover {
  background: var(--upb-dark-red);
  transform: translateX(8px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

.place-item {
  padding: 1.5rem 2rem;
  cursor: pointer;
  transition: all 0.4s var(--animation-smooth);
  border-left: 5px solid transparent;
  display: flex;
  align-items: center;
  gap: 1rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 8px;
  color: var(--upb-light-gold);
}

.place-item:hover {
  background: var(--gradient-primary);
  color: white;
  border-left-color: var(--upb-gold);
  transform: translateX(12px);
  box-shadow: 0 5px 15px rgba(196, 30, 58, 0.4);
}

.place-item i {
  font-size: 1.2rem;
}

/* Animations */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in {
  animation: fadeInUp 1s var(--animation-smooth);
}

/* Responsive */
@media (max-width: 1024px) {
  .map-sidebar {
    position: relative;
    width: 100%;
    margin-bottom: 2.5rem;
    top: 0;
    left: 0;
  }

  .map-container {
    height: 50vh;
    min-height: 400px;
  }
}

@media (max-width: 768px) {
  .header-content {
    padding: 0 1.5rem;
    flex-direction: column;
    gap: 1.5rem;
  }

  .logo-text h1 {
    font-size: 1.7rem;
  }

  .nav {
    flex-wrap: wrap;
    justify-content: center;
  }

  .hero {
    padding: 0 1.5rem;
  }

  .cta-button {
    padding: 1.2rem 3rem;
    font-size: 1.2rem;
  }
}
</style>