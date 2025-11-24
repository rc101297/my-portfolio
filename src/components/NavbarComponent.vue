<script setup>
import logo from "/images/logo.png";
</script>


<template>
  <!-- Navbar Section -->
  <nav
    class="navbar navbar-expand-lg navbar-light position-relative"
    role="navigation"
    aria-label="Main navigation"
  >
    <div
      class="container-fluid d-flex justify-content-lg-center justify-content-end"
    >
      <a class="navbar-brand p-2" href="#landing" id="logo-link">
        <img :src="logo" id="logo" alt="Website Logo" />
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbar"
        aria-controls="navbar"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse flex-lg-grow-0" id="navbar">
        <ul class="navbar-nav gap-4">
          <li class="nav-item mt-3 mt-lg-0">
            <a class="nav-link active" aria-current="page" href="#landing"
              >Home</a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#projects">My Projects</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#tools">Tools</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#contact">Contact</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <!-- Navbar Section End -->
</template>

<style scoped>
/* Navbar */
nav {
  background: #1cd0c6 !important;
}
nav a {
  font-family: Montserrat;
  font-weight: bold;
  font-size: 24px;
  color: #ffffff !important;
}
#logo-link {
  height: 70px;
  width: 70px;
}

#logo {
  height: 46px;
  width: 70px;
}
</style>