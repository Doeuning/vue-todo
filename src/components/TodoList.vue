<template>
    <div class="todo-list">
        <ul>
            <li v-for="(item, index) in propsdata" class="shadow">
                {{ item }}
                <button type="button" class="btn-del" @click="removeTodo(item, index)">X</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: [
        'propsdata'
    ],
    methods:{
        removeTodo(item, index){
            localStorage.removeItem(item);
            this.propsdata.splice(index,1);
        }
    }
}
</script>

<style>
    .todo-list { margin: 20px 0 0; }
    .todo-list ul { margin: 0; padding: 0; }
    .todo-list ul li { position: relative; overflow: hidden; margin: 10px 0 0; border-radius: 5px; padding: 0 20px; background: #ccc; line-height: 50px; text-align: left; list-style: none; }
    .todo-list ul li:first-child { margin: 0; }
    .todo-list ul li .btn-del { display: block; position: absolute; top: 0; right: 0; bottom: 0; width: 50px; border: none; background: #888888; font-weight: 700; font-style: 50px; color: #ffffff; outline: none; cursor: pointer; }
</style>

