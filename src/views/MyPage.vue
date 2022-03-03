<template>
    <div id="main">
        <Title v-if="this.show_title" :title="this.title" @add="addNew"/>
        <Button @title-check="titleCheck" :btn_text="this.btn_text" :btn_color="this.btn_color"/>
        <AllStuff :data="this.all_data" @delete-row="deleteRow" @change-row="changeRow"/>
    </div>
</template>

<script>
import Title from '../components/Title.vue';
import Button from '../components/Button.vue';
import AllStuff from '../components/AllStuff.vue';


//DATABASE
import AllData from '../database.json';


export default {
    components : {
        Title,
        Button,
        AllStuff,
    },

    data() {
        return {
            title : 'Unesi podatke',
            btn_text: 'Sakriji',
            btn_color: 'btn btn-success',
            show_title: false,
            all_data : '',
        }
    },


    methods: {
        titleCheck(){
            this.show_title = !this.show_title;

            if(this.btn_text === 'Prikaži'){
                this.btn_text = 'Sakriji';
                this.btn_color = 'btn btn-danger';
            }else{
                this.btn_text = 'Prikaži';
                this.btn_color = 'btn btn-success';
            }
        },

        database(){
            return AllData;
        },

        addNew(data) {
            this.all_data = [...this.all_data, data]
        },


        deleteRow(selectedRowId) {

            for(let i = 0; i < this.all_data.length; i++){
                if(this.all_data[i].id == selectedRowId){
                    console.log(this.all_data[i].first_name)
                    this.all_data.splice(i , 1)
                }
            }
        },

        changeRow(dataForChangeRow) {
            
            for(let i = 0; i < this.all_data.length; i++){
                if(this.all_data[i].id == dataForChangeRow.id){
                    this.all_data[i].first_name = dataForChangeRow.first_name;
                    this.all_data[i].message = dataForChangeRow.message;
                }
            }
        }

    },

    created() {
        this.all_data = this.database();
    },

}
</script>

<style scoped>
#main {
    height: auto;
    padding: 2rem;
    margin: auto;
    width: 90%;
    background-color: #f4f4f4f4;
}

</style>