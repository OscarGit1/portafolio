<script setup>
useHead({
  title: 'Portafolio de Proyectos',
  meta: [
    { name: 'description', content: 'Galería y catálogo de proyectos web y plataformas digitales.' }
  ]
});

const withBase = (path) => {
  if (!path || path.startsWith('http') || path.startsWith('#')) return path;
  const base = useRuntimeConfig().app.baseURL || '/';
  const cleanBase = base.endsWith('/') ? base : `${base}/`;
  const cleanPath = path.startsWith('/') ? path.slice(1) : path;
  return `${cleanBase}${cleanPath}`;
};

const projects = [
  {
    name: 'Carnes M',
    url: 'https://carnesm.com.mx/',
    image: '/CarnesM/CarnesM.png',
    tags: ['E-commerce', 'Tienda en Línea']
  },
  {
    name: 'Flores La Herradura',
    url: 'https://floreslaherradura.com/',
    image: '/FloresLaHerradura/Flores.png',
    tags: ['Sitio Web', 'Catálogo Digital']
  },
  {
    name: 'Dra. Emma',
    url: 'https://draemma.com/',
    image: '/DraEmma/DraEmma.png',
    tags: ['Sitio Web', 'Servicios Médicos']
  },
  {
    name: 'Electrivolt',
    url: '/Electrivolt/',
    image: '/Electrivolt/Electrivolt.png',
    tags: ['Sitio Web', 'Corporativo']
  },
  {
    name: 'Constancias',
    url: 'https://constancias.olaestudiocreativo.com/events/fonar-2025',
    image: '/Constancias/Constancias.png',
    tags: ['Plataforma Web', 'Sistema']
  },
  {
    name: 'AMCPER GDL',
    url: 'https://www.congresoamcper.mx/',
    image: '/AMCPERGDL/Banner.png',
    tags: ['Sitio Web', 'Eventos']
  },
  {
    name: 'Innovaciones AMCPER',
    url: 'https://innovacionesamcper.mx/',
    image: '/InnovacionesAMCPER/Innovaciones.png',
    tags: ['Plataforma Web', 'Portal Digital']
  },
  {
    name: 'Frame by Frame',
    url: 'https://estudiofbyf.com/',
    image: '/EstudioFramebyFrame/EstudioFramebyFrame.png',
    tags: ['Sitio Web', 'Portafolio']
  },
  {
    name: 'AMCPER',
    url: '/AMCPER/',
    image: '/AMCPER/AMCPER.png',
    tags: ['Sitio Web', 'Eventos']
  },
  {
    name: 'AMCPER CDMX',
    url: '/AMCPERCDMX/',
    image: '/AMCPERCDMX/AMCPERCDMX.png',
    tags: ['Sitio Web', 'Congresos']
  },
  {
    name: 'Foro Iberoamericano',
    url: '/ForoIberoamericanoAMCPER/',
    image: '/ForoIberoamericanoAMCPER/Foro.png',
    tags: ['Sitio Web', 'Congresos']
  }
];
</script>

<template>
  <main class="portfolio-container">
    <div class="container animate-in">
      <header class="page-header">
        <h1 class="page-title">Proyectos</h1>
        <p class="page-subtitle">Galería de sitios web y aplicaciones desarrolladas</p>
      </header>

      <!-- Grid exclusivo de proyectos -->
      <div class="projects-grid">
        <article v-for="(project, index) in projects" :key="index" class="project-card">
          <div class="project-image-wrapper">
            <img v-if="project.image" :src="withBase(project.image)" :alt="project.name" class="project-img" loading="lazy" />
            <div v-else class="project-placeholder">{{ project.name }}</div>
          </div>
          <div class="project-content">
            <h3>{{ project.name }}</h3>
            <div class="project-tags">
              <span v-for="tag in project.tags" :key="tag" class="badge">
                {{ tag }}
              </span>
            </div>
          </div>
          <div class="project-footer">
            <a v-if="project.url && project.url !== '#'" :href="withBase(project.url)" target="_blank" class="btn-link">
              Ver
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
    </div>
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
  padding: 40px 0 64px;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
}

/* Header */
.page-header {
  margin-bottom: 40px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.page-title {
  margin: 0;
  font-size: 2.2rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.5px;
}

.page-subtitle {
  margin: 0;
  font-size: 1.05rem;
  color: var(--text-secondary);
}

/* Projects Grid */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 28px;
}

.project-card {
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  transition: transform 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
}

.project-card:hover {
  transform: translateY(-5px);
  border-color: rgba(176, 92, 255, 0.4);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.35);
}

.project-image-wrapper {
  height: 210px;
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
  padding: 20px 22px 16px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.project-content h3 {
  margin: 0;
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.3px;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.badge {
  background: rgba(176, 92, 255, 0.12);
  border: 1px solid rgba(176, 92, 255, 0.28);
  padding: 4px 10px;
  border-radius: 6px;
  font-size: 0.78rem;
  font-weight: 600;
  color: #d8b4fe;
  letter-spacing: 0.3px;
}

.project-footer {
  padding: 14px 22px 18px;
  background: rgba(0, 0, 0, 0.1);
  margin-top: auto;
}

.btn-link {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 100%;
  padding: 11px;
  background: var(--accent-color);
  color: #fff;
  border: 1px solid var(--accent-color);
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  font-size: 0.95rem;
  transition: all 0.25s ease;
  box-shadow: 0 4px 12px rgba(176, 92, 255, 0.2);
}

.btn-link:hover {
  background: var(--accent-hover);
  border-color: var(--accent-hover);
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(176, 92, 255, 0.4);
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

/* Animations */
.animate-in {
  animation: fadeUp 0.6s cubic-bezier(0.16, 1, 0.3, 1) forwards;
  opacity: 0;
  transform: translateY(16px);
}

@keyframes fadeUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .portfolio-container {
    padding: 24px 0 48px;
  }

  .projects-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }
}
</style>
