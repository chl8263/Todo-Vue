<template>
    <td @click="onClickTd">{{cellData}}</td>
</template>

<script>
    import EventBus from './EventBus';
    export default {
        props: {
            cellData: String,
            rowIndex: Number,
            cellIndex: Number
        },
        methods: {
            onClickTd(){
                this.$set(this.$root.$data.tableData[this.rowIndex],this.cellIndex, this.$root.$data.turn);
                this.$root.$data.turn = this.$root.$data.turn === 'o' ? 'x' : 'o';
                EventBus.$emit('clickTd');
            }
        }
    }
</script>