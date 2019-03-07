<template>
    <b-button id='btn' class='btn' v-on:click="prueba">EPICIDAD {{count}}</b-button>
</template>

<script>
export default {
    name: 'Button',
    data () {
        return {
            count: 0
        }
    },
     methods: {
        prueba: function(event) {
            this.count++
            document.getElementById('btn').style.color = 'blue'
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

