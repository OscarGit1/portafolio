<script setup>
import { onMounted } from 'vue';

const withBase = (path) => {
  if (!path || path.startsWith('http') || path.startsWith('#')) return path;
  const base = useRuntimeConfig().app.baseURL || '/';
  const cleanBase = base.endsWith('/') ? base : `${base}/`;
  const cleanPath = path.startsWith('/') ? path.slice(1) : path;
  return `${cleanBase}${cleanPath}`;
};

const profile = {
  name: 'Oscar Jiménez Reyes',
  role: 'Full Stack Developer',
  phone: '+52 722 411 5899',
  email: 'ojr.gmr.1711@gmail.com',
  summary: 'Full Stack Developer con experiencia profesional desde 2022 desarrollando aplicaciones y plataformas web con Laravel, Vue.js y Nuxt.js. Experiencia trabajando en proyectos de principio a fin, incluyendo definición e implementación de interfaces, lógica de negocio, autenticación, APIs y configuración de entornos de producción. Enfoque en la construcción de aplicaciones mantenibles, responsive y orientadas a las necesidades del proyecto.'
};

const experience = [
  {
    title: 'Freelance — Full Stack Developer',
    date: 'Febrero 2024 – Actualidad',
    description: 'Desarrollo de aplicaciones, plataformas y sitios web para diferentes proyectos, cubriendo frontend, backend, integración de servicios y despliegue.',
    bullets: [
      'Desarrollo de aplicaciones web Full Stack utilizando Laravel, Vue.js y Nuxt.js.',
      'Diseño e implementación de APIs REST para comunicación entre aplicaciones.',
      'Desarrollo de interfaces responsive mediante Vue.js y Vuetify.',
      'Implementación de autenticación y autorización mediante Laravel Sanctum.',
      'Diseño de modelos y bases de datos con MySQL, MariaDB y Prisma ORM.',
      'Integración de servicios externos (REST, GraphQL, Shopify Storefront API).',
      'Configuración de entornos reproducibles y despliegues automáticos (GitHub Actions).'
    ]
  },
  {
    title: 'Coordinador de Desarrollo — Área de TI',
    date: 'Julio 2022 – Enero 2024',
    description: 'Desarrollo y mantenimiento de soluciones web para congresos, eventos y proyectos digitales, además de coordinación de actividades de desarrollo dentro del área de TI.',
    bullets: [
      'Desarrollo y mantenimiento de micrositios web para congresos y eventos.',
      'Implementación y personalización de sitios mediante WordPress.',
      'Desarrollo de interfaces y funcionalidades web de acuerdo con requerimientos específicos.',
      'Resolución de incidencias y mantenimiento de aplicaciones en producción.',
      'Coordinación y seguimiento de actividades relacionadas con desarrollo web y colaboración con diversas áreas.'
    ]
  }
];

const skillCategories = [
  {
    name: 'Frontend',
    skills: ['Vue.js 3', 'Nuxt.js 3', 'JavaScript', 'HTML5', 'CSS3', 'Vuetify', 'Pinia', 'Vue Router', 'GSAP']
  },
  {
    name: 'Backend',
    skills: ['Laravel', 'PHP', 'Node.js', 'REST APIs', 'Laravel Sanctum']
  },
  {
    name: 'Bases de datos',
    skills: ['MySQL', 'MariaDB', 'Prisma ORM']
  },
  {
    name: 'APIs e integraciones',
    skills: ['REST', 'GraphQL', 'Shopify Storefront API']
  },
  {
    name: 'DevOps / Herramientas',
    skills: ['Git', 'GitHub', 'GitHub Actions', 'cPanel']
  },
  {
    name: 'Web & Rendimiento',
    skills: ['Responsive Design', 'SSR', 'SEO técnico', 'Optimización de imágenes', 'Autenticación', 'Gestión de archivos']
  }
];

