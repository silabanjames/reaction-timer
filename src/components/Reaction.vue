<template>
<p>Reaction Time: {{ score }} ms</p>
<p class="rank">{{ rank }}</p>
</template>

<script>
export default{
    data(){
        return{
            rank: null,
        }
    },
    props: ['score'],
    mounted(){
        if(this.score < 200){
            this.rank = 'God of speed'
        } else if (this.score < 500){
            this.rank = 'Rapid Reflexs'
        }
        else{
            this.rank= 'Hoam..., forget you do the game'
        }
    }
}
</script>

<style>
.rank{
    font-size: 1.8em;
    font-weight: 600;
    color: rgb(78, 152, 78);
    margin-top: 30px;
}
</style>