<!-- eslint-disable prettier/prettier -->
<template>
  <div class="chat-app">
    <AppHeader />
    <AppMessage/>
  </div>
</template>
<!-- eslint-disable prettier/prettier -->
<script>
import AppHeader from "../chat/header/appHeader.vue";
import AppMessage from "../chat/message/conversation.vue";
export default {
  name: "ChatComponent",
  components: {
    AppHeader,
    AppMessage
  },
};
</script>
<!-- eslint-disable prettier/prettier -->
<style scoped>

.chat-app{
  background: #fff;
  border-radius: 10px;
}
</style>
