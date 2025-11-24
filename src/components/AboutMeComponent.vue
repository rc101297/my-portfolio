<script setup>
import Profile from "../assets/images/profile.jpg";
</script>

<template>
  <!-- Landing Page Section -->
  <div class="container-fluid py-5" id="landing">
    <div class="row align-items-center justify-content-center gap-3">
      <img
        :src="Profile"
        class="img-fluid col-lg-3 rounded-circle"
        id="profile"
        alt="Profile Picture"
      />
      <div
        class="col-lg-6 text-center mt-5 mt-lg-0 text-lg-start"
        id="about-text"
      >
        <h1>Rowena Cornejo-Cortel</h1>
        <h2>Full Stack Web Developer</h2>
        <p class="pt-2">
          Hi, I'm <strong>Wena</strong>, a Full Stack Web Developer with
          experience in building scalable and user-friendly web applications. I
          work with both front-end and back-end technologies, specializing in
          <strong>Html, CSS, JavaScript, React, Node.js, etc.</strong>.
        </p>
        <p>
          My passion lies in creating seamless user experiences and efficient,
          maintainable code. I'm always eager to learn and take on new
          challenges to deliver impactful digital solutions.
        </p>
        <div class="justify-content-center">
          <a href="../assets/files/Resume.pdf" download="Resume.pdf">
            <img
              src="../assets/images/icons/download.png"
              class="img-fluid"
              alt="Download Resume"
            />
          </a>
          <p class="d-lg-flex" id="download">Get My Resume Here!</p>
        </div>
      </div>
    </div>
  </div>
  <!-- Landing Page Section End -->
</template>

<style scoped>
/* Landing Page */
#landing {
  background: #4d8d74;
  color: #ffffff;
}

#profile {
  height: 450px;
  width: 400px;
}

#about-text h1 {
  font-family: "Merriweather";
  font-weight: bolder;
  font-size: 40px !important;
}

#about-text h2 {
  font-family: "Merriweather";
  font-weight: bolder;
  font-size: 30px !important;
}

#about-text p {
  font-family: "Merriweather";
  font-size: 18px !important;
}

#about-text img {
  width: 50px;
  height: 50px;
}

#download {
  font-family: "Merriweather";
  color: #1cd0c6;
  justify-content: center;
}
</style>