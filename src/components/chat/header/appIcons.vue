<!-- eslint-disable prettier/prettier -->
<template>
  <div class="icon-wrapper">
    <div class="head-icon" @click="menuModel()">
      <img src="../../../assets/images/cross.svg" />
    </div>
    <div class="head-icon">
      <img src="../../../assets/images/full-page.svg" />
    </div>
    <div class="head-icon">
      <img src="../../../assets/images/menu.svg" />
    </div>
    <MenuModel v-if="menuOpen" />
  </div>
</template>
<!-- eslint-disable prettier/prettier -->
<script>
import MenuModel from "../header/menuModel.vue";
export default {
  name: "AppIcons",
  components: {
    MenuModel,
  },
  data() {
    return {
      menuOpen: false,
    };
  },
  methods: {
    menuModel() {
      this.menuOpen = !this.menuOpen;
    },
  
  },
};
</script>
<!-- eslint-disable prettier/prettier -->
<style scoped>
.icon-wrapper {
  display: flex;
  align-items: center;
  position: relative;
}
.icon-wrapper .head-icon {
  width: 15px;
  height: 15px;
  margin-left: 10px;
  cursor: pointer;
}
.icon-wrapper .head-icon img {
  width: 100%;
  height: 100%;
}
</style>
