<template>
  <div id="app">
    <header>
      <h2>Universal Vocabulary Test</h2>
    </header>
    <FileUpload v-if="mode == 'read'" @done="startTest" />
    <Test :vocs="vocs" v-else @again="mode = 'read'"/>
  </div>
</template>

<script>
export default {
  name: "app",
  components: {
    'FileUpload': () => import('@/components/FileUpload.vue'),
    'Test': () => import('@/components/Test.vue')
  },
  data() {
    return {
      mode: "read",
      vocs: {}
    };
  },
  methods: {
    startTest(wb) {
      this.mode = "test";
      this.vocs = wb;
    }
  }
};
</script>



<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
header {
  background: #19232c;
  color: rgba(255, 255, 255, 0.959);
  height: 60px;
  margin-bottom: 3vh;
  padding: 15px;
}
</style>
