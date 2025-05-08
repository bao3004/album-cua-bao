<template>
  <div class="wrap">
    <!-- Button that triggers the popup -->
    <button
      @click="showPopup = true"
      class="btn btn-primary btn-ghost btn-shine"
    >
      Read Me
    </button>

    <!-- Popup Modal -->
    <transition name="fade">
      <div v-if="showPopup" class="popup-overlay" @click="handleOverlayClick">
        <div class="popup-content">
          <button class="close-btn" @click="closePopup">&times;</button>
          <div class="popup-body">
            <div class="popup-text">
              <h2 class="popup-title">About this Album</h2>
              <div v-html="content" class="popup-message"></div>
              <button class="ok-btn" @click="closePopup">OK</button>
            </div>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "PopupComponent",
  props: {
    content: {
      type: String,
      default: "Default message! Replace this dynamically.",
    },
  },
  data() {
    return {
      showPopup: false,
    };
  },
  methods: {
    closePopup() {
      this.showPopup = false;
    },
    handleOverlayClick(event) {
      // Kiểm tra nếu click vào chính lớp phủ (không phải nội dung popup)
      if (event.target.classList.contains("popup-overlay")) {
        this.closePopup();
      }
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap");

* {
  font-family: "Inter", sans-serif;
}

.wrap {
  padding-top: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn {
  padding: 0.75rem 2rem;
  font-size: 1rem;
  background-color: #00bcd4;
  color: white;
  border: none;
  cursor: pointer;
  transition: background 0.3s;
}

.btn:hover {
  background-color: #0097a7;
}

.popup-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 999;
}

.popup-content {
  background-color: #ffffff;
  padding: 2rem;
  width: 90%;
  max-width: 480px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  position: relative;
  animation: scaleIn 0.35s ease forwards;
}

@keyframes scaleIn {
  0% {
    transform: scale(0.95);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

.popup-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: #333;
  text-align: center;
  margin-bottom: 1rem;
}

.popup-message {
  font-size: 1rem;
  color: #555;
  margin-bottom: 1.5rem;
  text-align: center;
}

.ok-btn {
  padding: 0.6rem 2rem;
  background-color: #00bcd4;
  color: white;
  border: none;
  cursor: pointer;
  transition: background 0.3s ease;
}

.ok-btn:hover {
  background-color: #0097a7;
}

.close-btn {
  position: absolute;
  top: 12px;
  right: 12px;
  color: red;
  border: none;
  width: 36px;
  height: 36px;
  font-size: 18px;
  line-height: 36px;
  text-align: center;
  cursor: pointer;
  transition: background 0.3s ease;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

@media (max-width: 500px) {
  .btn {
    padding: 0.5rem 1.2rem;
    font-size: 0.9rem;
  }

  .popup-content {
    padding: 1.5rem;
  }

  .ok-btn {
    padding: 0.5rem 1.5rem;
    font-size: 0.95rem;
  }
}
</style>

<!-- 
Cách sử dụng:
B1: import comp này vào 1 comp cha
B2: <Description1Comp v-bind:content="popupContent" /> 
B3: vào data trong script, thêm dòng dưới đây và đổi theo ý thích:
popupContent:
        "Change your popup",
-->
