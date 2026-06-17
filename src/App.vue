<template>
  <div class="portfolio-page">
    <a class="skip-link" href="#contenu">Aller au contenu</a>

    <header class="navbar" :class="{ scrolled: isScrolled }">
      <nav class="nav-container" aria-label="Navigation principale">
        <a class="nav-logo" href="#accueil" @click="closeMenu">
          <span class="mini-logo" aria-hidden="true">RD</span>
          <span class="logo-text">
            <strong>Redwan DJEDIA</strong>
            <small>BUT Informatique · 2e année</small>
          </span>
        </a>

        <ul class="nav-menu" :class="{ active: isMenuOpen }">
          <li v-for="item in navItems" :key="item.id">
            <a
              :href="item.href"
              class="nav-link"
              :class="{ active: activeSection === item.id }"
              @click="closeMenu"
            >
              {{ item.label }}
            </a>
          </li>
        </ul>

        <button
          class="hamburger"
          :class="{ active: isMenuOpen }"
          type="button"
          :aria-expanded="isMenuOpen"
          aria-label="Ouvrir ou fermer le menu"
          @click="toggleMenu"
        >
          <span></span>
          <span></span>
          <span></span>
        </button>
      </nav>
    </header>

    <main id="contenu">
      <section id="accueil" class="hero section-observed">
        <div class="hero-orbit hero-orbit-one" aria-hidden="true"></div>
        <div class="hero-orbit hero-orbit-two" aria-hidden="true"></div>

        <div class="hero-container">
          <div class="hero-content" data-reveal>
            <p class="eyebrow">Développement web · données · automatisation</p>

            <h1>Redwan DJEDIA</h1>
            <p class="hero-role">Étudiant en deuxième année de BUT Informatique</p>

            <div class="hero-buttons">
              <a href="#parcours" class="btn btn-primary">Découvrir mon parcours</a>
              <a :href="cvUrl" target="_blank" rel="noreferrer" class="btn btn-secondary">
                Consulter mon CV
              </a>
            </div>

            <ul class="hero-meta" aria-label="Informations principales">
              <li><strong>BUT 2</strong><span>IUT de Villetaneuse</span></li>
              <li><strong>Safran</strong><span>Stage développeur</span></li>
              <li><strong>Mnémosyne</strong><span>Projet universitaire principal</span></li>
            </ul>
          </div>

          <aside class="hero-card" data-reveal aria-label="Résumé du profil">
            <div class="hero-card-top">
              <span class="status-dot" aria-hidden="true"></span>
              <span>Profil en évolution</span>
            </div>

            <div class="monogram" aria-hidden="true">
              <span>R</span>
              <span>D</span>
            </div>

            <div>
              <p class="card-kicker">Domaine de prédilection</p>
              <h2>Développement logiciel orienté données</h2>
            </div>

            <div class="hero-card-grid">
              <div>
                <span>Socle actuel</span>
                <strong>Web · Backend · SQL</strong>
              </div>
              <div>
                <span>Objectif</span>
                <strong>IA · Data · MLOps</strong>
              </div>
            </div>

            <a href="#projet-professionnel" class="text-link">
              Voir mon projet professionnel <span aria-hidden="true">→</span>
            </a>
          </aside>
        </div>
      </section>

      <section id="parcours" class="section section-observed">
        <div class="container">
          <header class="section-header" data-reveal>
            <p class="section-number">01 · Présentation personnelle</p>
            <h2>La logique de mon parcours</h2>
            <p>
              Mon orientation ne repose pas sur une technologie choisie au hasard : elle s’est
              précisée au fil des projets universitaires, du travail en équipe et de mon stage.
            </p>
          </header>

          <div class="journey-layout">
            <div class="journey-story text-card" data-reveal>
              <p class="lead">
                J’ai choisi l’informatique parce que j’aime transformer un besoin en solution
                concrète : comprendre un problème, organiser les données, développer une
                fonctionnalité, la tester puis la rendre utilisable par d’autres personnes.
              </p>

              <p>
                En BUT 1, j’ai acquis les bases en programmation, développement web, algorithmique
                et bases de données. Ces premiers projets m’ont surtout appris à passer d’un exercice
                isolé à une réalisation structurée, avec un cahier des charges, des délais et un
                résultat à présenter.
              </p>

              <p>
                En BUT 2, le projet Mnémosyne m’a confronté à une application plus complète :
                architecture MVC, logique métier, API, import de données, requêtes SQL et travail
                sur un dépôt partagé. J’ai compris qu’un bon développement ne se limite pas à faire
                fonctionner une page : il faut aussi rendre le code lisible, les données fiables et
                les évolutions faciles à reprendre.
              </p>

              <p>
                Mon stage chez Safran a confirmé cette évolution. J’ai dû prendre en main WinDev,
                WebDev, le WLangage et SQL Server dans un environnement professionnel existant.
                Cette expérience m’a appris à m’adapter à des outils inconnus, à tenir compte des
                usages métier et à accepter les retours pour améliorer une solution.
              </p>
            </div>

            <div class="timeline" data-reveal>
              <article v-for="step in journey" :key="step.title" class="timeline-step">
                <span class="timeline-dot" aria-hidden="true"></span>
                <p class="timeline-period">{{ step.period }}</p>
                <h3>{{ step.title }}</h3>
                <p>{{ step.text }}</p>
              </article>
            </div>
          </div>
        </div>
      </section>

      <section id="projet-professionnel" class="section section-alt section-observed">
        <div class="container">
          <header class="section-header" data-reveal>
            <p class="section-number">02 · Orientation et ambitions</p>
            <h2>La direction que je souhaite donner à mon parcours</h2>
            <p>
              Mon projet se construit par étapes : consolider d’abord mes compétences actuelles,
              poursuivre mes études, puis me spécialiser progressivement.
            </p>
          </header>

          <div class="ambition-layout">
            <ol class="ambition-roadmap" data-reveal>
              <li v-for="item in careerPlan" :key="item.title" class="ambition-step">
                <span class="ambition-index">{{ item.index }}</span>
                <div>
                  <p class="card-kicker">{{ item.label }}</p>
                  <h3>{{ item.title }}</h3>
                  <p>{{ item.text }}</p>
                </div>
              </li>
            </ol>

            <aside class="ambition-focus" data-reveal>
              <p class="section-number">Mon domaine de prédilection</p>
              <h3>Le développement backend et la gestion des données</h3>
              <p>
                Je suis particulièrement attiré par la logique serveur, les API, les bases de
                données et l’automatisation des traitements. Le MLOps représente pour moi une suite
                possible, car il associe le développement, la donnée, les tests, le déploiement et
                la supervision.
              </p>

              <div class="ambition-tags" aria-label="Domaines à approfondir">
                <span>Python</span>
                <span>Backend</span>
                <span>SQL</span>
                <span>Docker</span>
                <span>Cloud</span>
                <span>Machine Learning</span>
              </div>

              <div class="ambition-sector">
                <strong>Secteurs ciblés</strong>
                <p>
                  Logiciel, industrie et services numériques, dans une organisation qui développe
                  des applications métiers ou des plateformes de données ayant un usage concret.
                </p>
              </div>
            </aside>
          </div>
        </div>
      </section>

      <section id="qualites" class="section section-observed">
        <div class="container">
          <header class="section-header" data-reveal>
            <p class="section-number">03 · Qualités personnelles</p>
            <h2>Des qualités appuyées par des exemples</h2>
            <p>
              Je ne souhaite pas seulement les afficher : chacune correspond à une situation vécue
              pendant mes SAÉ ou mon stage.
            </p>
          </header>

          <div class="qualities-grid">
            <article v-for="quality in qualities" :key="quality.title" class="quality-card" data-reveal>
              <span class="quality-icon" aria-hidden="true">{{ quality.icon }}</span>
              <h3>{{ quality.title }}</h3>
              <p>{{ quality.definition }}</p>
              <div class="proof-box">
                <strong>Exemple concret</strong>
                <p>{{ quality.proof }}</p>
              </div>
            </article>
          </div>
        </div>
      </section>

      <section id="competences" class="section section-dark section-observed">
        <div class="container">
          <header class="section-header light" data-reveal>
            <p class="section-number">04 · Bilan des compétences de BUT 2</p>
            <h2>Ce que je sais faire aujourd’hui</h2>
            <p>
              Ce bilan sélectionne les acquis les plus utiles pour une entreprise ou une poursuite
              d’études. Chaque compétence est associée à une preuve et à une perspective de progression.
            </p>
          </header>

          <div class="competency-grid">
            <article
              v-for="competency in competencies"
              :key="competency.code"
              class="competency-card"
              data-reveal
            >
              <div class="competency-head">
                <span class="competency-code">{{ competency.code }}</span>
                <span class="level-chip">{{ competency.level }}</span>
              </div>

              <h3>{{ competency.title }}</h3>
              <p>{{ competency.summary }}</p>

              <div class="competency-detail">
                <strong>Preuve sélectionnée</strong>
                <p>{{ competency.proof }}</p>
              </div>

              <div class="competency-detail progress-detail">
                <strong>Perspective</strong>
                <p>{{ competency.progress }}</p>
              </div>
            </article>
          </div>
        </div>
      </section>

      <section id="sae" class="section section-observed">
        <div class="container">
          <header class="section-header" data-reveal>
            <p class="section-number">05 · SAÉ et projets universitaires</p>
            <h2>Les projets qui ont marqué mon parcours</h2>
            <p>
              Mnémosyne est le projet le plus important de mon BUT 2. Les autres SAÉ montrent la
              progression de mes compétences en programmation, algorithmique et bases de données.
            </p>
          </header>

          <article class="featured-sae" data-reveal>
            <div class="featured-sae-media">
              <img :src="saeProjects[0].image" :alt="`Aperçu du projet ${saeProjects[0].title}`" />
              <div class="featured-sae-overlay">
                <span>{{ saeProjects[0].semester }}</span>
                <strong>Projet principal</strong>
              </div>
            </div>

            <div class="featured-sae-content">
              <div class="project-heading">
                <div>
                  <p class="card-kicker">{{ saeProjects[0].type }}</p>
                  <h3>{{ saeProjects[0].title }}</h3>
                </div>
                <span class="project-number">{{ saeProjects[0].number }}</span>
              </div>

              <p class="project-summary">{{ saeProjects[0].summary }}</p>

              <div class="tag-list">
                <span v-for="tag in saeProjects[0].tags" :key="tag">{{ tag }}</span>
              </div>

              <div class="project-actions-row">
                <button
                  class="details-button compact-button"
                  type="button"
                  :aria-expanded="expandedProjectIds.includes(saeProjects[0].id)"
                  @click="toggleProject(saeProjects[0].id)"
                >
                  {{ expandedProjectIds.includes(saeProjects[0].id) ? 'Masquer l’analyse' : 'Voir l’analyse complète' }}
                  <span aria-hidden="true">{{ expandedProjectIds.includes(saeProjects[0].id) ? '−' : '+' }}</span>
                </button>

                <a
                  :href="saeProjects[0].github"
                  target="_blank"
                  rel="noreferrer"
                  class="project-github-link"
                >
                  Voir le dépôt GitHub <span aria-hidden="true">→</span>
                </a>
              </div>

              <div v-show="expandedProjectIds.includes(saeProjects[0].id)" class="sae-details">
                <div class="detail-grid">
                  <div>
                    <h4>Objectif</h4>
                    <p>{{ saeProjects[0].objective }}</p>
                  </div>
                  <div>
                    <h4>Ce que j’ai réalisé</h4>
                    <ul>
                      <li v-for="task in saeProjects[0].tasks" :key="task">{{ task }}</li>
                    </ul>
                  </div>
                  <div>
                    <h4>Compétences techniques</h4>
                    <ul>
                      <li v-for="skill in saeProjects[0].technical" :key="skill">{{ skill }}</li>
                    </ul>
                  </div>
                  <div>
                    <h4>Ce que le projet m’a apporté</h4>
                    <p>{{ saeProjects[0].learning }}</p>
                  </div>
                </div>

                <div class="project-conclusion">
                  <div>
                    <strong>Preuves mobilisables</strong>
                    <p>{{ saeProjects[0].evidence }}</p>
                  </div>
                  <div>
                    <strong>Point à consolider</strong>
                    <p>{{ saeProjects[0].improvement }}</p>
                  </div>
                </div>
              </div>
            </div>
          </article>

          <div class="all-projects-heading" data-reveal>
            <div>
              <p class="section-number">Toutes mes autres SAÉ</p>
              <h3>Des projets complémentaires</h3>
            </div>
            <p>Chaque carte peut être ouverte pour afficher l’objectif, mon travail et les acquis.</p>
          </div>

          <div class="sae-projects-grid">
            <article
              v-for="project in saeProjects.slice(1)"
              :key="project.id"
              class="sae-project-card"
              data-reveal
            >
              <div class="sae-project-image">
                <img :src="project.image" :alt="`Aperçu du projet ${project.title}`" />
                <span>{{ project.semester }}</span>
              </div>

              <div class="sae-project-body">
                <p class="card-kicker">{{ project.type }}</p>
                <h3>{{ project.title }}</h3>
                <p class="project-summary">{{ project.summary }}</p>

                <div class="tag-list">
                  <span v-for="tag in project.tags" :key="tag">{{ tag }}</span>
                </div>

                <button
                  class="details-button"
                  type="button"
                  :aria-expanded="expandedProjectIds.includes(project.id)"
                  @click="toggleProject(project.id)"
                >
                  {{ expandedProjectIds.includes(project.id) ? 'Masquer le détail' : 'Ouvrir la fiche' }}
                  <span aria-hidden="true">{{ expandedProjectIds.includes(project.id) ? '−' : '+' }}</span>
                </button>

                <div v-show="expandedProjectIds.includes(project.id)" class="sae-details compact-details">
                  <div class="compact-detail-block">
                    <h4>Objectif</h4>
                    <p>{{ project.objective }}</p>
                  </div>

                  <div class="compact-detail-block">
                    <h4>Ce que j’ai réalisé</h4>
                    <ul>
                      <li v-for="task in project.tasks" :key="task">{{ task }}</li>
                    </ul>
                  </div>

                  <div class="compact-detail-block">
                    <h4>Ce que ce projet m’a apporté</h4>
                    <p>{{ project.learning }}</p>
                  </div>

                  <div class="compact-detail-block">
                    <h4>Point à consolider</h4>
                    <p>{{ project.improvement }}</p>
                  </div>
                </div>
              </div>
            </article>
          </div>
        </div>
      </section>

      <section id="stage" class="section section-alt section-observed">
        <div class="container">
          <header class="section-header" data-reveal>
            <p class="section-number">06 · Expérience professionnelle</p>
            <h2>Ce que mon stage chez Safran a changé</h2>
            <p>
              Le stage m’a permis de confronter mes acquis universitaires à un environnement métier,
              à un code existant et à des utilisateurs réels.
            </p>
          </header>

          <div class="stage-layout">
            <article class="stage-main" data-reveal>
              <div class="stage-heading">
                <div>
                  <p class="card-kicker">Stage développeur informatique</p>
                  <h3>Safran · outils internes et données métier</h3>
                </div>
                <span class="stage-badge">BUT 2</span>
              </div>

              <p>
                J’ai participé au développement et à l’évolution d’outils internes permettant de
                faciliter l’accès, le traitement et l’exploitation de données métier. J’ai travaillé
                avec WinDev, WebDev, le WLangage et SQL Server, dans un contexte où il fallait d’abord
                comprendre l’existant avant de proposer une modification.
              </p>

              <div class="stage-columns">
                <div>
                  <h4>Ce que j’ai appris</h4>
                  <ul class="clean-list">
                    <li>Analyser un besoin avant de coder.</li>
                    <li>Prendre en main rapidement des outils propriétaires.</li>
                    <li>Adapter mon code aux pratiques et aux attentes de l’équipe.</li>
                    <li>Présenter un résultat, recevoir un retour et le corriger.</li>
                  </ul>
                </div>
                <div>
                  <h4>Difficulté surmontée</h4>
                  <p>
                    Le transfert des activités de Collins Aerospace vers Safran a retardé certains
                    accès techniques au début du stage. J’ai utilisé cette période pour me documenter,
                    comprendre l’environnement et préparer les premières tâches afin de rester actif
                    malgré les contraintes d’infrastructure.
                  </p>
                </div>
              </div>
            </article>

            <aside class="stage-impact" data-reveal>
              <p class="section-number">Impact sur mon orientation</p>
              <h3>Le code prend son sens lorsqu’il répond à un usage.</h3>
              <p>
                Cette expérience a renforcé mon intérêt pour les applications qui traitent des données
                réelles et qui doivent rester compréhensibles, maintenables et utiles dans la durée.
                Elle m’a aussi montré que je dois continuer à progresser en tests, documentation et
                déploiement, trois dimensions essentielles pour évoluer ensuite vers le MLOps.
              </p>

              <div class="confidential-note">
                <strong>Respect de la confidentialité</strong>
                <p>
                  Les exemples présentés restent volontairement généraux. Les preuves ajoutées au
                  portfolio doivent être anonymisées et ne contenir aucune donnée interne.
                </p>
              </div>
            </aside>
          </div>
        </div>
      </section>

      <section id="evolution" class="section section-observed">
        <div class="container">
          <header class="section-header" data-reveal>
            <p class="section-number">07 · Conclusion et évolution</p>
            <h2>Du BUT 1 au BUT 2 : une progression visible</h2>
            <p>
              Cette année m’a fait passer d’une logique d’apprentissage des outils à une logique de
              réalisation, de justification et d’amélioration continue.
            </p>
          </header>

          <div class="evolution-grid">
            <article class="evolution-card before" data-reveal>
              <span>BUT 1</span>
              <h3>Apprendre les bases</h3>
              <ul class="clean-list">
                <li>Écrire mes premiers programmes structurés.</li>
                <li>Découvrir le développement web et SQL.</li>
                <li>Travailler en équipe sur des projets guidés.</li>
                <li>Présenter un résultat principalement technique.</li>
              </ul>
            </article>

            <article class="evolution-card after" data-reveal>
              <span>BUT 2</span>
              <h3>Construire, expliquer et fiabiliser</h3>
              <ul class="clean-list">
                <li>Reprendre et faire évoluer une application existante.</li>
                <li>Relier logique métier, backend, API et base de données.</li>
                <li>Utiliser Git et une organisation collective plus rigoureuse.</li>
                <li>Adapter une solution à un contexte professionnel réel.</li>
              </ul>
            </article>
          </div>

          <div class="conclusion-panel" data-reveal>
            <div>
              <p class="section-number">Mes acquis pour la suite</p>
              <h3>Une base solide, mais encore beaucoup à approfondir</h3>
            </div>
            <p>
              Mes principaux points forts sont aujourd’hui ma capacité d’adaptation, ma progression
              en développement backend et en gestion de données, ainsi que mon sérieux dans le travail
              collectif. La bonne pratique que je veux conserver est de ne plus considérer une
              fonctionnalité comme terminée dès qu’elle fonctionne : elle doit aussi être comprise,
              testée, documentée et intégrée proprement. Ma prochaine étape est de renforcer ce socle
              en troisième année, puis de l’orienter vers les métiers de la data et du MLOps.
            </p>
          </div>
        </div>
      </section>

      <section id="contact" class="contact-section section-observed">
        <div class="container contact-inner" data-reveal>
          <div>
            <p class="section-number">08 · Contact</p>
            <h2>Échangeons autour d’un stage, d’une alternance ou d’un projet.</h2>
          </div>

          <div class="contact-actions">
            <a href="mailto:redwandjedia23@gmail.com" class="btn btn-light">Me contacter</a>
            <a href="https://github.com/Redwan9528" target="_blank" rel="noreferrer" class="btn btn-outline-light">
              GitHub
            </a>
            <a href="https://linkedin.com/in/redwan-djedia" target="_blank" rel="noreferrer" class="btn btn-outline-light">
              LinkedIn
            </a>
          </div>
        </div>
      </section>
    </main>

    <footer class="footer">
      <div class="container footer-inner">
        <div>
          <strong>Redwan DJEDIA</strong>
          <p>Portfolio S4 · BUT Informatique · IUT de Villetaneuse</p>
        </div>
        <p>© {{ currentYear }} · Développé avec Vue.js</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from 'vue'

