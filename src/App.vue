<template>
  <div class="app">
    <div class="sky-section">
      <div class="stars"></div>
      <div class="particles">
        <div
          v-for="i in 30"
          :key="i"
          class="particle"
        ></div>
      </div>
    </div>
    <div class="white-section">
      <div class="card-container">
        <NameCard />
      </div>
    </div>
  </div>
</template>

<script setup>
import NameCard from './components/NameCard.vue'

// 生成随机位置的星星
const stars = Array(300).fill(0)
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.app {
  min-height: 100vh;
  width: 100vw;
  position: relative;
  overflow-y: auto;
  scrollbar-width: none;
  -ms-overflow-style: none;
}

.app::-webkit-scrollbar {
  display: none;
}

.sky-section {
  min-height: 50vh;
  position: relative;
  background: linear-gradient(to bottom, #001122 0%, #003366 100%);
  overflow: hidden;
}

.white-section {
  min-height: 50vh;
  background: #ffffff;
  position: relative;
}

.card-container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 90%;
  max-width: 600px;
}

.stars {
  position: absolute;
  width: 100%;
  height: 100%;
}

.stars::before,
.stars::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background: transparent;
}

.stars::before {
  background-image:
    radial-gradient(2px 2px at 10% 20%, rgba(255, 255, 255, 0.8), transparent),
    radial-gradient(2px 2px at 30% 40%, rgba(255, 255, 255, 0.6), transparent),
    radial-gradient(1px 1px at 60% 15%, rgba(255, 255, 255, 0.7), transparent),
    radial-gradient(1px 1px at 80% 60%, rgba(255, 255, 255, 0.5), transparent),
    radial-gradient(2px 2px at 15% 80%, rgba(255, 255, 255, 0.6), transparent),
    radial-gradient(1px 1px at 40% 25%, rgba(255, 255, 255, 0.7), transparent),
    radial-gradient(1px 1px at 70% 45%, rgba(255, 255, 255, 0.8), transparent),
    radial-gradient(2px 2px at 90% 30%, rgba(255, 255, 255, 0.6), transparent),
    radial-gradient(1px 1px at 25% 55%, rgba(255, 255, 255, 0.5), transparent),
    radial-gradient(2px 2px at 50% 70%, rgba(255, 255, 255, 0.7), transparent),
    radial-gradient(1px 1px at 85% 85%, rgba(255, 255, 255, 0.6), transparent);
  background-repeat: repeat;
  background-size: 200px 200px;
  animation: twinkle 4s infinite ease-in-out;
}

.stars::after {
  background-image:
    radial-gradient(2px 2px at 5% 35%, rgba(173, 216, 230, 0.8), transparent),
    radial-gradient(1px 1px at 70% 5%, rgba(173, 216, 230, 0.6), transparent),
    radial-gradient(1px 1px at 90% 10%, rgba(173, 216, 230, 0.7), transparent),
    radial-gradient(2px 2px at 45% 65%, rgba(173, 216, 230, 0.7), transparent),
    radial-gradient(1px 1px at 75% 90%, rgba(173, 216, 230, 0.8), transparent),
    radial-gradient(2px 2px at 35% 55%, rgba(173, 216, 230, 0.5), transparent),
    radial-gradient(1px 1px at 60% 80%, rgba(173, 216, 230, 0.6), transparent),
    radial-gradient(2px 2px at 95% 70%, rgba(173, 216, 230, 0.8), transparent),
    radial-gradient(1px 1px at 20% 85%, rgba(173, 216, 230, 0.7), transparent),
    radial-gradient(1px 1px at 50% 50%, rgba(173, 216, 230, 0.6), transparent),
    radial-gradient(2px 2px at 85% 15%, rgba(173, 216, 230, 0.8), transparent);
  background-repeat: repeat;
  background-size: 300px 300px;
  animation: twinkle 6s infinite ease-in-out reverse;
}

@keyframes twinkle {
  0%, 100% {
    opacity: 0.8;
  }
  50% {
    opacity: 1;
  }
}

