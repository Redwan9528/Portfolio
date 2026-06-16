<template>
  <div>
    <nav class="navbar" :class="{ scrolled: isScrolled }">
      <div class="nav-container">
        <a href="#accueil" class="nav-logo">
          <span class="mini-logo">RD</span>
          <span>Redwan</span>
        </a>

        <ul class="nav-menu" :class="{ active: isMenuOpen }">
          <li v-for="item in navItems" :key="item.id">
            <a :href="item.href" class="nav-link" @click="closeMenu">
              {{ item.label }}
            </a>
          </li>
        </ul>

        <button class="hamburger" :class="{ active: isMenuOpen }" @click="toggleMenu">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
    </nav>

    <section id="accueil" class="hero">
      <div class="hero-container">
        <div class="hero-content">
          <span class="badge">Portfolio - BUT Informatique</span>

          <h1>
            Redwan DJEDIA <br />
            <span>Développeur Informatique</span>
          </h1>

          <h2>Développement logiciel, data et objectif IA / MLOps</h2>

          <p>
            Étudiant en deuxième année de BUT Informatique à l’Université Sorbonne Paris Nord,
            je construis progressivement un profil orienté développement logiciel, applications web,
            bases de données et exploitation de données. Mon parcours, mes projets et mon stage chez
            Safran m’amènent aujourd’hui à m’intéresser davantage à l’intelligence artificielle,
            au Machine Learning et au MLOps.
          </p>

          <div class="hero-buttons">
            <a href="#presentation" class="btn btn-primary">Découvrir mon profil</a>
            <a href="/REDWAN-DJEDIA-CV.pdf" target="_blank" class="btn btn-secondary">Voir mon CV</a>
          </div>
        </div>

        <div class="hero-visual">
          <div class="identity-card">
            <div class="monogram">
              <span>R</span>
              <span>D</span>
            </div>

            <h3>Redwan DJEDIA</h3>
            <p>Développeur informatique</p>

            <div class="identity-tags">

            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="presentation" class="section about">
      <div class="container">
        <div class="section-header">
          <span class="section-label">01</span>
          <h2>Présentation générale</h2>
          <p>Un parcours en construction entre développement, data et intelligence artificielle.</p>
        </div>

        <div class="about-grid">
          <div class="about-card large">
            <h3>Qui suis-je ?</h3>

            <p>
              Je suis actuellement étudiant en deuxième année de BUT Informatique à l’Université
              Sorbonne Paris Nord. Depuis mon entrée dans la formation, j’ai développé des compétences
              en programmation, développement web, bases de données, analyse des besoins et gestion de projet.
            </p>

            <p>
              Les différents projets réalisés, notamment Mnémosyne, m’ont permis de découvrir les
              contraintes d’un développement collaboratif et de travailler sur une application web complète.
              J’ai appris à passer d’un besoin à une solution concrète en structurant mon code et en
              travaillant avec une équipe.
            </p>

            <p>
              Mon stage chez Safran a renforcé cette expérience en me confrontant à des problématiques
              réelles d’entreprise, notamment autour du développement d’outils internes et de l’exploitation
              de données métier.
            </p>

            <p>
              Aujourd’hui, mon projet professionnel s’oriente progressivement vers l’intelligence
              artificielle, le Machine Learning et le MLOps, qui représentent pour moi la continuité
              naturelle entre développement logiciel, données et automatisation.
            </p>
          </div>

          <div class="about-card profile-side">
            <h3>Mon profil</h3>
            <ul class="clean-list">
              <li>Curieux et autonome</li>
              <li>Organisé et discipliné</li>
              <li>À l’aise avec le travail en équipe</li>
              <li>Intéressé par la data et l’IA</li>
              <li>Orienté solution et progression</li>
            </ul>
          </div>
        </div>

        <div class="skills">
          <h3>Compétences</h3>

          <div class="skills-grid">
            <div class="skill" v-for="skill in skills" :key="skill.name">
              <i :class="skill.icon"></i>
              <span>{{ skill.name }}</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="informatique" class="section">
      <div class="container">
        <div class="section-header">
          <span class="section-label">02</span>
          <h2>Pourquoi l’informatique ?</h2>
          <p>Une orientation qui s’est construite avec les projets et l’expérience.</p>
        </div>

        <div class="text-card">
          <p>
            J’ai choisi l’informatique parce que c’est un domaine qui permet de créer des outils utiles
            à partir d’un besoin concret. Ce qui m’intéresse, c’est de comprendre un problème,
            de le découper, puis de concevoir une solution fonctionnelle.
          </p>

          <p>
            Au fil du BUT, j’ai découvert que l’informatique demande autant de logique que de méthode.
            Il ne suffit pas que le programme fonctionne : il faut aussi qu’il soit clair, maintenable,
            organisé et adapté aux utilisateurs.
          </p>

          <p>
            Mon intérêt pour l’IA et le MLOps vient de cette envie d’aller plus loin : exploiter les
            données, automatiser des traitements, créer des modèles intelligents et apprendre à les
            déployer dans des environnements réels. C'est le futur de l'informatique !
          </p>
        </div>
      </div>
    </section>

    <section id="projets" class="section projects">
      <div class="container">
        <div class="section-header">
          <span class="section-label">03</span>
          <h2>Projets importants</h2>
          <p>Des projets qui montrent ma progression technique et ma capacité à travailler en équipe.</p>
        </div>

        <div class="projects-grid">
          <article class="project-card" v-for="project in projects" :key="project.id">
            <img :src="project.image" :alt="project.title" />

            <div class="project-content">
              <h3>{{ project.title }}</h3>
              <p>{{ project.short }}</p>

              <div class="tags">
                <span v-for="tag in project.tags" :key="tag">{{ tag }}</span>
              </div>

              <div class="project-actions">
                <button class="btn btn-small" @click="openProject(project)">
                  Voir le détail
                </button>

                <a
                  v-if="project.github"
                  :href="project.github"
                  target="_blank"
                  class="btn btn-small btn-github"
                >
                  GitHub
                </a>
              </div>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section id="stage" class="section">
      <div class="container">
        <div class="section-header">
          <span class="section-label">04</span>
          <h2>Expérience professionnelle</h2>
          <p>Un premier contact concret avec le développement en entreprise.</p>
        </div>

        <div class="text-card">
          <h3>Stage développeur informatique - Safran</h3>

          <p>
            Lors de mon stage chez Safran, j’ai travaillé sur le développement d’outils internes
            facilitant l’accès, l’exploitation et l’analyse de données métier.
          </p>

          <p>
            Cette expérience m’a permis de découvrir un environnement professionnel, de mieux comprendre
            l’importance de l’analyse des besoins et de proposer des solutions adaptées aux utilisateurs.
            J’ai également travaillé avec WinDev et WebDev, ce qui m’a permis d’élargir mes compétences
            au-delà des technologies vues en cours.
          </p>
        </div>
      </div>
    </section>

    <section id="progression" class="section about">
      <div class="container">
        <div class="section-header">
          <span class="section-label">05</span>
          <h2>Work in progress</h2>
          <p>Ce que je maîtrise aujourd’hui et ce que je souhaite approfondir.</p>
        </div>

        <div class="about-grid">
          <div class="about-card">
            <h3>Acquis actuels</h3>
            <ul class="clean-list">
              <li>Développement web avec Vue.js, HTML, CSS, JavaScript</li>
              <li>Développement backend avec PHP</li>
              <li>Programmation avec Python et Java</li>
              <li>Bases de données SQL, PostgreSQL et SQL Server</li>
              <li>Architecture MVC et API REST</li>
              <li>Travail collaboratif avec Git/GitHub</li>
            </ul>
          </div>

          <div class="about-card">
            <h3>Compétences à développer</h3>
            <ul class="clean-list">
              <li>Machine Learning</li>
              <li>Intelligence artificielle</li>
              <li>MLOps</li>
              <li>Docker et CI/CD</li>
              <li>Cloud computing</li>
              <li>Déploiement et supervision de modèles IA</li>
            </ul>
          </div>
        </div>

        <div class="text-card">
          <h3>Plan d’action</h3>
          <p>
            Pour atteindre mon objectif, je souhaite approfondir Python, apprendre les bases du Machine
            Learning avec des bibliothèques comme Scikit-Learn, TensorFlow ou PyTorch, puis découvrir
            les outils permettant de déployer et suivre des modèles en production.
          </p>
        </div>
      </div>
    </section>

    <section id="objectifs" class="section">
      <div class="container">
        <div class="section-header">
          <span class="section-label">06</span>
          <h2>Objectifs professionnels</h2>
          <p>Une trajectoire orientée développement, data et IA.</p>
        </div>

        <div class="timeline-grid">
          <div class="timeline-item">
            <span>Court terme</span>
            <h4>Réussir mon BUT Informatique</h4>
            <p>
              Consolider mes compétences techniques, réussir mes projets universitaires et continuer à
              progresser grâce à l’expérience professionnelle.
            </p>
          </div>

          <div class="timeline-item">
            <span>Moyen terme</span>
            <h4>Me spécialiser en IA / Data</h4>
            <p>
              Poursuivre mes études vers une formation orientée intelligence artificielle, data science
              ou Machine Learning.
            </p>
          </div>

          <div class="timeline-item">
            <span>Long terme</span>
            <h4>Évoluer vers le MLOps</h4>
            <p>
              Participer à la conception, au déploiement et à la supervision de solutions intelligentes
              utilisées dans des environnements réels.
            </p>
          </div>
        </div>
      </div>
    </section>

    <footer class="footer">
      <div class="footer-links">
        <a href="mailto:redwandjedia23@gmail.com">Email</a>
        <a href="https://github.com/Redwan9528" target="_blank">GitHub</a>
        <a href="https://linkedin.com/in/redwan-djedia" target="_blank">LinkedIn</a>
        <a href="/REDWAN-DJEDIA-CV.pdf" target="_blank">CV</a>
      </div>

      <p>© 2026 DJEDIA Redwan - Portfolio S4 BUT Informatique</p>
    </footer>

    <div class="modal" v-if="selectedProject" @click.self="closeProject">
      <div class="modal-content">
        <button class="close" @click="closeProject">&times;</button>

        <div class="project-gallery">
          <img
            v-for="photo in selectedProject.gallery"
            :key="photo"
            :src="photo"
            :alt="selectedProject.title"
          />
        </div>

        <h2>{{ selectedProject.title }}</h2>
        <p>{{ selectedProject.description }}</p>

        <h3>Compétences développées</h3>
        <div class="tags">
          <span v-for="tag in selectedProject.tags" :key="tag">{{ tag }}</span>
        </div>

        <h3>Ce que ce projet m’a apporté</h3>
        <p>{{ selectedProject.learning }}</p>

        <a
          v-if="selectedProject.github"
          :href="selectedProject.github"
          target="_blank"
          class="btn btn-primary modal-link"
        >
          Voir le projet sur GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isMenuOpen = ref(false)
