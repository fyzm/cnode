<template>
  <div class = "header">
    <router-link :to="{name:'root'}">
    <img src="../assets/cnodejs_light.svg" alt="">
    </router-link>
    <ul>
      <li><a href="#">首页</a></li>
      <li><a href="#">新手入门</a></li>
      <li><a href="#">API</a></li>
      <li><a href="#">关于</a></li>
      <li><a href="#">注册</a></li>
      <li><a href="#">登入</a></li>
    </ul>

  </div>
</template>

<script>
export default {
    name:"Header",  
}
</script>
<style scoped>
  .header{
    background-color: #444444;
    height: 50px;
  }
  img{
    max-width: 122px;
    margin-left:130px;
    margin-top:10px;
  }
  ul{
    list-style: none;
    float:right;
    margin: 4px;
  }
  li{
    display: inline-block;
    padding: 10px 15px;
  }
  a{
    text-decoration: none;
    color:#ccc;
    text-shadow: nonr;
  }
</style>
