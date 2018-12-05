<template>
  <div class="PostList">
    <div class = "loading" v-if="isLoading">
      <img src="../assets/loading.gif" alt="">
    </div>
    <div class="posts" v-else>
      <ul>
        <li>
          <div class =toobar>
            <span>全部</span>
            <span>精华</span>
            <span>分享</span>
            <span>问答</span>
            <span>招聘</span>
          </div>
        </li>
        <li v-for="post in posts" :key="post.id">

        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PostList',
  data () {
    return {
      
    }
  },
  methods:{
    getData(){
      this.$http.get('https://cnodejs.org/api/v1/topics',{
        params:{
          page:this.postpage,
          limit:20
        }
      })
        .then(res=>{
          this.isLoading = false;
          this.posts = res.data.data;
        })
        .catch(function(err){
          console.log(err)
        })
      },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
