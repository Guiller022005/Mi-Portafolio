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

       <!-- Seccion Habilidades -->
      <section id="skills" class="skills">
        <h3>Skills</h3>
        <div class="skills-grid">
          <div v-for="(skill, index) in skills" :key="skill.name" 
              class="skill-item" 
              :class="{'half-width': index >= skills.length - 2}" 
              @mouseover="flipCard(skill)" 
              @mouseleave="flipCard(skill)">
            <div class="card" :class="{ flipped: skill.flipped }">
              <div class="card-front">
                <img :src="skill.image" alt="Imagen de {{ skill.name }}" class="skill-image">
                <p>{{ skill.name }}</p>
              </div>
              <div class="card-back">
                <p>{{ skill.info }}</p>
              </div>
            </div>
          </div>
        </div>
      </section>


      <section id="soft-skills" class="soft-skills">
        <h3>Soft Skills</h3>
        <div class="pyramid">
          <div class="level level-1">
            <div class="pyramid-item">Liderazgo</div>
          </div>
          <div class="level level-2">
            <div class="pyramid-item">Proactividad</div>
            <div class="pyramid-item">Resolución de Problemas</div>
          </div>
          <div class="level level-3">
            <div class="pyramid-item">Trabajo en equipo</div>
            <div class="pyramid-item">Comunicación efectiva</div>
            <div class="pyramid-item">Creatividad</div>
            <div class="pyramid-item">Adaptabilidad</div>
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
               <a :href="project.url" class="project-link" target="_blank" rel="noopener noreferrer">Ver Proyecto →</a>
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
          <a href="https://mail.google.com/mail/?view=cm&fs=1&to=pauldiazjoseguillermo@gmail.com&su=Contacto%20desde%20tu%20portafolio&body=Escribe%20tu%20mensaje%20aquí" target="_blank" rel="noopener noreferrer">
            <img src="./assets/email.svg" alt="Correo" width="40px" height="40px"/>
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
  { image: '../src/assets/node.svg?height=200&width=300', name: 'Node.js', info: 'Crea aplicaciones rápidas en servidores.', flipped: false },
  { image: '../src/assets/nodeExpress.svg?height=200&width=300', name: 'Express', info: 'Facilita la creación de sitios web y servicios.', flipped: false },
  { image: '../src/assets/vue.svg?height=200&width=300', name: 'Vue.js', info: 'Hace las páginas web más rápidas e interactivas.', flipped: false },
  { image: '../src/assets/react.svg?height=200&width=300', name: 'React.js', info: 'Hace las páginas web más rápidas e interactivas.', flipped: false },
  { image: '../src/assets/javascript.svg?height=200&width=300', name: 'JavaScript', info: 'Da vida a las páginas web con interacción.', flipped: false },
  { image: '../src/assets/c++.svg?height=200&width=300', name: 'C++', info: 'Crea programas rápidos como videojuegos.', flipped: false },
  { image: '../src/assets/mysql.svg?height=200&width=300', name: 'MySQL', info: 'Almacena y organiza información en bases de datos.', flipped: false },
  { image: '../src/assets/mongo.svg?height=200&width=300', name: 'MongoDB', info: 'Guarda grandes volúmenes de datos de manera flexible.', flipped: false },
  { image: '../src/assets/python.svg?height=200&width=300', name: 'Python', info: 'Lenguaje fácil para múltiples tareas, como análisis de datos.', flipped: false },
  { image: '../src/assets/api.svg?height=200&width=300', name: 'APIs RESTful', info: 'Permiten que aplicaciones se comuniquen entre sí.', flipped: false },
  { image: '../src/assets/responsive.svg?height=200&width=300', name: 'Sitios web responsive', info: 'Adaptan un sitio para verse bien en cualquier dispositivo.', flipped: false },
  { image: '../src/assets/docker.svg?height=200&width=300', name: 'Docker', info: 'Adaptan un sitio para verse bien en cualquier dispositivo.', flipped: false },
]);

const projects = ref([
  {
    title: 'Plataforma de E-commerce',
    description: 'Una solución full-stack de comercio electrónico con gestión de inventario en tiempo real.',
    image: '../src/assets/ecomerce.png?height=200&width=300',
    url: 'https://guiller022005.github.io/ecommerCampusM1/?id=aps',
  },
  {
    title: 'SpaceX',
    description: 'Una aplicación web responsiva para la organización eficiente de tareas y colaboración en equipo.',
    image: '../src/assets/spaceX.png?height=200&width=300',
    url: 'https://guiller022005.github.io/SpaceX/',
  },
  {
    title: 'Plataforma de Cine',
    description: 'Una aplicación web para visualizar el catálogo de películas en cartelera y gestionar reservas.',
    image: '../src/assets/foodSite.png?height=200&width=300',
    url: 'https://guiller022005.github.io/proyectoWeb/',
  }
]);

const socials = ref([
  { name: 'GitHub', icon: GithubIcon, url: 'https://github.com/Guiller022005' },
  { name: 'LinkedIn', icon: LinkedinIcon, url: 'https://linkedin.com/in/josé-guillermo-paúl-díaz' },
  { name: 'Instagram', icon: InstagramIcon, url: 'https://instagram.com/pauldiazjoseguillermo' },
]);

const flipCard = (skill) => {
  skill.flipped = !skill.flipped;
};
</script>