const projects = [
  // Builds Estáticas (Archivados en el mismo dominio)
  {
    name: 'AMCPER',
    type: 'static',
    url: '/AMCPER/',
    desc: 'Micrositio web para promocionar y dar información detallada sobre los eventos y congresos organizados por AMCPER.',
    image: '/AMCPER/AMCPER.png',
    tags: ['Vue', 'Laravel', 'Archivado']
  },
  {
    name: 'AMCPER CDMX',
    type: 'static',
    url: '/AMCPERCDMX/',
    desc: 'Micrositio para promocionar y difundir la información oficial del evento AMCPER en Ciudad de México.',
    image: '/AMCPERCDMX/AMCPERCDMX.png',
    tags: ['Vue', 'Laravel', 'Archivado']
  },
  {
    name: 'Electrivolt',
    type: 'static',
    url: '/Electrivolt/',
    desc: 'Sitio web corporativo para empresa de ingeniería eléctrica, automatización, energías renovables y proyectos de media y baja tensión.',
    image: '/Electrivolt/Electrivolt.png',
    tags: ['Vue', 'Archivado']
  },
  {
    name: 'Foro Iberoamericano',
    type: 'static',
    url: '/ForoIberoamericanoAMCPER/',
    desc: 'Micrositio promocional e informativo para el Foro Iberoamericano organizado por AMCPER.',
    image: '/ForoIberoamericanoAMCPER/Foro.png',
    tags: ['Vue', 'Laravel', 'Archivado']
  },

  // Proyectos con enlaces (Activos)
  {
    name: 'AMCPER GDL',
    type: 'link',
    url: 'https://www.congresoamcper.mx/',
    desc: 'Micrositio oficial para promocionar y brindar información del Congreso AMCPER Guadalajara.',
    image: '/AMCPERGDL/Banner.png',
    tags: ['Activo', 'Nuxt']
  },
  {
    name: 'Carnes M',
    type: 'link',
    url: 'https://carnesm.com.mx/',
    desc: 'E-commerce headless desarrollado con Nuxt e integrado con Shopify Storefront API.',
    image: '/CarnesM/CarnesM.png',
    tags: ['Activo', 'Nuxt', 'Shopify']
  },
  {
    name: 'Constancias',
    type: 'link',
    url: 'https://constancias.olaestudiocreativo.com/events/fonar-2025',
    desc: 'Sistema de generación de constancias.',
    image: '/Constancias/Constancias.png',
    tags: ['Activo', 'Vue']
  },
  {
    name: 'Dra. Emma',
    type: 'link',
    url: 'https://draemma.com/',
    desc: 'Sitio web profesional enfocado en presencia digital y posicionamiento SEO en Google para sus servicios médicos y consultas.',
    image: '/DraEmma/DraEmma.png',
    tags: ['Activo', 'Nuxt', 'SEO']
  },
  {
    name: 'Frame by Frame',
    type: 'link',
    url: 'https://estudiofbyf.com/',
    desc: 'Sitio web y portafolio profesional para estudio especializado en servicios de fotografía para eventos.',
    image: '/EstudioFramebyFrame/EstudioFramebyFrame.png',
    tags: ['Activo', 'Vue']
  },
  {
    name: 'Flores La Herradura',
    type: 'link',
    url: '#',
    desc: 'Sitio web para presencia digital y exhibición del catálogo de flores. Por definir dominio.',
    image: '/FloresLaHerradura/Flores.png',
    tags: ['Nuxt', 'Por definir dominio']
  },
  {
    name: 'Innovaciones AMCPER',
    type: 'link',
    url: 'https://innovacionesamcper.mx/',
    desc: 'Plataforma digital de innovaciones para la comunidad médica AMCPER.',
    image: '/InnovacionesAMCPER/Innovaciones.png',
    tags: ['Activo', 'Vue', 'Laravel']
  }
];
</script>

