<template>
    <div class='inputBox Shadow'>

        <!-- <input type="text" v-model="newTodoItem"> -->
        <!-- <button v-on:click="addTodo">ADD</button> -->
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter='addTodo'>
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fa fa-plus" aria-hidden="true"></i>
        </span>
    </div>
</template>

<script>
export default{
    data() {
        return {
            newTodoItem: ' '  // data 를 function의 형태로 두는 이유가 뭐야?
        }
    },
    // data: {
    //     newTodoItem: ''
    // },
    methods: {
        addTodo() {
            if(this.newTodoItem !== "") {
                var value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.clearInput();
                console.log(`${this.newTodoItem}가 add되었습니다.`);
            }
        },
        clearInput() {
            this.newTodoItem='';
        }
    },
}
</script>

<style>
    input:focus {
        outline: none;
    }
    .inputBox {
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputbox input{
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer {
        float: right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display: inline-block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn {
        color: white;
        vertical-align: middle;
    }
</style>