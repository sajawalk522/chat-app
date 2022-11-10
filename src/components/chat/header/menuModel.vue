<!-- eslint-disable prettier/prettier -->
<template>
  <div>
    <div class="menu-wraper">
      <ul>
        <li @click="mediaModel()">Media</li>
        <li @click="settingModel()">Settings</li>
      </ul>
    </div>
    <MediaModel v-if="media"/>
    <SettingsModel v-if="setting"/>
  </div>
</template>
<!-- eslint-disable prettier/prettier -->
<script>
import SettingsModel from "../header/settings.vue";
import MediaModel from "../header/media.vue";
export default {
  components: {
    SettingsModel,
    MediaModel
  },
  data() {
    return {
      setting: false,
      media: false,
    };
  },
  methods: {
    settingModel() {
      this.setting = !this.setting;
    },
     mediaModel() {
      this.media = !this.media;
    },
  },
};
</script>
<!-- eslint-disable prettier/prettier -->
<style>
.menu-wraper {
  position: absolute;
  top: 24px;
  right: 0;
  background: #fff;
  border: 1px solid #eee;
  border-radius: 8px;
  width: 100px;
  padding: 10px 15px;
  box-shadow: 0 0 10px #0000001a;
}
.menu-wraper ul {
  list-style: none;
}
.menu-wraper ul li {
  padding: 10px 0;
  font-size: 14px;
  color: #000;
  cursor: pointer;
}
</style>