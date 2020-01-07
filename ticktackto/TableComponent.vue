<template>
    <table>
        <tr-component :key="index" v-for="(_, index) in tableData" :row-data="_" :row-index="index"/>
    </table>
</template>

<script>
    import trComponent from './TrComponent';

    export default {
        props: {
            tableData: Array
        },
        components: {
            'tr-component': trComponent
        },
        mounted(){
        }
    }
</script>

