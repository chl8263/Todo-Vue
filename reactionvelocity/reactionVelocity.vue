<template>
    <div>
        <div id="screen" :class="state" @click="onClickScreen">{{message}} ms</div>
        <template v-if="result.length">
            <div> average time: {{average}} </div>
            <button @click="onReset">Reset</button>
        </template>
    </div>
</template>
 
<script>
    let startTime = 0;
    let endTime = 0;
    let timeOut = null;
    export default {
        data(){
            return{
               result: [],
               state: 'waiting',
               message: 'Click to Start'
            }
        },
        computed: {
            average(){
                return this.result.reduce((a,c) => a+c ,0) / this.result.length || 0
            }
        },
        methods:{
          onReset(){
            this.result = [];
          },
          onClickScreen(){
              if(this.state === "waiting"){
                this.state = "ready";
                this.message = "Click if color greeen"
                timeOut = setTimeout(() => {
                    this.state = "now";
                    this.message = "click";
                    startTime = new Date();
                }, Math.floor(Math.random()* 1000) + 2000);
              }else if(this.state === "ready"){
                clearTimeout(timeOut);
                this.state = "waiting";
                this.message = "Not now...."
              }else if(this.state === "now"){
                endTime = new Date();
                this.state = "waiting";
                this.message = "Click to start"
                this.result.push(endTime - startTime);
              }
          }
        }
    };
</script>

<style scoped>
    #screen {
        width: 300px;
        height: 200px;
        text-align: center;
        user-select: none;
    }
    #screen.waiting {
        background-color: aqua;
    }
    #screen.ready {
        background-color: red;
    }
    #screen.now {
        background-color: greenyellow;
    }
</style>