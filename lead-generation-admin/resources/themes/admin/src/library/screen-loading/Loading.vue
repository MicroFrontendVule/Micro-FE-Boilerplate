<template>
  <div
    class="loading-screen"
    v-show="loading"
    v-bind:class="classes"
    v-bind:style="{backgroundColor:bc}"
  >
    <component v-if="customLoader" v-bind:is="customLoader"></component>
    <div v-else>
      <div class="loading-circle"></div>
      <p class="loading-text">{{text}}</p>
    </div>
  </div>
</template>
<script>
/* eslint-disable */
export default {
  data() {
    return {
      text: '',
      dark: false,
      classes: null,
      loading: false,
      background: null,
      customLoader: null,
    };
  },
  computed: {
    bc() {
      return (
        this.background ||
        (this.dark ? 'rgba(0,0,0,0.8)' : 'rgba(255,255,255,0.5)')
      );
    },
  },
};
</script>
<style scoped>
.loading-screen {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 99999999999;
  flex-direction: column;
  user-select: none;
  cursor: wait;
}
.loading-circle {
  width: 50px;
  height: 50px;
  border-radius: 100%;
  border: 2px solid transparent;
  border-left-color: #3389F0;
  animation: circleanimation 0.45s linear infinite;
}
.loading-text {
  margin-top: 15px;
  color: #3389F0;
  font-size: 14px;
  text-align: center;
}
@keyframes circleanimation {
  from {
    transform: rotateZ(0deg);
  }
  to {
    transform: rotateZ(360deg);
  }
}
</style>
