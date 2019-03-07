<template>
    <b-button id='btn' class='btn' v-on:click="other">CLICK</b-button>
</template>

<script>
export default {
    name: 'Button',
    data () {
        return {
            
        }
    },
     methods: {
        other: function(event) {
            window.location.href = 'https://github.com/';
        }
    }
}
</script>

<style scoped>
    .btn {
        color: orange;
        background-color: black;
    }
</style>