const isScrolled = ref(false)
const selectedProject = ref(null)

let observer = null

const navItems = [
  { id: 'accueil', label: 'Accueil', href: '#accueil' },
  { id: 'presentation', label: 'Profil', href: '#presentation' },
  { id: 'informatique', label: 'Pourquoi l’info ?', href: '#informatique' },
  { id: 'projets', label: 'Projets', href: '#projets' },
  { id: 'stage', label: 'Stage', href: '#stage' },
  { id: 'progression', label: 'Progression', href: '#progression' },
  { id: 'objectifs', label: 'Objectifs', href: '#objectifs' }
]

const skills = [
  { name: 'Python', icon: 'fa-brands fa-python' },
  { name: 'PHP', icon: 'fa-brands fa-php' },
  { name: 'JavaScript', icon: 'fa-brands fa-js' },
  { name: 'Vue.js', icon: 'fa-brands fa-vuejs' },
  { name: 'Java', icon: 'fa-brands fa-java' },
  { name: 'C', icon: 'fa-solid fa-code' },
  { name: 'SQL', icon: 'fa-solid fa-database' },
  { name: 'PostgreSQL', icon: 'fa-solid fa-database' },
  { name: 'SQL Server', icon: 'fa-solid fa-server' },
  { name: 'API REST', icon: 'fa-solid fa-plug' },
  { name: 'Architecture MVC', icon: 'fa-solid fa-diagram-project' },
  { name: 'GitHub', icon: 'fa-brands fa-github' },
  { name: 'Linux/Shell', icon: 'fa-brands fa-linux' },
  { name: 'WinDev', icon: 'fa-solid fa-laptop-code' },
  { name: 'WebDev', icon: 'fa-solid fa-globe' },
  { name: 'Analyse des besoins', icon: 'fa-solid fa-magnifying-glass-chart' }
]

