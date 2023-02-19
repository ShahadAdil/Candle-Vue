<script></script>

<template>
  <div id="wrapper-hero">
    <!-- <img src="../assets/img/candle.webp" class="img-fluid" alt="pic" height="40vh"/> -->

    <img class="HeroImg" />
    <div class="centered"></div>
  </div>
</template>

<style>
#wrapper-hero img {
  margin: 0 auto;

  height: 600px;
  width: 200vh;
  overflow-x: hidden;
}

.HeroImg {
  background: linear-gradient(rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.1)),
    url(../assets/img/cover.webp);
  background-repeat: no-repeat;
  background-size: cover;
  overflow: hidden;
  background-position: center;
}
.centered {
  position: absolute;
  top: 70%;
  left: 50%;
  transform: translate(-50%, 50%);
  color: rgb(168, 102, 57);
}

@media screen and (min-width: 360px) and (max-width: 980px) {
  body,
  html {
    overflow-x: hidden;
  }
}
</style>
