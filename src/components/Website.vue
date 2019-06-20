<template>
  <div class="frame">
    <div class="container">
      <!-- Header section that expands the main section -->
      <div id="about--eddo--projects">
        <h2 class="expandable-button" id="about-button" v-on:click="toggleAboutSection">About</h2>
        <img style="-webkit-transform: scaleY(-1); transform: scaleY(-1);" alt="Vue logo" src="../assets/eddo-logo-recentered.png">
        <h2 class="expandable-button" id="projects-button" v-on:click="toggleProjectsSection">Projects</h2>
      </div>

      <!-- Main section that displays About Me and showcases my projects -->
      <div id="main-section">
        <div id="about-section">
          <h1>Hi, I'm Eddo, a software developer!</h1>
          <p>I am a recent USC graduate, majoring in Computer Science & Business Administration (CSBA).</p>
          <p>I believe in quick engineering, but also in great engineering. I understand that Rome cannot be built in a day, but I am quick to try and break things, but most importantly, <i>learn things</i>, as fast as I can.</p>
          <p>I have long been a believer in depth-first expertise: I know what I'm good at, what I'm not, and I continuously direct more resources to honing the things I am good at. Arguably, however, in the software scene these days, depth expertise derives from breadth expertise. Understanding this, I can easily venture out my comfort zones and experiment with trendy tools and keen to try new tools. For example, even though React.js is my frontend library of choice, this portfolio website itself is built with Vue.js, and I learn new things about Javascript everyday.</p>
          <p>Recently, I completely rewrote the backend of a tax credit management system, dealing with challenges such as database infrastructure management and integrating with legacy code. In the past, I contributed to an open-source platform for collecting air quality data.</p>
          <p>Currently, I am bringing my fullstack development skills and a keen sense for products to modernize a local florist ecommerce shop, as well as empowering its owners by writing admini software to help them work from home remotely.</p>

          <p>Thank you for reading my bio! Please feel free to browse through the projects I have done.</p>
        </div>
        <div id="projects-section">
          <div class="featured-project">
            <h1 class="projects-column-header">Featured Project</h1>
            <div class="featured-project-body">
              <img alt="Featured project image" v-bind:src="featuredProject.img">
              <div class="project-tags">
                <p class="project-tag" v-for="tag in featuredProject.tags">#{{ tag }}</p>
              </div>
              <h1 id="featured-project-title">{{ featuredProject.title }}</h1>
              <h5 id="featured-project-tagline">
                <i>"{{ featuredProject.tagline }}"</i>
              </h5>
              <p class="featured-project-description" v-for="line in featuredProject.descriptionLines">
                {{ line }}
              </p>
              <img alt="Featured project image" class="featured-project-screenshot" src="../assets/rd-screenshot.png">
            </div>
          </div>
          <div class="other-projects">
            <h1 class="projects-column-header">Other Projects</h1>
            <div class="other-projects-body">
              <div class="nonfeatured-singular-project" v-for="project in projects">
                <img class="nonfeatured-singular-project-image" alt="Project image" v-bind:src="project.img">
                <div class="nonfeatured-singular-project-text">
                  <h2 class="nonfeatured-singular-project-title" v-if="project.link">
                    <a target="_blank" class="nonfeatured-singular-project-link" v-bind:href="project.link">
                      {{ project.name }}
                      <i class="fa fa-link"></i>
                    </a>
                  </h2>
                  <h2 class="nonfeatured-singular-project-title" v-else>
                    {{ project.name }}
                  </h2>
                  <h5 class="nonfeatured-singular-project-subheader" v-bind:if="project.subheader">
                    {{ project.subheader }}
                  </h5>
                  <p>{{ project.description }}</p>
                  <div class="project-tags">
                    <p class="project-tag" v-for="tag in project.tags">#{{ tag }}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Footer section that offers my contact information -->
      <div id="contact-section">
        <div id="github--linkedin--resume">
          <a target="_blank" href="https://github.com/eddowh/">
            <i class="fa fa-github" aria-hidden="true"></i>
          </a>
          <a target="_blank" href="https://www.linkedin.com/in/eddowhintoso/">
            <i class="fa fa-linkedin" aria-hidden="true"></i>
          </a>
          <a target="_blank">
            <i class="fa fa-file-text-o" aria-hidden="true"></i>
          </a>
        </div>
        <br />
        <div id="email--phone">
          <li>
            <i class="fa fa-envelope-o" aria-hidden="true"></i>
            <a href="mailto:eddo.hintoso@gmail.com" target="_blank" rel="noopener">eddo.hintoso@gmail.com
            </a>
          </li>
          |
          <li>
            <i class="fa fa-phone" aria-hidden="true"></i>
            <a target="_blank" rel="noopener">(213) 275-8982
            </a>
          </li>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Website',
  props: {
    msg: String,
  },

  data () {
    return {
      windowHeight: 0,
      expanded: false,

      featuredProject: {
        title: "R&D Analyzer",
        tagline: "A tax credit management system for startups, by a startup. Here to help earn back every little penny if eligible to qualify for R&D.",
        descriptionLines: [
          "As part of my senior capstone project, I was on a team that completely rewrote the backend of a tax credit management system. We followed many modern development and project management practices to integrate a new internal API with the legacy frontend Vue.js code",
          "I have learned to be an extremely effective Django developer when it comes to building APIs. This capstone project allowed me to take on a lot of responsibility and I made sure to do things right. I take pride in the fact that I can say I can build a robust and secure API, driven by best practices such as JWT and test-driven development. I also learned a few things or two about PostgreSQL, having to deal with database modeling and migrations when developing with Django.",
          "Other aspects of the project included report generation, Stripe integration, account management, etc. See below for a screenshot of the project.",
        ],
        wip: true,
        img: "https://media.licdn.com/dms/image/C4E0BAQHDkf77vhwoZA/company-logo_200_200/0?e=2159024400&v=beta&t=NjPfPdSniEIT67QdEB7X6syPh-SepKJ7bMdVEQv5UCY",
        tags: ['fullstack', 'RestAPI', 'JS', 'Python', 'Django', 'Vue', 'Stripe'],
      },
      projects: [
        {
          name: "Portfolio Website",
          description: "What you're seeing right now! Built with Vue.js",
          wip: false,
          img: require("../assets/logo.png"),
          tags: ['HTML', 'CSS', 'JS', 'Flexbox', 'Vue'],
        },
        {
          name: "openkongqi (Open 空氣)",
          link: "https://github.com/gams/openkongqi",
          description: "An open-source platform that periodically scraps public air quality data. Inspired by OpenAQ",
          wip: false,
          img: "https://media.licdn.com/dms/image/C560BAQHwU1W-o4aRcg/company-logo_400_400/0?e=1568851200&v=beta&t=1fgqlL2ipJ0NRt1rnrPyGtVu6JnIc1yFWMcfz1x2jng",
          tags: ['scrapping', 'open-source', 'Python', 'Redis', 'InfluxDB'],
        },
        {
          name: "Statistical Study on Admittance to the Yelp Elite",
          link: "https://goo.gl/tCJLAt",
          description: "Want to become a Yelp Elite? A simple statistical study might convince you otherwise...",
          wip: false,
          img: "http://onelincoln.net/wp-content/uploads/2015/06/yelp-icon-square.png",
          tags: ['data-wrangling', 'data-sience', 'statistics', 'R'],
        },
        {
          name: "Sweet Leilani Florist",
          description: "Currently revamping the ecommerce site for a local florist shop in Hawaii.",
          wip: true,
          img: "https://d2fimg.com/sweet-leilani-florist-f246702us-1.jpg",
          tags: ['fullstack', 'Python', 'Django', 'React', 'system-design'], 
        },
      ]
    }
  },

  watch: {
    windowHeight(newHeight, oldHeight) {
      console.log('Window height changed to ' + newHeight);
      if (this.expanded) this.adjustMainSectionHeight();
    }
  },

  mounted () {
    this.$nextTick(() => {
      window.addEventListener('resize', () => {
        this.windowHeight = window.innerHeight;
      });
    })
  },

  methods: {
    adjustMainSectionHeight () {
      let mainSection = document.getElementById('main-section');
      let filledHeight = (
          window.innerHeight - 50 -  // make sure to include padding too
          document.querySelector('#about--eddo--projects').clientHeight -
          document.querySelector('#contact-section').clientHeight
        );
      mainSection.style.height = filledHeight + 'px';
    },

    expandMainSection () {
      let mainSection = document.getElementById('main-section');
      if (mainSection.clientHeight) {
        // mainSection.style.height = 0;
      }
      else {
        this.adjustMainSectionHeight();
        this.expanded = true;
      }
    },
    toggleAboutSection (evt) {
      this.expandMainSection();
      var aboutSection = document.getElementById('about-section');
      var projectsSection = document.getElementById('projects-section');

      projectsSection.style.display = 'none';
      aboutSection.style.display = 'block';
    },
    toggleProjectsSection (evt) {
      this.expandMainSection();
      var aboutSection = document.getElementById('about-section');
      var projectsSection = document.getElementById('projects-section');

      aboutSection.style.display = 'none';
      projectsSection.style.display = 'flex';
    },
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.frame {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.container {
  max-height: 100vh;
  width: 80vw;

  /* XXX: borders */
  border-color: cyan;
  border-width: 5px;
  border-style: solid;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
  color: rgb(51,51,51);
}

#about--eddo--projects {
  display: inline-flex;
  padding-top: 10px;
  padding-bottom: 25px;
  width: 100%;
  justify-content: center;
  height: 100%;

  /* XXX: borders */
  border-color: red;
  border-width: 0px;
  border-style: solid;
}

#eddo-logo {
  color: white;
  background-color: black;
  height: 160px;
  width: 160px;
  font-size: 80px;
  margin: 8px;

  display: flex;
  align-items: center;
  justify-content: center;
}

