<template>
    <table class="pure-table pure-table-horizontal" style="margin:auto; width:80%; margin-top:2.5%">
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
            <tr v-for="Pos in [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]">
                <td v-if="PageNum*20+Pos<=PlayerCnt">{{PageNum*20+Pos}}</td>
                <td v-if="PageNum*20+Pos<=PlayerCnt">{{PlayerData[PageNum*20+Pos-1].name}}</td>
                <td v-if="PageNum*20+Pos<=PlayerCnt">{{PlayerData[PageNum*20+Pos-1].win}}</td>
                <td v-if="PageNum*20+Pos<=PlayerCnt">{{PlayerData[PageNum*20+Pos-1].lose}}</td>
                <td v-if="PageNum*20+Pos<=PlayerCnt">{{PlayerData[PageNum*20+Pos-1].rks}}</td>
            </tr>
        </tbody>
    </table>
    <div class="pure-g" style="margin-top:2.5%">
        <div class="pure-u-1-5"></div>
        <div class="pure-u-1-5" style="margin:auto;"><button class="pure-button pure-button-primary" @click="PageNum>0?PageNum--:null">上一页</button></div>
        <div class="pure-u-1-5" style="margin:auto;"><p style="margin:auto; white-space:nowrap;">第{{PageNum+1}}页,共{{Math.ceil(PlayerCnt/20)}}页</p></div>
        <div class="pure-u-1-5" style="margin:auto;"><button class="pure-button pure-button-primary" @click="PageNum<PlayerCnt/20-1?PageNum++:null">下一页</button></div>
        <div class="pure-u-1-5"></div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            PlayerData:JSON.parse(localStorage.getItem('PlayerData')),
            PageNum:0,
            PlayerCnt:JSON.parse(localStorage.getItem('PlayerData')).length
        }
    },
}
</script>

<style>

</style>