const isMenuOpen = ref(false)
const isScrolled = ref(false)
const activeSection = ref('accueil')
const expandedProjectIds = ref([1])

const currentYear = new Date().getFullYear()
const baseUrl = import.meta.env.BASE_URL
const cvUrl = `${baseUrl}REDWAN-DJEDIA-CV.pdf`

let revealObserver = null
let sectionObserver = null

const navItems = [
  { id: 'accueil', label: 'Accueil', href: '#accueil' },
  { id: 'parcours', label: 'Parcours', href: '#parcours' },
  { id: 'projet-professionnel', label: 'Projet pro', href: '#projet-professionnel' },
  { id: 'competences', label: 'Compétences', href: '#competences' },
  { id: 'sae', label: 'SAÉ', href: '#sae' },
  { id: 'stage', label: 'Stage', href: '#stage' },
  { id: 'evolution', label: 'Évolution', href: '#evolution' },
  { id: 'contact', label: 'Contact', href: '#contact' }
]

const journey = [
  {
    period: 'BUT 1',
    title: 'Découvrir les fondamentaux',
    text: 'Programmation, algorithmique, web, bases de données et premiers projets collectifs.'
  },
  {
    period: 'BUT 2',
    title: 'Travailler sur une application complète',
    text: 'Architecture MVC, API, traitements de données, Git et évolution du projet Mnémosyne.'
  },
  {
    period: 'Stage',
    title: 'M’adapter à un environnement professionnel',
    text: 'Prise en main de WinDev, WebDev, WLangage et SQL Server au sein de Safran.'
  },
  {
    period: 'Suite du parcours',
    title: 'Me spécialiser progressivement',
    text: 'Renforcer le développement et la data avant d’évoluer vers l’IA et le MLOps.'
  }
]