#about--eddo--projects img {
  height: 160px;
}

#about--eddo--projects
.expandable-button {
  font-size: 28px;
  padding: 0px 10px 0px 10px;
  margin-top: 0px;
  margin-bottom: 0px;
  width: 300px;

  color: black;

  display: flex;

  align-items: center;

  text-transform: uppercase;
  font-weight: 800;
}

#about-button {
  justify-content: flex-end;
}

#main-section {
  overflow: scroll;
  height: 0;
  -moz-transition: height .5s;
  -ms-transition: height .5s;
  -o-transition: height .5s;
  -webkit-transition: height .5s;
  transition: height .5s;

  /* XXX: borders
  border-color: green;
  border-width: 10px;
  border-style: solid;
  */
}

#main-section h3 {
  margin: 0px 0px 0px 0px;

  /* XXX: borders */
  border-color: purple;
  border-width: 1px;
  border-style: solid;
}

#about-section {
  display: none;
}

#about-section p {
  text-align: left;
  padding-left: 10vw;
  padding-right: 10vw;
}

#projects-section {
  display: flex;
  flex-flow: column wrap;
  height: 100%;
  max-height: 100%;
}

.projects-column-header {
  text-align: left;
  text-decoration: underline;
  margin-top: 0px;
  margin-bottom: 0px;

  /* XXX: borders */
  border-color: cyan;
  border-width: 5px;
  border-style: solid;
}

