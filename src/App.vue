<template>
  <div class="container">
    <!-- <div class="block" :class="{ animateLeft: animateBlockLeft }"></div> -->

    <Transition name="box">
      <div class="block" v-if="animateBlockLeft"></div>
    </Transition>
    <button @click="moveLeft">move left</button>
  </div>

  <div class="container">
    <!-- transition can have only one element inside it -->
    <Transition name="para">
      <p v-if="paraVisibility">Hey this is a paragraph.......</p>
    </Transition>

    <button @click="toggleParagraph">toggle Paragraph</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      animateBlockLeft: false,
      paraVisibility: false,
    };
  },
  methods: {
    moveLeft() {
      this.animateBlockLeft = !this.animateBlockLeft;
    },

    toggleParagraph() {
      this.paraVisibility = !this.paraVisibility;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
/* .animateLeft {
  transform: translateX(-250px); 
  animation: slide-fade 0.8s ease-in-out;
  animation-direction: alternate-reverse;
} */
.block {
  height: 200px;
  width: 200px;
  background-color: darkmagenta;
  margin-bottom: 20px;
  border-radius: 100%;
  transition: transform 0.8s ease-in-out;
}
.container {
  margin: 2rem auto;
  max-width: 40rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
button {
  background-color: crimson;
  color: beige;
  padding: 18px;
  border-radius: 20px;
  cursor: pointer;
}

button:hover {
  background-color: blueviolet;
  padding: 18px;
  color: azure;
  border-radius: 20px;
  border: none;
}
/* @keyframes slide-fade {
  0% {
    transform: translateX(0) scale(1);
  }
  50% {
    transform: translateX(-125px) scale(1.3);
  }
  100% {
    transform: translateX(-250px) scale(1);
  }
} */

.box-enter-from {
  opacity: 0;
  transform: translateX(-125px);
}
.box-enter-active {
  transition: all 0.8s ease-in;
}
.box-enter-to {
  opacity: 1;
  transform: translateX(-250px);
}
.box-leave-from {
  opacity: 1;
  transform: translateX(0);
}
.box-leave-active {
  transition: all 0.5s ease-in;
}
.box-leave-to {
  opacity: 0;
  transform: translateX(-125px);
}

.para-enter-from {
  opacity: 0;
  transform: translateY(-40px);
}
.para-enter-active {
  transition: all 0.5s ease-out;
  /* animation:para 0.5s ease-in reverse */
}
.para-enter-to {
  opacity: 1;
  transform: translateY(0);
}
.para-leave-from {
  opacity: 1;
  transform: translateY(0);
}
.para-leave-active {
  transition: all 0.3s ease-out;
  /* animation:para 0.5s ease-in */
}
.para-leave-to {
  opacity: 0;
  transform: translateY(-40px);
}
</style>

// by using keyframes

//  @keyframes para{
//   0%{
// transform:translateY(0) scale(1);
//   }
//    50%{
// transform:translateY(-125) scale(1.3);
//   }
//    100%{
// transform:translateY(-250) scale(1);
//   }
// }
