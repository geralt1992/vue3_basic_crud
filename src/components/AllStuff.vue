<template>
    <table class="table">
        <thead>
            <tr>
                <th scope="col">Name</th>
                <th scope="col">Poruka</th>
                <th scope="col">Delete</th>
            </tr>
        </thead>
        <tbody>
        <tr v-for="single in this.data" :key="single.id">
                <SingleStuff :single="single"
                    @delete-row2="deleteRow1"
                />
        </tr>  
        </tbody>
    </table>
</template>



<script>
import SingleStuff from '../components/SingleStuff.vue';

export default {
    name:'AllStuff',

    components: {
        SingleStuff,
    },


    props: {
        data: Array
    },


    methods: {
        deleteRow1(selectedRowId) {
            this.$emit('delete-row' , selectedRowId);
        }
    },

    emits: ['delete-row']
}
</script>


<style>

</style>