<template>
  <main class="portfolio-container">
    <!-- Navbar -->
    <nav class="navbar">
      <div class="nav-content container">
        <div class="logo">OJ.</div>
        <div class="nav-links">
          <a href="#experiencia">Experiencia</a>
          <a href="#proyectos">Proyectos</a>
          <a href="#habilidades">Habilidades</a>
          <a href="#contacto" class="nav-contact">Contacto</a>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero container animate-in">
      <div class="hero-content">
        <span class="greeting">Hola, soy</span>
        <h1 class="name">{{ profile.name }}</h1>
        <h2 class="role">{{ profile.role }}</h2>
        <p class="summary">{{ profile.summary }}</p>

        <div class="hero-actions">
          <a href="#proyectos" class="btn btn-primary">Ver Proyectos</a>
          <a href="#contacto" class="btn btn-secondary">Contactar</a>
        </div>
      </div>
    </section>

    <!-- Experience Section -->
    <section id="experiencia" class="experience section container animate-in" style="animation-delay: 0.1s;">
      <div class="section-header">
        <h2>Experiencia Profesional</h2>
        <div class="divider"></div>
      </div>

      <div class="timeline">
        <div v-for="(job, index) in experience" :key="index" class="timeline-item">
          <div class="timeline-dot"></div>
          <div class="timeline-content">
            <div class="timeline-header">
              <h3>{{ job.title }}</h3>
              <span class="timeline-date">{{ job.date }}</span>
            </div>
            <p class="timeline-desc">{{ job.description }}</p>
            <ul class="timeline-bullets">
              <li v-for="(bullet, bIndex) in job.bullets" :key="bIndex">{{ bullet }}</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="proyectos" class="projects section container animate-in" style="animation-delay: 0.2s;">
      <div class="section-header">
        <h2>Proyectos Destacados</h2>
        <div class="divider"></div>
      </div>

      <div class="projects-grid">
        <article v-for="(project, index) in projects" :key="index" class="project-card">
          <div class="project-image-wrapper">
            <img v-if="project.image" :src="withBase(project.image)" :alt="project.name" class="project-img" loading="lazy" />
            <div v-else class="project-placeholder">{{ project.name }}</div>
          </div>
          <div class="project-content">
            <h3>{{ project.name }}</h3>
            <p>{{ project.desc }}</p>
            <div class="project-tags">
              <span v-for="tag in project.tags" :key="tag" class="badge" :class="{ 'badge-active': tag === 'Activo' }">
                <span v-if="tag === 'Activo'" class="active-dot"></span>
                {{ tag }}
              </span>
            </div>
          </div>
          <div class="project-footer">
            <a v-if="project.url && project.url !== '#'" :href="withBase(project.url)" target="_blank" class="btn-link">
              Ver Proyecto
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none"
                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
                <polyline points="15 3 21 3 21 9"></polyline>
                <line x1="10" y1="14" x2="21" y2="3"></line>
              </svg>
            </a>
            <span v-else class="btn-link btn-disabled">
              Por definir dominio
            </span>
          </div>
        </article>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="habilidades" class="skills section container animate-in" style="animation-delay: 0.3s;">
      <div class="section-header">
        <h2>Habilidades Técnicas</h2>
        <div class="divider"></div>
      </div>

      <div class="skills-grid">
        <div v-for="(category, index) in skillCategories" :key="index" class="skill-category">
          <h3 class="category-title">{{ category.name }}</h3>
          <div class="skill-tags">
            <span v-for="skill in category.skills" :key="skill" class="skill-tag">{{ skill }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contacto" class="contact section container animate-in" style="animation-delay: 0.4s;">
      <div class="contact-card">
        <h2>Ponte en contacto</h2>
        <p>Actualmente estoy disponible para nuevos retos y oportunidades de colaboración. Escríbeme o llámame
          directamente.</p>

        <div class="contact-info">
          <div class="info-item">
            <span class="info-label">Email:</span>
            <a :href="'mailto:' + profile.email" class="info-value info-link">{{ profile.email }}</a>
          </div>
          <div class="info-item">
            <span class="info-label">Teléfono:</span>
            <a :href="'tel:' + profile.phone.replace(/[^0-9+]/g, '')" class="info-value info-link">{{ profile.phone
              }}</a>
          </div>
        </div>
      </div>
    </section>

    <footer class="footer">
      <div class="container">
        <p>© {{ new Date().getFullYear() }} {{ profile.name }}.</p>
      </div>
    </footer>
  </main>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

:root {
  --bg-primary: #0f1115;
  --bg-secondary: #16181d;
  --bg-card: #1c1e26;
  --text-primary: #f8fafc;
  --text-secondary: #94a3b8;
  --accent-color: #b05cff;
  --accent-hover: #9d4edd;
  --border-color: rgba(255, 255, 255, 0.08);
}

.portfolio-container {
  background-color: var(--bg-primary);
  background-image:
    radial-gradient(circle at 50% 0%, rgba(176, 92, 255, 0.15) 0%, transparent 60%),
    linear-gradient(rgba(255, 255, 255, 0.02) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.02) 1px, transparent 1px);
  background-size: 100% 100%, 40px 40px, 40px 40px;
  background-position: top center, center center, center center;
  background-attachment: fixed;
  min-height: 100vh;
  color: var(--text-primary);
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
  line-height: 1.6;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 24px;
}

/* Navbar */
.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  background: rgba(15, 17, 21, 0.85);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  z-index: 100;
  border-bottom: 1px solid var(--border-color);
}

.nav-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 70px;
}

.logo {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -1px;
}

.nav-links {
  display: flex;
  gap: 32px;
  align-items: center;
}

.nav-links a {
  color: var(--text-secondary);
  text-decoration: none;
  font-size: 0.95rem;
  font-weight: 500;
  transition: color 0.2s ease;
}

.nav-links a:hover {
  color: var(--text-primary);
}

