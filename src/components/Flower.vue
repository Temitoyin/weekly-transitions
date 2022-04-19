<script>
import { gsap } from "gsap";
export default {
  props: ['image'],
   methods: {
    // scale() {
    // const image = this.$refs.image;
    // const flowerHolder = this.$refs.flowerHolder;
    // console.log(this.$refs.flowerHolder, 'image');
    // gsap.to(this.$refs.flowerHolder, {
    //     css: {
    //         position: "fixed",
    //         top: 0,
    //         right: "-5px",
    //         left: 0,
    //         overflow: "hidden",
    //         width: "100vw",
    //         height: "100vh", 
    //         backgroundColor: "#e6b69e",
    //         marginTop: "-33px",
    //         zIndex: "100"
    //     }
    // })
    //  gsap.to(image, {
    //      x: 0,
    //      y:0,
    //      css: {
    //          position: "absolute",
    //          top: "0",
    //          right: "0",
    //          height: "100vh",
    //          width: "50%"
    //      },
    //      duration: 1,
    //  });
    //  document.body.style.overflow ="hidden";
    // }
  }
}

</script>
<!-- @click="scale" -->
<template>
<div  class="flower" ref="flowerHolder">
    <div class="flowerImg" ref="image">
        <img :src="image" alt="img"/>
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
    width: 100%;
    height: 100%;
}
</style>