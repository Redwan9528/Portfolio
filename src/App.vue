<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }">
    <div class="nav-container">
      <div class="nav-logo"><span>Portfolio</span></div>

      <ul class="nav-menu" :class="{ active: menuOpen }">
        <li v-for="item in navItems" :key="item.id" class="nav-item">
          <a :href="`#${item.id}`" class="nav-link" :class="{ active: activeSection === item.id }" @click="closeMenu">
            {{ item.label }}
          </a>
        </li>
      </ul>

      <button class="hamburger" :class="{ active: menuOpen }" @click="menuOpen = !menuOpen" aria-label="Ouvrir le menu">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </button>
    </div>
  </nav>

  <section id="accueil" class="hero">
    <div class="hero-container">
      <div class="hero-content">
        <h1 class="hero-title">
          <span class="greeting">Bonjour, je suis</span>
          <span class="name">Redwan DJEDIA</span>
        </h1>
        <p class="hero-subtitle">Développeur Informatique</p>
        <p class="hero-description">
          Étudiant en BUT Informatique. Je vous laisse découvrir mon profil et mes projets. 😉
        </p>
        <div class="hero-buttons">
          <a href="#projets" class="btn btn-primary">Voir mes projets</a>
          <a href="#contact" class="btn btn-secondary">Me contacter</a>
        </div>
      </div>

      <div class="hero-image">
        <div class="profile-card">
          <div class="logo-container"><div class="logo-initials">RD</div></div>
          <div class="profile-decoration"></div>
        </div>
      </div>
    </div>
    <div class="scroll-indicator"><div class="scroll-arrow"></div></div>
  </section>

  <section id="apropos" class="about">
    <div class="container">
      <SectionHeader title="À propos de moi" subtitle="Découvrez mon parcours et mes passions" />
      <div class="about-content">
        <div class="about-text">
          <div class="about-card">
            <h3>Mon Profil</h3>
            <p>
              Actuellement en BUT Informatique à l'Université Sorbonne Paris Nord, parcours Réalisation d'Application : Conception, Développement, Validation.
            </p>
          </div>
          <div class="about-card">
            <h3>Mes Qualités</h3>
            <p>
              Curieux, autonome, organisé et discipliné, j'aime résoudre des problèmes complexes et apprendre de nouvelles technologies.
            </p>
          </div>
        </div>
        <div class="skills-section">
          <h3>Compétences</h3>
          <div class="skills-grid">
            <div v-for="skill in skills" :key="skill.name" class="skill-item">
              <i :class="skill.icon"></i>
              <span>{{ skill.name }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section id="cv" class="cv-section">
    <div class="container">
      <SectionHeader title="Mon CV" subtitle="Mon parcours professionnel et académique" />
      <div class="cv-content">
        <div class="cv-column">
          <div class="cv-category">
            <h3><i class="fas fa-briefcase"></i> Expérience Professionnelle</h3>
            <div class="timeline">
              <TimelineItem
                date="2025 - En cours"
                title="Membre d'une Association"
                company="Numeric4You - Cergy"
                :items="['Collaboration efficace avec les autres membres de l\'association', 'Participation aux activités de l\'association', 'Contribution aux projets numériques']"
              />
              <TimelineItem
                date="2020"
                title="Stage d'observation"
                company="École Primaire Belle Épine - Cergy"
                :items="['Observation des tâches réalisées par les professionnels', 'Accompagnement d\'un salarié dans son travail', 'Assistance des employés expérimentés dans leurs tâches quotidiennes']"
              />
            </div>
          </div>
        </div>
        <div class="cv-column">
          <div class="cv-category">
            <h3><i class="fas fa-graduation-cap"></i> Formation</h3>
            <div class="timeline">
              <TimelineItem date="2024 - En cours" title="BUT Informatique" company="Université Sorbonne Paris Nord - Villetaneuse" description="Formation en développement informatique et gestion de données" />
              <TimelineItem date="2021 - 2024" title="Baccalauréat STI2D" company="Lycée Galilée - Cergy" description="Option SIN (Systèmes d'information et numérique) - Mention très bien" />
            </div>
          </div>
        </div>
      </div>
      <div class="cv-download">
        <a href="/CV-REDWAN-DJEDIA.pdf" class="btn btn-primary" target="_blank">
          <i class="fas fa-download"></i> Télécharger mon CV
        </a>
      </div>
    </div>
  </section>

  <section id="projets" class="projects">
    <div class="container">
      <SectionHeader title="Mes Projets" subtitle="Découvrez mes réalisations académiques" />
      <div class="projects-grid">
        <article v-for="project in projects" :key="project.id" class="project-card" @click="openProject(project)">
          <div class="project-image">
            <img :src="project.image" :alt="project.title">
            <div class="project-overlay"><button class="btn btn-primary project-btn">Voir le projet</button></div>
          </div>
          <div class="project-info">
            <h3>{{ project.title }}</h3>
            <p>{{ project.short }}</p>
            <div class="project-tags">
              <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>

  <section id="contact" class="contact">
    <div class="container">
      <SectionHeader title="Contactez-moi" subtitle="Hâte de discuter avec vous !" />
      <div class="contact-content">
        <div class="contact-info">
          <ContactItem icon="fas fa-envelope" title="Email" text="redwandjedia23@gmail.com" />
          <ContactItem icon="fas fa-phone" title="Téléphone" text="07 66 19 16 16" />
          <ContactItem icon="fas fa-map-marker-alt" title="Localisation" text="Île-de-France" />
          <div class="social-links">
            <a href="https://linkedin.com/in/redwan-djedia" class="social-link" target="_blank"><i class="fab fa-linkedin"></i></a>
            <a href="https://github.com/Redwan9528" class="social-link" target="_blank"><i class="fab fa-github"></i></a>
            <a href="mailto:redwandjedia23@gmail.com" class="social-link"><i class="fas fa-envelope"></i></a>
          </div>
        </div>

        <form class="contact-form" @submit.prevent="submitForm">
          <div class="form-group"><input v-model="form.name" type="text" placeholder="Votre nom" required></div>
          <div class="form-group"><input v-model="form.email" type="email" placeholder="Votre email" required></div>
          <div class="form-group"><input v-model="form.subject" type="text" placeholder="Sujet" required></div>
          <div class="form-group"><textarea v-model="form.message" placeholder="Votre message" rows="5" required></textarea></div>
          <button type="submit" class="btn btn-primary">Envoyer le message</button>
          <p v-if="messageSent" class="success-message">Message préparé dans votre messagerie ✅</p>
        </form>
      </div>
    </div>
  </section>

  <div v-if="selectedProject" class="modal" @click.self="closeProject">
    <div class="modal-content">
      <button class="close-modal" @click="closeProject">&times;</button>
      <div class="modal-body">
        <div class="project-detail">
          <div class="project-header">
            <h2>{{ selectedProject.title }}</h2>
            <p class="project-description">{{ selectedProject.description }}</p>
          </div>
          <div class="project-gallery">
            <img :src="selectedProject.image" :alt="selectedProject.title">
          </div>
          <div class="project-reports">
            <h3>Compétences développées</h3>
            <div class="report-item">
              <h4>Technologies / méthodes</h4>
              <p>{{ selectedProject.report }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <footer class="footer">
    <div class="container"><p>&copy; 2026 DJEDIA Redwan. Tous droits réservés.</p></div>
  </footer>
</template>

<script setup>
import { computed, defineComponent, h, onMounted, onUnmounted, reactive, ref } from 'vue'

const navItems = [
  { id: 'accueil', label: 'Accueil' },
  { id: 'apropos', label: 'À propos' },
  { id: 'cv', label: 'CV' },
  { id: 'projets', label: 'Projets' },
  { id: 'contact', label: 'Contact' },
]

const skills = [
  { name: 'Python', icon: 'fab fa-python' },
  { name: 'JavaScript', icon: 'fab fa-js-square' },
  { name: 'PostgreSQL', icon: 'fas fa-database' },
  { name: 'HTML/CSS', icon: 'fab fa-html5' },
  { name: 'Java', icon: 'fab fa-java' },
  { name: 'C', icon: 'fab fa-cuttlefish' },
  { name: 'Linux/Shell', icon: 'fab fa-linux' },
  { name: 'GitHub', icon: 'fab fa-github' },
]

const projects = [
  {
    id: 1,
    title: "SAE S101 - Simulation d'un Réseau Social",
    short: "Développement d'algorithmes pour modéliser et analyser les interactions dans un réseau social.",
    description: "Projet réalisé en Python autour de la simulation et de l'analyse d'un réseau social avec des structures de données adaptées.",
    image: 'https://images.unsplash.com/photo-1555949963-aa79dcee981c?w=800&h=500&fit=crop&crop=center',
    tags: ['Python', 'Algorithmique', 'Structures de données', 'CSV'],
    report: 'Manipulation de fichiers CSV, algorithmique, structuration du code et analyse de données.',
  },
  {
    id: 2,
    title: "SAE S102 - Comparaison d'Algorithmes",
    short: "Analyse comparative d'algorithmes et étude des complexités temporelles.",
    description: "Projet centré sur la mesure, la comparaison et l'optimisation des performances d'algorithmes.",
    image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=800&h=500&fit=crop&crop=center',
    tags: ['Python', 'Complexité', 'Optimisation', 'Tests'],
    report: 'Tests de performance, analyse de complexité et interprétation des résultats.',
  },
  {
    id: 3,
    title: 'SAE S105 - Recueil de Besoins IUT',
    short: "Enquête auprès des étudiants pour améliorer les infrastructures et services de l'IUT.",
    description: "Projet de recueil et d'analyse des besoins avec restitution structurée des résultats.",
    image: 'https://images.unsplash.com/photo-1586281380349-632531db7ed4?w=800&h=500&fit=crop&crop=center',
    tags: ['Analyse des besoins', 'Enquêtes', 'Rédaction', 'Équipe'],
    report: 'Questionnaire, analyse des réponses, synthèse et rédaction technique.',
  },
  {
    id: 4,
    title: 'SAE S106 - Environnement Économique et Écologique',
    short: "Analyse de l'impact environnemental de Sony et de ses stratégies.",
    description: "Projet de recherche documentaire sur les enjeux économiques et écologiques d'une entreprise du numérique.",
    image: 'https://images.unsplash.com/photo-1611224923853-80b023f02d71?w=800&h=500&fit=crop&crop=center',
    tags: ['Économie durable', 'Analyse', 'Recherche', 'Rédaction'],
    report: 'Recherche documentaire, analyse environnementale et présentation structurée.',
  },
  {
    id: 5,
    title: 'SAE S104 - Base de Données Catastrophes Climatiques',
    short: "Base de données PostgreSQL pour suivre les catastrophes climatiques mondiales.",
    description: "Projet de conception, modélisation et implémentation d'une base de données relationnelle.",
    image: 'https://images.unsplash.com/photo-1544383835-bda2bc66a55d?w=800&h=500&fit=crop&crop=center',
    tags: ['SQL', 'PostgreSQL', 'Modélisation', 'CSV'],
    report: 'Modèle relationnel, requêtes SQL, importation de données et exploitation des résultats.',
  },
  {
    id: 6,
    title: 'SAE S103/S203 - Installation de Services Réseaux LAMP',
    short: "Configuration d'un environnement LAMP avec services réseaux.",
    description: "Projet d'installation et de configuration de services sur un serveur Linux.",
    image: 'https://images.unsplash.com/photo-1558494949-ef010cbdcc31?w=800&h=500&fit=crop&crop=center',
    tags: ['Linux', 'Apache', 'MariaDB', 'PHP', 'SSH', 'FTP'],
    report: 'Administration système, configuration serveur, services réseau et tests de fonctionnement.',
  },
]

const menuOpen = ref(false)
const isScrolled = ref(false)
const activeSection = ref('accueil')
const selectedProject = ref(null)
const messageSent = ref(false)
const form = reactive({ name: '', email: '', subject: '', message: '' })

const closeMenu = () => { menuOpen.value = false }
const openProject = (project) => { selectedProject.value = project }
const closeProject = () => { selectedProject.value = null }

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
  const current = navItems.findLast?.((item) => {
    const section = document.getElementById(item.id)
    return section && window.scrollY >= section.offsetTop - 100
  })
  if (current) activeSection.value = current.id
}

const submitForm = () => {
  const body = encodeURIComponent(`Nom : ${form.name}\nEmail : ${form.email}\n\nMessage :\n${form.message}`)
  const subject = encodeURIComponent(form.subject)
  window.location.href = `mailto:redwandjedia23@gmail.com?subject=${subject}&body=${body}`
  messageSent.value = true
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

const SectionHeader = defineComponent({
  props: { title: String, subtitle: String },
  setup(props) {
    return () => h('div', { class: 'section-header' }, [
      h('h2', { class: 'section-title' }, props.title),
      h('p', { class: 'section-subtitle' }, props.subtitle),
    ])
  },
})

const TimelineItem = defineComponent({
  props: { date: String, title: String, company: String, description: String, items: Array },
  setup(props) {
    return () => h('div', { class: 'timeline-item' }, [
      h('div', { class: 'timeline-date' }, props.date),
      h('div', { class: 'timeline-content' }, [
        h('h4', props.title),
        h('p', { class: 'company' }, props.company),
        props.description ? h('p', props.description) : null,
        props.items?.length ? h('ul', props.items.map((item) => h('li', item))) : null,
      ]),
    ])
  },
})

const ContactItem = defineComponent({
  props: { icon: String, title: String, text: String },
  setup(props) {
    return () => h('div', { class: 'contact-item' }, [
      h('i', { class: props.icon }),
      h('div', [h('h4', props.title), h('p', props.text)]),
    ])
  },
})
</script>
