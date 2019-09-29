<template>
    <div class="home-page">
        <div class="header">
            <img src="../../img/avatar.jpg" alt="">
        </div>
        <div class="text">
            <p class="title">爱时尚精品屋</p>
            <p class="tips">公告：欢迎光临，流行爆款库存有限请尽早下单...</p>
        </div>
        <!-- 排列 导航 -->
        <!-- @ v-bind绑定事件 -->
        <div class="nav">
            <div class="nav-item" v-for="(item,index) in navList" :key={index} @click="sort(index)" :class="{active :index==currentIndex}">
               {{item}}
            </div>
        </div>
        <!-- 商品列表 -->
        <div class="list">
            <div class="good"></div>
        </div>
    </div>
</template>

<script>
import axios from "axios"
export default {
    name:'home',
    // 定义私有属性
    data:function(){
        return { 
            currentIndex:0,
            goodList:[],//保存所有的商品数据
            navList:['价格升序','价格降序','销量升序','销量降序'],
           
        }
    },
    // 定义所有的函数方法
    methods:{
        sort:function(index){
         this.currentIndex=index
        }
    },
    mounted:function(){
        axios.get("https://yantianfeng.com/api/goodList").then(res=>{
            console.log(res.data.goodList)
        })
    }
}

</script>
<style>
    .home-page .header{
        height: 200px;
        position: relative;
       background-position-x: center;
        background-size: cover;
        background-image: url("../../img/banner-2.png")
        
    }
    .home-page .header img{
        width: 80px;
        height: 80px;
        position: absolute;
        left: 50%;
        border-radius: 50%;
        bottom: -40px;
        margin-left: -40px;
    }
    .home-page>.text{
        margin:40px 0;
        line-height: 40px;
        text-align: center;
    }
    .home-page>.text .title{

        font-size: 20px;
        font-weight: bold;
    }
    .home-page>.text .tips{
        color: #888;
        font-size: 12px;
    }
     .home-page .nav .nav-item.active{
    color: red;
  }
  .home-page .nav .nav-item{
      float: left;
      margin-right: 5px;
  }
</style>