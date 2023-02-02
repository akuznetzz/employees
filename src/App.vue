<template>
  <div class="wrapper" id="app">
    <router-view />
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0px;

  position: absolute;
  width: 1920px;
  /* height: 1202px; */
  /* min-height: 100%; */
  left: 0px;
  top: 41px;

}
</style>
