<template>
    <div id="current-todos">
        <h3 v-if="todos.length > 0">当前项目({{todos.length}})</h3>
        <ul class="list-group">
            <li class="list-group-item" v-for="todo in todos">
                {{todo.body}}
                <div class="btn-group">
                    <button type="button" @click="edit(todo)" class="btn btn-default btn-sm">
                    <span class="glyphicon glyphicon-edit"></span> 编辑
                    </button>
                    <button type="button" @click="complete(todo)" class="btn btn-default btn-sm">
                    <span class="glyphicon glyphicon-ok-circle"></span> 完成
                    </button>
                    <button type="button" @click="remove(todo)" class="btn btn-default btn-sm">
                    <span class="glyphicon glyphicon-remove-circle"></span> 删除
                    </button>
                </div>
            </li>
        </ul>
    </div>
</template>
<script>
export default{
    methods: {
        edit(todo){
            this.$store.dispatch('editTodo', todo)
        },
        complete(todo){
            this.$store.dispatch('completeTodo', todo)
        },
        remove(todo){
            this.$store.dispatch('removeTodo', todo)
        }
    },
    computed: {
        todos(){
            return this.$store.getters.todos
        }
    }
}
</script>
<style>
    .btn-group{
        float: right;
    }
    h3{
      margin:15px 0;
    }
</style>
