<template>
    
    <table-component :table-data="tabledata"/>
    
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
                   ['','',''],
                   ['','',''],
                   ['','','']
               ]
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