<script setup>
import { computed, defineProps } from "vue";

const props = defineProps({
  project: Object,
});

const imageUrl = computed(
  () => new URL(props.project.image, import.meta.url).href
);
</script>

<template>
  <div class="card project-card h-100">
    <img
      :src="imageUrl"
      class="card-img-top pt-3 img-fluid"
      :alt="project.title"
    />

    <div class="card-body d-flex flex-column">
      <h5 class="card-title">{{ project.title }}</h5>
      <p class="card-text flex-grow-1">{{ project.description }}</p>

      <a
        href="#"
        target="_blank"
        rel="noopener noreferrer"
        class="btn btn-primary mt-auto"
      >
        Click here!
      </a>
    </div>
  </div>
</template>

<style scoped>
.project-card {
  width: 300px;
}
</style>
