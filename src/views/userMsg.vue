<template>
    <div class="userMsg">
        <navinfo></navinfo>
        <div class="main">
                <ul id="title" >
                  
                    <router-link to="/userMsg/orderPreview">
                    <li class="active" @click="select(0)"><h3>我的订单</h3></li>
                    </router-link>
               
                
                    <router-link to="/userMsg/historyPreview">
                    <li class="secondLi" @click="select(1)"><h3>历史订单</h3></li>
                    </router-link>
                </ul>
                
                <div class="showbox">
                    <el-scrollbar :style="{height: '100%'}">
                    <router-view></router-view>
                    </el-scrollbar>
                </div>
                
        </div>
    </div>
</template>
<script>
import navinfo from "../components/nav/nav";
export default {
    mounted(){
        if(this.$route.path=='/userMsg/historyPreview')
        {
            this.select(1);
        }
        let scroll = document.getElementsByClassName("el-scrollbar__wrap");
        console.log(scroll);
        scroll[0].style.overflowX = 'hidden';
    },
    methods: {
        select(num){
        var dv=document.getElementById("title");
        // var ularr=dv.getElementsByTagName("ul");
        var liarr=dv.getElementsByTagName("li");
           if(num==0){
               liarr[0].classList.add("active");
               liarr[1].classList.remove("active");
           }
           else{
               liarr[1].classList.add("active");
               liarr[0].classList.remove("active");
           }
        }
    },
     components:{
       navinfo
    }
}

</script>
<style lang="less" scoped>
    .userMsg{
        width: 100%;
        height: auto;
        background-color: #fafafa; 
        overflow: hidden;
    }
    .main {
        width: 1120px;
        margin: 30px auto; 
       
        h3 {
            display: inline-block;
        }
        p {
            height: 30px;
            line-height: 30px;
            font-size: 16px;
        }
    }
    #title{
        border: 1px solid #ebeef5;
        border-bottom: 0;
        box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
        margin: 0;
        padding: 0;
        text-decoration: none;
        background-color: #fafafa;
        li {
            display: inline-block;
            height: 80px;
            line-height: 80px;
            padding:0 30px;
            width: auto;
            color: #000;      
            background-color: #fafafa;
        } 
    }
    .active {
        background-color: #fff !important;
    }
    #test1 {
        float: right;
    }
    hr {
        background-color: rgb(211, 212, 211);
    }
    .showbox{
        overflow-x: hidden !important;
        width: 1120px;
        height: 600px;
        border-radius: 4px;
        border: 1px solid #ebeef5;
        box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
        border-top: 0;
        background-color: #fff;
        
    }
    .el-scrollbar__wrap {
  overflow-x: hidden !important; 
}
</style>
