<template>
    <button @click="titleFunction"
    class="btn btn-danger" >{{btn_text}}</button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        btn_text : String,
    },

    methods: {
        titleFunction(e) {
            e.preventDefault();
            this.$emit('title-check');
        }
    },

    emits: ['title-check']
}
</script>

<style>
    button{
        margin: 1.5rem;
    }
</style>