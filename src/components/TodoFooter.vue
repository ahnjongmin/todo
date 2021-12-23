<template>
    <div>
        <button v-on:click="removetodoItem">erase everything</button>
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