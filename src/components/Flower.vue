<script>
import { gsap } from "gsap";
import { Flip } from 'gsap/Flip';
gsap.registerPlugin(Flip);

export default {
  props: ['image'],
  data(){
      return {
          value: true
      }
  },
   methods: {
       scaleDown(){

       },
    scale() {


    const image = this.$refs.image;
    const flowerHolder = this.$refs.flowerHolder;
if(this.value == true){
    const textDiv =this.$parent.$refs.text;
    gsap.set(textDiv, {
        duration: 0.5,
        css: {
            backgroundColor: "#e6b69e",
            zIndex: 6,
        
        }
    })
    gsap.set(this.$parent.$refs.imageDiv, {
        css: {
            duration: 0.5,
            backgroundColor: "#e6b69e",
            zIndex: 6,
        }
    })

    const state = Flip.getState(image);
        // Change place
       let position =this.$parent.$refs.imageDiv.appendChild(image);
        // Flip
        Flip.from(state, {
            duration: 1,
            ease: 'power4.inOut',
            absolute: true,
        });
        this.value = !this.value; 
}
// if(this.value === false){
//     setTimeout(() => {
//         const state = Flip.getState(image);
//         // Change place
//         flowerHolder.appendChild(image);
//         // Flip
//         gsap.set(textDiv, {
//         duration: 0.5,
//         css: {
//             backgroundColor: "transparent",
//             zIndex: "-1 !important",
        
//         }
//     })
//     gsap.set(this.$parent.$refs.imageDiv, {
//         css: {
//             backgroundColor: "transparent",
//             duration: 0.5,
//             zIndex: -1,
//         }
//     })
//         Flip.from(state, {
//             duration: 1.2,
//             ease: 'power4.inOut',
//             absolute: true
//         }); 

//     }, 2000);

// }

    }
  }
}

</script>
<!-- @click="scale" -->
<template>
<div  class="flower" >
    <div class="flowerImg" ref="flowerHolder"  >
        <img :src="image" alt="img" ref="image" @click="scale()"/>
    </div>
</div>

</template>

<style>
.flower{
    position: static;
     margin-top: 20rem;
     overflow: hidden;
}

.flowerImg{
    width: 400px;
    height: 500px;
}
img{
    z-index: 6;
    width: 100%;
    height: 100%;
}
</style>