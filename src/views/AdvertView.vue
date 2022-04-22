<script>
import { gsap } from "gsap";
import { ref, onMounted} from "vue";


export default {
    components: {
  },

  setup(){
      const nav = ref(null);
      const image = ref(null);
      const logo = ref(null);
      const text = ref(null);
      const subHeader = ref(null);
      const header = ref(null);
      const button = ref(null);
      var tl = gsap.timeline();
      const list1 = ref(null);
      const list2 = ref(null);
      const list3 = ref(null);
      const list4 = ref(null);
      const links = [list1.value,list2.value,list3.value,list4.value]
      onMounted(() => {
          tl.set(image.value,{
              opacity:0,
          })
          tl.from(logo.value, {
              duration:0.5,
              opacity:0,
              y: 10,
          })
          tl.from([list1.value,list2.value,list3.value,list4.value], {
              duration: 1,
              y: 10,
              opacity:0,
              stagger: 0.3,
          })
      tl.fromTo(image.value, {
      duration: 1,
          css:{
              top: 0,
              left: -1000,
              height: "80vh",
              width: "55%",
              opacity: 1,
          }
      },
      {
    duration: 1,
          css:{
              top: "0px",
              right:0,
              left: "20%",
              height: "80vh",
              width: "55%",
                  opacity: 1,

          }
      },"-=1")
      .fromTo(image.value,
        {
    duration: 1,
          css:{
              top: "0px",
              right:0,
              left: "20%",
              height: "80vh",
              width: "55%",
              opacity: 1,

          }
        },
      {
    duration: 1,
    opacity: 1,
          css:{
              top: "-115.2px",
              right:0,
              left: "55%",
              height: "90vh",
              width: "45%",
              opacity: 1,

    }
      })
      tl.from([header.value,subHeader.value,button.value], {
          duration: 1,
          delay: -0.5,
          stagger: 0.1,
          y: 10,
          opacity: 0,
          
      })
    });
      return{
          image,
          nav,
          text,
          header,
          subHeader,
          button,
          list1,
          list2,
          list3,
          list4,
          logo
      };
  }
}

</script>


<template>
    <main class="main" >
        <div>
            <nav class="navigation" ref="nav">
    <div class="navigation__logoWrapper" ref="logo">
        <h1 class=navigation__logo>Advertising</h1>
    </div>
    <ol class="navigation__links">
        <li class="list" id="list" ref="list1">Benefits</li>
        <li class="list" id="list" ref="list2">Costs</li>
        <li class="list" id="list" ref="list3">Login</li>
        <li class="list" id="list" ref="list4">Signup</li>

    </ol>
</nav>
        <div class="container">
            <div class="container__text" id="text" ref="text">
                <h1 class="container__textHeader" ref="header">Reach<br>
                    680,000,000<br>
                    monthly users<br>
                </h1>
                <p class="container__textSubHeader" ref="subHeader">Connect with people at the right moment across work and life, reaching audiences who are ready to engage<br> and purchase online </p>
                <button class="container__textButton" ref="button">Start Now</button>
            </div>
            <div class="container__image" ref="image" id="image">
                <img src="../assets/flower7.jpg" alt="img" />
            </div>
        </div>
        </div>
        
    </main>
  </template>

  <style scoped>
  .main{
      position: relative;
      height: 100vh;
  }
  .navigation{
    display: flex;
    justify-content: space-between;
    color: Black;
    padding: 2rem 3rem;
    z-index: 1;
}
.navigation__logo{
    font-size: 2rem;
    font-weight: 500;
}
.navigation__links{
    list-style-type: none;
    display: flex;
}
li{
    font-size: 18px;
    margin-right: 20px;
}
li:last-child{
    margin-right: 0px;
}
  .container{
      display: flex;
  }
  .container__text{
      opacity: 1;
      align-self: flex-start;
      max-width: 40rem;
      margin: 9rem 0rem 0rem 10rem;
  }
  .container__textHeader{
      font-size: 3.5rem;
      line-height: 75px;
      font-weight: 600;
      color: Black;

  }
  .container__textSubHeader{
      font-size: 18px;
      font-weight: 400;
      color: darkGrey;
  }
  .container__textButton{
      border: 0px;
      color: white;
      font-size: 1rem;
      width: 6rem;
      height: 4rem;
      margin-top: 1rem;
      background-color: #39AEA9;
  }
  .container__image{
      position: absolute;
      left: -100px;
  }
  </style>