.nav-contact {
  background: var(--bg-secondary);
  padding: 8px 16px;
  border-radius: 6px;
  border: 1px solid var(--border-color);
}

/* Section Common */
.section {
  padding: 100px 0 40px;
}

.section-header {
  margin-bottom: 50px;
}

.section-header h2 {
  font-size: 2.5rem;
  margin: 0 0 16px 0;
  font-weight: 700;
  letter-spacing: -0.5px;
}

.divider {
  height: 4px;
  width: 60px;
  background: var(--accent-color);
  border-radius: 2px;
}

/* Hero Section */
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding-top: 80px;
}

.hero-content {
  max-width: 750px;
}

.greeting {
  display: block;
  font-size: 1.1rem;
  color: var(--accent-color);
  font-weight: 600;
  margin-bottom: 16px;
  text-transform: uppercase;
  letter-spacing: 2px;
}

.name {
  font-size: 4.5rem;
  font-weight: 700;
  margin: 0 0 8px 0;
  line-height: 1.1;
  letter-spacing: -2px;
  color: var(--text-primary);
}

.role {
  font-size: 2.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0 0 24px 0;
  line-height: 1.2;
}

.summary {
  font-size: 1.15rem;
  color: var(--text-secondary);
  margin-bottom: 40px;
  line-height: 1.8;
}

.hero-actions {
  display: flex;
  gap: 16px;
}

/* Buttons */
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 14px 28px;
  border-radius: 8px;
  font-weight: 600;
  font-size: 1rem;
  text-decoration: none;
  transition: all 0.2s ease;
  cursor: pointer;
}

.btn-primary {
  background-color: var(--accent-color);
  color: #fff;
  border: 1px solid transparent;
}

.btn-primary:hover {
  background-color: var(--accent-hover);
  transform: translateY(-2px);
}

.btn-secondary {
  background-color: transparent;
  color: var(--text-primary);
  border: 1px solid var(--border-color);
}

.btn-secondary:hover {
  background-color: rgba(255, 255, 255, 0.05);
  transform: translateY(-2px);
}

.btn-link {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 100%;
  padding: 12px;
  background: var(--accent-color);
  color: #fff;
  border: 1px solid var(--accent-color);
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  font-size: 0.95rem;
  transition: all 0.3s ease;
  box-shadow: 0 4px 12px rgba(176, 92, 255, 0.15);
}

.btn-link:hover {
  background: var(--accent-hover);
  border-color: var(--accent-hover);
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(176, 92, 255, 0.35);
}

.btn-disabled {
  background: rgba(255, 255, 255, 0.05);
  border-color: var(--border-color);
  color: var(--text-secondary);
  cursor: default;
  box-shadow: none;
}

.btn-disabled:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: var(--border-color);
  transform: none;
  box-shadow: none;
}

/* Timeline / Experience */
.timeline {
  position: relative;
  padding-left: 30px;
}

.timeline::before {
  content: '';
  position: absolute;
  top: 0;
  bottom: 0;
  left: 5px;
  width: 2px;
  background: var(--border-color);
}

.timeline-item {
  position: relative;
  margin-bottom: 40px;
}

.timeline-item:last-child {
  margin-bottom: 0;
}

.timeline-dot {
  position: absolute;
  left: -30px;
  top: 6px;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: var(--accent-color);
  border: 2px solid var(--bg-primary);
  box-shadow: 0 0 0 4px rgba(176, 92, 255, 0.1);
}

.timeline-header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  margin-bottom: 12px;
  flex-wrap: wrap;
  gap: 8px;
}

.timeline-header h3 {
  margin: 0;
  font-size: 1.4rem;
  color: var(--text-primary);
}

.timeline-date {
  font-size: 0.85rem;
  color: var(--text-primary);
  font-weight: 600;
  padding: 4px 12px;
  background: var(--bg-secondary);
  border: 1px solid var(--border-color);
  border-radius: 20px;
}

.timeline-desc {
  color: var(--text-secondary);
  font-size: 1.05rem;
  margin-bottom: 16px;
}

.timeline-bullets {
  padding-left: 20px;
  color: var(--text-secondary);
  margin: 0;
}

.timeline-bullets li {
  margin-bottom: 8px;
}

/* Projects Grid */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 30px;
}

.project-card {
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  transition: transform 0.3s ease, border-color 0.3s ease;
}

.project-card:hover {
  transform: translateY(-5px);
  border-color: rgba(255, 255, 255, 0.15);
}

.project-image-wrapper {
  height: 200px;
  background: #111;
  position: relative;
  overflow: hidden;
  border-bottom: 1px solid var(--border-color);
}

