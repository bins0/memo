<template>
    <div>
        <h2>메모</h2>
    <table>
        <tr v-for="(memo,i) in memo" :key=i>
            <td>{{memo.id}}</td>
            <td>{{memo.writer}}</td>
            <td @click="$router.push(`/list/${memo.id}`)">{{memo.title}}</td>
        </tr>
    </table>
    </div>
</template>

<script>
export default {
    data(){
        return({
            memo:[]
        })
    },
    created() {
        this.$http.get('/api/memo')
        .then((response)=>{
            this.memo = response.data;
        })
    }
    
}
</script>