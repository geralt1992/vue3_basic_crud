<template>
    <td id="itemName">{{single.first_name}}</td>
    <td id="itemMessage">{{single.message}}</td>
    <td style="display:none;" id="itemId">{{single.id}}</td>
    <td><button @click="deleteRowLv2" class="btn buttonDelete">X</button></td>
    <td><button @click="changeRowLv2" class="btn buttonChange">X</button></td>
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

        changeRowLv2(e) {
            e.preventDefault();
            let clickedRow = e.target.parentNode.parentNode;
            let selectedRowId = clickedRow.querySelector('#itemId').innerText;
            let selectedRowName = clickedRow.querySelector('#itemName').innerText;
            let selectedRowMessage = clickedRow.querySelector('#itemMessage').innerText;

            let rowForChange = {
                id : selectedRowId,
                first_name : selectedRowName,
                message : selectedRowMessage
            }

            this.$emit('change-row2' , rowForChange);


    },

    },

    emits: ['delete-row2' , 'change-row2']

}
</script>


<style>

</style>