<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <div id="app">
    <header @mousedown="startDrag">
      <nav class="navbar" id="custom-title-bar">
        <div class="navbar-left">QMCL</div>
        <div class="navbar-right">
          <img class="yellow-button" @click="minimizeWindow" @mousedown.stop src="./assets/minimize.png">
          <div class="button-spacing"></div>
          <img class="red-button" @click="closeWindow" @mousedown.stop src="./assets/close.png">
        </div>
      </nav>
    </header>
    <main>

    </main>
  </div>
</template>
<script>
import { ref } from 'vue';
import { appWindow } from '@tauri-apps/api/window';
export default {
  data() {
    return {
      message: 'Hello Vue!'
    };
  },
  methods: {
    async minimizeWindow() {
      console.log('minimizeWindow');
      await appWindow.minimize();
    },
    async closeWindow() {
      console.log('closeWindow');
      await appWindow.close();
    },
    async startDrag() {
      console.log('startDrag');
      await appWindow.startDragging();
    }
  }
};
</script>

<style scoped>
#app {
  max-width: unset; /* 取消最大宽度 */
  margin: unset; /* 取消外边距 */
  padding: unset; /* 取消内边距 */
  font-weight: unset; /* 取消字体粗细 */
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
