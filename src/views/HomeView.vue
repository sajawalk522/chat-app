<template>
  <div class="main-wrapper">
    <div class="container">
      <ChatComponent />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import ChatComponent from "../components/chat/index.vue";
export default {
  name: "HomeView",
  components: {
    ChatComponent,
  },
};
</script>
<style scoped>
.main-wrapper {
  background: #e7e6e6;
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
.container {
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
}
</style>
