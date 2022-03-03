<template>
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
    name:'Add',

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
        
        let data = {
          name: this.name,
          message: this.message
        }

        this.$emit('add' , data);
      }
    }
}
</script>

<style>

</style>