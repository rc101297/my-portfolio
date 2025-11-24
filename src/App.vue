<script setup>
import AboutMeComponent from "./components/AboutMeComponent.vue";
import ContactMeComponent from "./components/ContactMeComponent.vue";
import FooterComponent from "./components/FooterComponent.vue";
import NavbarComponent from "./components/NavbarComponent.vue";
import ProjectComponent from "./components/ProjectComponent.vue";
import ToolsComponent from "./components/ToolsComponent.vue";
</script>

<template>
  <NavbarComponent />
  <div>
    <AboutMeComponent />
    <ProjectComponent />
    <ToolsComponent />
    <ContactMeComponent />
  </div>
  <FooterComponent />
</template>

<style scoped>
</style>
