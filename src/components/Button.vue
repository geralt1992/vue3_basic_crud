<template>
    <button @click="titleFunction"
    :class="{btn_color}" >{{btn_text}}</button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        btn_text : String,
        btn_color : String,
    },

    data() {
        return {
            btn: ' btn-danger'
        }
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