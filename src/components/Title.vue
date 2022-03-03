<template>
    <h1>{{title}}</h1>

    <form>
        <div class="form-group">
            <label for="exampleInputEmail1">Ime</label>
            <input  v-model="this.name" type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter name">
        </div>
        <div class="form-group mt-3">
            <label for="exampleInputPassword1">Poruka</label>
            <input v-model="this.message" type="text" class="form-control" id="exampleInputPassword1" placeholder="Poruka">
        </div>
        <button @click="sendData" type="submit" class="btn btn-success">Pošalji</button>
    </form>
</template>

<script>
export default {
    name: 'Title',
    props: {
        title: String,
    },

    emits: ['add'],


    data() {
    return {
        name: '',
        message: ''
    }
    },

    methods: {
    sendData(e) {
        e.preventDefault();
        let idNum = Math.floor(Math.random() * 10000000)
        
        let data = {
        id: idNum,
        first_name: this.name,
        message: this.message
        }

        this.$emit('add' , data);
    }
    }
}
</script>

<style scoped>
    h1 {
        color: black;
        text-transform: uppercase;
    }


</style>