const careerPlan = [
  {
    index: '01',
    label: 'À court terme',
    title: 'Consolider mon socle technique',
    text: 'Je veux renforcer mes compétences en développement backend, en bases de données et en Python, tout en améliorant mes pratiques de test et de documentation.'
  },
  {
    index: '02',
    label: 'Après le BUT',
    title: 'Poursuivre vers une formation orientée IA, data ou cloud',
    text: 'Je souhaite intégrer une formation qui consolide le développement logiciel tout en ouvrant vers le Machine Learning, le cloud et le déploiement.'
  },
  {
    index: '03',
    label: 'À long terme',
    title: 'Évoluer vers le MLOps ou le Machine Learning',
    text: 'Je souhaite contribuer à la mise en production, au suivi et à la fiabilisation de modèles utilisés dans des applications réelles.'
  }
]

const qualities = [
  {
    icon: '01',
    title: 'Curiosité technique',
    definition: 'J’aime comprendre un nouvel outil plutôt que de rester limité aux technologies déjà connues.',
    proof: 'Chez Safran, j’ai dû découvrir WinDev, WebDev et le WLangage, puis comparer les pratiques de SQL Server avec celles de PostgreSQL utilisées en formation.'
  },
  {
    icon: '02',
    title: 'Autonomie',
    definition: 'Je sais rechercher une information, tester plusieurs pistes et avancer sans attendre une solution toute faite.',
    proof: 'Au début du stage, certains accès étaient retardés. J’ai utilisé la documentation PC SOFT et des ressources techniques pour préparer la prise en main de l’environnement.'
  },
  {
    icon: '03',
    title: 'Esprit d’équipe',
    definition: 'Je veille à rendre mon travail compréhensible et compatible avec celui des autres membres du projet.',
    proof: 'Sur Mnémosyne, j’ai travaillé avec un dépôt Git partagé, une répartition des tâches et des échanges réguliers pour intégrer les évolutions sans bloquer l’équipe.'
  },
  {
    icon: '04',
    title: 'Rigueur',
    definition: 'Je vérifie les données et le comportement d’une fonctionnalité avant de considérer le travail comme terminé.',
    proof: 'Lors des imports de données de Mnémosyne, j’ai contrôlé les comptages, recherché les doublons et corrigé les incohérences avant d’exploiter les cohortes.'
  }
]

