<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const isMobile = ref(false);

const checkScreenSize = () => {
  isMobile.value = window.innerWidth <= 992;
};

onMounted(() => {
  checkScreenSize();
  window.addEventListener("resize", checkScreenSize);
});

onBeforeUnmount(() => {
  window.removeEventListener("resize", checkScreenSize);
});
</script>

<template>
  <div class="cooking">
    <div class="container">
      <div class="cooking_inner">
        <div class="cooking_left">
          <img
            src="/public/cooking-img.png"
            alt="Cooking illustration"
            class="cooking_image"
          />
        </div>
        <div class="cooking_right">
          <div class="cooking_title">
            <div class="cooking_background-gradient-title"></div>
            We make <br />
            <span class="delicious-text">delicious</span>
          </div>
          <div class="cooking_subtitle">
            Only in 2021 we have made more than 100,000 <br />
            orders for you, your loved ones, all of you, and in <br />
            2022 we are ready to destroy the market
          </div>
          <div class="cooking_video">
            <div class="cooking_video_start-btn">
              <a
                href="https://youtu.be/hN9mgsNWZrU?si=IxT7dHOLKdfOXVYf"
                class="video-link"
              >
                <svg
                  width="20"
                  height="23"
                  viewBox="0 0 20 23"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                  class="play-icon"
                >
                  <path
                    d="M17.3594 11.0714C17.6839 11.2655 17.6839 11.7348 17.3594 11.9288L2.25683 20.9601C1.92359 21.1594 1.50008 20.9196 1.5 20.5314L1.5 2.46887C1.50008 2.08063 1.92359 1.84089 2.25684 2.04016L17.3594 11.0714Z"
                    stroke="white"
                    stroke-width="3"
                    stroke-miterlimit="1.55572"
                  />
                </svg>
                Cooking Process
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #121517;
  color: #fff;
}

.container {
  margin: 0 auto;
  padding: 0 130px;
  max-width: 1920px;
}

.cooking {
  margin-top: 135px;
  overflow: hidden;
}

.cooking_inner {
  display: flex;
  justify-content: space-around;
  align-items: center;
  gap: 60px;
}

.cooking_left {
  flex: 1;
  display: flex;
  justify-content: center;
  transform: translateY(0);
  transition: transform 0.5s ease;
}

.cooking_left:hover {
  transform: translateY(-10px);
}

.cooking_image {
  max-width: 100%;
  height: auto;
  transition: all 0.4s ease;
}

.cooking_right {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 50px;
}

.cooking_title {
  font-family: Montserrat;
  font-weight: 800;
  font-size: 80px;
  position: relative;
  line-height: 1.1;
}

.cooking_background-gradient-title {
  position: absolute;
  top: -80px;
  right: -80px;
  z-index: -1;
  width: 324px;
  height: 324px;
  border-radius: 50%;
  background-image: linear-gradient(to bottom, #2372498c, #35c66bba);
  filter: blur(175px) brightness(1.2);
  mix-blend-mode: screen;
  opacity: 1;
  transition: all 1s ease;
}

.cooking_title span {
  color: transparent;
  -webkit-background-clip: text;
  background-clip: text;
  background-image: linear-gradient(to left, #237249, #35c66b);
  transition: transform 0.3s ease;
  display: inline-block;
}

.delicious-text:hover {
  transform: scale(1.05);
  text-shadow: 0 0 15px rgba(53, 198, 107, 0.5);
}

.cooking_subtitle {
  font-family: Montserrat;
  font-weight: 400;
  font-size: 20px;
  line-height: 1.6;
  opacity: 0.9;
  transition: opacity 0.3s ease;
}

.cooking_subtitle:hover {
  opacity: 1;
}

.cooking_video {
  width: 447px;
  max-width: 100%;
  height: 275px;
  background-image: url(/public/cooking_video_preview_first.jpg);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 20px;
  overflow: hidden;
  position: relative;
  transition: all 0.4s ease;
}

.cooking_video::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.3);
  transition: background 0.4s ease;
}

