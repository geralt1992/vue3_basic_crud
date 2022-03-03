<template>

<!--ZA IZMJENU -->
    <table class="table" v-if="show_change">
        <thead>
            <tr>
                <th>
                    <form>
                        <div class="row">
                            <div class="col">
                            <input v-model="new_firstName" type="text" class="form-control" :placeholder="this.old_firstName">
                            </div>
                            <div class="col">
                            <input v-model="new_message" type="text" class="form-control" :placeholder="this.old_message">
                            </div>

                            <div class="nešto">
                                <button @click="changeRow" type="submit" class=" btn-warning" style="color:white">Izmijeni</button>
                            </div>
                        </div>
                    </form>
                </th>
            </tr>
        </thead>
    </table>




<!--ZA PRIKAZ -->
    <table class="table">
        <thead>
            <tr>
                <th scope="col">Name</th>
                <th scope="col">Poruka</th>
                <th scope="col">Delete</th>
                <th scope="col">Change</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="single in this.data" :key="single.id">
                    <SingleStuff :single="single"
                        @delete-row2="deleteRow1"
                        @change-row2="changeRow1ShowInput"
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

    data() {
        return {
            show_change: false,
            old_id: '',
            old_firstName: '',
            old_message: '',
            new_firstName: '',
            new_message: ''
        }
    },


    methods: {
        deleteRow1(selectedRowId) {
            this.$emit('delete-row' , selectedRowId);
        },

        changeRow1ShowInput(rowForChange) {
            this.show_change = true;
            this.old_id = rowForChange.id;
            this.old_firstName = rowForChange.first_name;
            this.old_message = rowForChange.message;
        },

        changeRow(e) {
            e.preventDefault();
            
            let dataForChangeRow = {
                id: this.old_id,
                first_name: this.new_firstName,
                message: this.new_message
            }
            console.log(dataForChangeRow)
            this.$emit('change-row' , dataForChangeRow);
            }

    },

    emits: ['delete-row' , 'change-row']
}
</script>


<style>

</style>

