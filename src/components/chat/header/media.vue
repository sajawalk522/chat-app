<!-- eslint-disable prettier/prettier -->
<template>
  <div class="model-wrapper">
    <div class="model-inner">
      <div class="close" @click="close()">
        <img src="../../../assets/images/menu.svg" />
      </div>
      <div class="title">
        <h5>Media</h5>
      </div>
    </div>
  </div>
</template>
<!-- eslint-disable prettier/prettier -->
<script>
export default {
  name: "settingsModel",
  methods: {
    close() {
      this.$parent.media = false;
    },
  },
};
</script>
<!-- eslint-disable prettier/prettier -->
<style scoped>
.model-wrapper {
  display: block;
  background: rgba(0, 0, 0, 0.32941);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 999;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.model-wrapper .model-inner {
  width: 40%;
  padding: 15px;
  position: fixed;
}
.model-wrapper .title {
  background: #A7C040;
  height: 300px;
  border-radius: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.model-wrapper .title h5 {
  font-size: 18px;
  color: #000;
}
.close {
  position: absolute;
  right: 25px;
  top: 25px;
  background: #fff;
  height: 25px;
  width: 25px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  cursor: pointer;
}
.close img {
  width: 15px;
}
</style>