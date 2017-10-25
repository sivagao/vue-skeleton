<template>
  <div id="app" class="app-container">
    <div class="app-side">
      <side-menu></side-menu>
    </div>
    <div class="app-main">
      <h1>{{ msg }}</h1>
      <el-button @click.native="startHacking">Yes!</el-button>
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import SideMenu from './components/SideMenu'

export default {
  name: 'app',
  components: {SideMenu},
  data () {
    return {
      msg: 'Want something new?'
    }
  },
  methods: {
    startHacking () {
      this.$notify({
        title: 'Shhh',
        message: 'Just be patient...',
        duration: 6000
      })
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 30px auto;
  padding: 0 20px;
  max-width: 1600px;
  min-width: 600px;
  display: flex;
}
.app-side {
  flex-basis: 200px;
}
.app-main {
  margin-left: 20px;
}
</style>
