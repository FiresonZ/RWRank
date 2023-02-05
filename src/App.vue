<template>
  <div class="pure-menu pure-menu-horizontal">
    <a href="" class="pure-menu-heading pure-menu-link" style="width:35px;weight:auto;"><img src="./assets/logo1.png" style="width:35px;weight:auto;"></a>
    <ul class="pure-menu-list">
        <li :class="ComName==='Home'?'pure-menu-selected pure-menu-item':'pure-menu-item'"><a href="" @click.prevent="ComName='Home'" class="pure-menu-link"><i class="bi bi-house-fill"></i> 首页</a></li>
        <li :class="ComName==='Rank'?'pure-menu-selected pure-menu-item':'pure-menu-item'"><a href="" @click.prevent="ComName='Rank'" class="pure-menu-link"><i class="bi bi-list-ol"></i> 排名</a></li>
        <li :class="ComName==='About'?'pure-menu-selected pure-menu-item':'pure-menu-item'"><a href="" @click.prevent="ComName='About'" class="pure-menu-link"><i class="bi bi-info-circle-fill"></i> 关于</a></li>
    </ul>
    <button @click="DataRefresh" class="pure-button pure-button-primary" style="float:right; margin-right:2%; margin-top:0.5%">更新数据</button>
</div>
<component :is="ComName" v-if="DataReady"></component>
</template>

<script>
import Rank from './components/Rank.vue'
import About from './components/About.vue'
import Home from './components/Home.vue'
import axios from 'axios'
export default{
  data(){
    return{
      ComName:'Home',
      DataReady:false,
    }
  },
  components:{Rank,About,Home},
  created:function(){
    this.ComName = localStorage.getItem('LstPage');
    if(localStorage.getItem('PlayerData')==null){
      axios.get(Config.API_URL)
      .then((res)=>{
        localStorage.setItem('PlayerData',JSON.stringify(res.data));
      })
      .catch((res)=>{
        console.log(res);
      })
    }
  },
  mounted:function(){
    this.DataReady=true;
  },
  updated:function(){
    localStorage.setItem('LstPage',this.ComName);
  },
  methods:{
    DataRefresh(){
      axios.get(Config.API_URL)
      .then((res)=>{
        localStorage.setItem('PlayerData',JSON.stringify(res.data));
      })
      .catch((res)=>{
        console.log(res);
      })
      location.reload();
    }
  }
}
</script>

<style>
@import url(./assets/pure/pure-min.css);
@import url(./assets/bootstrap-icons/bootstrap-icons.css);
</style>
