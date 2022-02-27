<template>
    <td>{{single.first_name}}</td>
    <td>{{single.message}}</td>
    <td style="display:none;" id="itemId">{{single.id}}</td>
    <td><button @click="deleteRowLv2" class="btn buttonDelete">X</button></td>
</template>

<script>
export default {
    name:'SingleStuff',

    props: {
        single: Object
    },

    methods: {
        deleteRowLv2(e) {
            e.preventDefault();
            let clickedRow = e.target.parentNode.parentNode;
            let selectedRowId = clickedRow.querySelector('#itemId').innerText;

            this.$emit('delete-row2' , selectedRowId);
    },
    },

    emits: ['delete-row2']

}
</script>


<style>

</style>