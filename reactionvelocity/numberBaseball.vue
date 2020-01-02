<template>
    <div>
        <h1> {{result}} </h1>
        <form @submit.prevent="onSubmitForm">
            <input type="number" ref="answer" minlength="4" maxlength="4" v-model="value"/>
            <button type="submit">Enter</button>
        </form>
        <div>count : {{tries.length}}</div>
        <div>status : {{result}}</div>
        <ul>
            <li v-for="t in tries">
                <div>{{t.try}}</div>
                <div>{{t.result}}</div>
            </li>
        </ul>
    </div>
</template>

<script>
    const getNumber = (count) => {
        const arr = [];
        for(let i = 0 ; i < count; i++){
            arr.push(Math.ceil(Math.random() * 9));
        }
        return arr;
    }
    
    export default {
        data(){
            return{
                answer: getNumber(4),
                tries: [],
                value: '',
                result: ''
            }
        },
        methods:{
            onSubmitForm(e){
                //e.preventDefault();
                if(this.value === this.answer.join('')){
                    this.tries.push({
                        try: this.value,
                        result: 'Homerun'
                    });
                    this.result = "Homerun!";
                    this.value = "";
                    this.count = "";
                    this.$refs.answer.focus();
                }else {
                    const strike = 0;
                    const ball = 0;
                    const answerArr = this.value.split('').map((v) => parseInt(v));
                    
                }
            }
        }
    };
</script>

<style>

</style>