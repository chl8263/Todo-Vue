<template>
    <div>
        <div id="computer" :style="computedStyleObject"></div>
        <div>
            <button @click="onclickButton('rock')">바위</button>
            <button @click="onclickButton('scissors')">가위</button>
            <button @click="onclickButton('paper')">보</button>
        </div>
        <div>{{result}}</div>
        <div>Present score {{score || 0}}</div>

        
    </div>
</template>
 
<script>
    const rspCoords = {
        rock: '0px',
        scissors: -'-142px',
        paper: '-284px'
    };
    let interval = 0;
    export default {
        data(){
           return {
               imgcode: '',
               result: '',
               score: '',
               imgcode: ''
           };
        },
        computed: {
            computedStyleObject(){
                return {
                    background: `url(https://en.pimg.jp/023/182/267/1/23182267.jpg) ${this.imgcode} 0` 
                }
                
            }
        },
        methods:{
          onclickButton(choice){

          }
        },
        created(){
            console.log("created");
        },
        mounted(){
            console.log("mounted"); 
            interval = setInterval(() => {
                if(this.imgcode === resCoords.rock){
                    this.resCoords = resCoords.scissors;
                }else if(this.imgcode === resCoords.scissors){
                    this.resCoords = resCoords.paper;
                }else if(this.imgcode === resCoords.paper){
                    this.resCoords = resCoords.rock;
                }
            }, 100);
        },
        updated(){
            console.log("updated"); 
        },
        beforeDestroy(){
            console.log("beforeDestroy");
            clearInterval(interval);
        },
        destroyed(){
            console.log("destroyed"); 
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