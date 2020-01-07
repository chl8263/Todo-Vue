<template>
    <table>
        <tr-component :key="" v-for="(_, index) in tableData" :row-data="rowData" :row-index="index" ></tr-component>
    </table>
</template>

<script>
    import trComponent from './TrComponent';

    export default {
        props: {
            tableData: Array
        },
        component: {
            'tr-component': trComponent
        }   
    }
</script>