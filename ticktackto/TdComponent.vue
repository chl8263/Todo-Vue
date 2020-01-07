<template>
    <td></td>
</template>

<script>
    export default {
        props: {
            cellData: String,
            rowIndex: Number,
            cellIndex: Number
        },
        methods: {
            onClickTd(){
                console.log(this.$root.$data);
            }
        }
    }
</script>