<template>
    <div>
        <h3>글작성공간</h3>
      
            <input type="text" v-model="title"><br>
            <textarea cols="30" rows="10" v-model="memo"></textarea><br>
           <button @click="addmemo">전송</button>
        
    </div>
</template>

<script>
export default {
    data(){
        return{
            title: "",
            memo: ""
        }
    },
    methods : {
        addmemo() {
            this.$http.post('/api/memo',{
                data : {
                    title:this.title,
                    memo : this.memo
                }
            }).then((response)=>console.log(response.data))
            this.$router.push('/')
        }
    }
}
</script>