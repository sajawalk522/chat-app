<!-- eslint-disable vue/no-textarea-mustache -->
<!-- eslint-disable prettier/prettier -->
<template>
  <div class="messaging">
    <!-- conversation section  -->
    <div class="conversation-main" ref="scrollFun">
      <section class="user-chat">
        <div class="conversation_wrapper">
          <div class="conversation-img">
            <p>JB</p>
          </div>
          <div class="conversation-title">
            <h5>Joe Bloggs</h5>
          </div>
          <span>12:23</span>
        </div>
        <div class="message-text">
          <div class="text">
            <p>Can you share those photos from last weeks press event?</p>
          </div>
        </div>
      </section>

      <section class="mychat">
        <div class="message-text">
          <div class="text">
            <p>OK! Just a moment.</p>
          </div>
        </div>
      </section>
      <section class="mychat">
        <div class="message-text">
          <div class="text">
            <p>Here you go?</p>
          </div>
        </div>
      </section>
      <section v-for="(txt, index) in chat" :key="index" :class="{ mychat: txt.user == 'me' }">
        <div class="message-text">
          <a class="file" v-if="txt.file" :href="downloadLink" download>
            <a>{{ txt.file.name }}</a>
            <p>{{ txt.file.size }}</p>
          </a>
          <div class="text">
            <p>{{ txt.text }}</p>
          </div>
        </div>
      </section>
    </div>
    <!-- conversation section  -->
    <!-- footer section  -->
    <div class="bottom-wrapper">
      <div class="uplaoded-wrapper" v-if="progress > 1">
        <div class="inner">
          <p>{{ fileName }} ({{file.size}})</p>
          <div class="img" @click="close">
            <img src="../../../assets/images/menu.svg" />
          </div>
        </div>
        <div class="progress-bar">
          <progress id="file" :value="progress" max="100">{{ progress }}%</progress>
        </div>
        <h1>{{ progress }}</h1>
      </div>
      <div class="text-message">
        <textarea v-model="text" id="msg" name="text" rows="5" placeholder="Type your message..."></textarea>
      </div>
      <div class="footer">
        <label for="fileInput" class="link-image">
          <input id="fileInput" type="file" @change="handleChange" accept=".zip, .rar, .7zip" />
          <img src="../../../assets/images/link.png" />
        </label>
        <div>
          <button class="btn" v-if="text || progress == 100" @click="send">Send</button>
          <button class="btn disable" v-else>Send</button>
        </div>
      </div>
    </div>
    <!-- footer section  -->
  </div>
