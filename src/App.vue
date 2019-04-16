<template>
  <!-- 只能有一个根标签 -->
  <div id="app">
    <app-header :show-home-page="showHomePage"
                :show-add-blog="showAddBlog"
                :show-about="showAbout"
                ></app-header>
    <div class="main">
      <!-- 调用其他组件 -->
    <!-- <home-page v-show="showHomePage" ref="homepage"></home-page>
    <add-blog v-show="showAddBlog" ref="addblog" @commit-to-add-blog="commitToAddBlog"></add-blog> -->
    <router-view @commit-to-add-blog="commitToAddBlog" :blogs="blogs" ></router-view>
    </div>
    <app-footer/>    
  </div>
</template>

<script>
// 调用其他组件
// import AddBlog from "./components/AddBlog"
import AppHeader from "./components/AppHeader"
import AppFooter from "./components/AppFooter"
// import HomePage from "./components/HomePage"

var blogs = [
      {
        id:28263736876275,
        title: "在vue2中使用CKEditor4第三方库",
        content: "\
        <p>1.在index.html中引入ckeditor.js文件：<br />\
        &lt;pre&gt;&lt;script src=&#39;./static/ckeditor.js&#39;&gt;&lt;/script&gt;&lt;/pre&gt;</p><br>\
        <p>2.在webpack.base.conf.js中配置：<br />\
        external: {<br />\
        &nbsp;&nbsp; &nbsp;&quot;CKEDITOR&quot;: &quot;window.CKEDITOR&quot;<br />\
        }</p><br>\
        <p>3.在CKEditor.vue子组件中创建CKEditor编辑框：<br />\
        3.1 在&lt;template&gt;模板中添加&lt;textarea id=&#39;editor&#39;&gt;&lt;/textarea&gt;标签（占位，需要添加id）<br />\
        3.2 在computed钩子函数中创建：<br />\
        this.editor = CKEDITOR.(&#39;editor&#39;, {}); &nbsp;// 第一个参数为&lt;textarea&gt;标签的id，第二个参数为文本框的样式</p><br>\
        <p>4.给文本框赋值/获取文本框的值：<br />\
        this.editor.setData(&#39;value&#39;); &nbsp;// 赋值<br />\
        this.editor.getData(); &nbsp; &nbsp; &nbsp; &nbsp; // 获值</p>",
        author: "小明",
        tags: ["Vue.js"],
        createdTime: "2019年3月24日 13:12:34"
      },
      {
        id: 1,
        title: "原生js给元素添加class属性1",
        content: "原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性",
        author: "小明",
        tags: ["Vue.js","JQuery"],
        createdTime: "2019年2月14日 13:12:34"
      },
      {
        id: 2,
        title: "原生js给元素添加class属性2",
        content: "原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性",
        author: "小明",
        tags: ["Vue.js","JQuery"],
        createdTime: "2019年2月13日 13:12:34"
      },
      {
        id: 3,
        title: "原生js给元素添加class属性3",
        content: "原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性",
        author: "小明",
        tags: ["Vue.js","JQuery"],
        createdTime: "2019年2月12日 13:12:34"
      },
      {
        id: 4,
        title: "原生js给元素添加class属性4",
        content: "原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性原生js给元素添加class属性",
        author: "小明",
        tags: ["Vue.js","JQuery"],
        createdTime: "2019年2月11日 13:12:34"
      },];

export default {
  name: 'App',
  // 注册其他组件
  components: {
    // 'add-blog': AddBlog,
    'app-header': AppHeader,
    'app-footer': AppFooter,
    // 'home-page': HomePage,
  },
  mounted() {
    this.show(this.$route.name);
  },
  watch: {
    $route (to, from) {
      this.show(this.$route.name);
    }
  },
  methods: {
    show: function (name) {
      this.showHomePage = 0;
      this.showAddBlog = 0;
      this.showAbout = 0;
      if (name == 'HomePage') {
        this.showHomePage = 1;
      } else if (name == 'AddBlog') {
        this.showAddBlog = 1;
      } else if (name == 'About'){
        this.showAbout = 1;
      }
    },
    commitToAddBlog: function (blog) {
      this.blogs.unshift(blog);
    },
  },
  
  data () {
    return {
      showHomePage: 0,
      showAddBlog: 0,
      showAbout: 0,
      blogs: blogs,
    }
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  /*margin: 10px;*/
  /*height: 100%;*/
}
.main {
  margin-top: 70px;
  min-height: 460px;
}
</style>
