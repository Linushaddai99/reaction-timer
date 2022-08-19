<template>
  <div class="result">
    <p>Reaction Time: {{ score }}ms</p>
    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
import { thisExpression } from '@babel/types'

export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score < 250){
            this.rank = 'Ninger Finger!!'
        } else if(this.score < 400) {
            this.rank = 'Rapid Reflexes!'
        } else {
            this.rank = 'Snail Pace...'
        }
    }
}
</script>

<style>
    .result {
        width: 400px;
        border-radius: 10px;
        background-color: orangered;
        text-align: center;
        padding: 80px 0;
        margin: 40px auto;
    }

    .rank {
        font-size: 1.44rem;
        color: white;
        font-weight: bold;
    }
</style>