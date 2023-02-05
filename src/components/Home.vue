<template>
<div>
    <table class="pure-table" style="width:80%;margin:auto;margin-top:5%">
        <thead>
            <tr>
                <th><i class="bi bi-search"></i> 搜索</th>
            </tr>
        </thead>
    
        <tbody style="height:40%">
            <tr>
                <td>
                    <form class="pure-form" >
                        <input v-model="SearchKey" type="text" style="width:100%" class="pure-input-rounded" placeholder="在此输入游戏名">
                    </form>
                    <table v-if="SearchKey!=''" class="pure-table pure-table-bordered" style="margin:auto; width:100%;margin-top:2%;">
                        <thead>
                            <tr>
                                <th>排名</th>
                                <th>名字</th>
                                <th>胜场</th>
                                <th>败场</th>
                                <th>分数</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="SearchRes in Fsearch">
                                <th>{{ SearchRes.id+1 }}</th>
                                <th>{{ SearchRes.name }}</th>
                                <th>{{ SearchRes.win }}</th>
                                <th>{{ SearchRes.lose }}</th>
                                <th>{{ SearchRes.rks }}</th>
                            </tr>
                        </tbody>
                    </table>
                </td>
            </tr>
        </tbody>
    </table>
    <table class="pure-table" style="width:80%;margin:auto;margin-top:2%">
        <thead>
            <tr>
                <th><i class="bi bi-info-lg"></i> 常见问题</th>
            </tr>
        </thead>
    
        <tbody style="height:40%">
            <tr>
                <td>
                    应该没有什么问题
                </td>
            </tr>
        </tbody>
    </table>
</div>
<div class="footer_box">
    <div class="align_center">
        <p>Made by <a href="https://github.com/firesonz">FiresonZ</a></p>
    </div>
</div>
</template>

<script>
export default {
    data(){
        return{
            SearchKey:'',
            PlayerData:JSON.parse(localStorage.getItem('PlayerData'))
        }
    },
    computed:{
        Fsearch(){
        if(this.SearchKey){
            return this.PlayerData.filter((value)=>{
                return value.name.includes(this.SearchKey);
        });
      }
    }
  }
}
</script>

<style>
.footer_box{
    bottom: 0%;
    text-align: center;
}
</style>
