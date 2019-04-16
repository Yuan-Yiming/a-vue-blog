<template>
  <div class="app-footer">
    <p><a v-bind:href="url" target="_blank">{{ footer }}</a></p>
  </div>
</template>

<script>
export default {
  name: 'AppFooter',
  data () {
    return {
      footer: 'Powered by Vue.js',
      url: 'https://vuejs.bootcss.com/',
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.app-footer {
  /*margin-top: 80px;*/
  width: 100%;
  background: #eee;
}
.app-footer p {
  width: 1200px;
  height: 80px;
  line-height: 80px;
  margin: 0 auto;
  text-align: center;
}
.app-footer p a {
  /*text-decoration: none;*/
  font-size: 18px;
  color: #000;
  font-weight: bold;
}
.app-footer p a:hover {
  color: #42b983;
}
</style>
