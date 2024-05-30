<template>
  <header>
    <img class="landscape-banner" src="@/assets/images/landscape-banner.jpg">
    <img class="portrait-banner" src="@/assets/images/portrait-banner.png">
  </header>
</template>

<style>
header {
  width: 100%;
  height: 100vh;
  background-color: black;
}

.landscape-banner {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

@media screen and (orientation: landscape) {
  .landscape-banner {
    display: block;
  }

  .portrait-banner {
    display: none;
  }
}

.portrait-banner {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

@media screen and (orientation: portrait) {
  .landscape-banner {
    display: none;
  }

  .portrait-banner {
    display: block;
  }
}
</style>