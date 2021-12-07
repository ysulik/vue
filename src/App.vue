<template>
  <div id="app">
    <div class="header">
      <h1>Котики!</h1>
      <h2>Нажми на кнопку и получишь нового котика</h2>
      <div class="buttonWraper">
        <button @click="geNewCat">&#128049;</button>
      </div>
    </div>
    <div class="content">
      <div class="imgWraper">
        <img :src="this.catURL" alt="" v-show="this.catURL" />
      </div>
    </div>
  </div>
</template>

<script>
import Axios from "axios";
export default {
  name: "App",
  data() {
    return {
      catURL: null,
    };
  },
  methods: {
    geNewCat() {
      Axios.get("https://thatcopy.pw/catapi/rest/").then((resp) => {
        this.catURL = resp.data.webpurl;
      });
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Merriweather:ital,wght@0,300;0,400;0,700;1,300;1,400;1,700&family=Roboto+Condensed&display=swap");

*,
body,
html {
  margin: 0;
  padding: 0;
}
body {
  background-image: url(../assets/cats_bg.png);
}
#app {
  min-height: 100vh;
  font-family: "Merriweather", serif;
  font-family: "Roboto Condensed", sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.header {
  width: 100%;
  border-bottom: solid 2px #333;
  background: rgb(34, 193, 195);
  background: -moz-linear-gradient(
    90deg,
    rgba(34, 193, 195, 1) 0%,
    rgba(249, 183, 42, 1) 100%
  );
  background: -webkit-linear-gradient(
    90deg,
    rgba(34, 193, 195, 1) 0%,
    rgba(249, 183, 42, 1) 100%
  );
  background: linear-gradient(
    90deg,
    rgba(34, 193, 195, 1) 0%,
    rgba(249, 183, 42, 1) 100%
  );
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr="#22c1c3",endColorstr="#f9b72a",GradientType=1);
}
h1,
h2 {
  text-align: center;
}
button {
  font-size: 50px;
  /* Сбрасываем дефолтные стили */
  border: none;
  outline: none;
  display: inline-block;
  text-align: center;
  text-decoration: none;
  cursor: pointer;
  border-radius: 50%;
  background-color: rgba(0, 0, 0, 0);
}
button:hover {
  /* box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2); */
  text-shadow: 0 1px 3px;
}
button:active {
  box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.2);
  text-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
}
.buttonWraper {
  display: flex;
  justify-content: center;
}
.content {
  /* border: 1px solid red; */
  height: 100%;
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}
.imgWraper {
  /* border: 1px solid blue; */
  position: flex;
  justify-content: center;
  overflow: hidden;
}
.imgWraper img {
  object-fit: cover;
        width: 100%;
        height: 100%;
}
</style>