const competencies = [
  {
    code: 'C1',
    title: 'Réaliser un développement d’application',
    level: 'Acquis confirmé',
    summary: 'Je peux participer au développement d’une application web structurée, du besoin jusqu’à l’intégration d’une fonctionnalité.',
    proof: 'Développement sur Mnémosyne avec PHP, architecture MVC, services métier, API REST et interface web.',
    progress: 'Mieux automatiser les tests et approfondir les frameworks backend modernes.'
  },
  {
    code: 'C2',
    title: 'Optimiser des applications informatiques',
    level: 'En consolidation',
    summary: 'Je sais analyser un traitement, corriger une logique et chercher une solution plus claire ou plus fiable.',
    proof: 'Évolution des filtres de cohortes, correction de requêtes et gestion de scénarios transformant certains statuts en réussite.',
    progress: 'Mesurer les performances, écrire davantage de tests unitaires et réduire la dette technique.'
  },
  {
    code: 'C3',
    title: 'Administrer des systèmes communicants',
    level: 'Socle fonctionnel',
    summary: 'Je maîtrise les bases nécessaires pour installer, utiliser et dépanner un environnement de développement.',
    proof: 'Utilisation de Linux et du shell, configuration locale des projets, gestion de versions et déploiement du portfolio sur GitHub Pages.',
    progress: 'Approfondir Docker, les réseaux et l’administration d’environnements de production.'
  },
  {
    code: 'C4',
    title: 'Gérer des données de l’information',
    level: 'Point fort',
    summary: 'Je sais modéliser, importer, contrôler et interroger des données relationnelles pour répondre à un besoin métier.',
    proof: 'Traitement des données Skodoc, modélisation MySQL, imports JSON, dédoublonnage et génération de données de cohortes.',
    progress: 'Approfondir l’optimisation SQL, les volumes importants et les pipelines de données.'
  },
  {
    code: 'C5',
    title: 'Conduire un projet',
    level: 'En progression',
    summary: 'Je sais découper un objectif, suivre les tâches et ajuster le travail en fonction des difficultés rencontrées.',
    proof: 'Planification des évolutions de Mnémosyne, messages de commit explicites, suivi des fonctionnalités et adaptation aux contraintes du stage.',
    progress: 'Utiliser plus systématiquement des indicateurs, des estimations et une gestion formalisée des risques.'
  },
  {
    code: 'C6',
    title: 'Collaborer au sein d’une équipe informatique',
    level: 'Acquis confirmé',
    summary: 'Je sais communiquer sur mon avancement, partager du code et intégrer les retours d’autres personnes.',
    proof: 'Travail en équipe sur Mnémosyne et échanges réguliers avec la tutrice et les collaborateurs de Safran lors des réunions de suivi.',
    progress: 'Pratiquer davantage la revue de code et la documentation collective.'
  }
]

