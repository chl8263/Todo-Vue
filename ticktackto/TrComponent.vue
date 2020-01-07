<template>
    <tr>
        <td-component :key="index" v-for="(celData, index) in rowData" :cell-data="celData" :cell-index="index" :row-index="rowIndex"></td-component>
    </tr>
</template>

<script>
    import tdComponent from './TdComponent'

    export default {
        props: {
            rowData: Array,
            rowIndex: Number
        },
        components: {
            'td-component': tdComponent
        },
        data(){
            return {
                parent: "trtrtrtrt"
            }
        },
        mounted(){
        }
    }   
</script>