.featured-project {
  height: 100%;
  width: 50%;
}

.featured-project > div {

  /* XXX: borders */
  border-color: orange;
  border-width: 1px;
  border-style: solid;
}

.featured-project-body {
  padding-top: 20px;
  width: 85%;
  /*
  display: flex;
  flex-flow: row wrap;
  justify-content: flex-start;
  */

  /* XXX: borders */
  border-color: orange;
  border-width: 1px;
  border-style: solid;
}

.featured-project-body > * {
  display: flex;
  align-content: flex-start;
  text-align: left;

  /* XXX: borders */
  border-color: purple;
  border-width: 1px;
  border-style: solid;
}

#featured-project-title {
  margin-bottom: 0px;
}

#featured-project-tagline {
  margin-top: 0px;
  margin-bottom: 0px;
  text-align: left;
}

.featured-project-screenshot {
  max-width: 100%;
}

.other-projects {
  width: 50%;
  height: 100%;
  overflow: scroll;

  /* XXX: borders */
  border-color: orange;
  border-width: 1px;
  border-style: solid;
}

.other-projects-body {
  padding-top: 20px;
  display: flex;
  flex-flow: row wrap;
}

.nonfeatured-singular-project {
  display: flex;
  width: 100%;

  margin-bottom: 30px;

  /* XXX: borders */
  border-color: red;
  border-width: 1px;
  border-style: solid;
}

.nonfeatured-singular-project-image {
  width: 120px;
  height: 120px;

  /* XXX: borders */
  border-color: blue;
  border-width: 1px;
  border-style: solid;
}

.nonfeatured-singular-project-text {
  flex-grow: 3;
  height: 100%;
  text-align: left;
  padding-left: 12px;

  margin-top: 0px;
  margin-bottom: 0px;

  /* XXX: borders */
  border-color: green;
  border-width: 1px;
  border-style: solid;
}

.nonfeatured-singular-project-text h2,h4,h5 {
  margin-top: 0px;
  margin-bottom: 0px;
}

.nonfeatured-singular-project-link {
  color: rgb(51, 51, 51);
  text-decoration: none;
}

.project-tags {
  display: flex;
  flex-flow: row wrap;
  justify-content: flex-start;
  overflow: scroll;

  /* XXX: borders */
  border-color: purple;
  border-width: 1px;
  border-style: solid;
}

.project-tag {
  font-size: 14px;
  margin: 0px 6px 0px 0px;
  padding: 4px 8px 4px 8px;
  border-radius: 12px;
  color: rgb(30,30,30);
  background-color: rgb(244, 209, 66),
}

#contact-section {
  letter-spacing: 0.2px;
  font-weight: bold;

  position: relative;
  padding-top: 25px;
  padding-bottom: 10px;

  /* XXX: borders */
  border-color: blue;
  border-width: 1px;
  border-style: solid;
}

#github--linkedin--resume .fa {
  font-size: 48px;
  margin-left: 8px;
  margin-right: 8px;
  color: black;
}

#email--phone .fa {
  padding-right: 8px;
}

@media only screen and (max-width: 1140px) {
  .container {
    width: 95vw;
  }

  .project-tag {
    font-size: 12px;
  }
}

@media only screen and (min-width: 1140px) {
  .container {
    width: 75vw;
  }
}

@media only screen and (min-width: 1600px) {
  .container {
    width: 60vw;
  }
}

@media only screen and (min-width: 1960px) {
  .container {
    width: 50vw;
  }
}

* {
  border-width: 0px !important;
}

</style>