const saeProjects = [
  {
    id: 1,
    number: '01',
    type: 'SAÉ principale · BUT 2',
    semester: 'Semestres 3 et 4',
    title: 'Mnémosyne – Application web de suivi des parcours étudiants',
    summary: 'Application web permettant de visualiser les parcours et les formations des étudiants à partir de données issues de Skodoc.',
    objective: 'Faire évoluer une application web complète afin de structurer, importer et exploiter les données nécessaires au suivi des étudiants, des formations, des parcours et des cohortes.',
    tasks: [
      'Analyse de l’architecture existante organisée autour des contrôleurs, services, modèles, vues et de la base de données.',
      'Développement backend en PHP avec une architecture MVC et des services métier.',
      'Conception et évolution de la base de données, import de données JSON issues de Skodoc et contrôle des données insérées.',
      'Développement des cohortes, des filtres et de règles métier liées aux statuts de réussite.',
      'Intégration des fonctionnalités dans un dépôt Git commun et vérification du fonctionnement de l’application.'
    ],
    technical: [
      'PHP, architecture MVC et API REST.',
      'MySQL, modélisation relationnelle et requêtes SQL.',
      'Import et traitement de données JSON.',
      'Git, GitHub, branches, commits et intégration.'
    ],
    learning: 'Ce projet m’a permis de comprendre le fonctionnement d’une application web complète. Il m’a aussi appris l’importance de l’architecture logicielle, de la qualité du code, de la fiabilité des données et de la coordination dans un projet collectif.',
    evidence: 'Dépôt GitHub, organisation du code, historique des commits, captures de l’application, schéma de base de données et requêtes de contrôle des imports.',
    improvement: 'Mettre en place davantage de tests automatisés et documenter plus précisément les règles métier afin de faciliter les prochaines évolutions.',
    github: 'https://github.com/Mnemosyne-S301/Mnemosyne',
    image: `${baseUrl}images/mnemosyne-1.png`,
    tags: ['PHP', 'MVC', 'API REST', 'MySQL', 'JSON', 'Git']
  },
  {
    id: 2,
    number: '02',
    type: 'SAÉ · Programmation orientée objet',
    semester: 'BUT 1',
    title: 'Jeu d’échecs en Java',
    summary: 'Conception et réalisation d’un jeu d’échecs en utilisant la programmation orientée objet et la modélisation UML.',
    objective: 'Développer un jeu d’échecs fonctionnel en représentant les pièces, l’échiquier, les déplacements et les principales règles du jeu.',
    tasks: [
      'Modélisation des classes et des relations entre les différents éléments du jeu.',
      'Programmation des pièces et de leurs déplacements spécifiques.',
      'Mise en place de la logique métier et vérification des règles.',
      'Utilisation de Git pour organiser les différentes étapes du développement.'
    ],
    technical: ['Java', 'Programmation orientée objet', 'UML', 'Git'],
    learning: 'Ce projet m’a permis de mieux comprendre l’importance de la conception avant le développement. J’ai appris à découper un problème complexe en classes ayant chacune une responsabilité précise.',
    evidence: 'Diagrammes UML, code Java, historique Git et démonstration du fonctionnement du jeu.',
    improvement: 'Ajouter davantage de tests automatisés pour contrôler les déplacements particuliers et les situations limites.',
    image: 'https://images.unsplash.com/photo-1528819622765-d6bcf132f793?w=1200&h=800&fit=crop',
    tags: ['Java', 'POO', 'UML', 'Git']
  },
  {
    id: 3,
    number: '03',
    type: 'SAÉ · Algorithmique',
    semester: 'BUT 1',
    title: 'Simulation d’un réseau social en Python',
    summary: 'Projet Python permettant de simuler les interactions entre des utilisateurs et de manipuler différentes structures de données.',
    objective: 'Représenter un réseau d’utilisateurs, leurs relations et leurs interactions afin de mettre en pratique l’algorithmique et les structures de données.',
    tasks: [
      'Création des utilisateurs et représentation de leurs relations.',
      'Développement des fonctions permettant d’ajouter, rechercher et analyser des connexions.',
      'Choix de structures de données adaptées aux différents traitements.',
      'Tests des algorithmes sur plusieurs scénarios.'
    ],
    technical: ['Python', 'Algorithmique', 'Structures de données'],
    learning: 'J’ai mieux compris l’importance du choix des structures de données pour résoudre efficacement un problème et rendre un programme plus clair.',
    evidence: 'Code Python, jeux de données de test et résultats obtenus pour les différents scénarios.',
    improvement: 'Comparer les performances de plusieurs structures et ajouter une interface permettant de mieux visualiser le réseau.',
    image: 'https://images.unsplash.com/photo-1555949963-aa79dcee981c?w=1200&h=800&fit=crop',
    tags: ['Python', 'Algorithmique', 'Données']
  },
  {
    id: 4,
    number: '04',
    type: 'SAÉ · Bases de données',
    semester: 'BUT 1',
    title: 'Conception d’une base de données PostgreSQL',
    summary: 'Conception, modélisation et exploitation d’une base de données relationnelle à partir d’un besoin défini.',
    objective: 'Passer d’un besoin fonctionnel à une base relationnelle structurée, puis exploiter les données grâce à des requêtes SQL.',
    tasks: [
      'Identification des entités, des associations et des contraintes.',
      'Création du modèle de données et transformation en schéma relationnel.',
      'Création des tables et insertion des données.',
      'Écriture de requêtes SQL pour rechercher, filtrer et regrouper les informations.'
    ],
    technical: ['SQL', 'PostgreSQL', 'Modélisation', 'Schéma relationnel'],
    learning: 'J’ai compris qu’une base bien conçue facilite l’analyse, limite les incohérences et fiabilise les informations utilisées par une application.',
    evidence: 'Modèle de données, script de création, jeu d’insertion et requêtes SQL.',
    improvement: 'Approfondir l’optimisation des requêtes, les index et la gestion de volumes de données plus importants.',
    image: 'https://images.unsplash.com/photo-1544383835-bda2bc66a55d?w=1200&h=800&fit=crop',
    tags: ['SQL', 'PostgreSQL', 'Modélisation']
  }
]

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}

