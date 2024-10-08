<template>
  <div class="portfolio">
    <header>
      <nav>
        <h1>José Guillermo Paúl Díaz</h1>
        <ul>
          <li v-for="item in navItems" :key="item">
            <!-- Asigna dinámicamente el href según el nombre del item -->
            <a :href="item === 'Sobre mí' ? '#profile' : item === 'Habilidades' ? '#skills' : item === 'Proyectos' ? '#projects' : item === 'Contacto' ? '#contact' : '#'">
              {{ item }}
            </a>
          </li>
        </ul>
      </nav>
    </header>

    <main>
      <!-- Sección Sobre mí -->
      <section id="profile" class="profile">
        <div class="profile-image">
          <img src="/foto.png?height=400&width=400" alt="Tu Foto">
        </div>
        <div class="profile-content">
          <h2>Desarrollador Full-Stack</h2>
          <p>Profesional orientado al logro, con una gran motivación por implementar nuevas tecnologías en los avances de la innovación. Mi objetivo es aplicar y expandir mis conocimientos en un entorno profesional y personal, contribuyendo de manera significativa al éxito de los proyectos en los que participe. Estoy dispuesto a enfrentar nuevos desafíos y superar las expectativas.</p>
          <a href="#contact" class="cta-button">Contáctame</a>
        </div>
      </section>

      <!-- Sección Habilidades -->
      <section id="skills" class="skills">
        <h3>Habilidades y Tecnologías</h3>
        <div class="skills-grid">
          <div v-for="skill in skills" :key="skill" class="skill-item">
            {{ skill }}
          </div>
        </div>
      </section>

      <!-- Sección Proyectos -->
      <section id="projects" class="projects">
        <h3>Proyectos Destacados</h3>
        <div class="projects-grid">
          <div v-for="project in projects" :key="project.title" class="project-item">
            <img :src="project.image" :alt="project.title">
            <div class="project-content">
              <h4>{{ project.title }}</h4>
              <p>{{ project.description }}</p>
              <a href="#" class="project-link">Ver Proyecto →</a>
            </div>
          </div>
        </div>
      </section>

      <!-- Sección Contacto -->
      <section id="contact" class="contact">
        <h3>Contacto</h3>
        <div class="social-icons">
          <a v-for="social in socials" :key="social.name" :href="social.url" target="_blank" rel="noopener noreferrer">
            <component :is="social.icon" width="40px" height="40px"/>
          </a>
        </div>
        <p>pauldiazjoseguillermo@gmail.com | +57 317 800 1452</p>
      </section>
    </main>

    <footer>
      <p>&copy; 2024 José Guillermo Paúl Díaz. Todos los derechos reservados.</p>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { GithubIcon, LinkedinIcon, InstagramIcon } from 'lucide-vue-next';

const navItems = ref(['Sobre mí', 'Habilidades', 'Proyectos', 'Contacto']);

const skills = ref([
  'JavaScript', 'Vue.js', 'React', 'Node.js',
  'Python', 'Django', 'PostgreSQL', 'MongoDB',
  'Docker', 'AWS', 'Git', 'APIs RESTful'
]);

const projects = ref([
  {
    title: 'Plataforma de E-commerce',
    description: 'Una solución full-stack de comercio electrónico con gestión de inventario en tiempo real.',
    image: '/foto.png?height=200&width=300'
  },
  {
    title: 'App de Gestión de Tareas',
    description: 'Una aplicación web responsiva para la organización eficiente de tareas y colaboración en equipo.',
    image: '/foto.png?height=200&width=300'
  },
  {
    title: 'Plataforma de Cine',
    description: 'Una aplicación web para visualizar el catálogo de películas en cartelera y gestionar reservas.',
    image: '/foto.png?height=200&width=300'
  }
]);

