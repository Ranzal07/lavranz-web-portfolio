
<template>
  <q-page class="portfolio-page">
    <q-header class="navbar">
      <q-toolbar class="navbar-inner">
        <a href="#home" class="logo">
          LAVRANZ<span>.</span>
        </a>

        <q-space />

        <div class="desktop-menu">
          <a href="#home" @click.prevent="scrollToSection('home')">Home</a>
          <a href="#about" @click.prevent="scrollToSection('about')">About</a>
          <a href="#skills" @click.prevent="scrollToSection('skills')">Skills</a>
          <a href="#projects" @click.prevent="scrollToSection('projects')">Projects</a>
          <a href="#experience" @click.prevent="scrollToSection('experience')">Experience</a>
          <a href="#education" @click.prevent="scrollToSection('education')">Education</a>
          <a href="#contact" class="contact-link" @click.prevent="scrollToSection('contact')">Contact</a>
        </div>

        <q-btn
          flat
          round
          icon="menu"
          class="mobile-menu"
          @click="menuOpen = !menuOpen"
        />
      </q-toolbar>

      <q-slide-transition>
        <div v-if="menuOpen" class="mobile-links">
          <a
            v-for="item in navItems"
            :key="item.id"
            :href="'#' + item.id"
            @click.prevent="scrollToSection(item.id)"
          >
            {{ item.label }}
          </a>
        </div>
      </q-slide-transition>
    </q-header>

    <section id="home" class="hero section-container">
      <div class="hero-content">
        <div class="availability">
          <span class="status-dot"></span>
          FULL-STACK DEVELOPER
        </div>

        <p class="eyebrow">HELLO, I'M</p>

        <h1>
          Lavranz<br />
          <span class="gradient-text">Tradio.</span>
        </h1>

        <h2>Building digital experiences from front to back.</h2>

        <p class="description">
          I'm a Full-Stack Developer passionate about creating
          modern, responsive, and user-friendly web applications.
          I enjoy turning ideas into meaningful digital solutions.
        </p>

        <div class="hero-buttons">
          <q-btn
            unelevated
            label="View My Projects"
            @click="scrollToSection('projects')"
            class="primary-btn"
          />

          <q-btn
            outline
            label="Contact Me"
            @click="scrollToSection('contact')"
            class="secondary-btn"
          />
        </div>
      </div>

      <div class="hero-profile">
        <div class="profile-avatar">
          <img src="/profile.jpg" alt="Lavranz Tradio" />
        </div>
        <h3>Lavranz Tradio</h3>
        <p>Full-Stack Developer</p>
        <div class="profile-line"></div>
        <span>Building. Learning. Creating.</span>
      </div>
    </section>

    <section id="about" class="section-container section-block">
      <div class="section-label">01 / ABOUT ME</div>
      <h2>Get to know <span class="gradient-text">me.</span></h2>

      <div class="content-card">
        <h3>Hi, I'm Lavranz!</h3>

        <p>
          I'm a Full-Stack Developer interested in building
          modern web & mobile applications, and digital solutions.
        </p>

        <p>
          I enjoy working on both frontend and backend
          development, solving technical problems, and
          learning new technologies.
        </p>

        <p>
          My goal is to create functional, responsive,
          and user-friendly applications.
        </p>
      </div>
    </section>

    <section id="skills" class="section-container section-block">
      <div class="section-label">02 / MY SKILLS</div>
      <h2>Technologies I <span class="gradient-text">use.</span></h2>

      <div class="skills-grid">
        <div
          v-for="group in skillGroups"
          :key="group.title"
          class="content-card"
        >
          <h3>{{ group.title }}</h3>

          <div class="skill-list">
            <span
              v-for="skill in group.skills"
              :key="skill"
              class="skill-chip"
            >
              {{ skill }}
            </span>
          </div>
        </div>
      </div>
    </section>

    <section id="projects" class="section-container section-block">
      <div class="section-label">03 / MY WORK</div>
      <h2>Featured <span class="gradient-text">projects.</span></h2>

      <div class="projects-grid">
        <div
          v-for="project in projects"
          :key="project.title"
          class="project-card"
        >
          <div class="project-preview">
            <span>{{ project.number }}</span>

            <img
              :src="project.image"
              :alt="project.title + ' preview'"
              :class="project.imageClass"
            />
          </div>

          <div class="project-info">
            <small>{{ project.category }}</small>
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>

            <div class="skill-list">
              <span
                v-for="tech in project.technologies"
                :key="tech"
                class="skill-chip"
              >
                {{ tech }}
              </span>
            </div>

            <div class="project-links">
              <a
                v-if="project.github"
                :href="project.github"
                target="_blank"
                rel="noopener"
              >
                GitHub ↗
              </a>

              <a
                v-if="project.demo"
                :href="project.demo"
                target="_blank"
                rel="noopener"
              >
                Live Demo ↗
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="experience" class="section-container section-block">
      <div class="section-label">04 / EXPERIENCE</div>
      <h2>My professional <span class="gradient-text">journey.</span></h2>

      <div class="timeline">
        <div
          v-for="experience in experiences"
          :key="experience.role"
          class="timeline-item"
        >
          <small>{{ experience.date }}</small>
          <h3>{{ experience.role }}</h3>
          <h4>{{ experience.company }}</h4>
          <ul class="experience-list">
            <li
              v-for="(item, index) in experience.description"
              :key="index"
            >
              {{ item }}
            </li>
          </ul>
        </div>
      </div>
    </section>

    <section id="education" class="section-container section-block">
      <div class="section-label">05 / EDUCATION</div>
      <h2>My academic <span class="gradient-text">background.</span></h2>

      <div class="content-card">
        <h3>{{ education.degree }}</h3>
        <h4>{{ education.school }}</h4>
        <p>{{ education.year }}</p>
        <p>{{ education.description }}</p>
      </div>
    </section>

    <section id="contact" class="section-container section-block">
      <div class="section-label">06 / CONTACT</div>
      <h2>Let's work <span class="gradient-text">together.</span></h2>

      <div class="contact-grid">
        <div>
          <h3>Have a project in mind?</h3>

          <p>
            Feel free to reach out. I'd love to hear about
            your ideas, projects, and opportunities.
          </p>

          <a :href="'mailto:' + contactEmail">
            {{ contactEmail }}
          </a>

		  <div class="social-links">
			  <a
			    :href="linkedInUrl"
			    target="_blank"
			    rel="noopener noreferrer"
			  >
			    LinkedIn ↗
			  </a>

			  <a
			    :href="githubUrl"
			    target="_blank"
			    rel="noopener noreferrer"
			  >
			    GitHub ↗
			  </a>
			</div>
        </div>

        <q-form @submit="sendMessage" class="contact-form">
          <q-input
            v-model="form.name"
            label="Your Name"
            dark
            outlined
            :rules="[val => !!val || 'Name is required']"
          />

          <q-input
            v-model="form.email"
            label="Your Email"
            type="email"
            dark
            outlined
            :rules="[
              val => !!val || 'Email is required',
              val => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(val) || 'Enter a valid email'
            ]"
          />

          <q-input
            v-model="form.subject"
            label="Subject"
            dark
            outlined
            :rules="[val => !!val || 'Subject is required']"
          />

          <q-input
            v-model="form.message"
            label="Message"
            type="textarea"
            dark
            outlined
            :rules="[val => !!val || 'Message is required']"
          />

          <q-btn
            type="submit"
            label="Send Message"
            class="primary-btn full-width"
          />
        </q-form>
      </div>
    </section>

    <footer class="footer">
      <h3>LAVRANZ<span>.</span></h3>
      <p>Designed and developed by Lavranz Tradio.</p>
      <p>© {{ currentYear }} All rights reserved.</p>
    </footer>
  </q-page>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'

