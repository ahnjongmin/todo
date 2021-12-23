<template>
    <div>
        <!-- <button v-on:click="removetodoItem">erase everything</button> -->
        <span class="removeAllBtn" type="button" v-on:click="removetodoItem">
            <i class="fa fa-trash-o" aria-hidden="true"></i>
        </span>
    </div>

</template>

<script>
export default{
    components: {
            
    },
    methods: {
        removetodoItem(){
            console.log("todofooter");
            this.$emit('removetodoItem');
        },
    }
}
</script>

<style>
</style>