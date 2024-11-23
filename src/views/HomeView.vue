<script setup>
import sliderBackground from '/images/slider_background.jpg'
import { onMounted } from 'vue'

import { modul } from '@/data.json'

function loadExternalScript(src) {
  return new Promise((resolve, reject) => {
    const script = document.createElement('script')
    script.src = src
    script.onload = () => {
      // console.log(`${src} loaded`)
      resolve()
    }
    script.onerror = () => {
      console.error(`${src} failed to load`)
      reject()
    }
    document.body.appendChild(script)
  })
}

// Lifecycle mounted untuk memuat semua script eksternal secara berurutan
onMounted(async () => {
  console.log(modul)
  const scripts = [
    // jQuery
    'js/jquery-3.2.1.min.js',
    'styles/bootstrap4/popper.js',
    'styles/bootstrap4/bootstrap.min.js',
    'plugins/greensock/TweenMax.min.js',
    'plugins/greensock/TimelineMax.min.js',
    'plugins/scrollmagic/ScrollMagic.min.js',
    'plugins/greensock/animation.gsap.min.js',
    'plugins/greensock/ScrollToPlugin.min.js',
    'plugins/OwlCarousel2-2.2.1/owl.carousel.js',
    'plugins/scrollTo/jquery.scrollTo.min.js',
    'plugins/easing/easing.js',
    'js/custom.js',
  ]

  for (const src of scripts) {
    try {
      await loadExternalScript(src)
    } catch {
      console.error(`Failed to load script: ${src}`)
    }
  }
})
</script>

<template>
  <main>
    <div class="home" style="height: 100vh">
      <div class="hero_slider_container">
        <div class="hero_slider owl-carousel">
          <!-- Hero Slide -->
          <div class="hero_slide">
            <div
              class="hero_slide_background"
              :style="{ backgroundImage: `url(${sliderBackground})` }"
            ></div>
            <div
              class="hero_slide_container d-flex flex-column align-items-center justify-content-center"
            >
              <div class="hero_slide_content text-center">
                <h1 data-animation-in="fadeInUp" data-animation-out="animate-out fadeOut">
                  Get your <span>Education</span> today!
                </h1>
              </div>
            </div>
          </div>

          <!-- Hero Slide -->
          <div class="hero_slide">
            <div
              class="hero_slide_background"
              :style="{ backgroundImage: `url(${sliderBackground})` }"
            ></div>
            <div
              class="hero_slide_container d-flex flex-column align-items-center justify-content-center"
            >
              <div class="hero_slide_content text-center">
                <h1 data-animation-in="fadeInUp" data-animation-out="animate-out fadeOut">
                  Get your <span>Education</span> today!
                </h1>
              </div>
            </div>
          </div>

          <!-- Hero Slide -->
          <div class="hero_slide">
            <div
              class="hero_slide_background"
              :style="{ backgroundImage: `url(${sliderBackground})` }"
            ></div>
            <div
              class="hero_slide_container d-flex flex-column align-items-center justify-content-center"
            >
              <div class="hero_slide_content text-center">
                <h1 data-animation-in="fadeInUp" data-animation-out="animate-out fadeOut">
                  Get your <span>Education</span> today!
                </h1>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="popular page_section">
      <div class="container">
        <div class="row">
          <div class="col">
            <div class="section_title text-center">
              <h1>Modul Terbaru</h1>
            </div>
          </div>
        </div>

        <div class="row course_boxes">
          <!-- Popular Course Item -->
          <div class="col-lg-4 course_box" v-for="(mdl, i) in modul" :key="i">
            <div class="card">
              <img class="card-img-top" :src="mdl.image" :alt="mdl.name" />
              <div class="card-body text-center">
                <div class="card-title">
                  <a :href="mdl.link">{{ mdl.name }}</a>
                </div>
                <!-- <div class="card-text">Adobe Guide, Layes, Smart Objects etc...</div> -->
              </div>
              <div class="price_box d-flex justify-content-around px-0 flex-row align-items-center">
                <div class="course_author_image">
                  <img class="img-fluid" :src="mdl.author_image" :alt="mdl.author_image" />
                </div>
                <div class="course_author_name">{{ mdl.author }} <span>Author</span></div>
              </div>
            </div>
          </div>

          <div class="col-12 d-flex justify-content-center pt-5">
            <div class="button button_line_1 text-center trans_200">
              <router-link to="/modul">Read More</router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
