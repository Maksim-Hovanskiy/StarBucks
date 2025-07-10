<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const isMenuOpen = ref(false);
const isScrolled = ref(false);

// Обработка скролла для изменения стиля шапки
const handleScroll = () => {
  isScrolled.value = window.scrollY > 10;
};

// Анимация меню
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const closeMenu = (e) => {
  if (!e.target.closest(".nav-container") && !e.target.closest(".hamburger")) {
    isMenuOpen.value = false;
  }
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  document.addEventListener("click", closeMenu);
});

onBeforeUnmount(() => {
  window.removeEventListener("scroll", handleScroll);
  document.removeEventListener("click", closeMenu);
});
</script>

<template>
  <header :class="{ 'header-scrolled': isScrolled }">
    <div class="container">
      <div class="header__inner">
        <a class="header_logo" href="/">StarBucks</a>

        <button
          class="hamburger"
          :class="{ 'hamburger--active': isMenuOpen }"
          @click="toggleMenu"
          aria-label="Toggle menu"
        >
          <span></span>
          <span></span>
          <span></span>
        </button>

        <div
          class="nav-container"
          :class="{ 'nav-container--active': isMenuOpen }"
        >
          <nav>
            <ul>
              <li><a href="#" class="header_item_link">Home</a></li>
              <li><a href="#" class="header_item_link">Select</a></li>
              <li><a href="#" class="header_item_link">Shop</a></li>
            </ul>
          </nav>
        </div>
      </div>
    </div>
  </header>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  margin: 0 auto;
  padding: 0 130px;
}

header {
  margin-top: 48px;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
  margin-bottom: 120px;
}

.header-scrolled {
  margin-top: 0;
  padding: 15px 0;
  background: rgba(18, 21, 23, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
}

.header__inner {
  display: flex;
  align-items: center;
  gap: 95px;
  justify-content: space-between;
}

.header_logo {
  font-family: Montserrat;
  font-weight: 800;
  font-style: ExtraBold;
  font-size: 37.6px;
  text-decoration: none;
  color: transparent;
  -webkit-background-clip: text;
  background-clip: text;
  background-image: linear-gradient(to left, #237249, #35c66b);
  transition: transform 0.3s ease;
  z-index: 1001;
}

.header_logo:hover {
  transform: scale(1.05);
}

ul {
  display: flex;
  list-style: none;
  gap: 93px;
}

.header_item_link {
  color: #fff;
  text-decoration: none;
  font-family: Montserrat;
  font-weight: 400;
  font-style: Regular;
  font-size: 19.17px;
  transition: all 0.5s;
  position: relative;
  padding-bottom: 5px;
}

.header_item_link:hover {
  color: transparent;
  -webkit-background-clip: text;
  background-clip: text;
  background-image: linear-gradient(to left, #237249, #35c66b);
}

.header_item_link::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(to left, #237249, #35c66b);
  transition: width 0.5s ease;
}

.header_item_link:hover::after {
  width: 100%;
}

.hamburger {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 30px;
  height: 21px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
  z-index: 1001;
}

.hamburger span {
  display: block;
  height: 3px;
  width: 100%;
  background: linear-gradient(to left, #237249, #35c66b);
  border-radius: 2px;
  transition: all 0.3s ease;
}

/* Анимация гамбургера */
.hamburger--active span:nth-child(1) {
  transform: translateY(9px) rotate(45deg);
}

.hamburger--active span:nth-child(2) {
  opacity: 0;
}

.hamburger--active span:nth-child(3) {
  transform: translateY(-9px) rotate(-45deg);
}

/* Медиазапросы для адаптива */
@media (max-width: 1200px) {
  .container {
    padding: 0 80px;
  }

  ul {
    gap: 60px;
  }
}

@media (max-width: 992px) {
  .container {
    padding: 0 60px;
  }

  .header__inner {
    gap: 50px;
  }

  ul {
    gap: 40px;
  }

  .header_logo {
    font-size: 32px;
  }
}

@media (max-width: 768px) {
  .header {
    margin-top: 1200px;
  }
  .container {
    padding: 0 30px;
  }

  .hamburger {
    display: flex;
  }

  .nav-container {
    position: fixed;
    top: 0;
    right: -100%;
    width: 70%;
    height: 100vh;
    background: rgba(18, 21, 23, 0.98);
    backdrop-filter: blur(10px);
    z-index: 1000;
    transition: right 0.6s cubic-bezier(0.77, 0.2, 0.05, 1);
    padding: 100px 30px 30px;
    box-shadow: -5px 0 15px rgba(0, 0, 0, 0.2);
  }

  .nav-container--active {
    right: 0;
  }

  ul {
    flex-direction: column;
    gap: 35px;
    align-items: flex-start;
  }

  .header_item_link {
    font-size: 22px;
    display: block;
    transform: translateX(-20px);
    opacity: 0;
    transition: transform 0.5s ease, opacity 0.5s ease;
  }

  .nav-container--active .header_item_link {
    transform: translateX(0);
    opacity: 1;
  }

  .nav-container--active .header_item_link:nth-child(1) {
    transition-delay: 0.2s;
  }

  .nav-container--active .header_item_link:nth-child(2) {
    transition-delay: 0.3s;
  }

  .nav-container--active .header_item_link:nth-child(3) {
    transition-delay: 0.4s;
  }
}

@media (max-width: 576px) {
  .container {
    padding: 0 20px;
  }

  .header_logo {
    font-size: 28px;
  }

  .nav-container {
    width: 85%;
  }

  header {
    margin-top: 25px;
  }

  .header-scrolled {
    padding: 10px 0;
  }
}

@media (max-width: 480px) {
  .header_logo {
    font-size: 24px;
  }

  ul {
    gap: 30px;
  }

  .header_item_link {
    font-size: 20px;
  }
}
</style>