const menuOpen = ref(false)
const currentYear = new Date().getFullYear()
const contactEmail = 'lavranztradio@gmail.com'
const linkedInUrl = 'https://www.linkedin.com/in/lavranz/'
const githubUrl = 'https://github.com/Ranzal07'

const navItems = [
  { label: 'Home', id: 'home' },
  { label: 'About', id: 'about' },
  { label: 'Skills', id: 'skills' },
  { label: 'Projects', id: 'projects' },
  { label: 'Experience', id: 'experience' },
  { label: 'Education', id: 'education' },
  { label: 'Contact', id: 'contact' }
]

const skillGroups = [
  {
    title: 'Programming Languages',
    skills: [
      'Java',
      'Python',
      'C',
      'JavaScript',
      'TypeScript',
      'Dart',
      'PHP'
    ]
  },
  {
    title: 'Backend Development & Frameworks',
    skills: [
      'Node.js',
      'Spring',
      'Spring Boot',
      'Grails',
      'Flask',
      'Django',
      'REST API',
      'API Integration',
      'Authentication',
      'JWT'
    ]
  },
  {
    title: 'Frontend & Mobile Development',
    skills: [
      'HTML5',
      'CSS3',
      'JavaScript',
      'Vue.js',
      'Quasar',
      'Flutter',
      'Responsive Web Design',
      'UI Development',
      'Mobile App Development'
    ]
  },
  {
    title: 'Databases & Data Management',
    skills: [
      'MySQL',
      'PostgreSQL',
      'Redis',
      'Firebase',
      'Database Design',
      'SQL',
      'Database Management'
    ]
  },
  {
    title: 'Git Version Control & Collaboration',
    skills: [
      'Git',
      'GitHub',
      'GitLab',
      'Version Control',
      'Team Collaboration'
    ]
  },
  {
    title: 'Monitoring & Visualization',
    skills: [
      'Grafana',
      'Application Monitoring',
      'Performance Monitoring',
      'Data Visualization'
    ]
  },
  {
    title: 'UI/UX Design & Modeling Tools',
    skills: [
      'Figma',
      'Lucidchart',
      'Wireframing',
      'Prototyping',
      'UI/UX Design',
      'System Modeling'
    ]
  },
  {
    title: 'Development Tools & Technologies',
    skills: [
      'VS Code',
      'Postman',
      'npm',
      'Maven',
      'Gradle',
      'JSON'
    ]
  },
  {
    title: 'Software Development Practices',
    skills: [
      'Object-Oriented Programming (OOP)',
      'MVC Architecture',
      'Debugging',
      'Software Testing',
      'Clean Code',
      'Agile Development'
    ]
  }
]

