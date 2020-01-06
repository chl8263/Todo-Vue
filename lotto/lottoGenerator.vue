<template>
    <div>
       <div>Number</div>
       <div id="result">
           <lotto-ball v-for="ball in winballs" :key="ball" v-bind:number=ball></lotto-ball>
       </div>
       <div>Bonus</div>
       <lotto-ball v-if="bonus" v-bind:number="bonus"></lotto-ball>
       <button v-if="redo" @click="onClickRedo">One more time!</button>
    </div>
</template>
 
<script>
    import LottoBall from './LottoBall';

    function getWinNUmbers(){
        const candidate = Array(45).fill().map((v, i) => i+1);
        const shuffle = [];
        while(candidate.length > 0){
            shuffle.push(candidate.splice(Math.floor(Math.random() * candidate.length),1)[0]);
        }
        const bonusNumber = shuffle[shuffle.length - 1];
        const winNumbers = shuffle.slice(0, 6).sort((p, c) => p - c);
        return [...winNumbers, bonusNumber];
    }
    const timeouts= [];
    export default {
        components: {
            'lotto-ball': LottoBall
        },
        data(){
            return {
                winNumbers: getWinNUmbers(),
                winballs: [],
                bonus : null,
                redo : false,
            }
        },
        computed: {
        },
        methods:{
            onClickRedo(){
                this.winNumbers = getWinNUmbers();
                this.winballs = [];
                this.bonus = null;
                this.redo = false;
            },
            showBalls(){
                for(let i = 0; i< this.winNumbers.length -1 ; i++){
                    timeouts.push(setTimeout(() => {
                        this.winballs.push(this.winNumbers[i]);
                    }, (i+1)*1000));
                }
                timeouts.push(setTimeout(() => {
                    this.bonus = this.winNumbers[this.winNumbers.length-1];
                    this.redo = true;
                }, 7000));
            }
        },

        mounted(){
            this.showBalls();
        },
        beforeDestroyed(){
            timeouts.forEach((i) => clearTimeout(i));
        },
        watch: {
            winballs(val, oldVal){
                if(val.length === 0){
                    this.showBalls();
                }
            }
        }
         
    };
</script>