const toggleProject = projectId => {
  if (expandedProjectIds.value.includes(projectId)) {
    expandedProjectIds.value = expandedProjectIds.value.filter(id => id !== projectId)
    return
  }

  expandedProjectIds.value = [...expandedProjectIds.value, projectId]
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 24
}

const handleKeydown = event => {
  if (event.key === 'Escape') {
    closeMenu()
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
  window.addEventListener('keydown', handleKeydown)
  handleScroll()

  revealObserver = new IntersectionObserver(
    entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible')
          revealObserver?.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.12 }
  )

  document.querySelectorAll('[data-reveal]').forEach(element => {
    revealObserver?.observe(element)
  })

  sectionObserver = new IntersectionObserver(
    entries => {
      const visibleSections = entries
        .filter(entry => entry.isIntersecting)
        .sort((a, b) => b.intersectionRatio - a.intersectionRatio)

      if (visibleSections[0]?.target?.id) {
        activeSection.value = visibleSections[0].target.id
      }
    },
    {
      rootMargin: '-32% 0px -55% 0px',
      threshold: [0.05, 0.2, 0.5]
    }
  )

  document.querySelectorAll('.section-observed').forEach(section => {
    sectionObserver?.observe(section)
  })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
  window.removeEventListener('keydown', handleKeydown)
  revealObserver?.disconnect()
  sectionObserver?.disconnect()
})
</script>