const projects = [
  {
    number: '01',
    visual: 'e-Trade',
    image: '/projects/etrade.png',
    imageClass: 'asset-tracker-image',
    category: 'FULL-STACK WEB APPLICATION',
    title: 'e-Trade',
    description: 'An e-Government Web Application System from CDEC (Cargo Data Exchange Center, Inc.) used for facilitating end to end e-commerce solutions linking trade & logistics service.',
    technologies: ['Groovy', 'JavaScript', 'Java', 'CSS', 'HTML', 'Grails', 'Spring', 'MySQL'],
    github: '',
    demo: 'https://www.etrade.net.ph/'
  },
  {
    number: '02',
    visual: 'PEZA',
    image: '/projects/peza.png',
    imageClass: '',
    category: 'FULL-STACK WEB APPLICATION',
    title: 'PEZA',
    description: 'An e-Government Web Application System used by PEZA (Philippine Economic Zone Authority) for managing import & export clearances and documentation.',
    technologies: ['JavaScript', 'Groovy', 'CSS', 'HTML', 'Java', 'Grails', 'Spring', 'MySQL'],
    github: '',
    demo: 'https://peza.etrade.net.ph/'
  },
  {
    number: '03',
    visual: 'WORKCONNECT',
    image: '/projects/workconnect.png',
    imageClass: '',
    category: 'FULL-STACK WEB DEVELOPMENT',
    title: 'WorkConnect',
    description: 'An internal administrative web application for monitoring the network connectivity status of 7-Eleven stores nationwide.',
    technologies: ['Spring Boot', 'Java', 'Python', 'Quasar', 'Vue.js', 'JavaScript', 'TypeScript', 'Redis', 'PostgreSQL'],
    github: '',
    demo: 'https://workconnect.apolloglobal.net/'
  },
  {
    number: '04',
    visual: 'Asset Tracker App',
    image: '/projects/asset-tracker-app.png',
    imageClass: '',
    category: 'FULL-STACK MOBILE APPLICATION',
    title: 'Asset Tracker App',
    description: 'A mobile application used for scanning and tracking assets and their whereabouts for efficient asset management, real-time monitoring, inventory control, and improved accountability.',
    technologies: ['Flutter', 'Dart', 'Spring Boot', 'Java', 'PostgreSQL', 'Firebase'],
    github: '',
    demo: ''
  }
]

const experiences = [
  {
    date: 'NOV 2023 - PRESENT',
    role: 'Software Developer',
    company: 'Apollotech Software Corporation',
    description: [
      'Develop and maintain three software applications, consisting of two web applications and one mobile application.',
      'Contribute to the development of eGovernment web systems and internal network monitoring system.',
      'Handle frontend and backend development, API integration, and database management.',
      'Perform bug fixing, troubleshooting, and application maintenance.',
      'Implement new features and improve system functionality, reliability, and performance.',
      'Collaborate with the development team to deliver and maintain software solutions.'
    ]
  }
]

const education = {
  degree: 'Bachelor of Science in Computer Science',
  school: 'Caraga State University',
  year: '2023',
  description: 'Graduated as Cum Laude, demonstrating strong academic performance'
}

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

function sendMessage() {
  const body = [
    `Name: ${form.name}`,
    `Email: ${form.email}`,
    '',
    form.message
  ].join('\n')

  const mailtoLink =
    `mailto:${contactEmail}?subject=${encodeURIComponent(form.subject)}&body=${encodeURIComponent(body)}`

  window.open(mailtoLink, '_blank')
}

function scrollToSection(id: string) {
  const section = document.getElementById(id)

  if (section) {
    const top = section.getBoundingClientRect().top + window.scrollY - 40

    window.scrollTo({ top, behavior: 'smooth' })
  }

  menuOpen.value = false
}
</script>