.cooking_video:hover {
  transform: scale(1.02);
  box-shadow: 0 10px 30px rgba(53, 198, 107, 0.3);
}

.cooking_video:hover::before {
  background: rgba(0, 0, 0, 0.1);
}

.cooking_video_start-btn {
  width: 326px;
  max-width: 90%;
  height: 75px;
  opacity: 1;
  border-radius: 82.83px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-image: linear-gradient(to left, #237249, #35c66b);
  position: relative;
  z-index: 2;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(35, 114, 73, 0.4);
}

.cooking_video_start-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 7px 20px rgba(35, 114, 73, 0.6);
  background-image: linear-gradient(to left, #2a8657, #3de67c);
}

.cooking_video_start-btn:active {
  transform: translateY(1px);
}

.video-link {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 15px;
  font-family: Montserrat;
  font-weight: 600;
  font-size: 24px;
  text-decoration: none;
  color: #fff;
  transition: transform 0.3s ease;
}

.play-icon {
  transition: transform 0.3s ease;
}

.video-link:hover .play-icon {
  transform: scale(1.2);
}

/* Адаптивные стили */
@media (max-width: 1440px) {
  .container {
    padding: 0 80px;
  }

  .cooking_title {
    font-size: 70px;
  }
}

@media (max-width: 1200px) {
  .container {
    padding: 0 60px;
  }

  .cooking_title {
    font-size: 60px;
  }

  .cooking_subtitle {
    font-size: 18px;
  }

  .cooking_video {
    height: 230px;
  }
}

@media (max-width: 992px) {
  .container {
    padding: 0 40px;
  }

  .cooking_inner {
    flex-direction: column;
    text-align: center;
    gap: 40px;
  }

  .cooking_left {
    width: 80%;
    margin: 0 auto;
  }

  .cooking_right {
    align-items: center;
  }

  .cooking_title {
    font-size: 65px;
  }

  .cooking_background-gradient-title {
    top: -60px;
    right: 50%;
    transform: translateX(50%);
    width: 250px;
    height: 250px;
  }

  .cooking_video {
    width: 100%;
    height: 250px;
  }
}

@media (max-width: 768px) {
  .cooking {
    margin-top: 80px;
  }

  .cooking_title {
    font-size: 50px;
  }

  .cooking_subtitle {
    font-size: 17px;
  }

  .cooking_video {
    height: 200px;
  }

  .cooking_video_start-btn {
    height: 65px;
    width: 280px;
  }

  .video-link {
    font-size: 20px;
  }
}

@media (max-width: 576px) {
  .container {
    padding: 0 20px;
  }

  .cooking {
    margin-top: 60px;
  }

  .cooking_title {
    font-size: 40px;
  }

  .cooking_background-gradient-title {
    width: 200px;
    height: 200px;
    top: -40px;
  }

  .cooking_subtitle {
    font-size: 16px;
  }

  .cooking_video {
    height: 180px;
  }

  .cooking_right {
    gap: 30px;
  }

  .cooking_video_start-btn {
    height: 60px;
    width: 260px;
  }

  .video-link {
    font-size: 18px;
    gap: 10px;
  }
}

@media (max-width: 480px) {
  .cooking_title {
    font-size: 36px;
  }

  .cooking_subtitle br {
    display: none;
  }

  .cooking_video {
    height: 160px;
  }

  .cooking_video_start-btn {
    height: 55px;
    width: 240px;
  }

  .video-link {
    font-size: 16px;
  }
}

/* Анимации */
@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.cooking_image {
  animation: float 4s ease-in-out infinite;
}

.cooking_background-gradient-title {
  animation: pulse 6s infinite alternate;
}

@keyframes pulse {
  0% {
    filter: blur(175px) brightness(1.2);
  }
  100% {
    filter: blur(200px) brightness(1.4);
  }
}
</style>
