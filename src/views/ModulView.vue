<script setup>
import { modul } from '@/data.json'
</script>
<template>
  <main>
    <div class="home">
      <div class="home_background_container prlx_parent">
        <div
          class="home_background prlx"
          style="background-image: url(images/courses_background.jpg)"
        ></div>
      </div>
      <div class="home_content">
        <h1>Modul</h1>
      </div>
      <p class="text-capitalize">
        Modul Praktikum Digital berbasis codelabs untuk Jurusan rekayasa Perangkat Lunak,SMK
        ANTARTIKA 1 SIDOARJO
      </p>
    </div>

    <!-- Popular -->

    <div class="popular page_section">
      <div class="container">
        <div class="row">
          <div class="col">
            <div class="section_title text-center">
              <h1>List Modul</h1>
            </div>
          </div>
        </div>

        <div class="row course_boxes">
          <!-- Popular Course Item -->
          <div class="col-lg-4 course_box" v-for="(mdl, i) in modul" :key="i">
            <div class="card">
              <img class="card-img-top" :src="mdl.image" :alt="mdl.name" />
              <div class="card-body text-center">
                <div class="card-title mb-4">
                  <a :href="mdl.link">{{ mdl.name }}</a>
                </div>
                <div class="card-text">
                  Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto tempora unde nemo
                  debitis aliquid explicabo accusamus quos assumenda? Magni, debitis.
                </div>
              </div>
              <div class="price_box d-flex justify-content-around px-0 flex-row align-items-center">
                <div class="course_author_image">
                  <img class="img-fluid" :src="mdl.author_image" :alt="mdl.author_image" />
                </div>
                <div class="course_author_name">{{ mdl.author }} <span>Author</span></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
