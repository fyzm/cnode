<template>
  <div class="UserInfo">
    <div class="loading" v-if = "isLoading">
      <img src="../assets/loading.gif">
    </div>
    <div class="userInformation" v-else>
      <section>
        <img :src="userinfo.avatar_url">
        <span>{{userinfo.loginname}}</span>
        <p>
          {{userinfo.score}}积分
        </p>
        <p>
          注册时间:{{userinfo.create_at | formatDate }}
        </p>
      </section>
      <div class="replies">
        <p>回复的主题</p>
        <ul>
          <li v-for = "item in userinfo.recent_replies" :key="item.id">
              <router-link :to="{
                name:'post_content',
                params:{
                  id:item.id
                }
              }">
                {{item.title}}
              </router-link>
          </li>
        </ul>
      </div>
      <div class="topics">
        <p>创建的主题</p>
      </div>

    </div>
  </div>
</template>
<script>
export default {
    name:"UserInfo",
  data(){
    return {
      isLoading:false,
      userinfo:{}
    }
  },
  methods:{
    getData(){
      this.$http.get(`https://cnodejs.org/api/v1/user/${this.$route.params.name}`)
        .then(res=>{
          console.log(res);
          this.isLoading = false;//加载成功，去除动画
          this.userinfo = res.data.data;
          console.log(this.userinfo)
        })
        .catch(function(err){
          //处理返回失败的问题
          console.log(err)
        })
    }
  },
  beforeMount(){
    this.isLoading = true;//加载成功之前显示加载动画
    this.getData();//页面加载钱获取数据
  }
}
</script>
