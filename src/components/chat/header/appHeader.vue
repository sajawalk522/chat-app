<!-- eslint-disable prettier/prettier -->
<template>
  <div class="header">
    <User/>
    <AppIcons/>
  </div>
</template>
<!-- eslint-disable prettier/prettier -->
<script>
import User from "../header/user.vue"
import AppIcons from "../header/appIcons.vue"
export default {
  name: "AppHeader",
  components:{
    User,
    AppIcons
  }
};
</script>
<!-- eslint-disable prettier/prettier -->
<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 15px;
  border-bottom: 1px solid #eee;
}
</style>
