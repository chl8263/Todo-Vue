<template>
    <tr>
        <td-component :key="" v-for="(celData, index) in rowData" :cell-data="cellData" :cell-index="cellIndex" :row-index="rowIndex"></td-component>
    </tr>
</template>

<script>
    import tdComponent from './TdComponent'

    export default {
        props: {
            rowData: Array,
            rowIndex: Number
        },
        component: {
            'td-component': tdComponent
        }
    }   
</script>