<template>
    <h3>Reaction Time: {{reactionTime}}ms</h3>
    <h3>{{rank}}</h3>
</template>

<script>
export default {
    props:['reactionTime'],
    data(){
        return{
            rank: null,

        }
    },
    mounted(){ // update rank when mounted to the DOM
        if(this.reactionTime < 250){
            this.rank = 'Ninja Fingers'
        }else if(this.reactionTime < 400){
            this.rank= 'Rapid Reflexes'
        }else{
            this.rank="Snail Pace"
        }
    }
}
</script>

<style>
.rank{
    color: #0faf87;
    font-weight: bold;
}
</style>