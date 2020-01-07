<template>    
    <div>
        <table-component :table-data="tableData"/>
        <div>Now {{turn}}</div>
    </div>
</template>
 
<script>
    import tableComponent from './TableComponent';
    import EventBus from './EventBus';
  
    export default {
        components: {
            'table-component': tableComponent
        },
        data(){
            return {
               tableData: [
                   [' ',' ',' '],
                   [' ',' ',' '],
                   [' ',' ',' ']
               ],
               turn: 'o'
            }
        },
        computed: {
        },
        methods:{
            onClickTd(){
                console.log('clickTd!');
            }
        },
        created(){
            EventBus.$on('clickTd', this.onClickTd);
        },
        mounted(){
        },
        beforeDestroyed(){
        },
    };
</script>

<style>
    table {
        border-collapse: collapse;
    }
    td {
        border: 1px solid black;
        width: 40px;
        height: 40px;
        text-align: center;
    }
</style>