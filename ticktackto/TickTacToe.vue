<template>    
    <table-component :table-data="tableData"/>
</template>
 
<script>
    import tableComponent from './TableComponent';
  
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