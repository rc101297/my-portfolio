<script setup>
import ProjectCardComponent from "./ProjectCardComponent.vue";
import projects from "../data/projects.json";
import { computed } from "vue";

const chunkSize = 2;

const projectSlides = computed(() => {
  const slides = [];
  for (let i = 0; i < projects.length; i += chunkSize) {
    slides.push(projects.slice(i, i + chunkSize));
  }
  return slides;
});
console.log(projectSlides);
</script>

<template>
  <div class="container-fluid py-5 text-center" id="projects">
    <h3 class="mb-5">My Projects</h3>

    <div
      id="projectCarousel"
      class="carousel slide"
      data-bs-ride="carousel"
      data-bs-interval="false"
    >
      <div class="carousel-inner">
        <!-- Each slide -->
        <div
          class="carousel-item"
          v-for="(slide, index) in projectSlides"
          :key="index"
          :class="{ active: index === 0 }"
        >
          <div
            class="d-flex flex-sm-row flex-column align-items-center justify-content-center card-item"
          >
            <ProjectCardComponent
              v-for="project in slide"
              :key="project.id"
              :project="project"
            />
          </div>
        </div>
      </div>

      <!-- Controls -->
      <button
        class="carousel-control-prev"
        type="button"
        data-target="#projectCarousel"
        data-slide="prev"
      >
        <span class="carousel-control-prev-icon"></span>
      </button>

      <button
        class="carousel-control-next"
        type="button"
        data-target="#projectCarousel"
        data-slide="next"
      >
        <span class="carousel-control-next-icon"></span>
      </button>
    </div>
  </div>
</template>

<style scoped>
.card-item {
  gap: 30px;
}
</style>
