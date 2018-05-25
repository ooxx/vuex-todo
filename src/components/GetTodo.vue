<template>
    <div id="get-todo">
        <input class="form-control"
               :value="newTodo"
               @change="getTodo"
               placeholder="输入项目...">
        <button class="btn btn-primary" @click="addTodo">添加项目</button>
    </div>
</template>
<script>
    export default{
        methods: {
            getTodo(e){
                this.$store.dispatch('getTodo', e.target.value)
            },
            addTodo(){
                this.$store.dispatch('addTodo')
                this.$store.dispatch('clearTodo')
            }
        },
        computed: {
            newTodo(){
                return this.$store.getters.newTodo
            }
        }
    }
</script>

<style>
    #get-todo{
      margin-top: 15px;
    }
    .btn-primary{
      margin-top: 5px;
    }
</style>
