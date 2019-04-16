<template>
  <div id="read-blog">
    <h2>{{ blog.title }}</h2>
    <p class="info"><span >作者：{{ blog.author }}</span> | 
        <span>发表：{{ blog.createdTime }}</span> | 
        <span>标签：<span v-for="tag in blog.tags" class="tag">{{ tag }}</span></span></p>
      <p class="content" v-html="blog.content"></p>
  </div>
</template>

<script>
export default {
  name: 'ReadBlog',
  props:["blogs"],
  computed:{
    blog: function () {
      for (var i = 0; i < this.blogs.length; i ++) {
        if (this.blogs[i].id == this.id) {
          return this.blogs[i];
        }
      }
    },
  },
  data () {
    return {
      id: '',
    }
  },
  created() {
    this.id = this.$route.params.id;
  },
};
</script>

<style scoped>
#read-blog {
  width: 70%;
  margin: 100px auto 30px auto;
  background-color: #eee; 
  padding: 30px 50px;
  min-height: 360px;
  line-height: 1.8em;
}
h1, h2 {
  font-weight: normal;
  margin-bottom: 20px;
  font-weight: bold;
  color: #424242;
  /*border-bottom: 1px solid #424242;*/
  /*text-align: center;*/
}
.info {
  margin: 10px 0;
  font-size: 13px;
  color: #42b983;
  line-height: 1em;
}
.tag {
  display: inline-block;
  padding: 3px 5px;
  /*border: 1px solid red;*/
  background-color: #42b983;
  /*opacity: 0.9;*/
  color: #fff;
  border-radius: 10px;
  margin-right: 5px;
  font-size: 12px;
}
.content {
  margin-top: 20px;
}

</style>
