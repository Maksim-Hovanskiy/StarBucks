<script setup>
import { onMounted, ref } from "vue";

const isVisible = ref(false);

onMounted(() => {
  isVisible.value = true;
});
</script>

<template>
  <div class="success" :class="{ visible: isVisible }">
    <div class="succes_background-gradient-circle_first"></div>
    <div class="succes_background-gradient-circle_second"></div>
    <div class="success_label">
      <img src="/public/label.png" alt="Success label" />
    </div>
    <div class="succes_cards">
      <div
        class="succes_card"
        v-for="(card, index) in cards"
        :key="index"
        :style="{ 'transition-delay': `${index * 0.1}s` }"
      >
        <div class="succes_card_img">
          <div class="succes_card_img_background_circle">
            <img :src="card.icon" :alt="card.title" />
          </div>
        </div>
        <div class="succes_card_title">{{ card.title }}</div>
        <div class="succes_card_subtitle" v-html="card.subtitle"></div>
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
}

.container {
  margin: 0 auto;
  padding: 0 130px;
}

.success {
  max-width: 1000px;
  height: auto;
  min-height: 372px;
  background-color: #fff;
  border-radius: 46px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  position: relative;
  margin-top: 110px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 40px 20px;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.6s ease-out, transform 0.6s ease-out;
}

.succes_background-gradient-circle_first {
  position: absolute;
  width: 408px;
  left: -20%;
  top: -25%;
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
  z-index: -999;
  height: 327px;
}

.succes_background-gradient-circle_second {
  position: absolute;
  width: 408px;
  right: -20%;
  bottom: -25%;
  border-radius: 50%;
  background-image: linear-gradient(to bottom, #d9d9d94d);
  filter: blur(175px) brightness(1.2);
  mix-blend-mode: screen;
  opacity: 1;
  transition: all 0.8s ease;
  z-index: -999;
  height: 327px;
}

.success.visible {
  opacity: 1;
  transform: translateY(0);
}

.success_label {
  position: absolute;
  top: -25%;
  left: -10%;
  transition: all 0.4s ease;
}

.success_label img {
  width: 220px;
  height: 220px;
  transition: all 0.4s ease;
  z-index: 999;
}

.succes_cards {
  display: flex;
  gap: 150px;
  flex-wrap: wrap;
  justify-content: center;
  padding: 20px;
  transition: all 0.4s ease;
}

.succes_card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  opacity: 0;
  transform: scale(0.9);
  transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.success.visible .succes_card {
  opacity: 1;
  transform: scale(1);
}

.succes_card_img_background_circle {
  width: 148px;
  height: 148px;
  background-image: linear-gradient(to bottom, #237249, #35c66b);
  border-radius: 50%;
  position: relative;
  transition: all 0.3s ease;
}

.succes_card:hover .succes_card_img_background_circle {
  transform: scale(1.05);
  box-shadow: 0 10px 20px rgba(35, 114, 73, 0.3);
}

.succes_card_img_background_circle img {
  position: absolute;
  z-index: 999;
  top: -8%;
  right: -3%;
  transition: all 0.3s ease;
}

.succes_card:hover .succes_card_img_background_circle img {
  transform: scale(1.1);
}

.succes_card_title {
  font-family: Montserrat;
  font-weight: 500;
  font-style: Medium;
  font-size: 32px;
  text-align: center;
  transition: all 0.3s ease;
  z-index: 999;
}

.succes_card:hover .succes_card_title {
  color: #237249;
}

.succes_card_subtitle {
  font-family: Montserrat;
  font-weight: 400;
  font-style: Regular;
  font-size: 20.13px;
  text-align: center;
  transition: all 0.3s ease;
  z-index: 999;
}

/* Адаптивные стили */
@media (max-width: 1200px) {
  .success {
    max-width: 900px;
    margin-left: auto;
    margin-right: auto;
  }

  .succes_cards {
    gap: 100px;
  }

  .success_label {
    left: -5%;
  }
}

@media (max-width: 992px) {
  .success {
    margin-left: auto;
    margin-right: auto;
    max-width: 750px;
    margin-top: 80px;
  }

  .succes_cards {
    gap: 70px;
  }

  .success_label {
    top: -15%;
    left: -3%;
  }

  .success_label img {
    width: 180px;
    height: 180px;
  }
}

@media (max-width: 768px) {
  .success {
    margin-left: auto;
    margin-right: auto;
    max-width: 90%;
    margin-top: 60px;
    border-radius: 36px;
    padding: 30px 15px;
  }

  .succes_cards {
    gap: 50px;
  }

  .succes_card_img_background_circle {
    width: 120px;
    height: 120px;
  }

  .succes_card_title {
    font-size: 28px;
  }

  .succes_card_subtitle {
    font-size: 18px;
  }

  .success_label {
    top: -10%;
    left: 0;
  }

  .success_label img {
    width: 150px;
    height: 150px;
  }
}

@media (max-width: 576px) {
  .success {
    margin-left: auto;
    margin-right: auto;
    margin: 0 auto;
    border-radius: 26px;
    padding: 25px 10px;
  }

  .succes_background-gradient-circle_first {
    display: none;
  }

  .succes_cards {
    gap: 40px;
    flex-direction: column;
    align-items: center;
  }

  .succes_card {
    width: 100%;
    max-width: 250px;
  }

  .succes_card_img_background_circle {
    width: 100px;
    height: 100px;
  }
  .succes_card_img_background_circle img {
    width: 130px;
    height: 130px;
  }

  .succes_card_title {
    font-size: 24px;
  }

  .succes_card_subtitle {
    font-size: 16px;
  }

  .success_label {
    display: none;
  }
}

@media (max-width: 400px) {
  .success {
    margin-top: 40px;
    border-radius: 20px;
  }

  .succes_card_title {
    font-size: 22px;
  }

  .succes_card_subtitle {
    font-size: 15px;
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

.success_label img {
  animation: float 4s ease-in-out infinite;
}

/* Оптимизация для темной темы */
@media (prefers-color-scheme: dark) {
  .success {
    background-color: #1e1e1e;
    color: #fff;
  }

  .succes_card_title {
    color: #fff;
  }

  .succes_card_subtitle {
    color: #ccc;
  }
}
</style>

<script>
export default {
  data() {
    return {
      cards: [
        {
          icon: "/public/heart.png",
          title: "Tasty",
          subtitle: "We have the <br />most delicious coffee",
        },
        {
          icon: "/public/raketa.png",
          title: "Fast",
          subtitle: "Quick service <br />and delivery",
        },
        {
          icon: "/public/money.png",
          title: "Affordable",
          subtitle: "Great prices <br />for everyone",
        },
      ],
    };
  },
};
</script>
