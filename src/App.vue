<template>
  <div>
    <nav class="navbar" :class="{ scrolled: isScrolled }">
      <div class="nav-container">
        <a href="#accueil" class="nav-logo">Redwan<span>.</span></a>

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
          <span class="badge">Portfolio S4 - BUT Informatique</span>

          <h1>
            Redwan DJEDIA <br />
            <span>Développeur Informatique</span>
          </h1>

          <h2>Développement logiciel, Data & futur parcours IA / MLOps</h2>

          <p>
            Étudiant en deuxième année de BUT Informatique à l’Université Sorbonne Paris Nord,
            je développe progressivement des compétences en développement web, bases de données,
            analyse des besoins et conception d’applications. Mon objectif est de m’orienter vers
            l’intelligence artificielle, le Machine Learning et le MLOps.
          </p>

          <div class="hero-buttons">
            <a href="#presentation" class="btn btn-primary">Découvrir mon profil</a>
            <a href="#projets" class="btn btn-secondary">Voir mes projets</a>
          </div>
        </div>

        <div class="hero-card">
          <div class="logo-circle">RD</div>

          <div class="hero-stats">
            <div>
              <strong>BUT</strong>
              <span>Informatique</span>
            </div>
            <div>
              <strong>IA</strong>
              <span>Objectif futur</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="presentation" class="section about">
      <div class="container">
        <div class="section-header">
          <span class="section-label">01</span>
          <h2>Présentation personnelle</h2>
          <p>Mon parcours, mes qualités et mon évolution.</p>
        </div>

        <div class="about-grid">
          <div class="about-card large">
            <h3>Mon profil</h3>
            <p>
              Je suis Redwan DJEDIA, étudiant en deuxième année de BUT Informatique à l’Université
              Sorbonne Paris Nord. Je suis actuellement en stage chez Safran en tant que développeur
              informatique.
            </p>
            <p>
              Ma formation m’a permis de développer des compétences en programmation, développement
              web, bases de données, architecture logicielle, analyse des besoins et travail en équipe.
              Les projets réalisés m’ont aussi permis de mieux comprendre les attentes d’un projet
              informatique complet.
            </p>
          </div>

          <div class="about-card">
            <h3>Mes qualités</h3>
            <p>
              Je suis curieux, autonome, organisé et discipliné. J’aime apprendre de nouvelles
              technologies, comprendre les problèmes et chercher des solutions concrètes.
            </p>
          </div>
        </div>

        <div class="skills">
          <h3>Compétences techniques</h3>

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
          <p>Une réflexion personnelle sur mon choix d’orientation.</p>
        </div>

        <div class="text-card">
          <p>
            J’ai choisi l’informatique parce que ce domaine permet de transformer une idée ou un besoin
            en solution concrète. Ce qui m’intéresse particulièrement, c’est le fait de concevoir,
            développer et améliorer des outils utiles.
          </p>

          <p>
            Au fil de ma formation, j’ai compris que l’informatique ne se limite pas au code. Il faut
            aussi analyser un besoin, organiser son travail, communiquer avec une équipe, tester ses
            solutions et documenter ses choix.
          </p>

          <p>
            Mon intérêt évolue aujourd’hui vers la donnée, l’intelligence artificielle, le Machine
            Learning et le MLOps. Ces domaines m’attirent car ils combinent programmation, exploitation
            des données, automatisation et innovation.
          </p>
        </div>
      </div>
    </section>

    <section id="projets" class="section projects">
      <div class="container">
        <div class="section-header">
          <span class="section-label">03</span>
          <h2>Projets et compétences développées</h2>
          <p>Mes projets les plus importants et ce qu’ils m’ont apporté.</p>
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
                  Voir l’analyse
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
          <p>Mon stage chez Safran et ce qu’il m’apporte.</p>
        </div>

        <div class="text-card">
          <h3>Développeur Informatique - Safran</h3>

          <p>
            Lors de mon stage chez Safran, j’ai participé au développement d’outils internes
            facilitant l’accès, l’exploitation et l’analyse de données métier.
          </p>

          <p>
            Cette expérience m’a permis de travailler avec des environnements professionnels comme
            WinDev et WebDev, tout en renforçant mes compétences en analyse des besoins,
            automatisation et communication avec les utilisateurs.
          </p>

          <p>
            Ce stage m’aide à mieux comprendre les attentes d’une entreprise et à faire le lien
            entre les compétences acquises en BUT Informatique et leur application dans un contexte réel.
          </p>
        </div>
      </div>
    </section>

    <section id="progression" class="section about">
      <div class="container">
        <div class="section-header">
          <span class="section-label">05</span>
          <h2>Work in progress</h2>
          <p>Mes acquis actuels et les compétences que je souhaite développer.</p>
        </div>

        <div class="about-grid">
          <div class="about-card">
            <h3>Ce que je maîtrise mieux aujourd’hui</h3>
            <ul class="clean-list">
              <li>Développement web</li>
              <li>Programmation PHP, Python, Java et JavaScript</li>
              <li>Bases de données SQL</li>
              <li>Travail collaboratif avec Git/GitHub</li>
              <li>Analyse des besoins</li>
              <li>Architecture MVC</li>
            </ul>
          </div>

          <div class="about-card">
            <h3>Ce que je veux approfondir</h3>
            <ul class="clean-list">
              <li>Machine Learning</li>
              <li>Intelligence Artificielle</li>
              <li>MLOps</li>
              <li>Docker et CI/CD</li>
              <li>Cloud Computing</li>
              <li>Déploiement d’applications</li>
            </ul>
          </div>
        </div>

        <div class="text-card">
          <h3>Plan d’action</h3>
          <p>
            Pour atteindre mon objectif professionnel, je souhaite approfondir Python, découvrir des
            bibliothèques de Machine Learning comme Scikit-Learn, TensorFlow ou PyTorch, puis me former
            progressivement aux pratiques MLOps permettant de déployer et superviser des modèles
            d’intelligence artificielle en production.
          </p>
        </div>
      </div>
    </section>

    <section id="objectifs" class="section">
      <div class="container">
        <div class="section-header">
          <span class="section-label">06</span>
          <h2>Mes objectifs</h2>
          <p>Mes perspectives à court, moyen et long terme.</p>
        </div>

        <div class="timeline-grid">
          <div class="timeline-item">
            <span>Court terme</span>
            <h4>Réussir mon BUT Informatique</h4>
            <p>
              Mon objectif immédiat est de valider mon année, renforcer mes compétences techniques
              et continuer à progresser dans mes projets universitaires et professionnels.
            </p>
          </div>

          <div class="timeline-item">
            <span>Moyen terme</span>
            <h4>Poursuivre vers l’IA, la Data ou le Machine Learning</h4>
            <p>
              Après le BUT, je souhaite poursuivre mes études dans une formation spécialisée en
              intelligence artificielle, data science ou Machine Learning.
            </p>
          </div>

          <div class="timeline-item">
            <span>Long terme</span>
            <h4>Évoluer vers l’IA / MLOps</h4>
            <p>
              À long terme, je souhaite travailler dans les domaines de l’intelligence artificielle,
              du Machine Learning et du MLOps, afin de concevoir, déployer et superviser des solutions
              intelligentes à grande échelle.
            </p>
          </div>
        </div>
      </div>
    </section>

    <footer class="footer">
      <div class="footer-links">
        <a href="mailto:redwandjedia23@gmail.com">Email</a>
        <a href="https://github.com/Redwan9528" target="_blank">GitHub</a>
        <a href="https://github.com/Mnemosyne-S301/Mnemosyne" target="_blank">Mnémosyne</a>
        <a href="https://linkedin.com/in/redwan-djedia" target="_blank">LinkedIn</a>
        <a href="/CV-REDWAN-DJEDIA.pdf" target="_blank">CV</a>
      </div>

      <p>© 2026 DJEDIA Redwan - Portfolio S4 BUT Informatique</p>
    </footer>

    <div class="modal" v-if="selectedProject" @click.self="closeProject">
      <div class="modal-content">
        <button class="close" @click="closeProject">&times;</button>

        <img :src="selectedProject.image" :alt="selectedProject.title" />

        <h2>{{ selectedProject.title }}</h2>

        <p>{{ selectedProject.description }}</p>

        <h3>Prise de conscience</h3>
        <p>{{ selectedProject.awareness }}</p>

        <h3>Compétences développées</h3>
        <div class="tags">
          <span v-for="tag in selectedProject.tags" :key="tag">{{ tag }}</span>
        </div>

        <h3>Perspective de progression</h3>
        <p>{{ selectedProject.progress }}</p>

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
    short:
      'Application web permettant de visualiser les parcours et les formations des étudiants.',
    description:
      'Mnémosyne est un projet universitaire réalisé en équipe. J’ai travaillé sur l’ensemble du projet : conception, développement backend PHP, architecture MVC, API REST, gestion de la base de données, intégration et travail collaboratif avec Git/GitHub.',
    awareness:
      'Ce projet m’a permis de comprendre le fonctionnement d’une application web complète. J’ai pris conscience de l’importance de l’architecture logicielle, de l’organisation du code et de la communication dans un projet en équipe.',
    progress:
      'Je souhaite continuer à progresser sur les architectures web modernes, la qualité du code, les API et les bonnes pratiques de développement collaboratif.',
    github: 'https://github.com/Mnemosyne-S301/Mnemosyne',
    image:
      'https://images.unsplash.com/photo-1516321318423-f06f85e504b3?w=1200&h=800&fit=crop',
    tags: ['PHP', 'MVC', 'API REST', 'SQL', 'Git', 'GitHub', 'Travail en équipe']
  },
  {
    id: 2,
    title: 'Jeu d’échecs en Java',
    short:
      'Conception et réalisation d’un jeu d’échecs en programmation orientée objet.',
    description:
      'Ce projet avait pour objectif de concevoir un jeu d’échecs en Java. Il m’a permis de travailler la programmation orientée objet, la modélisation UML, la logique métier et le travail en équipe avec Git.',
    awareness:
      'J’ai compris que la conception est une étape essentielle avant le développement. Un projet bien modélisé est plus simple à coder, tester et faire évoluer.',
    progress:
      'Je souhaite approfondir les design patterns, la qualité du code et la conception logicielle orientée objet.',
    image:
      'https://images.unsplash.com/photo-1528819622765-d6bcf132f793?w=1200&h=800&fit=crop',
    tags: ['Java', 'POO', 'UML', 'Git', 'Logique métier']
  },
  {
    id: 3,
    title: 'Simulation d’un réseau social en Python',
    short:
      'Projet visant à simuler un réseau social et manipuler des structures de données.',
    description:
      'Ce projet m’a permis de mettre en pratique les bases de l’algorithmique et du langage Python à travers la simulation d’interactions entre utilisateurs.',
    awareness:
      'J’ai compris l’importance du choix des structures de données et de l’organisation du programme pour résoudre efficacement un problème.',
    progress:
      'Je souhaite approfondir les algorithmes, les graphes et leur lien avec l’analyse de données.',
    image:
      'https://images.unsplash.com/photo-1555949963-aa79dcee981c?w=1200&h=800&fit=crop',
    tags: ['Python', 'Algorithmique', 'Structures de données', 'Résolution de problèmes']
  },
  {
    id: 4,
    title: 'Base de données PostgreSQL',
    short:
      'Conception, modélisation et exploitation d’une base de données relationnelle.',
    description:
      'Ce projet m’a permis de travailler sur la conception d’une base de données, la modélisation, les requêtes SQL et l’exploitation de données.',
    awareness:
      'J’ai compris qu’une base de données bien conçue facilite l’exploitation, l’analyse et la fiabilité des informations.',
    progress:
      'Je souhaite renforcer mes compétences en SQL avancé, optimisation de requêtes et exploitation de données.',
    image:
      'https://images.unsplash.com/photo-1544383835-bda2bc66a55d?w=1200&h=800&fit=crop',
    tags: ['SQL', 'PostgreSQL', 'Modélisation', 'Base de données']
  },
  {
    id: 5,
    title: 'Stage développeur informatique - Safran',
    short:
      'Développement d’outils internes et automatisation de processus métier.',
    description:
      'Durant mon stage chez Safran, j’ai participé au développement d’outils facilitant l’accès et l’exploitation de données métier. J’ai travaillé avec des environnements comme WinDev et WebDev.',
    awareness:
      'Cette expérience m’a permis de découvrir les contraintes du développement en entreprise, l’importance de l’analyse des besoins et la nécessité de proposer des solutions adaptées aux utilisateurs.',
    progress:
      'Je souhaite poursuivre vers des projets mêlant développement, data, automatisation et intelligence artificielle.',
    image:
      'https://images.unsplash.com/photo-1516321165247-4aa89a48be28?w=1200&h=800&fit=crop',
    tags: ['WinDev', 'WebDev', 'Analyse métier', 'Automatisation', 'Données']
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
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>