.particles {
  position: absolute;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.particle {
  position: absolute;
  border-radius: 50%;
  animation: floatUp linear infinite;
}

.particle:nth-child(5n) {
  width: 3px;
  height: 3px;
  background: linear-gradient(to top, rgba(255, 255, 255, 0.8), rgba(173, 216, 230, 0.6));
  animation-duration: 12s;
  animation-delay: -2s;
  left: calc(70% + var(--random, 0) * 30%);
  --end-y: -100px;
}

.particle:nth-child(5n+1) {
  width: 4px;
  height: 4px;
  background: linear-gradient(to top, rgba(173, 216, 230, 0.8), rgba(255, 255, 255, 0.6));
  animation-duration: 15s;
  animation-delay: -4s;
  left: calc(20% + var(--random, 0) * 60%);
  --end-y: -120px;
}

.particle:nth-child(5n+2) {
  width: 2px;
  height: 2px;
  background: rgba(255, 255, 255, 0.9);
  animation-duration: 10s;
  animation-delay: -1s;
  left: calc(50% + var(--random, 0) * 40%);
  --end-y: -90px;
}

.particle:nth-child(5n+3) {
  width: 3px;
  height: 3px;
  background: linear-gradient(to top, rgba(220, 220, 220, 0.8), rgba(173, 216, 230, 0.7));
  animation-duration: 13s;
  animation-delay: -6s;
  left: calc(10% + var(--random, 0) * 80%);
  --end-y: -110px;
}

.particle:nth-child(5n+4) {
  width: 5px;
  height: 5px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.9), rgba(173, 216, 230, 0.5));
  animation-duration: 18s;
  animation-delay: -3s;
  left: calc(40% + var(--random, 0) * 50%);
  --end-y: -130px;
}

@keyframes floatUp {
  from {
    transform: translateY(100vh);
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  to {
    transform: translateY(var(--end-y, -80px));
    opacity: 0;
  }
}

.particle:nth-child(1) { --random: 0.1; bottom: 0; }
.particle:nth-child(2) { --random: 0.2; bottom: -50px; }
.particle:nth-child(3) { --random: 0.3; bottom: -100px; }
.particle:nth-child(4) { --random: 0.4; bottom: -20px; }
.particle:nth-child(5) { --random: 0.5; bottom: -80px; }
.particle:nth-child(6) { --random: 0.6; bottom: -30px; }
.particle:nth-child(7) { --random: 0.7; bottom: -60px; }
.particle:nth-child(8) { --random: 0.8; bottom: -120px; }
.particle:nth-child(9) { --random: 0.9; bottom: -40px; }
.particle:nth-child(10) { --random: 0.1; bottom: -90px; }
.particle:nth-child(11) { --random: 0.2; bottom: -10px; }
.particle:nth-child(12) { --random: 0.3; bottom: -70px; }
.particle:nth-child(13) { --random: 0.4; bottom: -150px; }
.particle:nth-child(14) { --random: 0.5; bottom: -20px; }
.particle:nth-child(15) { --random: 0.6; bottom: -110px; }
.particle:nth-child(16) { --random: 0.7; bottom: -60px; }
.particle:nth-child(17) { --random: 0.8; bottom: -80px; }
.particle:nth-child(18) { --random: 0.9; bottom: -130px; }
.particle:nth-child(19) { --random: 0.1; bottom: -40px; }
.particle:nth-child(20) { --random: 0.2; bottom: -100px; }
.particle:nth-child(21) { --random: 0.3; bottom: -50px; }
.particle:nth-child(22) { --random: 0.4; bottom: -120px; }
.particle:nth-child(23) { --random: 0.5; bottom: -30px; }
.particle:nth-child(24) { --random: 0.6; bottom: -90px; }
.particle:nth-child(25) { --random: 0.7; bottom: -60px; }
.particle:nth-child(26) { --random: 0.8; bottom: -80px; }
.particle:nth-child(27) { --random: 0.9; bottom: -100px; }
.particle:nth-child(28) { --random: 0.1; bottom: -40px; }
.particle:nth-child(29) { --random: 0.2; bottom: -70px; }
.particle:nth-child(30) { --random: 0.3; bottom: -140px; }
</style>