</template>
<!-- eslint-disable prettier/prettier -->
<script>
export default {
  name: "AppConversation",
  data() {
    return {
      text: null,
      chat: [],
      //
      progress: 0,
      downloadLink: "",
      file: null,
    };
  },
  methods: {
    close() {
      this.file = null;
      this.progress = 0;
      this.downloadLink = "";
    },
    formatBytes(bytes, decimals = 2) {
      if (!+bytes) return "0 Bytes";
      const k = 1024;
      const dm = decimals < 0 ? 0 : decimals;
      const sizes = ["Bytes", "KB", "MB", "GB", "TB", "PB", "EB", "ZB", "YB"];
      const i = Math.floor(Math.log(bytes) / Math.log(k));
      return `${parseFloat((bytes / Math.pow(k, i)).toFixed(dm))} ${sizes[i]}`;
    },
    send() {
      // if (!this.text || !this.file) return;
      var chat = {};
      chat.name = "test";
      chat.user = "me";
      chat.text = this.text;
      chat.file = this.file;
      this.chat = [...this.chat, chat];
      //
      this.progress = 0;
      this.downloadLink = "";
      this.file = null;
      this.text = "";
      this.$refs.scrollFun.scrollTop = this.$refs.scrollFun.scrollHeight;
    },
    handleChange(e) {
      this.progress = 0;
      const newFile = e.target.files[0];
      var file = {};
      file.name = newFile.name;
      file.size = this.formatBytes(newFile.size);
      this.file = file;
      this.fileName = newFile.name;
      // selected file read
      var progCheck = (val) => {
        this.progress = val;
      };
      var reader = new FileReader();
      reader.onprogress = function (data) {
        if (data.lengthComputable) {
          var progress = parseInt((data.loaded / data.total) * 100, 10);
          console.log(progress);
          progCheck(progress);
        }
      };
      reader.onload = (e) => {
        this.downloadLink = e.target.result;
      };
      reader.readAsDataURL(e.target.files[0]);
      e.target.value = "";
    },
  },
};
</script>
<!-- eslint-disable prettier/prettier -->
<style scoped>
.conversation-main {
  padding: 15px;
  height: 200px;
  overflow-y: scroll;
  scroll-behavior: smooth;
}
.conversation-main::-webkit-scrollbar {
  display: none;
}
.conversation-main {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
.user-chat .message-text {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-direction: column;
}
.mychat .message-text {
  display: flex;
  justify-content: center;
  align-items: flex-end !important;
  flex-direction: column;
}
.conversation-main .message-text .text {
  padding: 6px 5px 6px 40px;
  text-align: right;
}
.conversation-main .message-text .file {
  border-radius: 5px;
  background: #e7e6e6;
  margin: 7px 5px 0px 40px;
  padding: 10px;
  cursor: pointer;
  text-decoration: none;
}
.conversation-main .message-text .file a {
  font-size: 16px;
  color: #1d95e0;
  text-decoration: none;
  word-break: break-all;
}
.conversation-main .message-text .file p {
  font-size: 12px;
  color: #000;
  line-height: 1.3;
  margin-top: 5px;
  word-break: break-all;
}
.conversation-main .message-text .text p {
  font-size: 16px;
  color: #000;
  text-align: left;
  line-height: 1.3;
}
.user-chat .conversation_wrapper {
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
.mychat .conversation_wrapper {
  display: flex;
  justify-content: flex-end !important;
  align-items: center;
}
.conversation_wrapper .conversation-img {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background: #8fded9;
  display: flex;
  justify-content: center;
  align-items: center;
}
.conversation_wrapper .conversation-img p {
  font-size: 14px;
}
.conversation_wrapper .conversation-title {
  margin-left: 10px;
}
.conversation_wrapper .conversation-title h5 {
  font-size: 16px;
  font-weight: 600;
}
.conversation_wrapper span {
  font-size: 12px;
  font-weight: 400;
  margin-left: 6px;
}
.text-message {
  padding: 15px;
  border-top: 1px solid #c6c6c6;
  display: flex;
  justify-content: center;
}
.text-message textarea {
  outline: none!important;
   resize: none!important;
  padding: 15px;
  border: 2px solid #c6c6c6;
  border-radius: 10px;
  width: 92%;
  background: #fff;
  resize:vertical; /* Chrome */
}
.text-message textarea:focus {
  outline: none !important;
  border-color: #a7c040;
  width: 92% !important;
  -webkit-text-size-adjust: none!important;
}
/* footer css  */
.footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  border-top: 1px solid #c6c6c6;
}
.footer .link-image {
  width: 25px;
  position: relative;
  cursor: pointer;
}
.footer .link-image input {
  display: none;
}
.footer .link-image img {
  width: 100%;
}
.footer .btn {
  outline: none;
  border: none;
  font-size: 14px;
  background: #a7c040;
  border-radius: 3px;
  color: #000;
  padding: 10px 15px;
  cursor: pointer;
}
.uplaoded-wrapper {
  padding: 15px;
  border-top: 1px solid #c6c6c6;
}
.uplaoded-wrapper .inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.uplaoded-wrapper .inner p {
  font-size: 14px;
  color: #000;
  width: 70%;
  line-height: 1.3;
  word-break: break-all;
}
.uplaoded-wrapper .inner .img {
  width: 15px;
  height: 15px;
  cursor: pointer;
}
.uplaoded-wrapper .inner .img img {
  width: 100%;
  height: 100%;
}
.progress-bar {
  margin-top: 10px;
}
.progress-bar progress {
  width: 85%;
  height: 10px;
  color: lightblue;
  border: none;
  background: #d9d9d9;
  border-radius: 20px;
}

progress::-moz-progress-bar {
  background: lightcolor;
}

progress::-webkit-progress-value {
  background: #a7c040;
  border-radius: 20px;
}

progress::-webkit-progress-bar {
  background: #d9d9d9;
  border-radius: 20px;
}
.disable {
  background-color: #e7e6e6 !important;
  color: #b9b8b8 !important;
}
</style>
