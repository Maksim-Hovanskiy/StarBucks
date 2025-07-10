```vue
<script setup>
import { ref, onMounted } from "vue";

const isLoaded = ref(false);

onMounted(() => {
  setTimeout(() => {
    isLoaded.value = true;
  }, 300);
});
</script>

<template>
  <div class="hero" :class="{ loaded: isLoaded }">
    <div class="container">
      <div class="hero_inner">
        <div class="hero_info">
          <div class="hero_title">
            New Cafe <br />
            by
            <span>StarBucks</span>
            <div class="hero_title_background-gradient-circle"></div>
          </div>
          <div class="hero_subtitle">
            Have time to buy the most harmonious drinks in the <br />
            new Starbucks coffee and don't forget about the discount!
          </div>
          <div class="hero_buttons">
            <button>Select a coffee</button>
            <button>More</button>
          </div>
          <div class="hero_stats">
            <div class="hero_stats_block">
              <div class="hero_stats_title">9k <span>+</span></div>
              <div class="hero_stats_subtitle">Premium Users</div>
            </div>
            <div class="hero_stats_block">
              <div class="hero_stats_title">2k <span>+</span></div>
              <div class="hero_stats_subtitle">Happy Customer</div>
            </div>
            <div class="hero_stats_block">
              <div class="hero_stats_title">28 <span>+</span></div>
              <div class="hero_stats_subtitle">Awards Winning</div>
            </div>
          </div>
        </div>
        <div class="hero_preview">
          <div class="white_backround-lines">
            <img src="/public/whitebackgroundslines.png" alt="" />
          </div>
          <div class="hero_coffe_preview_image">
            <img src="/public/CoffePreview.png" alt="Starbucks Coffee" />
            <div class="hero_preview_background-gradient-circle_first"></div>
            <div class="hero_preview_background-gradient-circle_second"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* === ОСНОВНЫЕ СТИЛИ (НЕ МЕНЯТЬ) === */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #121517;
}

.container {
  margin: 0 auto;
  padding: 0 130px;
  max-width: 1600px;
}

.hero {
  margin-top: 80px;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.8s cubic-bezier(0.215, 0.61, 0.355, 1),
    transform 0.8s cubic-bezier(0.215, 0.61, 0.355, 1);
}

.hero.loaded {
  opacity: 1;
  transform: translateY(0);
}

.hero_inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.white_backround-lines {
  position: absolute;
  right: 0;
  top: 352px;
  z-index: -999;
}

.hero_title {
  position: relative;
  z-index: 2;
  font-family: Montserrat;
  font-weight: 800;
  font-style: ExtraBold;
  font-size: 80px;
  line-height: 109.00000000000001%;
  letter-spacing: -3%;
  color: #fff;
  transition: transform 0.5s ease;
}

.hero_title span {
  color: transparent;
  -webkit-background-clip: text;
  background-clip: text;
  background-image: linear-gradient(to left, #237249, #35c66b);
  transition: background-image 0.5s ease;
}

.hero_title_background-gradient-circle {
  position: absolute;
  top: -30%;
  left: -5%;
  z-index: -1;
  width: 324px;
  height: 324px;
  border-radius: 50%;
  background-image: linear-gradient(
    to bottom,
    rgba(35, 114, 73, 0.55),
    rgba(53, 198, 107, 0.73)
  );
  filter: blur(175px) brightness(1.2);
  mix-blend-mode: screen;
  opacity: 1;
  transition: all 0.8s ease;
}

.hero_subtitle {
  font-family: Montserrat;
  font-weight: 400;
  font-style: Regular;
  font-size: 20px;
  margin-top: 54px;
  margin-bottom: 54px;
  color: #fff;
  opacity: 0;
  transform: translateX(-20px);
  transition: opacity 0.8s ease 0.2s, transform 0.8s ease 0.2s;
}

.hero.loaded .hero_subtitle {
  opacity: 1;
  transform: translateX(0);
}

.hero_buttons {
  display: flex;
  gap: 16px;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.8s ease 0.4s, transform 0.8s ease 0.4s;
}

.hero.loaded .hero_buttons {
  opacity: 1;
  transform: translateY(0);
}

button {
  color: #fff;
  padding: 20px 78px;
  border-radius: 82px;
  font-family: Montserrat;
  font-weight: 639;
  font-style: SemiBold;
  font-size: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 0;
  cursor: pointer;
  transition: all 0.3s ease;
}

button:first-child {
  background-image: linear-gradient(to left, #237249, #35c66b);
}

button:first-child:hover {
  background-image: linear-gradient(#121517);
  border: 1px solid #dadada;
  transform: translateY(-3px);
  box-shadow: 0 10px 20px rgba(53, 198, 107, 0.3);
}

button:nth-child(2) {
  background-color: #121517;
  border: 1px solid #dadada;
}

button:nth-child(2):hover {
  background-image: linear-gradient(to left, #237249, #35c66b);
  border-color: transparent;
  transform: translateY(-3px);
  box-shadow: 0 10px 20px rgba(53, 198, 107, 0.3);
}

.hero_stats {
  display: flex;
  color: #fff;
  gap: 64px;
  margin-top: 54px;
  opacity: 0;
  transition: opacity 0.8s ease 0.6s;
}

.hero.loaded .hero_stats {
  opacity: 1;
}

.hero_stats_title {
  font-family: Montserrat;
  font-weight: 400;
  font-style: Regular;
  font-size: 62px;
  transition: transform 0.3s ease;
}

.hero_stats_block:hover .hero_stats_title {
  transform: scale(1.05);
}

.hero_stats_title span {
  color: transparent;
  -webkit-background-clip: text;
  background-clip: text;
  background-image: linear-gradient(to left, #237249, #35c66b);
}

.hero_stats_subtitle {
  font-family: Montserrat;
  font-weight: 400;
  font-style: Regular;
  font-size: 20px;
}

.hero_coffe_preview_image {
  position: relative;
  transform: scale(0.95);
  opacity: 0;
  transition: all 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275) 0.4s;
}

.hero.loaded .hero_coffe_preview_image {
  transform: scale(1);
  opacity: 1;
}

.hero_coffe_preview_image img {
  transition: transform 0.5s ease;
}

.hero_preview_background-gradient-circle_first {
  position: absolute;
  top: 0;
  left: -20%;
  z-index: -1;
  width: 324px;
  height: 324px;
  border-radius: 50%;
  background-image: linear-gradient(to bottom, #d9d9d94d);
  filter: blur(175px) brightness(1.2);
  mix-blend-mode: screen;
  opacity: 1;
  transition: all 1s ease;
}

.hero_preview_background-gradient-circle_second {
  position: absolute;
  bottom: 0;
  right: 0;
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

@keyframes floating {
  0% {
    transform: translateY(0) rotate(0deg);
  }
  50% {
    transform: translateY(-15px) rotate(2deg);
  }
  100% {
    transform: translateY(0) rotate(0deg);
  }
}

.hero_coffe_preview_image img {
  animation: floating 4s ease-in-out infinite;
  transform-origin: center bottom;
  transition: transform 0.5s ease;
}

/* Для плавного старта после появления */
.hero.loaded .hero_coffe_preview_image img {
  animation-delay: 0.8s;
}

/* === ЛУЧШИЙ АДАПТИВ С АНИМАЦИЯМИ ДЛЯ ВСЕХ УСТРОЙСТВ === */

/* --- 1. Большие экраны (max-width: 1400px) --- */
@media (max-width: 1400px) {
  .container {
    max-width: 1100px;
    padding: 0 40px;
  }
  .hero_title {
    font-size: 62px;
  }
  .hero_title_background-gradient-circle {
    width: 220px;
    height: 220px;
    top: -25%;
    left: -3%;
    filter: blur(120px) brightness(1.2);
  }
  .hero_coffe_preview_image {
    max-width: 400px;
  }
  .hero_stats {
    gap: 36px;
  }
  .hero_stats_title {
    font-size: 44px;
  }
}

/* --- 2. Ноутбуки (max-width: 1024px) --- */
@media (max-width: 1024px) {
  .container {
    padding: 0 20px;
    max-width: 900px;
  }
  .hero {
    margin-top: 60px;
  }
  .hero_inner {
    gap: 28px;
  }
  .hero_title {
    font-size: 48px;
  }
  .hero_title_background-gradient-circle {
    width: 160px;
    height: 160px;
    top: -18%;
    left: -2%;
    filter: blur(90px) brightness(1.2);
  }
  .hero_subtitle {
    font-size: 16px;
    margin-top: 30px;
    margin-bottom: 30px;
    line-height: 1.4;
  }
  .hero_buttons {
    gap: 12px;
    flex-wrap: wrap;
  }
  button {
    padding: 14px 38px;
    font-size: 18px;
    min-width: 170px;
  }
  .hero_stats {
    gap: 24px;
    margin-top: 25px;
  }
  .hero_stats_title {
    font-size: 32px;
  }
  .hero_stats_subtitle {
    font-size: 13px;
  }
  .white_backround-lines {
    top: 200px;
    opacity: 0.6;
    right: -50px;
  }
  .hero_coffe_preview_image {
    max-width: 320px;
  }
  .hero_preview_background-gradient-circle_first,
  .hero_preview_background-gradient-circle_second {
    width: 130px;
    height: 130px;
    filter: blur(70px) brightness(1.1);
  }
}

/* --- 3. Планшеты (max-width: 768px) --- */
@media (max-width: 768px) {
  .container {
    padding: 0 10px;
    max-width: 600px;
  }
  .hero_inner {
    flex-direction: column;
    gap: 0;
    text-align: center;
    align-items: center;
  }
  .hero_title {
    margin-top: 20px;
    font-size: 38px;
    line-height: 1.18;
  }
  .hero_title_background-gradient-circle {
    left: 50%;
    transform: translateX(-50%);
    width: 110px;
    height: 110px;
    top: -12%;
  }
  .hero_subtitle {
    margin: 18px 0 20px 0;
    font-size: 15px;
    padding: 0 6px;
    line-height: 1.35;
  }
  .hero_buttons {
    justify-content: center;
    gap: 10px;
    flex-direction: row;
  }
  button {
    padding: 12px 10px;
    font-size: 15px;
    min-width: 100px;
    width: 45vw;
    max-width: 220px;
  }
  .hero_stats {
    gap: 13px;
    margin-top: 15px;
    justify-content: center;
    flex-wrap: wrap;
  }
  .hero_stats_block {
    min-width: 90px;
  }
  .hero_stats_title {
    font-size: 22px;
  }
  .hero_stats_subtitle {
    font-size: 10px;
  }
  .white_backround-lines {
    display: none;
  }
  .hero_preview {
    margin: 0 auto;
    margin-top: 20px;
    width: 100%;
    display: flex;
    justify-content: center;
  }
  .hero_coffe_preview_image {
    display: flex;
    justify-content: center;
    max-width: 180px;
    margin: 0 auto;
  }
  .hero_coffe_preview_image img {
    max-width: 100%;
    height: auto;
    animation: floating 5s cubic-bezier(0.6, 0, 0.4, 1) infinite;
  }
  .hero_preview_background-gradient-circle_first,
  .hero_preview_background-gradient-circle_second {
    width: 90px;
    height: 90px;
    filter: blur(38px) brightness(1.15);
  }
  .hero_preview_background-gradient-circle_first {
    left: 15%;
  }
  .hero_preview_background-gradient-circle_second {
    right: 5%;
  }
}

/* --- 4. Мобильные устройства (max-width: 480px) --- */
@media (max-width: 480px) {
  .container {
    padding: 0 5px;
    max-width: 98vw;
  }
  .hero {
    margin-top: 60px;
  }
  .hero_inner {
    flex-direction: column;
    gap: 0;
    text-align: center;
  }
  .hero_title {
    font-size: 28px;
    margin-top: 10px;
    line-height: 1.12;
  }
  .hero_title_background-gradient-circle {
    width: 70px;
    height: 70px;
    top: -10%;
  }
  .hero_subtitle {
    font-size: 12px;
    margin: 12px 0 13px 0;
    padding: 0 2px;
  }
  .hero_buttons {
    flex-direction: column;
    align-items: center;
    gap: 8px;
  }
  button {
    width: 100%;
    max-width: 98vw;
    padding: 10px;
    font-size: 13px;
    min-width: unset;
  }
  .hero_stats {
    flex-direction: column;
    gap: 8px;
    margin-top: 15px;
    align-items: center;
  }
  .hero_stats_block {
    margin-bottom: 5px;
    min-width: unset;
  }
  .hero_stats_title {
    font-size: 18px;
  }
  .hero_stats_subtitle {
    font-size: 8px;
  }
  .hero_preview {
    margin-top: 18px;
    width: 100%;
    display: flex;
    justify-content: center;
  }
  .hero_coffe_preview_image {
    max-width: 120px;
    margin: 0 auto;
  }
  .hero_coffe_preview_image img {
    max-width: 92vw;
    height: auto;
  }
  .hero_preview_background-gradient-circle_first,
  .hero_preview_background-gradient-circle_second {
    width: 60px;
    height: 60px;
    filter: blur(23px) brightness(1.1);
  }
}

/* --- 5. Очень маленькие устройства (max-width: 360px) --- */
@media (max-width: 360px) {
  .hero_title {
    font-size: 18px;
  }
  .hero_subtitle {
    font-size: 9px;
  }
  button {
    font-size: 10px;
    padding: 7px;
  }
  .hero_stats_title {
    font-size: 12px;
  }
  .hero_stats_subtitle {
    font-size: 6px;
  }
  .hero_preview_background-gradient-circle_first,
  .hero_preview_background-gradient-circle_second {
    width: 35px;
    height: 35px;
  }
}

/* === ДОПОЛНИТЕЛЬНЫЕ АДАПТИВНЫЕ АНИМАЦИИ === */
@media (max-width: 768px) {
  .hero_title,
  .hero_subtitle,
  .hero_buttons button,
  .hero_stats_block {
    animation: fadeInUp 0.95s both;
  }
  .hero_title {
    animation-delay: 0.05s;
  }
  .hero_subtitle {
    animation-delay: 0.1s;
  }
  .hero_buttons button {
    animation-delay: 0.15s;
  }
  .hero_stats_block {
    animation-delay: 0.2s;
  }
}

/* === АНИМАЦИИ === */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px) scale(0.98);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@keyframes scaleIn {
  from {
    transform: scale(0.9);
    opacity: 0;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}
</style>
```
