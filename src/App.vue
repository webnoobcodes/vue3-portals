<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <button @click='showNotification'>Trigger Notification!</button>
  <Teleport v-if="isOpen" to='#notification-target'>
    <div class='notification'>
      This is a notification!
    </div>
  </Teleport>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data: () => {
    return {
      isOpen: false,
      timeout: false
    }
  },
  components: {
    HelloWorld
  },
  methods: {
    showNotification() {
      this.isOpen = true;

      clearTimeout(this.timeout)

      this.timeout = setTimeout(() => {
        this.isOpen = false
      }, 3000)
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#notification-target {
  position: absolute;
  top: 16px;
  right: 16px;
}

.notification {
  width: 300px;
  padding: 32px;
  margin-bottom: 16px;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1.4rem;
  color: #fefefe;
  background-color: #333;
}
</style>
