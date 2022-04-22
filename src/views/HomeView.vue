<script>
import Navigation from "../components/Navigation.vue";
import Flower from "../components/Flower.vue";
import Flower1 from "../assets/flower1.jpg";
import Flower2 from "../assets/flower2.jpg";
import Flower3 from "../assets/flower3.jpg";
import Flower4 from "../assets/flower4.jpg";

import { gsap } from "gsap";
import { ref, onMounted } from "vue";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
   data() {
    return {
      images: [ Flower1, Flower2,Flower3, Flower4],
    };
  },
  components: {
    Navigation,
    Flower
  },
  setup() {
    const home = ref(null);
    const progress = ref(null);
   
    onMounted(() => {
      console.log(home.value, "home vlaue");
      gsap.to(home.value, {
        x: () =>
          -(home.value.scrollWidth - document.documentElement.clientWidth) +
          "px",
        ease: "none",
        scrollTrigger: {
          trigger: home.value,
          start: "-33px top",
          end: () => "+=" + home.value.offsetWidth,
          scrub: true,
          markers: true,
          pin: true,
          anticipatePin: 1,
        },
      });
      gsap.to(progress.value, {
        value: 100,
        ease: "none",
        scrollTrigger: { scrub: 0.3 },
      });
    });
    return {
      home,
      progress,
    };
  },
};
</script>

<template>
  <main class="main" >
    <Navigation />
    <div class="home" id="home" ref="home">
      <div class="item" v-for="image in images">
      <Flower
      :key="image"
      :image="image"
      ></Flower>
      </div>
      
    </div>
    <h2>Flowers</h2>
    <progress max="100" value="0" ref="progress"></progress>
  </main>
</template>

<style scoped>
.main {
  position: relative;
  background: #e6b69e;
}
.home {
  display: flex;
  position: fixed;
  height: 80vh;
  width: 200%;
  overscroll-behavior: none;
  z-index: 2;
}
h2 {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 16rem;
  font-family: "Cinzel", serif;
  font-weight: 300;
  z-index: 1;
}
.item {
  width: 400px;
  height: 500px;
    margin-right: 35rem;
    z-index: 1;
  font-size: 7rem;
  cursor: pointer;

}
.item:last-child{
  margin-right: 0;
}
progress {
  position: fixed;
  bottom: 10%;
  left: 50%;
  transform: translateX(-50%);

  -webkit-appearance: none;
  appearance: none;
  width: 20rem;
  height: 2px;
  border: none;
  background: white;
}
progress::-webkit-progress-bar {
  background: transparent;
}
progress::-webkit-progress-value {
  /* background: linear-gradient(to left, #db38b5,#01b3e3,#25ce7b,#fdc741,#ff6b01,#fc4236); */
  background: maroon;
  background-attachment: fixed;
}
</style>
