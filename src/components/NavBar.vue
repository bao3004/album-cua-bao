<template>
  <div class="wrapper">
    <div class="top-section" :class="{ shrink: isShrunk }">
      <div class="logo" :class="{ shrink: isShrunk }" @click="navigateToHome">
        HFKSUE123
      </div>
      <nav class="navbar" :class="{ shrink: isShrunk }">
        <router-link to="/" @click="closeDropdown">Home</router-link>
        <router-link to="/profile" @click="closeDropdown">About Me</router-link>
        <router-link to="/albuminfo" @click="closeDropdown"
          >Gallery</router-link
        >
        <router-link to="/feedback" @click="closeDropdown"
          >Feedback</router-link
        >
      </nav>
      <div
        class="toggle-btn"
        :class="{ open: isDropdownOpen, isShrunk: isShrunk }"
        @click="toggleDropdown"
      >
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
      </div>

      <!-- Dropdown with logo, blur, and footer text -->
      <div class="dropdown" :class="{ open: isDropdownOpen }">
        <div
          class="blur-background"
          v-if="isDropdownOpen"
          @click="closeDropdown"
        ></div>
        <div class="dropdown-logo">HFKSUE123</div>
        <router-link to="/" @click="closeDropdown">Home</router-link>
        <router-link to="/profile" @click="closeDropdown">About Me</router-link>
        <router-link to="/albuminfo" @click="closeDropdown"
          >Gallery</router-link
        >
        <router-link to="/feedback" @click="closeDropdown"
          >Feedback</router-link
        >
        <div class="dropdown-footer">©2024 hfksue123</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isDropdownOpen: false,
      isShrunk: false,
    };
  },
  methods: {
    navigateToHome() {
      this.$router.push("/home");
    },
    toggleDropdown() {
      this.isDropdownOpen = !this.isDropdownOpen;
    },
    closeDropdown() {
      this.isDropdownOpen = false;
    },
    handleScroll() {
      this.isShrunk = window.scrollY > 50;
    },
  },
  mounted() {
    document.addEventListener("click", (event) => {
      if (!this.$el.contains(event.target) && this.isDropdownOpen) {
        this.closeDropdown();
      }
    });
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
  },
};
</script>

<style scoped src="../css/NavBar.css"></style>
