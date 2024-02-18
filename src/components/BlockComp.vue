<template>
    <div class="block" v-if="isShow" @click="stopTimer">click me</div>
</template>

<script>
export default{
    props: ["delay"],
    data(){
        return{
            isShow : false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted(){
        setTimeout(()=> {
            this.isShow  = true
            this.startTimer()
        }, this.delay)
    },
    updated(){
        console.log("Component Updated");
    },
    unmounted(){
        console.log("unmounted");
    },
   methods: {
    startTimer(){
        this.timer = setInterval(() => {
            this.reactionTime += 10
        }, 10)
    },
    stopTimer(){
        clearInterval(this.timer)
        console.log(this.reactionTime)
        this.$emit("end", this.reactionTime)
    }
   }

}
</script>

<style>
.block{
    width: 400px;
    border-radius: 10px;
    background-color: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>