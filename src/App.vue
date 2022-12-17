<script>
import { isVSlot } from "@vue/compiler-core";
// I save some information to have to use less code later in the project. I didn't do this for the Icons because I only use them once.
export default {
  data() {
    return {
      largeImage: false,
      imagePieter: "src/assets/Pieter.jpg",
    };
  },
};
</script>

<template id>
  <div>
    <!-- This is the personcard -->
    <div class="container">
      <!-- The image with some simple logic to make it larger when clicked -->
      <div class="personImage">
        <img
          @click="largeImage = !largeImage"
          :src="imagePieter"
          alt="person"
        />
      </div>
      <!-- Name, work and location -->
      <div class="personInfo">
        <h1>Pieter van der Werff</h1>
        <div class="job">
          <p>Front-End Developer</p>
        </div>
        <div class="location">
          <img src="src/assets/Icon-material-location-on.svg" alt="" />
          <span>Århus, Denmark?</span>
        </div>
      </div>
      <!-- Skills -->
      <div class="personSkills">
        <h1>Skills</h1>
        <div class="vue">
          <img id="vue" src="src/assets/Icon-simple-vuejs.svg" alt="" />
          <span>VueJs</span>
        </div>
        <div class="css">
          <img src="src/assets/Icon-metro-css3.svg" alt="" /> <span>CSS</span>
        </div>
        <div class="adobe">
          <img src="src/assets/Icon-awesome-adobe.svg" alt="" />
          <span>Adobe Xd, Ai, Ps & Ae</span>
        </div>
      </div>
      <!-- All the contact information with links -->
      <div class="personContact">
        <h1>Contact me</h1>
        <div
          onclick="window.open('mailto:p.j.j.van.der.werff@st.hanze.nl','mywindow');"
          style="cursor: pointer"
          class="mail"
        >
          <img src="src/assets/Icon-material-email.svg" alt="" />
          <span>Email me</span>
        </div>
        <div
          onclick="window.open('tel:+31611769998','mywindow');"
          style="cursor: pointer"
          class="phone"
        >
          <img src="src/assets/Icon-awesome-phone-square-alt.svg" alt="" />
          <span>Call me</span>
        </div>
        <div
          onclick="window.open('https://www.linkedin.com/in/pieter-van-der-werff/','mywindow');"
          style="cursor: pointer"
          class="linkedIn"
        >
          <img src="src/assets/Icon-awesome-linkedin.svg" alt="" />
          <span>LinkedIn</span>
        </div>
      </div>
    </div>
  </div>
  <img
    v-show="largeImage"
    @click="largeImage = !largeImage"
    style="position: absolute; width: 40%; border-radius: 50%"
    :src="imagePieter"
    alt="person"
  />
  <!-- This is the enlarged image. It works but I do get an error that it should be inside of a div. 
    However, If I place it inside of a div it will look terrible because it will be inside of the personcard, which shouldn't happen. -->
</template>

<style>
/* Font and variables used */
@import url("https://use.typekit.net/mkw3upx.css");
@import "./assets/variables.css";
/* take the right font and put everything in the middle */
#app {
  font-family: new-order, sans-serif;
  font-weight: 200;
  font-style: normal;
  color: #707070;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  margin: 0;
  background-color: #e9f1fb;
}
* {
  box-sizing: border-box;
}
/* Create the container devide it in 4 parts that can be filled with information */
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  width: 1321px;
  gap: 1%;
  margin: 0;
  background-color: white;

  border-radius: 84px;
  box-shadow: 6px 6px 10px rgba(0, 0, 0, 0.1);
}
/* Some css to put the img on the right location and the right size. Also added an effect when hovering. */
.personImage {
  margin: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.personImage img {
  width: 80%;
  border-radius: 50%;
  object-fit: cover;
  margin: auto;
  transition: filter 0.4s;
}
.personImage img:hover {
  filter: grayscale(100%);
}
/* Put borders around the front end developer text */
.job p {
  text-align: center;
  background: #9affe6;
  border-radius: 50px;
  font-size: 18px;
  margin: 0;
  color: #707070;
  padding: 10px 10px;
}
/* Some css to put all icons and text next to eachother and look good. I feel like I can do this smarter but dont know how... */
.personInfo img {
  padding: 10px 10px 0px 0px;
}
.personInfo span {
  font-size: 23px;
}
.personSkills {
  padding: 0 0 0 10px;
}
.personSkills img {
  padding: 10px 10px 0px 0px;
}
.personSkills span {
  font-size: 23px;
}
.personContact img {
  padding: 10px 10px 0px 0px;
}
.personContact span {
  font-size: 23px;
}
/* Animations for the contact part. I used a variable for the animation. It's saved in variables.css*/

.mail:hover {
  animation: var(--contact-animation);
  transform: translate3d(0, 0, 0);
  transform-origin: 0% 50%;
}
.phone:hover {
  animation: var(--contact-animation);
  transform: translate3d(0, 0, 0);
  transform-origin: 0% 50%;
}
.linkedIn:hover {
  animation: var(--contact-animation);
  transform: translate3d(0, 0, 0);
  transform-origin: 0% 50%;
}
@keyframes scale-up-center {
  0% {
    -webkit-transform: scale(1);
    transform: scale(1);
  }
  50% {
    -webkit-transform: scale(1.2);
    transform: scale(1.2);
  }
  100% {
    -webkit-transform: scale(1);
    transform: scale(1);
  }
}
</style>
