<script>
import Navigation from "../components/Navigation.vue";
import Flower from "../components/Flower.vue";
import Flower1 from "../assets/flower1.jpg";
import Flower2 from "../assets/flower2.jpg";
import Flower3 from "../assets/flower3.jpg";
import Flower4 from "../assets/flower4.jpg";

import { gsap } from "gsap";
import { Flip } from 'gsap/Flip';
import { ref, onMounted } from "vue";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);
gsap.registerPlugin(Flip);

export default {
   data() {
    return {
      images: [ Flower1, Flower2,Flower3, Flower4],
    };
  },
  el: "#image",
  components: {
    Navigation,
    Flower
  },
  methods:{
      openContent(image,event){
        if (event) {
      event.preventDefault()
    }
         // Get state
         const state = Flip.getState(image);
        // Change place
        imageDiv.value.appendChild(image);
        // Flip
        Flip.from(state, {
            duration: 1.2,
            ease: 'power4.inOut',
            absolute: true
        });
      }
    },
  setup() {
    const home = ref(null);
    const progress = ref(null);
    const image = ref(null);
    const imageDiv = ref(null);
    const text = ref(null);
    const images = [document.querySelectorAll('#image')];
    onMounted(() => {
      // this.$el.addEventListener('click', console.log($el, 'element'));

//       console.log(home.value, "home vlaue");
//       console.log(image, 'images');
//       images.forEach((image) => {  
//     //     image.addEventListener('click', (e) => {
//     //     openContent(image, e);
//     // }
//     // );
//     console.log(image, 'image');
// }
// );
    
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
    <div class="imageWrapper">
      <div class="text" ref="text"></div>
      <div class="imagePosition" ref="imageDiv"></div>
    </div>
  <main class="main" >
    <Navigation />
    <div class="home" id="home" ref="home">
      <div class="item" v-for="image in images" id="image" ref="image">
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
.text{
  position: fixed;
  top: 0;
  left: 0;
  z-index: 1;
  height: 100vh;
  width: 50%;
}
.imagePosition{
  position: fixed;
  top: 0;
  right: 0;
  z-index: 1;
  height: 100vh;
  width: 50%;
  /* background-color: green; */
}
.home {
  display: flex;
  position: fixed;
  height: 80vh;
  width: 200%;
  overscroll-behavior: none;
  z-index: 2;
}
img{
  z-index: 6;
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
