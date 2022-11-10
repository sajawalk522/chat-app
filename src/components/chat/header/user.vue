<!-- eslint-disable prettier/prettier -->
<template>
  <section class="user_wrapper">
    <div class="user-img">
      <p>JB</p>
    </div>
    <div class="user-title">
      <h5>Joe Bloggs</h5>
    </div>
  </section>
</template>
<!-- eslint-disable prettier/prettier -->
<script>
export default {
  name: "UserComponent",
};
</script>
<!-- eslint-disable prettier/prettier -->
<style scoped>
.user_wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
}
.user_wrapper .user-img {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background: #8fded9;
  display: flex;
  justify-content: center;
  align-items: center;
}
.user_wrapper .user-img p {
  font-size: 14px;
}
.user_wrapper .user-title{
  margin-left: 10px;
}
.user_wrapper .user-title h5 {
  font-size: 16px;
  font-weight: 600;
}
</style>
