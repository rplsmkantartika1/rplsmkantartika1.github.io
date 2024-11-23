<script setup>
import { computed, onMounted } from 'vue'
import { RouterLink, RouterView } from 'vue-router'

const sosmed = [
  {
    class: 'fab fa-whatsapp',
    link: 'https://wa.me/6281293920187',
  },
  {
    class: 'fab fa-instagram',
    link: 'https://www.instagram.com/smkantartika1sda/',
  },
  {
    class: 'fas fa-envelope',
    link: 'mailto:smks.antartika1.sda@gmail.com',
  },
  {
    class: 'fas fa-globe',
    link: 'https://www.smkantartika1sda.sch.id/',
  },
]

// Fungsi untuk memuat script eksternal secara sekuensial
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

const created = 2024

const createdYear = computed(() => {
  const currentYear = new Date().getFullYear()
  return currentYear == created ? created : created + ' - ' + currentYear
})
</script>

<template>
  <div class="super_container">
    <!-- Header -->

    <header class="header d-flex flex-row">
      <div class="header_content d-flex flex-row align-items-center">
        <!-- Logo -->
        <div class="logo_container">
          <div class="logo">
            <img src="/assets/images/logo-smartone-removebg-preview.png" alt="" />
            <!-- <span>course</span> -->
          </div>
        </div>

        <nav class="main_nav_container">
          <div class="main_nav">
            <ul class="main_nav_list">
              <li class="main_nav_item">
                <router-link active-class="active" to="/">Home</router-link>
              </li>
              <li class="main_nav_item">
                <router-link active-class="active" to="/modul">modul</router-link>
              </li>
            </ul>
          </div>
        </nav>
      </div>
      <!-- <div class="header_side d-flex flex-row justify-content-center align-items-center">
        <img src="/images/phone-call.svg" alt="" />
        <span>+43 4566 7788 2457</span>
      </div> -->

      <!-- Hamburger -->
      <div class="hamburger_container">
        <i class="fas fa-bars trans_200"></i>
      </div>
    </header>

    <!-- Menu -->
    <div class="menu_container menu_mm">
      <!-- Menu Close Button -->
      <div class="menu_close_container">
        <div class="menu_close"></div>
      </div>

      <!-- Menu Items -->
      <div class="menu_inner menu_mm">
        <div class="menu menu_mm">
          <ul class="menu_list menu_mm text-uppercase">
            <li class="menu_item menu_mm">
              <router-link active-class="active" to="/">Home</router-link>
            </li>
            <li class="menu_item menu_mm">
              <router-link active-class="active" to="/about">modul</router-link>
            </li>
          </ul>

          <!-- Menu Social -->

          <div class="menu_social_container menu_mm">
            <ul class="menu_social menu_mm">
              <li class="menu_social_item menu_mm" v-for="(item, i) in sosmed" :key="i">
                <a target="_blank" :href="item.link"><i :class="item.class"></i></a>
              </li>
            </ul>
          </div>

          <!-- <div class="menu_copyright menu_mm">Colorlib All rights reserved</div> -->
        </div>
      </div>
    </div>
    <router-view v-slot="{ Component }">
      <transition name="fade">
        <component :is="Component" />
      </transition>
    </router-view>

    <footer class="footer pt-0">
      <div class="container">
        <!-- Newsletter -->

        <!-- Footer Content -->

        <!-- Footer Copyright -->

        <div class="footer_bar d-flex flex-column flex-sm-row align-items-center">
          <div class="footer_copyright">
            <span
              ><!-- Link back to Colorlib can't be removed. Template is licensed under CC BY 3.0. -->
              Copyright &copy;
              <span v-text="createdYear"></span>
              All rights reserved
              <!-- Link back to Colorlib can't be removed. Template is licensed under CC BY 3.0. --></span
            >
          </div>
          <div class="footer_social ml-sm-auto">
            <ul class="menu_social">
              <li class="menu_social_item" v-for="(item, i) in sosmed" :key="i">
                <a target="_blank" :href="item.link"><i :class="item.class"></i></a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
/* Transition fade styles */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