.project-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: top;
  transition: transform 0.5s ease;
}

.project-card:hover .project-img {
  transform: scale(1.05);
}

.project-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #555;
  font-weight: 600;
  font-size: 1.2rem;
}

.project-content {
  padding: 24px;
  flex: 1;
  display: flex;
  flex-direction: column;
}

.project-content h3 {
  margin: 0 0 12px 0;
  font-size: 1.3rem;
}

.project-content p {
  color: var(--text-secondary);
  margin: 0 0 20px 0;
  font-size: 0.95rem;
  flex: 1;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.badge {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.15);
  padding: 4px 10px;
  border-radius: 4px;
  font-size: 0.75rem;
  font-weight: 600;
  color: var(--text-primary);
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.badge-active {
  background: rgba(16, 185, 129, 0.15);
  border-color: rgba(16, 185, 129, 0.4);
  color: #34d399;
  font-weight: 700;
  display: inline-flex;
  align-items: center;
  gap: 6px;
}

.active-dot {
  width: 6px;
  height: 6px;
  background-color: #34d399;
  border-radius: 50%;
  box-shadow: 0 0 6px #34d399;
  display: inline-block;
  animation: pulseDot 2s infinite;
}

@keyframes pulseDot {
  0% {
    transform: scale(0.95);
    box-shadow: 0 0 0 0 rgba(52, 211, 153, 0.7);
  }
  70% {
    transform: scale(1);
    box-shadow: 0 0 0 5px rgba(52, 211, 153, 0);
  }
  100% {
    transform: scale(0.95);
    box-shadow: 0 0 0 0 rgba(52, 211, 153, 0);
  }
}

.project-footer {
  padding: 16px 24px;
  border-top: 1px solid var(--border-color);
  background: rgba(0, 0, 0, 0.1);
}

/* Skills Grid */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 32px;
}

.skill-category {
  background: var(--bg-card);
  padding: 32px;
  border-radius: 12px;
  border: 1px solid var(--border-color);
}

.category-title {
  margin: 0 0 24px 0;
  font-size: 1.2rem;
  color: var(--text-primary);
  display: flex;
  align-items: center;
  gap: 12px;
}

.category-title::after {
  content: '';
  flex: 1;
  height: 1px;
  background: var(--border-color);
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
}

.skill-tag {
  background: rgba(255, 255, 255, 0.05);
  padding: 8px 16px;
  border-radius: 6px;
  font-size: 0.9rem;
  color: var(--text-primary);
  border: 1px solid rgba(255, 255, 255, 0.15);
  transition: all 0.2s ease;
}

.skill-tag:hover {
  background: var(--accent-color);
  color: #fff;
  border-color: var(--accent-color);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(176, 92, 255, 0.25);
}

/* Contact */
.contact-card {
  background: var(--bg-card);
  padding: 60px;
  border-radius: 16px;
  border: 1px solid var(--border-color);
  text-align: center;
}

.contact-card h2 {
  font-size: 2.5rem;
  margin: 0 0 16px 0;
}

.contact-card p {
  color: var(--text-secondary);
  font-size: 1.1rem;
  margin: 0 0 40px 0;
  max-width: 500px;
  margin-left: auto;
  margin-right: auto;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 16px;
  max-width: 400px;
  margin: 0 auto;
  text-align: left;
}

.info-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px;
  background: var(--bg-secondary);
  border-radius: 8px;
  border: 1px solid var(--border-color);
}

.info-label {
  color: var(--text-secondary);
  font-weight: 500;
}

.info-value {
  color: var(--text-primary);
  font-weight: 600;
}

.info-link {
  text-decoration: none;
  transition: color 0.2s ease;
}

.info-link:hover {
  color: var(--accent-color);
}

/* Footer */
.footer {
  padding: 40px 0;
  text-align: center;
  border-top: 1px solid var(--border-color);
  color: var(--text-secondary);
  font-size: 0.9rem;
}

/* Animations */
.animate-in {
  animation: fadeUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards;
  opacity: 0;
  transform: translateY(20px);
}

@keyframes fadeUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Responsive */
@media (max-width: 768px) {
  .name {
    font-size: 3rem;
  }

  .role {
    font-size: 1.6rem;
  }

  .section {
    padding: 60px 0 20px;
  }

  .hero {
    padding-top: 100px;
  }

  .nav-links {
    display: none;
  }

  .contact-card {
    padding: 40px 20px;
  }

  .info-item {
    flex-direction: column;
    align-items: flex-start;
    gap: 4px;
  }
}
</style>
