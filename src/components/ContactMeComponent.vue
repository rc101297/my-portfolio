<script setup>
import { onBeforeMount, onMounted, ref } from "vue";

import { Notyf } from "notyf";
import "notyf/notyf.min.css";

const notyf = new Notyf();

const WEB3FORMS_ACCESS_KEY = "69fc1022-7b4a-4bbb-996d-e6b7a0c6e6b5";

const subject = "New message from Portfolio Contact Form";

const name = ref("");
const email = ref("");
const message = ref("");

const isLoading = ref(false);

// function for submit form
const submitForm = async () => {
  if (!recaptchaToken.value) {
    notyf.error("Please verify that you are not a robot.");
    return;
  }
  isLoading.value = true;

  try {
    const response = await fetch("https://api.web3forms.com/submit", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Accept: "application/json",
      },
      body: JSON.stringify({
        access_key: WEB3FORMS_ACCESS_KEY,
        subject: subject,
        name: name.value,
        email: email.value,
        message: message.value,
      }),
    });
    const result = await response.json();

    if (result.data.subject) {
      console.log(result);

      isLoading.value = false;
      notyf.success("Message Sent!");
    }
  } catch (error) {
    console.log(error);

    isLoading.value = false;
    notyf.error("Failed to send message.");
  } finally {
    resetRecaptcha();
  }
};

const SITE_KEY = "6Lc_xREsAAAAAD8Y_AMJPjkMfEOXec5ONipUFRgs";
const recaptchaContainer = ref(null);
const recaptchaWidgetId = ref(null);
const recaptchaToken = ref("");

function onRecaptchaSucess(token) {
  recaptchaToken.value = token;
}

function onRecaptchaExpired() {
  recaptchaToken.value = "";
}

function renderRecaptcha() {
  if (!window.grecaptcha) {
    console.error("reCAPTCHA not loaded");
    return;
  }
  recaptchaWidgetId.value = window.grecaptcha.render(recaptchaContainer.value, {
    sitekey: SITE_KEY,
    size: "normal",
    callback: onRecaptchaSucess,
    "expired-callback": onRecaptchaExpired,
  });
}

function resetRecaptcha() {
  if (recaptchaWidgetId.value !== null) {
    window.grecaptcha.reset(recaptchaWidgetId.value);
    recaptchaToken.value = "";
  }
}

onMounted(() => {
  const interval = setInterval(() => {
    if (window.grecaptcha && window.grecaptcha.render) {
      renderRecaptcha();
      clearInterval(interval);
    }
  }, 100);
  onBeforeMount(() => {
    clearInterval(interval);
  });
});
</script>

<template>
  <!-- Contact Section -->
  <div class="container-fluid" id="contact">
    <h3 class="pt-5 pb-3 text-center">Contact</h3>
    <div class="row pb-5 gap-5 justify-content-center">
      <!-- Map -->
      <iframe
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3864.7621425560624!2d120.97501777573873!3d14.383169282361763!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3397d3dd599f41d5%3A0xcf4d2b72b0b2735c!2sSM%20City%20Molino!5e0!3m2!1sen!2sph!4v1756360118108!5m2!1sen!2sph"
        allowfullscreen=""
        loading="lazy"
        referrerpolicy="no-referrer-when-downgrade"
        class="col-12 col-lg-4 px-0"
      ></iframe>

      <!-- Contact Form -->
      <div class="col-12 col-lg-4">
        <div class="mx-auto" id="form-col">
          <form class="p-3 rounded">
            <div class="form-group">
              <label for="name">Name</label>
              <input
                type="text"
                class="form-control"
                id="name"
                placeholder="Full Name"
                required
                autocomplete
              />
            </div>
            <div class="form-group">
              <label for="email">Email Address</label>
              <input
                type="email"
                class="form-control"
                id="email"
                placeholder="name@example.com"
                required
                autocomplete
              />
            </div>
            <div class="form-group">
              <label for="message">Message</label>
              <textarea class="form-control" id="message" rows="7"></textarea>
            </div>
            <div class="d-flex justify-content-between mt-3 align-items-center">
              <div class="d-flex gap-2">
                <div class="icons">
                  <a
                    href="https://www.linkedin.com/"
                    target="_blank"
                    rel="noopener noreferrer"
                  >
                    <img
                      src="../assets/images/icons/linkedin.png"
                      class="img-fluid"
                      alt="linkedin logo"
                    />
                  </a>
                </div>
                <div class="icons">
                  <a
                    href="https://gitlab.com/"
                    target="_blank"
                    rel="noopener noreferrer"
                  >
                    <img
                      src="../assets/images/icons/gitlab.svg"
                      class="img-fluid"
                      alt="gitlab logo"
                    />
                  </a>
                </div>
                <div class="icons">
                  <a
                    href="https://github.com/"
                    target="_blank"
                    rel="noopener noreferrer"
                  >
                    <img
                      src="../assets/images/icons/github.png"
                      class="img-fluid"
                      alt="github logo"
                    />
                  </a>
                </div>
              </div>
              <button
                type="submit"
                class="submit-btn pl-5 pr-5"
                :disabled="isLoading"
              >
                {{ isLoading ? "Sending..." : "Submit" }}
              </button>

              <div class="d-flex justify-content-end mt-2">
                <div ref="recaptchaContainer"></div>
              </div>
            </div>
          </form>
        </div>
      </div>
      <!-- Contact Form End -->
    </div>
  </div>
  <!-- Contact Section End -->
</template>