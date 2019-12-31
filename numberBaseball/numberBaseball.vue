<template>
    <div>
        <h1> {{result}} </h1>
        <form v-on:submit="onSubmitForm()">
            <input type="number" ref="answer" maxlength="4" v-model="value"/>
            <button>Enter</button>
        </form>
        <div>count : {{}}</div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                value: '',
                resurt: ''
            }
        },
        methods:{
            onSubmitForm(e){
                e.preventDefault();
            }
        }
    };
</script>

<style>

</style>