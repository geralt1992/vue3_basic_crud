<template>
    <div id="main">
        <Title v-show="this.show_title" :title="this.title"/>
        <Button @title-check="titleCheck" :btn_text="this.btn_text"/>
        <Button :btn_text="this.btn_text2"/> 
        <router-link to="/" ><button class="btn">d</button></router-link>
        <AllStuff :data="this.all_data" @delete-row="deleteRow"/>
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
            title : 'Moj Vue App',
            btn_text: 'Show',
            btn_text2: 'Add',
            show_title: false,
            all_data : '',
        }
    },

    methods: {
        titleCheck(){
            this.show_title = !this.show_title;
        },

        database(){
            return AllData;
        },

        deleteRow(selectedRowId) {
            console.log(selectedRowId + ' zadnji level');
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