const projects = [
  {
    id: 1,
    title: 'Mnémosyne - Application web',
    short: 'Application web permettant de visualiser les parcours et formations des étudiants.',
    description:
      'Mnémosyne est un projet universitaire réalisé en équipe. J’ai travaillé sur l’ensemble du projet : conception, développement backend PHP, architecture MVC, API REST, gestion de la base de données, intégration et travail collaboratif avec Git/GitHub.',
    learning:
      'Ce projet m’a permis de comprendre le fonctionnement d’une application web complète. Il m’a aussi appris l’importance de l’architecture logicielle, de la qualité du code et de la coordination dans un projet collectif.',
    github: 'https://github.com/Mnemosyne-S301/Mnemosyne',
    image:  'https://images.unsplash.com/photo-1516321318423-f06f85e504b3?w=1200&h=800&fit=crop',
    gallery: ['/images/mnemosyne-1.png', '/images/mnemosyne-2.png'],
    tags: ['PHP', 'MVC', 'API REST', 'SQL', 'Git', 'GitHub']
  },
  {
    id: 2,
    title: 'Jeu d’échecs en Java',
    short: 'Conception et réalisation d’un jeu d’échecs en programmation orientée objet.',
    description:
      'Projet Java visant à concevoir un jeu d’échecs complet en utilisant la programmation orientée objet, la modélisation UML et la logique métier.',
    learning:
      'Ce projet m’a permis de mieux comprendre l’importance de la conception avant le développement.',
    image:  'https://images.unsplash.com/photo-1528819622765-d6bcf132f793?w=1200&h=800&fit=crop',
    gallery: [],
    tags: ['Java', 'POO', 'UML', 'Git']
  },
  {
    id: 3,
    title: 'Simulation d’un réseau social en Python',
    short: 'Projet Python permettant de manipuler des structures de données.',
    description:
      'Projet Python permettant de simuler des interactions entre utilisateurs afin de mettre en pratique l’algorithmique et les structures de données.',
    learning:
      'J’ai mieux compris l’importance du choix des structures de données pour résoudre efficacement un problème.',
    image:'https://images.unsplash.com/photo-1555949963-aa79dcee981c?w=1200&h=800&fit=crop',
    gallery: [],
    tags: ['Python', 'Algorithmique', 'Structures de données']
  },
  {
    id: 4,
    title: 'Base de données PostgreSQL',
    short: 'Conception, modélisation et exploitation d’une base relationnelle.',
    description:
      'Projet de base de données portant sur la modélisation, la création de tables, les requêtes SQL et l’exploitation de données.',
    learning:
      'J’ai compris qu’une base bien conçue facilite l’analyse et fiabilise les informations.',
    image: 'https://images.unsplash.com/photo-1544383835-bda2bc66a55d?w=1200&h=800&fit=crop',
    gallery: [],
    tags: ['SQL', 'PostgreSQL', 'Modélisation']
  },
  {
    id: 5,
    title: 'Stage développeur informatique - Safran',
    short: 'Développement d’outils internes et automatisation de processus métier.',
    description:
      'Durant mon stage chez Safran, j’ai participé au développement d’outils facilitant l’accès et l’exploitation de données métier.',
    learning:
      'Cette expérience m’a permis de découvrir les contraintes du développement en entreprise et l’importance de l’analyse des besoins.',
    image: 'https://images.unsplash.com/photo-1516321165247-4aa89a48be28?w=1200&h=800&fit=crop',
    gallery: [],
    tags: ['WinDev', 'WebDev', 'Analyse métier', 'Automatisation']
  }
]

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}

const openProject = project => {
  selectedProject.value = project
  document.body.style.overflow = 'hidden'
}

const closeProject = () => {
  selectedProject.value = null
  document.body.style.overflow = 'auto'
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll()

  observer = new IntersectionObserver(
    entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('show')
        }
      })
    },
    { threshold: 0.15 }
  )

  document
    .querySelectorAll('.section, .project-card, .about-card, .text-card, .timeline-item, .skills')
    .forEach(element => {
      element.classList.add('reveal')
      observer.observe(element)
    })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)

  if (observer) {
    observer.disconnect()
  }
})
</script>