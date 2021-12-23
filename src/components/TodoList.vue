<template>
    <section>
        <div class="correction">
            <input type="text" v-model="changeTodoItem" placeholder="Change Value" v-on:keyup.enter='doit' v-if='flag'>
        </div>
        <ul>
            <li v-for="(todoItem, index) in propsdata" class="shadow">
                <i class="checkBtn fa fa-check" aria-hidden="true"></i>
                {{ todoItem }}
                <span class="changeBtn" type="button" v-on:click="changeTodo(todoItem, index)">
                    <i class="fa fa-trash-o" aria-hidden="true"></i>
                </span>
                <span class="removeBtn" type="button" v-on:click="removeTodo(todoItem, index)">
                    <i class="fa fa-trash-o" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>

<script>
export default{
    props: ['propsdata'],
    flagprops: ['flagprops'],
    data() {
        return {
            todoItems: [],
            changeTodoItem: '',
            flag : false,
            local_todoItem:[],
            local_index: '',
        }
    },

    beforeUpdate() {
        },

    methods: {
        removeTodo(todoItem, index) {
            console.log("removeTodo in TodoList.vue");
            this.$emit('removeTodo', todoItem, index);
            this.flag = false;
        },

        changeTodo(todoItem, index) {
            console.log("changeTodo in TodoList.vue");
            this.flag=true;
            this.local_todoItem = todoItem;
            this.local_index = index;
            this.changeTodoItem = todoItem;
        },
        doit(){
            this.flag=false;
            this.$emit('changeTodo', this.local_todoItem, this.changeTodoItem, this.local_index);
        }
    }

}
</script>

<style>
    ul {
        list-style-type: none;
        padding-left : 0px;
        margin-top : 0px;
        text-align : left;
    }
    li {
        display: flex;
        min-height : 50px;
        height : 50px;
        line-height : 50px;
        margin : 0.5rem 0;
        padding : 0 0.9rem;
        background : white;
        border-radius: 5px;
    }
    .checkBtn {
        line-height : 45px;
        color : #62acde;
        margin-right: 5px;
    }
    .removeBtn {
        margin-left : auto;
        color : #de4343;
    }
    .changeBtn {
        margin-left : auto;
        color : #de4343;
    }
</style>