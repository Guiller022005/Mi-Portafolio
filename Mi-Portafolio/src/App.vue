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
        <h3>Skills</h3>
        <div class="skills-grid">
          <div v-for="(skill, index) in skills" :key="skill.name" 
            class="skill-item" 
            :class="{'half-width': index >= skills.length - 2}" 
            @mouseover="flipCard(skill)" 
            @mouseleave="flipCard(skill)">
          <div class="card" :class="{ flipped: skill.flipped }">
            <div class="card-front">{{ skill.name }}</div>
            <div class="card-back"><p>{{ skill.info }}</p></div>
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
            <div class="pyramid-item">Empatía</div>
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
  { name: 'Node.js', info: 'Crea aplicaciones rápidas en servidores.', flipped: false },
  { name: 'Express', info: 'Facilita la creación de sitios web y servicios.', flipped: false },
  { name: 'Vue.js', info: 'Hace las páginas web más rápidas e interactivas.', flipped: false },
  { name: 'JavaScript', info: 'Da vida a las páginas web con interacción.', flipped: false },
  { name: 'C++', info: 'Crea programas rápidos como videojuegos.', flipped: false },
  { name: 'MySQL', info: 'Almacena y organiza información en bases de datos.', flipped: false },
  { name: 'MongoDB', info: 'Guarda grandes volúmenes de datos de manera flexible.', flipped: false },
  { name: 'Python', info: 'Lenguaje fácil para múltiples tareas, como análisis de datos.', flipped: false },
  { name: 'APIs RESTful', info: 'Permiten que aplicaciones se comuniquen entre sí.', flipped: false },
  { name: 'Sitios web responsive', info: 'Adaptan un sitio para verse bien en cualquier dispositivo.', flipped: false },
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
  { name: 'Instagram', icon: InstagramIcon, url: 'https://instagram.com/pauldiazjoseguillermo' },
]);

const flipCard = (skill) => {
  skill.flipped = !skill.flipped;
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  height: 100%;
}

.portfolio {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  width: 100%; /* Asegura que el contenedor principal ocupe todo el ancho */
  background: linear-gradient(to bottom right, #000203, #006DA3, #5CC9FF, #000203);
  color: #f7fafc;
  font-family: Arial, sans-serif;
}

header {
  position: fixed;
  top: 0;
  left: 0; /* Asegura que el header comience desde el borde izquierdo */
  right: 0; /* Asegura que el header llegue hasta el borde derecho */
  width: 100%;
  background-color: rgba(0, 2, 3, 0.8);
  z-index: 1000;
  padding: 1rem 0;
}

nav {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 100%;
  padding: 0 2rem; /* Ajusta el padding horizontal si es necesario */
}

nav ul {
  display: flex;
  gap: 2rem; /* Ajusta el espacio entre los enlaces del menú */
  list-style-type: none;
}

nav a {
  color: #f7fafc;
  text-decoration: none;
  font-size: 1rem;
  transition: color 0.3s;
}

nav a:hover {
  color: #63b3ed;
}

main {
  flex: 1;
  padding: 3rem 1rem;
  margin-top: 100px;
}


.profile {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 4rem;
  padding-left: 10vw;
}

.profile-image img {
  width: 30rem;
  height: 30rem;
  object-fit: contain;
  border-radius: 0.5rem;
  border: 4px solid #006DA3;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  background-color: #2f3339;
}

.profile-content {
  text-align: center;
  margin-top: 2rem;
  margin-right: 3rem;
}

.profile-content h2 {
  font-size: 2.25rem;
  font-weight: bold;
  margin-bottom: 1rem;
}

.profile-content p {
  font-size: 1.25rem;
  text-align: justify;
  margin-bottom: 1.5rem;
}

.cta-button {
  background-color: #0D456E;
  color: white;
  font-weight: bold;
  padding: 1rem 2rem;
  border-radius: 1rem;
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
  font-size: 3rem;
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

.skill-item.half-width {
  grid-column: span 2; /* Esto hace que ocupen dos columnas */
}

.skill-item:nth-last-child(2) {
  grid-column: 2; /* Segunda columna */
}

.skill-item:nth-last-child(1) {
  grid-column: 3; /* Tercera columna */
}

.skill-item {
    background-color: #2d3748;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2), 0 6px 20px rgba(0, 0, 0, 0.19); /* Sombra suave */
    padding: 6rem;
    border-radius: 0.5rem;
    text-align: center;
    transition: transform 0.6s, background-color 0.3s; /* Animación suave */
    transform-style: preserve-3d;
    perspective: 1000px;
}

.skill-item:hover {
    background-color: #4a5568;
    transform: rotateY(180deg); /* Efecto de giro al pasar el mouse */
}

.skill-item::before {
    content: attr(data-front); /* Contenido del frente de la carta */
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden; /* Oculta la parte trasera durante el giro */
}

 .skill-item::after {
    content: attr(data-back); /* Contenido de la parte trasera */
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    transform: rotateY(180deg); /* Parte trasera de la carta */
}

.card {
  width: 100%;
  height: 100px;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  position: relative;
}

.card-front,
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #2d3748;
  padding: 1rem;
  border-radius: 0.5rem;
  color: #f7fafc;
}

.card-front {
  background-color: #2d3748;
}

.card-back {
  background-color: #4a5568;
  transform: rotateY(180deg);
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
  color: #00527A;
  transition: color 0.3s;
}

.social-icons a:hover {
  color: #1573B7;
}

footer {
  background-color: #2d3748;
  padding: 1rem 0; /* Cambia el padding vertical si lo deseas */
  text-align: center;
  left: 0; /* Asegura que el header comience desde el borde izquierdo */
  right: 0; /* Asegura que el header llegue hasta el borde derecho */
  bottom: 0;
  width: 100%;
}

@media (min-width: 768px) {
  .profile {
    flex-direction: row;
    text-align: left;
  }

  .profile-image {
    width: 50%;
    margin-right: 3rem;
  }

  .profile-content {
    width: 50%;
    text-align: left;
  }
}

.soft-skills {
    margin-bottom: 4rem;
  }

  .soft-skills {
  margin-bottom: 4rem;
}

.pyramid {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.level {
  display: flex;
  justify-content: center;
  margin-bottom: 1rem;
}

.pyramid-item {
  background-color: #2d3748;
  color: #f7fafc;
  padding: 1rem;
  border-radius: 0.5rem;
  margin: 0.5rem;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  min-width: 150px; /* Puedes ajustar este valor según el tamaño deseado */
  min-height: 50px; /* Altura mínima para hacer que todos tengan una apariencia uniforme */
}

/* Ajusta los niveles con más elementos */
.level-1 .pyramid-item {
  width: 200px; /* El nivel superior con un solo elemento más ancho */
  height: 80PX;
  padding: 1.5vw;
}

.level-2 .pyramid-item {
  width: 200px;
  height: 80PX;
  padding: 1.5vw;
}

.level-3 .pyramid-item {
  width:  200px;
  height: 80PX;
  padding: 1.5vw;
}

</style>