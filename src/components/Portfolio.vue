<template>
  <div class="container">
    <header role="banner">
      <nav role="navigation">
        <div class="navbar"
             id="navbar">
          <ul>
            <li><a href="#welcome-section"
                 class="nav active">Welcome</a></li>
            <li><a href="#projects-section"
                 class="nav">Projects</a></li>
            <li><a href="#contacts-section"
                 class="nav">Contacts</a></li>
          </ul>
        </div>
      </nav>
    </header>

    <main role="main">
      <div id="welcome-section"
           class="fullscreen bg-chocolate">
        <section id="welcome"
                 class="section">
          <h1 class="text-center show-on-scroll">
            <i class="fa fa-user-circle"
               aria-hidden="true"></i>Nicky Keyse</h1>
          <h2 class="text-center text-spaced show-on-scroll">Learning responsive accessible front end web developement.</h2>
        </section>
      </div>

      <div id="projects-section"
           class="fullscreen bg-slateblue">
        <section id="projects"
                 class="section">
          <div class="projects">
            <div class="project-tile">
              <a id="project-link"
                 href="https://codepen.io/taramouse/full/LZYGvX"
                 target="_blank">
                <img src="https://i.ibb.co/wYyg14m/local-weather.png"
                     alt="Local Weather"
                     class="thumbnail show-on-scroll">
                <p class="text-spaced">Local Weather Project</p>
              </a>
            </div>
            <div class="project-tile">
              <a href="https://codepen.io/taramouse/full/WxegOQ"
                 target="_blank">
                <img src="https://i.ibb.co/42wQpW8/quote-machine.png"
                     alt="Quote Machine"
                     class="thumbnail show-on-scroll">
                <p class="text-spaced">Quote Machine Project</p>
              </a>
            </div>
            <div class="project-tile">
              <a href="https://codepen.io/taramouse/full/YzKZVEa"
                 target="_blank">
                <img src="https://i.ibb.co/2cRP1XZ/tech-docs.png"
                     alt="Technical Document"
                     class="thumbnail show-on-scroll">
                <p class="text-spaced">Survey Form Project</p>
              </a>
            </div>
          </div>
        </section>
      </div>

      <div id="contacts-section"
           class="fullscreen bg-slategrey">
        <section id="contacts"
                 class="section">
          <div class="contacts">
            <!-- Social media links -->
            <a href="https://twitter.com/nkeyse"
               aria-label="My Twitter profile."
               target="_blank">
              <span class="fa-stack fa-3x"
                    style="vertical-align: top;">
                <i class="fa fa-circle fa-stack-2x"
                   aria-hidden="true"></i>
                <i class="fa fa-twitter fa-stack-1x"
                   aria-hidden="true"></i>
              </span>
            </a>

            <a href="https://uk.linkedin.com/in/nkeyse"
               aria-label="My LinkedIn Profile"
               target="_blank">
              <span class="fa-stack fa-3x"
                    style="vertical-align: top;">
                <i class="fa fa-circle fa-stack-2x"
                   aria-hidden="true"></i>
                <i class="fa fa-linkedin fa-stack-1x"
                   aria-hidden="true"></i>
              </span>
            </a>

            <a id="profile-link"
               href="https://github.com/taramouse"
               aria-label="My GitHub Profile"
               target="_blank">
              <span class="fa-stack fa-3x"
                    style="vertical-align: top;">
                <i class="fa fa-circle fa-stack-2x"
                   aria-hidden="true"></i>
                <i class="fa fa-github fa-stack-1x"
                   aria-hidden="true"></i>
              </span>
            </a>
          </div>
          <h2 class="text-center text-spaced show-on-scroll">Visit my profiles on the web for further information.</h2>
        </section>
      </div>
    </main>
    <footer role="contentinfo">
      <div class="footer">
        <p class="text-center">&copy; Nicky Keyse 2019</p>
        <p class="text-center">Special thanks to <a href="freecodecamp.org">freeCodeCamp</a> for their excellent
          corriculum</p>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  mounted () {
    this.setActiveNav()
    // use intersection observer to detect elements in the viewport.
    const setVisibleCallback = entries => {
      entries.forEach(function (entry) {
        if (entry.isIntersecting) {
          // console.log('Adding is-visible to ', entry.target)
          entry.target.classList.add('is-visible')
        } else {
          // console.log('Removing is-visible from ', entry.target)
          entry.target.classList.remove('is-visible')
        }
      })
    }

    let options = {
      root: null,
      threshold: 0.5
    }

    const observer = new IntersectionObserver(setVisibleCallback, options)

    const targets = document.querySelectorAll('.show-on-scroll')
    targets.forEach(function (target) {
      observer.observe(target)
    })
  },
  methods: {
    setActiveNav () {
      //  set active nav on scroll
      let mainNavLinks = document.querySelectorAll('.navbar ul li a')

      window.addEventListener('scroll', event => {
        let fromTop = window.scrollY

        mainNavLinks.forEach(link => {
          let section = document.querySelector(link.hash)
          let sectionOffsetTop = section.offsetTop - 40
          if (
            sectionOffsetTop <= fromTop &&
            sectionOffsetTop + section.offsetHeight > fromTop
          ) {
            link.classList.add('active')
          } else {
            link.classList.remove('active')
          }
        })
      })
    }
  }
}
</script>

<style>
</style>
