<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>
</template>

<script>
export default{
    props: ['delay'],
    data(){
        return{
            showBlock: false,
            timer: null,
            reactionTime: 0,
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showBlock = true,
            this.startTimer()
        }, this.delay)
    },
    methods:{
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime += 10
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.showBlock = false
            console.log(this.reactionTime)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style scoped>
.block{
    background-color: rgb(67, 134, 67);
    color: rgb(255, 255, 255);
    padding: 60px 30px;
    margin: 40px auto;
    width: 400px;
    text-align: center;
    border-radius: 20px;
}
</style>