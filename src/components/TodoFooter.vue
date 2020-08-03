<template>
    <div class="claer-all">
        <button type="button" class="btn-clear shadow" v-on:click="removeAllTrg">Clear All</button>
    </div>
</template>

<script>
export default {
    methods: {
        removeAllTrg(){
            this.$emit('removeAll');
        }
    },
}
</script>

<style>
    .claer-all {margin: 20px 0 0;}
    .claer-all .btn-clear {display: block; height: 50px; width: 100%; border: none; border-radius: 5px; outline: none; cursor: pointer;}
</style>

