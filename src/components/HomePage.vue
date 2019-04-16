<template>
  <div id="home">
    <h2>博客列表<input type="" name="" v-model="query"></h2>
    <div v-for="blog in filteredBlogs" class="item">
      <h3><router-link :to="{name: 'ReadBlog', params: {id: blog.id}}">{{ blog.title }}</router-link></h3>
      <p class="blog-info"><span >作者：{{ blog.author }}</span> | 
        <span>发表：{{ blog.createdTime }}</span> | 
        <span>标签：<span v-for="tag in blog.tags">{{ tag }}{{ blog.tags.indexOf(tag) == blog.tags.length-1 ? "" : "," }}  </span></span></p>
      <p>{{ blog.content | cutContent }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  methods: {
  },
  props: ["blogs"],
  data () {
    return {
      query: '',
    }
  },
  computed: {
    filteredBlogs: function() {
      return this.blogs.filter((blog) => {
        return blog.title.match(this.query);
      })
    }
  },
  filters: {
    cutContent: function (content) {
      var clearContent = content.replace(/<[^>]*>/g, '');
      if (clearContent.length > 140) {
        return clearContent.slice(0,140) + ' ......';
      } else {
        return clearContent + ' ......';
      } 
    },
  }
};
</script>

<style scoped>
#home {
  /*background-color: red;*/
  min-height: 480px;
  padding: 20px;
}
h2 {
  width: 70%;
  margin: 0 auto;
  font-weight: bold;
  /*text-align: center;*/
  margin-bottom: 20px;
  /*border: 1px solid red;*/
}
input {
  margin-left: 30px;
  color: #424242;
  width: 220px;
  height: 30px;
  padding: 0 10px 0 34px;
  line-height: 30px;
  display: inline-block;
  border: none;
  outline: none;
  border-radius: 15px;
  font-size: 18px;
  vertical-align: -1px;
  /*background-color: rgba(255,255,255,.5);*/
  /*background-color: ;*/
  border: 1px solid #8a8a8a;
  opacity: 0.5;
  background: #fff url('../assets/search-icon2.svg') no-repeat;
  background-size: 16px 16px;
  background-position: 10px 7px;
  vertical-align: 3px;
}
input:focus {
  opacity: 1;
  width: 320px;
  border-color: #42b983;
}
.item {
  width: 70%;
  margin: 20px auto;
  padding: 20px;
  background-color: rgba(240,240,240,0.8);
}
.item h3 {
  margin-bottom: 10px;
}
.item h3 a {
  color: #42b983;
  text-decoration: none;
}
.item .blog-info {
  margin: 10px 0;
  font-size: 12px;
  color: #999;
}

</style>