const socials = ref([
  { name: 'GitHub', icon: GithubIcon, url: 'https://github.com/Guiller022005' },
  { name: 'LinkedIn', icon: LinkedinIcon, url: 'https://linkedin.com/in/josé-guillermo-paúl-díaz' },
  { name: 'Instagram', icon: InstagramIcon, url: 'https://instagram.com/pauldiazjoseguillermo' }
]);
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.portfolio {
  width: 100%;
  height: 100%;
  background: linear-gradient(to bottom right, #0c1445, #1a237e, #0c1445);
  color: #f7fafc;
  font-family: Arial, sans-serif;
  display: flex;
  flex-direction: column;
}

header {
  padding: 2rem 1rem;
}

nav {
  display: flex;
  width: 100vw; 
  justify-content: center;
  gap: 20vw;
}

nav h1 {
  font-size: 1.5rem;
  font-weight: bold;
}

nav ul {
  display: flex;
  gap: 4rem;
  margin-left: 40px;
}

nav a {
  color: #f7fafc;
  text-decoration: none;
  transition: color 0.3s;
}

nav a:hover {
  color: #63b3ed;
}

main {
  flex-grow: 1; /* Hace que el main ocupe todo el espacio disponible */
  max-width: 1200px;
  margin: 0 auto;
  padding: 3rem 1rem;
}

.profile {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 4rem;
}

.profile-image img {
  width: 16rem;
  height: 16rem;
  object-fit: contain;
  border-radius: 0.5rem;
  border: 4px solid #2b6cb0;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  background-color: #2f3339;
}

.profile-content {
  text-align: center;
  margin-top: 2rem;
}

.profile-content h2 {
  font-size: 2.25rem;
  font-weight: bold;
  margin-bottom: 1rem;
}

.profile-content p {
  font-size: 1.25rem;
  margin-bottom: 1.5rem;
}

.cta-button {
  background-color: #2b6cb0;
  color: white;
  font-weight: bold;
  padding: 0.5rem 1rem;
  border-radius: 0.25rem;
  text-decoration: none;
  transition: background-color 0.3s;
}

.cta-button:hover {
  background-color: #2c5282;
}

.skills, .projects, .contact {
  margin-bottom: 4rem;
}

h3 {
  font-size: 1.5rem;
  font-weight: bold;
  text-align: center;
  margin-bottom: 1.5rem;
}

.skills-grid, .projects-grid {
  display: grid;
  gap: 1rem;
}

.skills-grid {
  display: grid;
  gap: 1.5rem;
  grid-template-columns: repeat(4, 1fr); /* 4 columnas */
}

.skill-item {
  background-color: #2d3748;
  padding: 3rem;
  border-radius: 0.5rem;
  text-align: center;
  transition: all 0.3s;
}

.skill-item:hover {
  background-color: #4a5568;
  transform: scale(1.05);
}

.projects-grid {
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
}

.project-item {
  background-color: #2d3748;
  border-radius: 0.5rem;
  overflow: hidden;
  transition: all 0.3s;
}

.project-item:hover {
  background-color: #4a5568;
  transform: scale(1.05);
}

.project-item img {
  width: 100%;
  height: 12rem;
  object-fit: cover;
}

.project-content {
  padding: 1rem;
}

.project-content h4 {
  font-size: 1.25rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.project-link {
  color: #64b5f6;
  text-decoration: none;
}

.project-link:hover {
  color: #4299e1;
}

.contact {
  text-align: center;
}

.social-icons {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.social-icons a {
  color: #a0aec0;
  transition: color 0.3s;
}

.social-icons a:hover {
  color: #63b3ed;
}

footer {
  margin-top: auto; /* Asegura que el footer se mantenga al final */
  background-color: #2d3748;
  padding: 1rem;
  text-align: center;
}

@media (min-width: 768px) {
  .profile {
    flex-direction: row;
    text-align: left;
  }

  .profile-image {
    width: 50%;
    margin-right: 2rem;
  }

  .profile-content {
    width: 50%;
    text-align: left;
  }
}
</style>