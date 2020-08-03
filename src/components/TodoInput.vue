<template>
    <div class="input-wrap shadow">
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" placeholder="할 일을 추가하세요.">
        <button type="button" class="btn-add" v-on:click="addTodo">+</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoItem: ''
        }
    },
    methods: {
        addTodo(){
            if (this.newTodoItem !== '') {
                var value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.claerInput();
            }
        },
        claerInput(){
            this.newTodoItem = '';
        }
    }
}
</script>

<style scoped>
    .input-wrap {
        overflow: hidden;
        position: relative;
        height: 50px;
        border-radius: 5px;
        background: #ffffff;
    }
    input {
        width: 100%;
        height: 50px;
        border: none;
    }
    input:focus {
        outline: none;
    }
    .btn-add {
        display: block;
        position: absolute;
        top: 0;
        right: 0;
        z-index: 10;
        width: 50px;
        height: 100%;
        border: none;
        background: linear-gradient(to right, #6478fb, #8763fb);
        font-weight: 700;
        font-size: 26px;
        color: #ffffff;
        outline: none;
        cursor: pointer;
    }
</style>

